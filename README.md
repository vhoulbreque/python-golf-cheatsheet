# python-golf-cheatsheet

This is a golf cheatsheet that lists techniques to reduce the number of chars in Python code.

# INTEGERS

## Check if a number is a power of 2

```python
n&~-n  # zero for powers of 2, non-zero for others
# or
n&~-n<1
# or
n&-n-n  # zero for powers of 2, non-zero for others
# or
n&-n==n
```

instead of

```python
(n & (n-1) == 0) and n != 0
# or
import math;math.log(n, 2).is_integer()
# or
bin(num).count("1") == 1
```

## Check if a number is a power of q

```python
q**n%n  # zero for powers of q, non-zero for others
# or
q**n%n<1
```

instead of

```python
import math;math.log(n, q).is_integer()
```

# STRINGS

## Generate the entire alphabet

```python
map(chr,range(65,91))
# ABCDEFGHIJKLMNOPQRSTUVWXYZ

map(chr,range(97,123))
# abcdefghijklmnopqrstuvwxyz
```

instead of:

```python
"ABCDEFGHIJKLMNOPQRSTUVWXYZ"
"abcdefghijklmnopqrstuvwxyz"
[chr(i+97)for i in range(26)]
```

## Extended slicing

```python
for i in 0,1,2:
    print("fbboaaorz"[i::3])
# foo
# bar
# baz
```

instead of:

```python
for i in 0,1,2:
    if i == 0:
        print("foo")
    elif i == 1:
        print("bar")
    else:
        print("baz")
```

It works with strings that are the same size (+- 1 char).
For `True` and `False`, see:

```python
print("FTarlusee"[condition::2])
# False (if condition is False)
# True (if condition is True)
```

# ITERABLES

## Get the last element of a list

```python
L=[1,3,4,8]
*_,a=L
# a = 8
```

instead of:

```python
L=[1,3,4,8]
a=L[-1]
# a = 8
```

## Get an element from the back of a list

```python
L=[1,2,3,4,5]
i=2
a=L[~i]  # 3
```

instead of

```python
L=[1,2,3,4,5]
i=2
a=L[-i-1]  # 3
```

**Explanation**: `~` is the bitwise inversion, leading to `~i` being equal to `-i-1`.

## Add an element to a list

```python
L=[1,2,3,4,5]
a=6
L+=a,
```

instead of

```python
L=[1,2,3,4,5]
a=6
L+=[a]
# or
L.append(a)
```

## Add 2 lists together

```python
L=[1,2,3]
M=[4,5,6]
L+=M
```

instead of

```python
L=[1,2,3]
M=[4,5,6]
L.extend(M)
```

# LOOPS

## Merge 2 for loops together

```python
for i in range(m*n):
    print(i//n, i%n)
```

instead of

```python
for i in range(m):
    for j in range(n):
        print(i, j)
```

## Merge 3 for loops together

```python
for i in range(m*n*o):
    print(i//n//o, i%(n*o)//o, i%o)
```

instead of

```python
for i in range(m):
    for j in range(n):
        for k in range(o):
            print(i, j, k)
```

# CONDITIONS

## Ternary operation

```python
s = [a, b][condition]
```

instead of:

```python
s = b if condition else a
```

**CAVEAT:**
`condition` must be `True`, `False`, `0` or `1`. Being "truthy"/"untruthy" is not sufficient.

# MISC

## Instantiate several variables

```python
a=b=c=d=0
e,f=1,2
```

instead of:

```python
a = 0
b = 0
c = 0
d = 0
e = 1
f = 2
```

**CAVEAT:** `a=b=c=d=[]` does not work with lists. Indeed:

```python
a=b=c=d=[]
a.append(1)
print(a, b, c, d)  # [1] [1] [1] [1]
```