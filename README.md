pybencode
=========

Simple bencode implementation in python.

This is only meant as a simple and readable implementation of bencoding. No
optimization is made so it really should not be used in production.

The module is tested in python 2.7. Plans for python3 is on the way but
currently it will not work in python3.

Usage
-----

assuming

```python
from bencode import encode, decode
```

you can do the following:

Encoding

```python
assert encode("Hello") == "5:Hello"
assert encode(23) == "i23e"
assert encode([1, 2, 3]) == "li1ei2ei3ee"
assert encode(dict(str="Hello", list=[1, 2, 3])) == \
	'd4:listli1ei2ei3ee3:str5:Helloe'
```

Decoding:

```python
assert decode(bytes("5:Hello")) == "Hello"
assert decode(bytes("i23e")) == 23
assert decode(bytes("li1ei2ei3ee")) == [1, 2, 3]
assert decode(bytes("d4:listli1ei2ei3ee3:str5:Helloe")) == \
    dict(str="Hello", list=[1, 2, 3])
```
