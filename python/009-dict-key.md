---
id: 009-dict-key.md
title: Python dict.key vs dict[key]
tags:
  - python
  - dict
  - dictionaries
  - dict-keys
author: Zoran Pandovski
meta-description: Difference between python's dict.key and dict[key] explained with examples
date: 2020-06-05 21:13:49 +0200
keywords: python, dict, dictionaries, dict-keys
template: post
categories:
  - python
cover: ../../images/categories/python.png
---

To get the value from the dictionary the most pythonic way would be to use the square brackets `[ ]` e.g

```python
# note that dict keys are case-sensitive
capitals = {
    'usa' : 'washinghton',
    'england' : 'london',
    'france' : 'paris'
}
capitals['usa']
>>>'washinghton'
```

Also, you can use the `get` method e.g

```python
capitals = {
    'usa' : 'washinghton',
    'england' : 'london',
    'france' : 'paris'
}
capitals.get('usa')
>>>'washinghton'
```
So, in both examples we got the same response 'washinghton'. The question now is what is the difference between this two examples? Let's try
another example, using the key that isn't in the capitals dict:

```python
capitals = {
    'usa' : 'washinghton',
    'england' : 'london',
    'france' : 'paris'
}
capitals['spain']
>>> KeyError: 'spain'
```

We got the [KeyError](https://docs.python.org/3/library/exceptions.html#KeyError), which is quite expected because we know that the 'spain' key is not avaiable in the dictionary. Let's try with `get` method now:


```python
capitals = {
    'usa' : 'washinghton',
    'england' : 'london',
    'france' : 'paris'
}
capitals.get('germany')
>>>
```

We didn't get any Error back, just the empty value. That is the difference between using `get method` and `square brackets`. The dict[key] will always throw KeyError when the key is not found. The [`get method`](https://docs.python.org/3/library/stdtypes.html#dict.get) accepts additonal parameter `dict.get(key, [default])` which returnes the default value in case the key is not found. In our case we didn't specify value so it was setup as None. 