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
