

```python
#1.match 
import re

a = re.compile(r'match')
b = 'matchsongzhiruimatchyingmathehmatch'
bb = 'qmatchsongzhiruimatchyingmathehmatch'

c = re.match(a,b)
cc = re.match(a,bb)

#返回的结果是一个match对象，需要调用group获取返回值。如有多个返回值，添加具体的索引即可获取到对应的值。
print(c)
c.group()
print(cc)#由于开头是Q所以返回值为None。

#macth 从字符串的首字母开始匹配；区别于search。match和search 都是返回一个match对象。


```

    <_sre.SRE_Match object; span=(0, 5), match='match'>
    None





    'match'




```python
#2.search
#如果string中存在多个pattern子串，只返回第一个。
d=re.search(a,b)
d.group()
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-16-e85500f91a0f> in <module>()
          2 #如果string中存在多个pattern子串，只返回第一个。
          3 d=re.search(a,b)
    ----> 4 d.group(2)
    

    IndexError: no such group



```python
#3.findall
#返回string中所有与pattern相匹配的全部字串，返回形式为list。如果返回的结果多余一个则以元祖的形式返回，组成数组。
f=re.findall(a,bb)
f
```




    ['match', 'match', 'match']




```python
#4.finditer
#与findall一样，只是返回值为一个迭代器。
ff=re.finditer(a,bb)
print(type(ff))
#ff.next().group() python3中的可迭代对象已经没有next()属性了。
for i in ff:
    print(type(i))
    print(i.group())
```

    <class 'callable_iterator'>
    <class '_sre.SRE_Match'>
    match
    <class '_sre.SRE_Match'>
    match
    <class '_sre.SRE_Match'>
    match



```python

```
