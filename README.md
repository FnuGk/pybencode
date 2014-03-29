pybencode
=========

Simple bencode implementation in python.
________________________________________

This is only meant as a simple and readable implementation of bencoding. No
optimization is made.

Usage
-----

assuming

```python
from benched import encode, decode
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
assert decode(bytearray("5:Hello", "utf-8")) == "Hello"
assert decode(bytearray("i23e", "utf-8")) == 23
assert decode(bytearray("li1ei2ei3ee", "utf-8")) == [1, 2, 3]
assert decode(bytearray("d4:listli1ei2ei3ee3:str5:Helloe", "utf-8")) == \
	dict(str="Hello", list=[1, 2, 3])
```
