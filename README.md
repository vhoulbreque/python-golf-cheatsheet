# python-golf-cheatsheet

This is a golf cheatsheet that lists techniques to reduce the number of chars in Python code.

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
```# python-golf-cheatsheet

This is a golf cheatsheet that lists techniques to reduce the number of chars.

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