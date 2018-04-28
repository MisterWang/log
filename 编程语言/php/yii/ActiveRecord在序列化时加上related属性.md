---
title: ActiveRecord在序列化时加上related属性
categories: 
- php
- yii
tags:
- php
layout: post
---

实现JsonSerializable接口
```php
class MyRecord extends ActiveRecord implements JsonSerializable{
  public function jsonSerialize(){
      $array=$this->getAttributes($this->fields());
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
* Arrayable
* SimpleXMLElement
* Iterator

中，JsonSerializable只需实现一个方法...或者重写ArrayableTrait的toArray方法？

结论还是实现JsonSerializable简单...
