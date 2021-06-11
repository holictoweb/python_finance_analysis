

- get value by key
```pyton
>>> a = {'name':'pey', 'phone':'0119993323', 'birth': '1118'}
>>> print(a.get('nokey'))
None
>>> print(a['nokey'])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'nokey'

# key 값이 존재 하는지 확인
>>> a = {'name':'pey', 'phone':'0119993323', 'birth': '1118'}
>>> 'name' in a
True
>>> 'email' in a
False

```

- insert, delete
```python
a[key] = value

del a[key]
```


- looping dictionary
```python
for value in a_dict.values():
  print(value)

for key in a_dict.keys():
  print(value)

# item -> key value loop
prices = {'apple': 0.40, 'orange': 0.35, 'banana': 0.25}
for k, v in prices.items():
  prices[k] = round(v * 0.9, 2)  # Apply a 10% discount
>>> prices
{'apple': 0.36, 'orange': 0.32, 'banana': 0.23}
 
```

- dict 안에서 find
```python
>>> a_dict = {'color': 'blue', 'fruit': 'apple', 'pet': 'dog'}
>>> 'pet' in a_dict.keys()
True
>>> 'apple' in a_dict.values()
True
>>> 'onion' in a_dict.values()
False
```

- sort dict
```python
# value 기준 sort
x = {1: 2, 3: 4, 4: 3, 2: 1, 0: 0}
{k: v for k, v in sorted(x.items(), key=lambda item: item[1])}
{0: 0, 2: 1, 1: 2, 4: 3, 3: 4}


#############################
orders = {
	'cappuccino': 54,
	'latte': 56,
	'espresso': 72,
	'americano': 48,
	'cortado': 41
}

# value 기준 asc
sort_orders = sorted(orders.items(), key=lambda x: x[1])

for i in sort_orders:
	print(i[0], i[1])

# value 기준 desc
sort_orders = sorted(orders.items(), key=lambda x: x[1], reverse=True)

for i in sort_orders:
	print(i[0], i[1])

# key도 동일하게 적용 가능하지만 기본적으로 sorted 함수를 사용하면 key 기준으로 sort
sort_orders = sorted(orders.items())

for i in sort_orders:
	print(i[0], i[1])


```



- example

```python
my_list = ["one", 2, 3, 2, "one"]


new_list = {}
for each_key in my_list:
  new_list[each_key]=my_list.count(each_key)
return new_list

```
