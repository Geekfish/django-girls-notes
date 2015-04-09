Unicode
=======

I get `UnicodeEncodeError` what am I doing wrong?!
--------------------------------------------------
When you put such special characters in your code, such as characters with accents, letters from non-latin alphabets etc, you need to use something called Unicode (sometimes also refered to as utf-8, which is a related thing).
If you use python3 then all strings are unicode. If you use an older version of python then you need to explicitly use unicode strings. Example:
in python 3.4

```python
>>> a_string = “I am a unicode string with Greek - καλημέρα!”

in python 2.7
```python
a_string = u“I am a unicode string with Greek - καλημέρα!”
```

Back to python 3 then:
```python
>>> a_string = “I am a unicode string with Greek - καλημέρα!”
a_string.encode('ascii’)
#Traceback (most recent call last):
# File "<stdin>", line 1, in <module>
# UnicodeEncodeError: 'ascii' codec can't encode characters in position 35-42: ordinal # not in range(128)
>>> a_string.encode('utf-8')
b'I am a unicode string with Greek - \xce\xba\xce\xb1\xce\xbb\xce\xb7\xce\xbc\xce\xad\xcf\x81\xce\xb1!’
```
As you can see the first statement returns an error, but the second one works (but it returns some weird text!).

What does this all mean?
------------------------

Todo
