实现JsonSerializable接口
```php
class MyRecord extends ActivityRecord implements JsonSerializable{
  public function jsonSerialize(){
      $array=$this->getAttributes();
      $relate=$this->getRelatedRecords();
      return $array+$relate;  
 }
}
```

yii\helpers\BaseJosn obj的预处理
```php
if (is_object($data)) {
  if ($data instanceof JsExpression) {
      $token = "!{[$expPrefix=" . count($expressions) . ']}!';
      $expressions['"' . $token . '"'] = $data->expression;

      return $token;
  } elseif ($data instanceof \JsonSerializable) {
      return static::processData($data->jsonSerialize(), $expressions, $expPrefix);
  } elseif ($data instanceof Arrayable) {
      $data = $data->toArray();
  } elseif ($data instanceof \SimpleXMLElement) {
      $data = (array) $data;
  } else {
      $result = [];
      foreach ($data as $name => $value) {
          $result[$name] = $value;
      }
      $data = $result;
  }

  if ($data === []) {
      return new \stdClass();
  }
}
```
在接口
* JsExpression
* JsonSerializable
* SimpleXMLElement
* Iterator
中，JsonSerializable只需实现一个方法...
