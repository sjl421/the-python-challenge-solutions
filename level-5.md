# Python Challenge - Level 5

- Link: http://www.pythonchallenge.com/pc/def/peak.html

## Problem


![](src/level_05/peakhell.jpg)

> pronounce it 

Page Source:

```html
<peakhell src="banner.p"/>
<!-- peak hell sounds familiar ? -->
```

*peakhell*, *peakhell*... sounds like... "pickle"(which is Python's object serialization module)

## Solution

Let's print out the raw data:

```python
>>> from urllib.request import urlopen
>>> raw = urlopen("http://www.pythonchallenge.com/pc/def/banner.p").read()
>>> raw
b"(lp0\n(lp1\n(S' '\np2\nI95\ntp3\naa..."
```

Normally plain text can be encoded as utf-8 or some other form, once we call ``.decode()`` it will reveal it self, 
however this one is tough:

```python
>>> raw.decode()
"(lp0\n(lp1\n(S' '\np2\nI95\ntp3\naa..."
```

As hinted, let's use pickle to deserialize it:

```python
>>> import pickle
>>> data = pickle.load(urlopen("http://www.pythonchallenge.com/pc/def/banner.p"))
>>> data
[[(' ', 95)], [(' ', 14), ('#', 5), (' ', 70), ('#', 5), (' ', 1)], [(' ', 15), ('#', 4), (' ', 71), ('#', 4), (' ', 1)], [(' ', 15), ('#', 4), (' ', 71), ('#', 4), (' ', 1)], [(' ', 15), ('#', 4), (' ', 71), ('#', 4), (' ', 1)], [(' ', 15), ('#', 4), (' ', 71), ('#', 4), (' ', 1)], [(' ', 15), ('#', 4), (' ', 71), ('#', 4), (' ', 1)], [(' ', 15), ('#', 4), (' ', 71), ('#', 4), (' ', 1)], [(' ', 15), ('#', 4), (' ', 71), ('#', 4), (' ', 1)], [(' ', 6), ('#', 3), (' ', 6), ('#', 4), (' ', 3), ('#', 3), (' ', 9), ('#', 3), (' ', 7), ('#', 5), (' ', 3), ('#', 3), (' ', 4), ('#', 5), (' ', 3), ('#', 3), (' ', 10), ('#', 3), (' ', 7), ('#', 4), (' ', 1)], [(' ', 3), ('#', 3), (' ', 3), ('#', 2), (' ', 4), ('#', 4), (' ', 1), ('#', 7), (' ', 5), ('#', 2), (' ', 2), ('#', 3), (' ', 6), ('#', 4), (' ', 1), ('#', 7), (' ', 3), ('#', 4), (' ', 1), ('#', 7), (' ', 5), ('#', 3), (' ', 2), ('#', 3), (' ', 5), ('#', 4), (' ', 1)], [(' ', 2), ('#', 3), (' ', 5), ('#', 3), (' ', 2), ('#', 5), (' ', 4), ('#', 4), (' ', 3), ('#', 3), (' ', 3), ('#', 4), (' ', 4), ('#', 5), (' ', 4), ('#', 4), (' ', 2), ('#', 5), (' ', 4), ('#', 4), (' ', 3), ('#', 3), (' ', 5), ('#', 3), (' ', 3), ('#', 4), (' ', 1)], [(' ', 1), ('#', 3), (' ', 11), ('#', 4), (' ', 5), ('#', 4), (' ', 3), ('#', 3), (' ', 4), ('#', 3), (' ', 4), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 3), (' ', 6), ('#', 4), (' ', 2), ('#', 4), (' ', 1)], [(' ', 1), ('#', 3), (' ', 11), ('#', 4), (' ', 5), ('#', 4), (' ', 10), ('#', 3), (' ', 4), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 3), (' ', 7), ('#', 3), (' ', 2), ('#', 4), (' ', 1)], [('#', 4), (' ', 11), ('#', 4), (' ', 5), ('#', 4), (' ', 5), ('#', 2), (' ', 3), ('#', 3), (' ', 4), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 4), (' ', 5), ('#', 4), (' ', 1), ('#', 4), (' ', 7), ('#', 3), (' ', 2), ('#', 4), (' ', 1)], [('#', 4), (' ', 11), ('#', 4), (' ', 5), ('#', 4), (' ', 3), ('#', 10), (' ', 4), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 4), (' ', 5), ('#', 4), (' ', 1), ('#', 14), (' ', 2), ('#', 4), (' ', 1)], [('#', 4), (' ', 11), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 3), (' ', 4), ('#', 4), (' ', 4), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 4), (' ', 5), ('#', 4), (' ', 1), ('#', 4), (' ', 12), ('#', 4), (' ', 1)], [('#', 4), (' ', 11), ('#', 4), (' ', 5), ('#', 4), (' ', 1), ('#', 4), (' ', 5), ('#', 3), (' ', 4), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 4), (' ', 5), ('#', 4), (' ', 1), ('#', 4), (' ', 12), ('#', 4), (' ', 1)], [(' ', 1), ('#', 3), (' ', 11), ('#', 4), (' ', 5), ('#', 4), (' ', 1), ('#', 4), (' ', 5), ('#', 3), (' ', 4), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 3), (' ', 12), ('#', 4), (' ', 1)], [(' ', 2), ('#', 3), (' ', 6), ('#', 2), (' ', 2), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 3), (' ', 4), ('#', 4), (' ', 4), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 4), (' ', 5), ('#', 4), (' ', 3), ('#', 3), (' ', 6), ('#', 2), (' ', 3), ('#', 4), (' ', 1)], [(' ', 3), ('#', 3), (' ', 4), ('#', 2), (' ', 3), ('#', 4), (' ', 5), ('#', 4), (' ', 3), ('#', 11), (' ', 3), ('#', 4), (' ', 5), ('#', 4), (' ', 2), ('#', 4), (' ', 5), ('#', 4), (' ', 4), ('#', 3), (' ', 4), ('#', 2), (' ', 4), ('#', 4), (' ', 1)], [(' ', 6), ('#', 3), (' ', 5), ('#', 6), (' ', 4), ('#', 5), (' ', 4), ('#', 2), (' ', 4), ('#', 4), (' ', 1), ('#', 6), (' ', 4), ('#', 11), (' ', 4), ('#', 5), (' ', 6), ('#', 3), (' ', 6), ('#', 6)], [(' ', 95)]]
```

OK! So data is a list  of lists of tuples... It does not look like a **banner**(the file name), but more like the result of a simple string compression: convert the repetitive characters to tuples of (character, number of appearance). This level is all about serialization and compression, isn't it. Let's unravel the string:

```python
>>> for line in data:
...     print("".join([k * v for k, v in line]))
... 
                                                                                               
              #####                                                                      ##### 
               ####                                                                       #### 
               ####                                                                       #### 
               ####                                                                       #### 
               ####                                                                       #### 
               ####                                                                       #### 
               ####                                                                       #### 
               ####                                                                       #### 
      ###      ####   ###         ###       #####   ###    #####   ###          ###       #### 
   ###   ##    #### #######     ##  ###      #### #######   #### #######     ###  ###     #### 
  ###     ###  #####    ####   ###   ####    #####    ####  #####    ####   ###     ###   #### 
 ###           ####     ####   ###    ###    ####     ####  ####     ####  ###      ####  #### 
 ###           ####     ####          ###    ####     ####  ####     ####  ###       ###  #### 
####           ####     ####     ##   ###    ####     ####  ####     #### ####       ###  #### 
####           ####     ####   ##########    ####     ####  ####     #### ##############  #### 
####           ####     ####  ###    ####    ####     ####  ####     #### ####            #### 
####           ####     #### ####     ###    ####     ####  ####     #### ####            #### 
 ###           ####     #### ####     ###    ####     ####  ####     ####  ###            #### 
  ###      ##  ####     ####  ###    ####    ####     ####  ####     ####   ###      ##   #### 
   ###    ##   ####     ####   ###########   ####     ####  ####     ####    ###    ##    #### 
      ###     ######    #####    ##    #### ######    ###########    #####      ###      ######
````



You got it: 

> channel

### Put Everything Together

```python
from urllib.request import urlopen
import pickle

h = urlopen("http://www.pythonchallenge.com/pc/def/banner.p")
data = pickle.load(h)

for line in data:
    print("".join([k * v for k, v in line]))
```

## Next Level

http://www.pythonchallenge.com/pc/def/channel.html
