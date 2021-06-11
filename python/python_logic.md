## list 기본 연산
```python


# index 삽입 (index i에 x 값 삽입)
s.insert(i, x)
# index 삭제
s.pop([i]) # 값 return
del.s[i] 
del.s[i:j]

# x 값을 가진 첫번째 삭제 
s.remove(x)

# range
>>> list(range(0, -10, -1))
[0, -1, -2, -3, -4, -5, -6, -7, -8, -9]
```

## string



- 중복 제거
```python
my_list = ['A', 'B', 'C', 'D', 'B', 'D', 'E']
my_set = set(my_list) #집합set으로 변환
my_list = list(my_set) #list로 변환
print(new_list)

['D', 'B', 'A', 'E', 'C']

my_list = ['A', 'B', 'C', 'D', 'B', 'D', 'E']
new_list = []
for v in my_list:
    if v not in new_list:
        new_list.append(v)
print(new_list)

['A', 'B', 'C', 'D', 'E']
```


- 문자열 문자 제거
```python

```


