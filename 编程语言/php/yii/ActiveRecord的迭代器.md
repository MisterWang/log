---
title: ActiveRecord的迭代器
categories: 
- php
- yii
tags:
- php
layout: post
---

实现接口

```php
class Model extends Component implements StaticInstanceInterface, IteratorAggregate, ArrayAccess, Arrayable

```

实现IteratorAggregate接口

```php
/**
 * Returns an iterator for traversing the attributes in the model.
 * This method is required by the interface [[\IteratorAggregate]].
 * @return ArrayIterator an iterator for traversing the items in the list.
 */
public function getIterator()
{
    $attributes = $this->getAttributes();
    return new ArrayIterator($attributes);
}
```
