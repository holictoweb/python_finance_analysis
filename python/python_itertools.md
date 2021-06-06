


## 조합형 이터레이터

| 이터레이터                                                   | 인자               | 결과                                                         |
| :----------------------------------------------------------- | :----------------- | :----------------------------------------------------------- |
| [`product()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.product) | p, q, … [repeat=1] | 데카르트 곱(cartesian product), 중첩된 for 루프와 동등합니다 |
| [`permutations()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.permutations) | p[, r]             | r-길이 튜플들, 모든 가능한 순서, 반복되는 요소 없음          |
| [`combinations()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.combinations) | p, r               | r-길이 튜플들, 정렬된 순서, 반복되는 요소 없음               |
| [`combinations_with_replacement()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.combinations_with_replacement) | p, r               | r-길이 튜플들, 정렬된 순서, 반복되는 요소 있음               |

| 예                                         | 결과                                              |
| :----------------------------------------- | :------------------------------------------------ |
| `product('ABCD', repeat=2)`                | `AA AB AC AD BA BB BC BD CA CB CC CD DA DB DC DD` |
| `permutations('ABCD', 2)`                  | `AB AC AD BA BC BD CA CB CD DA DB DC`             |
| `combinations('ABCD', 2)`                  | `AB AC AD BC BD CD`                               |
| `combinations_with_replacement('ABCD', 2)` | `AA AB AC AD BB BC BD CC CD DD`                   |





**가장 짧은 입력 시퀀스에서 종료되는 이터레이터:**

| 이터레이터                                                   | 인자                        | 결과                                                         | 예                                                         |
| :----------------------------------------------------------- | :-------------------------- | :----------------------------------------------------------- | :--------------------------------------------------------- |
| [`accumulate()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.accumulate) | p [,func]                   | p0, p0+p1, p0+p1+p2, …                                       | `accumulate([1,2,3,4,5]) --> 1 3 6 10 15`                  |
| [`chain()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.chain) | p, q, …                     | p0, p1, … plast, q0, q1, …                                   | `chain('ABC', 'DEF') --> A B C D E F`                      |
| [`chain.from_iterable()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.chain.from_iterable) | iterable                    | p0, p1, … plast, q0, q1, …                                   | `chain.from_iterable(['ABC', 'DEF']) --> A B C D E F`      |
| [`compress()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.compress) | data, selectors             | (d[0] if s[0]), (d[1] if s[1]), …                            | `compress('ABCDEF', [1,0,1,0,1,1]) --> A C E F`            |
| [`dropwhile()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.dropwhile) | pred, seq                   | seq[n], seq[n+1], pred가 실패할 때 시작                      | `dropwhile(lambda x: x<5, [1,4,6,4,1]) --> 6 4 1`          |
| [`filterfalse()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.filterfalse) | pred, seq                   | pred(elem)이 거짓인 seq의 요소들                             | `filterfalse(lambda x: x%2, range(10)) --> 0 2 4 6 8`      |
| [`groupby()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.groupby) | iterable[, key]             | key(v)의 값으로 그룹화된 서브 이터레이터들                   |                                                            |
| [`islice()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.islice) | seq, [start,] stop [, step] | seq[start:stop:step]의 요소들                                | `islice('ABCDEFG', 2, None) --> C D E F G`                 |
| [`starmap()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.starmap) | func, seq                   | func(*seq[0]), func(*seq[1]), …                              | `starmap(pow, [(2,5), (3,2), (10,3)]) --> 32 9 1000`       |
| [`takewhile()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.takewhile) | pred, seq                   | seq[0], seq[1], pred가 실패할 때까지                         | `takewhile(lambda x: x<5, [1,4,6,4,1]) --> 1 4`            |
| [`tee()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.tee) | it, n                       | it1, it2, … itn 하나의 이터레이터를 n개의 이터레이터로 나눕니다 |                                                            |
| [`zip_longest()`](https://docs.python.org/ko/3.8/library/itertools.html#itertools.zip_longest) | p, q, …                     | (p[0], q[0]), (p[1], q[1]), …                                | `zip_longest('ABCD', 'xy', fillvalue='-') --> Ax By C- D-` |







## groupby

```phthon
groups = []
uniquekeys = []
data = sorted(data, key=keyfunc)
for k, g in groupby(data, keyfunc):
    groups.append(list(g))      # Store group iterator as a list
    uniquekeys.append(k)
```

```
class groupby:
    # [k for k, g in groupby('AAAABBBCCDAABBB')] --> A B C D A B
    # [list(g) for k, g in groupby('AAAABBBCCD')] --> AAAA BBB CC D
    def __init__(self, iterable, key=None):
        if key is None:
            key = lambda x: x
        self.keyfunc = key
        self.it = iter(iterable)
        self.tgtkey = self.currkey = self.currvalue = object()
    def __iter__(self):
        return self
    def __next__(self):
        self.id = object()
        while self.currkey == self.tgtkey:
            self.currvalue = next(self.it)    # Exit on StopIteration
            self.currkey = self.keyfunc(self.currvalue)
        self.tgtkey = self.currkey
        return (self.currkey, self._grouper(self.tgtkey, self.id))
    def _grouper(self, tgtkey, id):
        while self.id is id and self.currkey == tgtkey:
            yield self.currvalue
            try:
                self.currvalue = next(self.it)
            except StopIteration:
                return
            self.currkey = self.keyfunc(self.currvalue)
```
