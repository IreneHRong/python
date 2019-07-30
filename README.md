---
title: Python / Python3 教學
tags: Templates, Talk
description: View the slide with "Slide Mode".
---

## Python / Python3 教學
首先，我們需要認識python的基本語法。


注意Python中默認的編碼格式是ASCII格式，在沒修改編碼格式時無法正確打印漢字，所以在讀取中文時會報錯。
解決方法為只要在文件開頭加入`-*-編碼：UTF-8-*- `或者 `coding=utf-8`就行了
注意：`coding=utf-8` 等號兩邊不要空格。

### 變數 (variable) 
我們使用**變數**來命名資料，將資料儲存在變數裡。呼叫資料時只要指名變數就可以。
而python的 **變數型態** (variable type)主要有三種：
>   ```python= 
>  [1] 
>  a = 123 
>   print (a)
>   print type(a)    #python 語法
>   print (type(a))  #python3 語法
>```
>在這邊可以看到，在不同python版本裡的語法(print)有些差異，但結果相同。
>###### [1] [Out] 
>`123`
>`int (整數)` 
>`int (整數）`

>```python=5
>[2] 
>b = 12.2
>print (type(b))
>```
>###### [2] [Out] `float (浮點數)`
>```python=8
>[3] 
>c = '3'              # 使用單引號('')或雙引號(“”)的結果會相同
>print (c)
>print (type(c))
>```
>###### [３] [Out] 
>`3`
>`str (字串)`
>

### Python 标识符
- 在 Python 裡，變數名稱由字母、數字和底線组成。
- 在 Python 中，變數可以包括英文、数字以及下底線(_)，但不能以數字開頭。
- Python 中的變數是是區分大小寫的。
- 以下底線開頭的變數是有特殊意義的。以下舉例說明：
    >foo_：不使用，為避免和built-in keywords 或 built-in functions取一樣的名稱
    >_foo : 不能用 `from xxx import ` 而導入。
    >__foo : 以兩個下底線開頭的，
    >＿foo＿ 通常是核心開發人員才會使用的特殊函式，如 ＿init()＿ 。

Python 可以同一行显示多条语句，方法是用分号 ; 分开，如：
```python
>>> print 'hello';print 'runoob';
hello
runoob
```
### 字符串格式化 (%)
```python=12
print "My name is %s and weight is %d kg!" % ('Zara', 21) 
```
###### [Out]  `My name is Zara and weight is 21 kg!`


也可以一次命名多個資料：
```python=13
a, b, c = 5, 12.09, 'K'
```


>### 相同的變數形態之間可以做運算
> 數值
>```python=14
>a = 7
>b = 3
>print (a + b)     # a加上b的數值
>print (a * b)     # a乘以b的數值
>print (a / b)     # a除以b的數值
>print (a ** b)    # a的b次方 
>print (a // b)    # a除以b的整除部分（商數）
>print (a % b)     # a除以b的餘數
>c // = a          # c = c // a
>c + = a           # c = c + a
>```
>###### [out]
>`10`
>`21`
>`2.3333333333333335`
>`343`
>`2`
>`1`
>

### 字串
> ```python=24
> a = 'Hello '
> b = 'world!'
> print a+b    #python
> print (a+b)  #python3
> print (type (a+b))
> ```
> ###### [out] 
> `Hello world!`
> `Hello world!`
> `str`
> 

>數值和字串
>```python=29
>a = 123
>b = '456'
>print (a+int(b))
>print (type(a+int(b)))
>print (str(a)+b)
>print (str(a)+b)
>```
>###### [out] 
>`123456`
>`int`
>`123456`
>`str`

### 字串 / 字符串也有運算：

S.find（substring，[start [，end]]）可指範圍查找子串，返回索引值，否則返回-1

S.rfind（substring，[start [，end]]）反向查找

S.index（substring，[start [，end]]）同上，只是找不到產生ValueError異常

S.rindex（substring，[start [，end]]）同上反向查找

S.count（substring，[start [，end]]）返回找到子串的個數


S.lowercase（） 使首個字母小寫

S.capitalize（）使首個字母大寫

S.lower（）轉小寫

S.upper（）轉大寫

S.swapcase（）大小寫互換


S.split（str，''）將字符串轉錄，以空格切分

S.join（list，''）將list轉string，以空格連接

處理字符串的內置函數


len（str）串長度

cmp（“我的朋友”，str）字符串比較。第一個大，返回1

max（'abcxyz'）尋找字符串中最大的字符

min（'abcxyz'）尋找字符串中最小的字符

## Python 命令行参数
Python 提供了 getopt 模块来获取命令行参数。
`$ python test.py arg1 arg2 arg3`
Python 中也可以所用 sys 的 sys.argv 来获取命令行参数：
- sys.argv 是命令行参数列表。
- len(sys.argv) 是命令行参数个数。

注：sys.argv[0] 表示脚本名。

实例
test.py 文件代码如下：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import sys

print '参数个数为:', len(sys.argv), '个参数。'
print '参数列表:', str(sys.argv)
```
执行以上代码，输出结果为：
```
$ python test.py arg1 arg2 arg3`
参数个数为: 4 个参数。
参数列表: ['test.py', 'arg1', 'arg2', 'arg3']
```
### getopt模块
getopt模块是专门处理命令行参数的模块，用于获取命令行选项和参数，也就是sys.argv。命令行选项使得程序的参数更加灵活。支持短选项模式（-）和长选项模式（--）。
该模块提供了两个方法及一个异常处理来解析命令行参数。
### getopt.getopt 方法
getopt.getopt 方法用于解析命令行参数列表，语法格式如下：
`getopt.getopt(args, options[, long_options])`
方法参数说明：

- args: 要解析的命令行参数列表。
- options : 以字符串的格式定义，options 后的冒号 : 表示如果设置该选项，必须有附加的参数，否则就不附加参数。
- long_options : 以列表的格式定义，long_options 后的等号 = 表示该选项必须有附加的参数，不带冒号表示该选项不附加参数。
该方法返回值由两个元素组成: 第一个是 (option, value) 元组的列表。 第二个是参数列表，包含那些没有 - 或 -- 的参数。

另外一个方法是 getopt.gnu_getopt，这里不多做介绍。
### Exception getopt.GetoptError
在没有找到参数列表，或选项的需要的参数为空时会触发该异常。
异常的参数是一个字符串，表示错误的原因。属性 msg 和 opt 为相关选项的错误信息。
实例
假定我们创建这样一个脚本，可以通过命令行向脚本文件传递两个文件名，同时我们通过另外一个选项查看脚本的使用。脚本使用方法如下：
`usage: test.py -i <inputfile> -o <outputfile>`
test.py 文件代码如下所示：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import sys, getopt

def main(argv):
   inputfile = ''
   outputfile = ''
   try:
      opts, args = getopt.getopt(argv,"hi:o:",["ifile=","ofile="])
   except getopt.GetoptError:
      print 'test.py -i <inputfile> -o <outputfile>'
      sys.exit(2)
   for opt, arg in opts:
      if opt == '-h':
         print 'test.py -i <inputfile> -o <outputfile>'
         sys.exit()
      elif opt in ("-i", "--ifile"):
         inputfile = arg
      elif opt in ("-o", "--ofile"):
         outputfile = arg
   print '输入的文件为：', inputfile
   print '输出的文件为：', outputfile

if __name__ == "__main__":
   main(sys.argv[1:])
```
执行以上代码，输出结果为：
```
$ python test.py -h
usage: test.py -i <inputfile> -o <outputfile>

$ python test.py -i inputfile -o outputfile
输入的文件为： inputfile
输出的文件为： outputfile
```
一些python語法：


![](https://i.imgur.com/AJbMuRj.png)

---

## python數據類型： 
| 數字| 字串|列表|元組|字典|
| ------ | ----- | ----- | ----- | ------ |
|Number| String | List | Tuple | Dictionary |
| 2 | '2' | list=[1,'2'] | tuple=(1,2) | {key1 : value1, key2 : value2 }|
|數字| 字串|可以修改內容|不能修改|可以重新指向dic|
### 字串string
轉義字符，以‘\’加在前面。
字符串內建函數：

|名称|叙述|
|-----|------|
|1. capitalize()|将字符串的第一个字符转换为大写|
|2. center(width, fillchar)|返回一个指定的宽度 width 居中的字符串，fillchar 为填充的字符，默认为空格。|
|3. count(str, beg= 0,end=len(string))|返回 str 在 string 里面出现的次数，如果 beg 或者 end 指定则返回指定范围内 str 出现的次数|
|4. bytes.decode(encoding="utf-8", errors="strict")|Python3 中没有 decode 方法，但我们可以使用 bytes 对象的 decode() 方法来解码给定的 bytes 对象，这个 bytes 对象可以由 str.encode() 来编码返回。|
|5. encode(encoding='UTF-8',errors='strict')|以 encoding 指定的编码格式编码字符串，如果出错默认报一个ValueError 的异常，除非 errors 指定的是'ignore'或者'replace'|
|6.
endswith(suffix, beg=0, end=len(string))|检查字符串是否以 obj 结束，如果beg 或者 end 指定则检查指定的范围内是否以 obj 结束，如果是，返回 True,否则返回 False.|
|7. expandtabs(tabsize=8)|把字符串 string 中的 tab 符号转为空格，tab 符号默认的空格数是 8 。|
|8. find(str, beg=0, end=len(string))|检测 str 是否包含在字符串中，如果指定范围 beg 和 end ，则检查是否包含在指定范围内，如果包含返回开始的索引值，否则返回-1|
|9. index(str, beg=0, end=len(string))|跟find()方法一样，只不过如果str不在字符串中会报一个异常.|
|10. isalnum()|如果字符串至少有一个字符并且所有字符都是字母或数字则返 回 True,否则返回 False|
|11. isalpha()|如果字符串至少有一个字符并且所有字符都是字母则返回 True, 否则返回 False|
|12. isdigit()|如果字符串只包含数字则返回 True 否则返回 False.|
|13. islower()|如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是小写，则返回 True，否则返回 False|
|14. isnumeric()|如果字符串中只包含数字字符，则返回 True，否则返回 False|
|15. isspace()|如果字符串中只包含空白，则返回 True，否则返回 False.|
|16. istitle()|如果字符串是标题化的(见 title())则返回 True，否则返回 False|
|17. isupper()|如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是大写，则返回 True，否则返回 False|
|18. join(seq)|以指定字符串作为分隔符，将 seq 中所有的元素(的字符串表示)合并为一个新的字符串|
|19. len(string)|返回字符串长度|
|20. ljust(width[, fillchar])|返回一个原字符串左对齐,并使用 fillchar 填充至长度 width 的新字符串，fillchar 默认为空格。|
|21. lower()|转换字符串中所有大写字符为小写|
|22. lstrip()|截掉字符串左边的空格或指定字符。|
|23. maketrans()|创建字符映射的转换表，对于接受两个参数的最简单的调用方式，第一个参数是字符串，表示需要转换的字符，第二个参数也是字符串表示转换的目标。|
|24. max(str)|返回字符串 str 中最大的字母。|
|25. min(str)|返回字符串 str 中最小的字母。|
|26. replace(old, new [, max])|将字符串中的 str1 替换成 str2,如果 max 指定，则替换不超过 max 次。|
|27. rfind(str, beg=0,end=len(string))|类似于 find()函数，不过是从右边开始查找.|
|28. rindex( str, beg=0, end=len(string))|类似于 index()，不过是从右边开始.|
|29. rjust(width,[, fillchar])|返回一个原字符串右对齐,并使用fillchar(默认空格）填充至长度 width 的新字符串|
|30. rstrip()|删除字符串字符串末尾的空格.|
|31. split(str="", num=string.count(str))|num=string.count(str)) 以 str 为分隔符截取字符串，如果 num 有指定值，则仅截取 num+1 个子字符串|
|32. splitlines([keepends])|按照行('\r', '\r\n', \n')分隔，返回一个包含各行作为元素的列表，如果参数 keepends 为 False，不包含换行符，如果为 True，则保留换行符。|
|33. startswith(substr, beg=0,end=len(string))|检查字符串是否是以指定子字符串 substr 开头，是则返回 True，否则返回 False。如果beg 和 end 指定值，则在指定范围内检查。|
|34. strip([chars])|在字符串上执行 lstrip()和 rstrip()|
|35. swapcase()|将字符串中大写转换为小写，小写转换为大写|
|36. title()|返回"标题化"的字符串,就是说所有单词都是以大写开始，其余字母均为小写(见 istitle())|
|37. translate(table, deletechars="")|根据 str 给出的表(包含 256 个字符)转换 string 的字符, 要过滤掉的字符放到 deletechars 参数中|
|38. upper()|转换字符串中的小写字母为大写|
|39. zfill (width)|返回长度为 width 的字符串，原字符串右对齐，前面填充0|
|40. isdecimal()|检查字符串是否只包含十进制字符，如果是返回 true，否则返回 false|

### 列表（list)
>```python=1
>ls = [1, '8', 3, 5, 6]
>
>print (ls[1])
>print (len(ls))
>```
>###### [Out] ` 8`
>###### [Out] ` 5`
> ls[0] = 1，ls[1] = 8，分別為int和str的型態。列表內的個數則用len()這個函數來表示。
>```python=5
>print (ls[1:3], ls[-2], ls[2:]) 
>```
>###### [Out] ` ['8', 3]` `5`
>ls [a`:`b]代表從ls[a]一直到ls[b-1]都要被print出來。
>ls[-2]則是倒數第二項要被print出來。
>ls[2:]是從ls[2]開始print。
>
>建立一個空的 list : `a = list()` 或是 `a = []` 都可以。
>
>而list的合併可以用下面這種方式做到：
>```python=6
>ls1 = [1, 2, 3]
>ls2 = [4, 5, 6]
>print (ls1+ls2)
>```
>###### [Out] `[1, 2, 3, 4, 5, 6]`
> ### 列表的修改
>動態增加元素:  #注意有`()`
>-- list.append(x): 把變數x塞到list的最後面
>-- list.insert(i, x): 把變數x塞到ls[i]這個位置上
>-- list.pop(): 把list的最後一格丟掉，且返回該元素的值
>-- list.pop(i): 把list的第i格丟掉
>-- list.remove(x): 移除第一個出現的值x
>-- list.clear(): 把list內的資料全部清光光
>-- list.sort(cmp=None, key=None, reverse=False) :
> > 實例
>>  ```python
>>  #!/usr/bin/python
>># -*- coding: UTF-8 -*-
>># 获取列表的第二个元素
>>def takeSecond(elem):
>>    return elem[1] 
>># 列表
>>random = [(2, 2), (3, 4), (4, 1), (1, 3)] 
>># 指定第二个元素排序
>>random.sort(key=takeSecond) 
>># 输出类别
>>print '排序列表：', random
>>```
>>輸出結果
>>`排序列表：[(4, 1), (2, 2), (1, 3), (3, 4)]`
>
>-- list.count(obj.)：統計某個元素在列表中出現的次數
>-- list.copy() : 複製列表
>-- list.reverse() : 反轉列表
>-- list.extend(seq) : 在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）
>
> 與常見函數的結合:
>-- cmp(list1, list2):
>>如果比較的元素是同類型的,則比較其值,返回結果。
如果兩個元素不是同一種類型,則檢查它們是否是數字。
如果是數字,執行必要的數字強制類型轉換,然後比較。
如果有一方的元素是數字,則另一方的元素"大"(數字是"最小的")
否則,通過類型名字的字母順序進行比較。
如果有一個列表首先到達末尾,則另一個長一點的列表"大"。
如果我們用盡了兩個列表的元素而且所 有元素都是相等的,那麼結果就是個平局,就是說返回一個 0。
>
>-- max(list): 找出list中最大值
>>
>-- min(list): 找出list中最小值
>-- sum(list): 找出list數字總和
例子：
```python=
numbers = [12, 37, 5, 42, 8, 3]
even = []
odd= []
while len(numbers) >0:
    number = numbers.pop()        # list.pop()  刪除list中最後一項
    if number % 2 == 0:
        even.append(number)       # list.append() 加入括號內容到最後一項
    else:
        odd.append(number)
print(even,odd)
```

>### 將列表當作隊列使用
>也可以把列表當做隊列用，只是在隊列裡第一加入的元素，第一個取出來；但是拿列表用作這樣的目的效率不高。在列表的最後添加或者彈出元素速度快，然而在列表裡插入或者從頭部彈出速度卻不快（因為所有其他的元素都得一個一個地移動）。
>```python=
>>>> from collections import deque
>>> queue = deque(["Eric", "John", "Michael"])
>>> queue.append("Terry")           # Terry arrives
>>> queue.append("Graham")          # Graham arrives
>>> queue.popleft()                 # The first to arrive now leaves
>'Eric'
>>> queue.popleft()                 # The second to arrive now leaves
>'John'
>>> queue                           # Remaining >queue in order of arrival
>deque(['Michael', 'Terry', 'Graham'])
>```
>

### 元組(tuple)
>```python=
>tup1 = ('physics', 2000)
>tup2 = (1,)
> 
>print "tup1[0]: ", tup1[0]
>print "tup2[1:5]: ", tup2[1:5]
>```
>元組不同於列表，以小括號表示，而若元組內只有一項，其後要加``,``。
>元組內容不能被修改，只能透過以元組為單位的相加。
>```python=6
>tup3 = tup1 + tup2
>print (tup3)
>```
>###### [Out] `('physics', 2000, 1)`
>### 刪除元組
>```python
>tup = ('Google', 'Runoob', 1997, 2000)
>
>print (tup)
>del tup;
>print ("删除后的元组 tup : ")
>print (tup)
>```
>刪除後的元組：
>```python
>删除后的元组 tup : 
>Traceback (most recent call last):
>    File "test.py", line 8, in <module>
>        print (tup)
>NameError: name 'tup' is not defined
>```
### 字典(Dictionary)
>字典的每個鍵值 key 和 value 會用` :` 分割，每一個字會用`,`分割，整個字典包括在中括號內。鍵(key)必須是不可變的字串、數字或元組，值(value)則可以取任何的數據類型。
>`dict()`用于创建字典
>```python=8
>dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}
>print ("dict['Name']: ", dict['Name'])
>#或是以數字作為key：
>dict2 = { 'abc': 123, 98.6: 37 }
>```
>###### [Out] `dict['Name']: Zara`
>- 鍵不重複，而後面的鍵值對會替換前面的，值不需要唯一。
>- chr和ord有時在字典也用得到哦！（後面補充）
>
>字典有一些函式
>
>| 名稱 | 功能 |
>| -------- | -------- |
>| dict.has_key(key)| 檢查字典內是否有這個鍵值對, 有則返回True否則False|
>|dict.popitem()|刪除字典內最後一項。|
>|len(dict)|鍵值對的數量。|
>|str(dict)|輸出字典，以可印出的字符串表示。|
>
>例子如下：
>```python=10
>dic = {'s':2, 'e':1}
>o=dic.popitem()
>print (o)
>print (dic)
>print (len(dic))
>```
>###### [Out] 
>`('e', 1)` 
>`{'s', 2}`
>`2`
>```python=15
># 字典轉字串用法
>
> dc = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
> print (str(dc))
>```
>###### [Out] ` "{'Name': 'Runoob', 'Class': 'First', 'Age': 7}"`
>```python=19
>#dict加上str.format用法
>
>dict = { 'D': 19 , 'I':20 }
>print( 'Daniel is{D:3d} and Irene is{I:3d}.'.format(**dict) )
>```
>###### [Out] `Daniel is 19 and Irene is 20.`
>若有 `KeyError` 代表字典內沒有對應的鍵值對。
>### 修改字典
>向字典添加新内容的方法是增加新的键/值对，修改或删除已有键/值对如下实例:
>```python
>dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
>
>dict['Age'] = 8             # 更新 Age
>dict['School'] = "菜鸟教程"  # 添加信息
>
>print ("dict['Age']: ", dict['Age'])
>print ("dict['School']: ", dict['School'])
>```
> ###### [Out] 
>`dict['Age']:  8`
>`dict['School']:  菜鸟教程`
>### 刪除字典
>显示删除一个字典用del命令。在del操作後執行命令會引發異常，因為字典已不存在。
>### 字典函數：
	
>|名稱|描述|
>|-|-|
>|1.	radiansdict.clear()|删除字典内所有元素|
>|2.	radiansdict.copy()|返回一个字典的浅复制|
>|3. radiansdict.fromkeys()|创建一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值|
>|4.	radiansdict.get(key, default=None)|返回指定键的值，如果值不在字典中返回default值|
>|5. key in dict|如果键在字典dict里返回true，否则返回false|
>|6.radiansdict.items()|以列表返回可遍历的(键, 值) 元组数组|
>|7.radiansdict.keys()|返回一个迭代器，可以使用 list() 来转换为列表|
>|8. 	radiansdict.setdefault(key, default=None)|和get()类似, 但如果键不存在于字典中，将会添加键并将值设为default|
>|9. radiansdict.update(dict2)|把字典dict2的键/值对更新到dict里|
>|10. radiansdict.values()|返回一个迭代器，可以使用 list() 来转换为列表|
>|11. pop(key[,default])|删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值。|
>|12. popitem()|随机返回并删除字典中的一对键和值(一般删除末尾对)。|
### 檢查成員是否存在於字串、列表、元組內

以列表(list)為例
```python=
a = 10
b = 20
list = [1, 2, 3, 4, 5 ];
 
if a in list :
   print ("變量a在給定的列表list中")
else:
   print （"變量a不在给定的列表中list中"）
 
if b not in list :
   print （"變量b不在给定的列表中list中"）
else:
   print （"變量b在给定的列表中list中"）
```
>### Python数据类型转换

|函式|意義|
|----|--|
|tuple ( s )| 將序列 s 轉換為一個元组|
| list ( s ) | 將序列 s 轉換为一個列表 | 
| dict ( d )| 創建一个字典。d 必須是一個序列 (key,value)元组| 
| chr ( x ) | 將一個整數轉換為一個字符 |
|ord ( x ) |將一個字符轉換為它的整數值 |

### 集合
>是一個無序的不重複元素序列。
>只關心數據是否出現，並不在意其位置。
>使用大括號`{}`或者`set()`函數創建集合，注意：創建一個空集合必須用`set（）`而不是`{}`，因為`{}`是用來創建一個空字典。
>```python=
>basket = {'apple', 'orange'}
>print(basket)
>```
>###### [Out] `{'apple', 'orange'}`
>```python=3
>basket2 = set('abracadabra')
>print(basket2)
>```
>###### [Out] `{'a', 'r', 'b', 'c', 'd'}`
>集合之間的運算：
>```python=5
>a = set('1234')
>b = set('3456')
>print(a^b)           # 不同時包含於a,b
>```
###### [Out] `{'1', '2', '5', '6'}`
>集合的基本操作：
>[ 1 ] `set.update()`：
>加入参数，可以是列表、元组、字典等，但若參數已存在就不進行任何操作。
>或是使用 `set.add(x)`將 x 變數加入set中。
>```python=8
>[1]
>thisset = set(("Google", "Runoob", "Taobao"))
> thisset.update({1,3})
> print(thisset)
> ```
>###### [Out] `{1, 3, 'Google', 'Taobao', 'Runoob'}`
>```python=11
> thisset.update([1,4],[5,6])  
> print(thisset)
> ```
>###### [Out] `{1, 3, 4, 5, 6, 'Google', 'Taobao', 'Runoob'}`
>[ 2 ] `set.remove(x)`:
>將元素 x 從 set 中移除，如果元素不存在，則會發生錯誤。
>[ 3 ] `set.discard(x) `
>也是將元素 x 從 set 中移除，但如果元素不存在，不會發生錯誤
> :::info
> 注意 list 中並沒有 discard 的用法 
>:::
>```python=13
>[2] 
>thisset.remove("Taobao")
> print(thisset)
>```
>###### [Out] `{'Google', 'Runoob'}`
>集合內置方法：

>-- add() : 為集合添加新元素
>-- clear()：移除集合中的所有元素
>-- copy()：拷貝一個集合
>-- difference() : 返回多個集合的差集
>-- difference update()移除集合中的元素，該元素在，則指定的集合也存在
>== isdisjoint() : 判斷兩個集合是否包含相同的元素，如果沒有返回True，否則返回False
>-- issubset()：判斷指定集合是否為指定的紫及
>-- issuperset : 判斷該方法的參數集合是指定集合的子集
>-- pop() : 隨機移除元素
>-- remove() : 同list。
>-- symmetric difference()：返回兩個集合中不重複的元素集合
>-- symmetric difference update : 移除當前集合中蠆另外一個指定集合相同的元素，並將另外一個指定集合元素插入到當前集合中
>-- union()：返回兩個集合的交集
>-- update() : 添加元素到集合

### 列表推導式
>列表推導式提供了從序列創建列表的簡單途徑。通常應用程序將一些操作應用於某個序列的每個元素，用其獲得的結果作為生成新列表的元素，或者根據確定的判定條件創建子序列。
每個列表推導式都在 for 之後跟一個表達式，然後有零到多個 for 或 if 子句。返回結果是一個根據表達從其後的 for 和 if 上下文環境中生成出來的列表。如果希望表達式推導出一個元組，就必須使用括號。
(https://blog.csdn.net/lqian1993/article/details/80162145)
它只是一種創建列表的簡潔方法，目的是為了讓大家寫程序時更方便更快捷，寫出更簡潔的代碼，相對的，也比較難理解
以列表推導式舉例，原先的正常寫法：
```python=
a = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
b = []
for i in a:
for j in i:
b.append(j)
print b
```
列表推導式中就會這樣寫：
```python=
a = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
b = [j for i in a for j in i]
print(b)
```
兩者結果相同，但可以看見各自具可閱讀性和簡潔性的優缺。

>**一、 列表推導式**

>1、使用 `[]` 生成列表

>基本格式：
`variable = [out_exp_res for out_exp in input_list if out_exp == 2]`

- out_exp_res:列表生成元素表示式，可以是有返回值的函式。
- for out_exp in input_list：迭代input_list將out_exp傳入out_exp_res表示式中。
- if out_exp == 2：根據條件過濾哪些值可以。

```python=
[1]
def squared(x):
return x*x
multiples = [squared(i) for i in range(30) if i % 3 is 0]
print multiples
# Output: [0, 9, 36, 81, 144, 225, 324, 441, 576, 729]
```
```python=7
[2]
multiples = [i for i in range(30) if i % 3 is 0]
print(multiples)
# Output: [0, 3, 6, 9, 12, 15, 18, 21, 24, 27]
```

>2. 使用`()`生成generator(生成器)
生成器的好处是惰性计算，不会一下子占用太多内存。

```python=
multiples = (i for i in range(30) if i % 3 is 0)
print(type(multiples))
# Output: <type 'generator'>
```

生成器
>在Python中，使用了yield的函數被稱為生成器（generator）。
跟普通函數不同的是，生成器是一個返回迭代器的函數，只能用於迭代操作，更簡單點理解生成器就是一個迭代器。
在調用生成器運行的過程中，每次遇到yield時函數會暫停並保存當前所有的運行信息，返回yield的值，並在下一次執行next（）方法時從當前位置繼續運行。
調用一個生成器函數，返回的是一個迭代器對象。

>**二、字典推導式**
字典推導和列表推導的使用方法是類似的，只不中括號該改成大括號。直接舉例說明：
```python=
[1]大小寫合併
mcase = {'a': 10, 'b': 34, 'A': 7, 'Z': 3}
mcase_frequency = {
k.lower(): mcase.get(k.lower(), 0)   mcase.get(k.upper(), 0)
for k in mcase.keys()
if k.lower() in ['a','b']
}
print mcase_frequency
# Output: {'a': 17, 'b': 34}
```

```python=10
[2]快速更換value和key

mcase = {'a': 10, 'b': 34}
mcase_frequency = {v: k for k, v in mcase.items()}
print mcase_frequency
# Output: {10: 'a', 34: 'b'}
```
>**三、集合推導式**
它們跟列表推導式也是類似的。 唯一的區別在於它使用大括號{}。
```python=
squared = {x**2 for x in [1, 1, 2]}
print(squared)
# Output: set([1, 4])
```
### 元组和序列
元组在输出时总是有括号的，以便于正确表达嵌套结构。在输入时可能有或没有括号， 不过括号通常是必须的（如果元组是更大的表达式的一部分）。
元组由若干逗号分隔的值组成，例如：
```python=
>>> t = 12345, 54321, 'hello!'
>>> t[0]
12345
>>> t
(12345, 54321, 'hello!')
>>> # Tuples may be nested:
... u = t, (1, 2, 3, 4, 5)
>>> u
((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
```

### 嵌套列表解析
python的列表還可以嵌套
```python
>>> transposed = []
>>> for i in range(4):
...     transposed.append([row[i] for row in matrix])
...
>>> transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```


------

### Python 函數

你可以定義一個由自己想要功能的函數，以下是簡單的規則：
- 函數代碼塊以`def`關鍵詞開頭，後接函數標識符名稱和圓括號（）。
- 任何傳入參數和自變量必須放在圓括號中間，圓括號之間可以用於定義參數。
- 函數的第一行語句可以選擇性地使用文檔字符串 - 用於存放函數說明。
- 函數內容以冒號起始，並且縮進。
- `return `(表達式) 結束函數，選擇性地返回一個值給調用方。不帶表達式的返回相當於返回無。

例子如下 :
```python
#!/usr/bin/python3
 
# 计算面积函数
def area(width, height):
    return width * height
 
def print_welcome(name):
    print("Welcome", name)
 
print_welcome("Runoob")
w = 4
h = 5
print("width =", w, " height =", h, " area =", area(w, h))
```

### mutable（可變）與immutable（不可變）對象
>在python中，strings，tuples，和numbers是不可更改的對象，而list，dict等則是可以修改的對象。
不可變類型：變量賦值a = 5後再賦值a = 10，這裡實際是新生成一個int值對象10，再讓a指向它，而5被丟棄，不是改變a的值，相當於新生成了a 。
可變類型：變量賦值la = [1,2,3,4]後再賦值la [2] = 5則是將列表la的第三個元素值更改，本身la沒有動，只是其內部的一部分值被修改了。
python函數的參數傳遞：
不可變類型：類似c ++的值傳遞，如整數，字符串，元組。如fun（a），傳遞的只是a的值，沒有影響a對象本身。比如在fun（a）內部修改a的值，只是修改另一個複制的對象，不會影響一個本身。
可變類型：類似c ++的引用傳遞，如列表，字典。如fun（la），則是將la真正的傳過去，修改後 fun 外部的 la 也會受影響
python中一切都是對象，嚴格意義我們不能說值傳遞還是引用傳遞，我們應該說傳不可變對象和傳可變對象。



### del 語句
>使用 del 語句可以從一個列表中依索引而不是值來刪除一個元素。這與使用 pop() 返回一個值不同。可以用 del 語句從列表中刪除一個切割，或清空整個列表（我們以前介紹的方法是給該切割賦一個空列表）。

python循環語法（遍歷）
根据index循环

1
```python
list1 = ['item1', 'item2', 'item3']
index = 0
for item in list1:
    print('index:' + str(index) + ', value:' + item)
    index +=1
 ```
###### [Out]
index:0, value:item1
index:1, value:item2
index:2, value:item3
2
```python
list1 = ['item1', 'item2', 'item3']
for index in range(len(list1)):
    print('index:' + str(index) + ', value:' + list1[index])
```
###### [Out]
index:0, value:item1
index:1, value:item2
index:2, value:item3
3
```python
list1 = ['item1', 'item2', 'item3']
for index, item in enumerate(list1):
    print('index:' + str(index) + ', value:' + item)
``` 
###### [Out]
index:0, value:item1
index:1, value:item2
index:2, value:item3

>### 多个数组同时循环

>普通方式
```python
list1 = ['item1-1', 'item1-2', 'item1-3']
list2 = ['item2-1', 'item2-2', 'item2-3']
 
for index in range(len(list1)):
    print('list1:' + list1[index] + ', list2:' + list2[index])
```
###### [Out]
list1:item1-1, list2:item2-1
list1:item1-2, list2:item2-2
list1:item1-3, list2:item2-3

同时遍历两个或更多的序列，可以使用 zip() 组合：
>zip //数组元素数量一致时

```python
list1 = ['item1-1', 'item1-2', 'item1-3']
list2 = ['item2-1', 'item2-2', 'item2-3']
 
for item1, item2 in zip(list1, list2):
    print('list1:' + item1 + ', list2:' + item2)
 ```
//结果
list1:item1-1, list2:item2-1
list1:item1-2, list2:item2-2
list1:item1-3, list2:item2-3

>zip //数组元素数量不一致时

```python
print('sample7')
list1 = ['item1-1', 'item1-2', 'item1-3']
list2 = ['item2-1', 'item2-2', 'item2-3', 'item2-4']
for item1, item2 in zip(list1, list2):
    print('list1:' + item1 + ', list2:' + item2)
```
//结果
list1:item1-1, list2:item2-1
list1:item1-2, list2:item2-2
list1:item1-3, list2:item2-3

>### 数组里元素操作

>通常方式

```python
list1 = ['item1-1', 'item1-2', 'item1-3']
newList = []
for item in list1:
    newList.append(item + '-1')
 ```
//结果
['item1-1-1', 'item1-2-1', 'item1-3-1']
>list内部方式
```python
list1 = ['item1-1', 'item1-2', 'item1-3']
newList = [item + '-1' for item in list1]
print(newList)
 ```
//结果
['item1-1-1', 'item1-2-1', 'item1-3-1']
>list内部方式含if判断

```pythonlist1 = ['item1-1', 'item1-2', 'item1-3']
newList = [item + '-1' for item in list1 if not item.endswith('1')]
print(newList)
 ```
//结果
['item1-2-1', 'item1-3-1']

>在序列中遍歷時，索引位置和对应值可以使用 enumerate() 函数同时得到：
```python
>>> for i, v in enumerate(['tic', 'tac', 'toe']):
...     print(i, v)
```
###### [Out]
`0 tic`
`1 tac`
`2 toe`

### Python 隨機函数


| 名稱| 功能 | 
| -------- | -------- | 
|choice(seq)   | 從序列的元素中隨機挑選一個元素， 比如random.choice(range(10))，從0到9中隨機挑選一個整數。   | 
| randrange ([start,] stop [,step]) | 從指定範圍內，按指定基數遞增的集合中獲取一個隨機數，基數缺省值為1 |
| random()   | 隨機生成下一個實數，它在[0,1)範圍内。   | 
|seed([x])|改變隨機數生成器的種子seed。你不必特別去設定seed，Python會自訂。|
|uniform(x, y)|隨機生成下一個實數，它在[x,y]範圍內。|
k-means內常用到random()這個函數。


### Python 文件I/O函數
>open 文件
>創建一個file並使用python內建的open()函數。
>```python
>file = open(“檔名”, “方法”, encoding=”編碼”)
>
>file = open("text", "r", encoding="utf8")
>print(file.read())     # 直接使用file.read()讀取檔案內容！
> file.close()           # 讀取結束後，要記得把檔案關閉
>```
>開啟檔案更安全的寫法是：
>with open('路徑', '開啟後用途', encoding ='編碼' ) as file，**檔案讀取** 如下：
>```python
>my_list = []
>with open('text', 'r', encoding="utf8") as read_f:
>    for row in read_f.readlines():
>        # 去除換行符號( strip("\n")）後，text的每一項變成my_list裡的字串
>        my_list.append(row.strip('\n'))       
>
>for data in my_list:
>    print(data)
>```
>> 常用模式參數：
> 
| r | w | a |r+|
| -------- | -------- | -------- | ---|
| 僅讀取    | 完全取代原有內容   | 新增新的內容至文件尾端（追加）  | 讀取加寫入|

>常用file對象函數：( f = open('txt','mode') )

>|函數|功能|
>|---|---|
>|f.close()|關閉後不可再讀寫|
>|f.fileno()|返回文件描述符，用在如os模塊的讀方法等一些底層操作上。|
>|f.read()|從文件讀取指定的字節數，如果未給定或為負則讀取所有。|
>|f.readline([size])|讀取整行，包括“\ n”字符。
>|f.readlines()|讀取所有行並返回列表，若給定sizeint>0， 返回總和大約為sizeint字節的行， 實際讀取值可能比sizeint較大，因為需要填充緩衝區。
>|f.flush()|刷新文件內部緩衝 主動把數據寫入文件，而不是被動的等待輸出緩衝區寫入。|
>|f.seek(offset[,whence])|設置文件當前位置 offset：開始的偏移量，也就是代表需要移動偏移的字節數，如果是負數 表示從倒數第幾位開始; whence：可選，默認值為0.給偏置定義一個參數，表示要從哪個位置開始偏移; 0代表從文件開頭開始算起，1代表從當前位置開始算起，2代表從文件末尾算起。成功則返回新的文件位置，失敗則函數返回-1|
>|f.tell()|返回文件當前位置。|
>|file.truncate([size])|從文件的首行首字符開始截斷，截斷文件為size個字符，無大小表示從當前位置截斷;截斷之後後面的所有字符被刪除，其中Widnows系統下的換行代表2個字符大小。|
>|file.write(str)|將字符串寫入文件，返回的是寫入的字符長度。|
>|file.writelines(sequence)|向文件寫入一個序列字符串列表，如果需要換行則要自己加入每行的換行符。|
>
>使用write寫入文件：
>```python
>write_f = open('text', 'w', encoding="utf8")
>for i in range(5):
>    write_f.write("Python Writing:我是傳奇{0}.\n".format(i))
>write_f.close()
>```
>另以`with open`的方式取代`open`來寫：
>```python
>with open('/Users/irenehuang/desktop/0722p.py','w') as file:
>    file.write('\tdodorong\n')
>```
## python模組
import所需要的函式庫。 
先以一個例子看看模塊的用法
```python 
import sys
 
print('命令行参数如下:')
for i in sys.argv:
   print(i)
 
print('\n\nPython 路径为：', sys.path, '\n')
```
###### [Out]
```python
$ python using_sys.py 参数1 参数2
命令行参数如下:
using_sys.py
参数1
参数2

Python 路径为： ['/root', '/usr/lib/python3.4', '/usr/lib/python3.4/plat-x86_64-linux-gnu', '/usr/lib/python3.4/lib-dynload', '/usr/local/lib/python3.4/dist-packages', '/usr/lib/python3/dist-packages'] 
```
- 1、import sys 引入 python 标准库中的 sys.py 模块；这是引入某一模块的方法。
- 2、sys.argv 是一个包含命令行参数的列表。
- 3、sys.path 包含了一个 Python 解释器自动查找所需模块的路径的列表。

其中`sys`就是包含所有你定義的函數和變量的文件，其後綴名是`.py`。模塊可以被別的程序引入，以使用該模塊中的函數等功能。這也是使用 python 標準庫的方法。

路徑
>當解釋器遇到 import 語句，如果模塊在當前的搜索路徑就會被導入。
搜索路徑是一個解釋器會先進行搜索的所有目錄的列表。如想要導入模塊 support，需要把命令放在腳本的頂端

>如果是自己創建的函式，需要放在同一資料夾，且import時不需加副檔名。
如果不在同一個目錄下：
import module_name實際找module_name.py檔案，是檔案就一定要有路徑。
匯入模組就是：找到.py檔案的位置，把它執行一遍，從哪裡找呢？sys.path.

import
>import 和 from 的區別：
import 匯入使用時，加字首 module.func()。相當於把模組程式碼放在當前檔案中執行一遍。
from可以指定需要的函式或變數匯入。
一個模塊只會被導入一次，不管你執行了多少次import。這樣可以防止導入模塊被一遍又一遍地執行。

>當我們使用import語句的時候，Python解釋器是怎樣找到對應的文件的呢？
這就涉及到Python的搜索路徑，搜索路徑是由一系列目錄名組成的，Python解釋器就依次從這些目錄中去尋找所引入的模塊。
這看起來很像環境變量，事實上，也可以通過定義環境變量的方式來確定搜索路徑。

再來個例子：
```python=
# 斐波那契(fibonacci)数列模块
 
def fib(n):    # 定义到 n 的斐波那契数列
    a, b = 0, 1
    while b < n:
        print(b, end=' ')
        a, b = b, a+b
    print()
 
def fib2(n): # 返回到 n 的斐波那契数列
    result = []
    a, b = 0, 1
    while b < n:
        result.append(b)
        a, b = b, a+b
    return result
```
然后进入Python解释器，使用下面的命令导入这个模块：
```python
>>> import fibo
```
```python
>>>fibo.fib(1000)
[Out] 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987
>>> fibo.fib2(100)
[Out] [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
>>> fibo.__name__
'fibo'
```

模組
>匯入模組和當前py檔案都有同一個函式，呼叫會呼叫哪一個？
因為python是解釋型，所以後面覆蓋前面。
>匯入一個模組本質就是解釋執行一個python檔案
匯入一個包本質就是解釋該包下的__init__.py檔案

>__init__.py
包：本質就是一個目錄（必須帶有一個__init__.py檔案），用來從邏輯上組織模組
匯入包，怎麼匯入？
匯入包的本質：執行包下面的__init__.py檔案

>深入模塊
模塊除了方法定義，還可以包括可執行的代碼。這些代碼一般用來初始化這個模塊。這些代碼只有在第一次被導入時才會被執行。
每個模塊有各自獨立的符號表，在模塊內部為所有的函數當作全局符號表來使用。
所以，模塊的作者可以放心大膽的在模塊內部使用這些全局變量，而不用擔心把其他用戶的全局變量搞花。
從另一個方面，當你確實知道你在做什麼的話，你也可以通過 modname.itemname 這樣的表示法來訪問模塊內的函數。
模塊是可以導入其他模塊的。在一個模塊（或者腳本，或者其他地方）的最前面使用 import 來導入一個模塊，當然這只是一個慣例，而不是強制的。被導入的模塊的名稱將被放入當前操作的模塊的符號表中。
還有一種導入的方法，可以使用 import 直接把模塊內（函數，變量的）名稱導入到當前操作模塊。比如:
```python
>>> from fibo import fib, fib2
>>> fib(500)
1 1 2 3 5 8 13 21 34 55 89 144 233 377
```
這種導入的方法不會把被導入的模塊的名稱放在當前的字符表中（所以在這個例子裡面，fibo 這個名稱是沒有定義的）。
這還有一種方法，可以一次性的把模塊中的所有（函數，變量）名稱都導入到當前模塊的字符表:
```python
>>> from fibo import *
>>> fib(500)
1 1 2 3 5 8 13 21 34 55 89 144 233 377
```
這將把所有的名字都導入進來，但是那些由單一下劃線（_）開頭的名字不在此例。大多數情況， Python程序員不使用這種方法，因為引入的其它來源的命名，很可能覆蓋了已有的定義。

### __name__屬性
一個模塊被另一個程序第一次引入時，其主程序將運行。如果我們想在模塊被引入時，模塊中的某一程序塊不執行，我們可以用__name__屬性來使該程序塊僅在該模塊自身運行時執行。
```python
#!/usr/bin/python3
# Filename: using_name.py

if __name__ == '__main__':
   print('程序自身在運行')
else:
   print('我來自另一模塊')
```
運行輸出如下：
```
$ python using_name.py
程序自身在運行
```
```
$ python
>>> import using_name
我來自另一模塊
```
說明： 每個模塊都有一個__name__屬性，當其值是'__main__'時，表明該模塊自身在運行，否則是被引入。
說明：__name__ 與 __main__ 底下是雙下劃線， _ _ 是這樣去掉中間的那個空格。

常用的有matplot
os 模塊提供了非常豐富的方法用来處理文件和目錄。常用的方法如下表所示：

|名稱|方法及描述|
|---|---|
|1. os.access(path, mode)|检验权限模式|
|2. os.chdir(path)|改變當前工作目錄|
|3. os.chflags(path, flags)|設置路徑的標記為數字標記|
|4. os.chmod(path, mode)|更改權限|
|5. os.chown(path, uid, gid)|更改文件所有者|
|6. os.chroot(path)|改變當前進程的根目錄|
|7. os.close(fd)|關閉文件敘述符 fd|
|8. os.closerange(fd_low, fd_high)|關閉所有文件描述符，從fd_low(包含)到fd_high（不包含） 會忽略錯誤|
|9. os.dup(fd)|複製文件描述符 fd｜
|10. os.dup2(fd, fd2)|將一個文字描述符 fd 複製到另一個 fd2|
|11. os.fchdir(fd)|通過文件描述符改變當前工作目錄|
|12. os.fchmod(fd, mode)|改變一個文件的訪問權限，該文件由參數 fd 指定，參數mode是Unix下的文件訪問權限|
|13. os.fchown(fd, uid, gid)|修改一個文件的所有權，這個函數修改一個文件的用戶ID， 該文件油文件描述符 fd指定|
|14. os.fdatasync(fd)|強制將文件寫入磁盤，該文件由文件描述符fd指定， 但不強制更新文件的狀態信息|
|15. os.fdopen(fd[,mode[,bufsize]])|通过文件描述符 fd 创建一个文件对象，并返回这个文件对象|
|16	os.fpathconf(fd, name)|返回一个打开的文件的系统配置信息。name为检索的系统配置的值，它也许是一个定义系统值的字符串，这些名字在很多标准中指定（POSIX.1, Unix 95, Unix 98, 和其它）。|
|17. os.fstat(fd)|返回文件描述符fd的状态，像stat()。|
|18. os.fstatvfs(fd)|返回包含文件描述符fd的文件的文件系统的信息，Python 3.3 相等于 statvfs()。|
|19. os.fsync(fd)|强制将文件描述符为fd的文件写入硬盘。|
|20. os.ftruncate(fd, length)|裁剪文件描述符fd对应的文件, 所以它最大不能超过文件大小。|
|21. os.getcwd()|返回当前工作目录|
|22. os.getcwdu()|返回一个当前工作目录的Unicode对象|
|23. os.isatty(fd)|如果文件描述符fd是打开的，同时与tty(-like)设备相连，则返回true, 否则False。|
|24. os.lchflags(path, flags)|设置路径的标记为数字标记，类似 chflags()，但是没有软链接|
|25. os.lchmod(path, mode)|修改连接文件权限|
|26. os.lchown(path, uid, gid)|更改文件所有者，类似 chown，但是不追踪链接。|
|27. os.link(src, dst)|创建硬链接，名为参数 dst，指向参数 src|
| 28. os.listdir(path)|返回path指定的文件夹包含的文件或文件夹的名字的列表。  path = "/var/www/html/" dirs = os.listdir( path )|
|29. os.lseek(fd, pos, how)|设置文件描述符 fd当前位置为pos, how方式修改: SEEK_SET 或者 0 设置从文件开始的计算的pos; SEEK_CUR或者 1 则从当前位置计算; os.SEEK_END或者2则从文件尾部开始. 在unix，Windows中有效|
|30. os.lstat(path)|像stat(),但是没有软链接|
|31. os.major(device)|从原始的设备号中提取设备major号码 (使用stat中的st_dev或者st_rdev field)。|
|32. os.makedev(major, minor)|以major和minor设备号组成一个原始设备号|
|33. os.makedirs(path[, mode])|递归文件夹创建函数。像mkdir(), 但创建的所有intermediate-level文件夹需要包含子文件夹。|
|34. os.minor(device)|从原始的设备号中提取设备minor号码 (使用stat中的st_dev或者st_rdev field )。|
|35. os.mkdir(path[, mode])|以数字mode的mode创建一个名为path的文件夹.默认的 mode 是 0777 (八进制)。|
|36. os.mkfifo(path[, mode])|创建命名管道，mode 为数字，默认为 0666 (八进制)|
|37. os.mknod(filename[, mode=0600, device])|创建一个名为filename文件系统节点（文件，设备特别文件或者命名pipe）。|
|38. os.open(file, flags[, mode])|打开一个文件，并且设置需要的打开选项，mode参数是可选的|
|39. os.openpty()|打开一个新的伪终端对。返回 pty 和 tty的文件描述符。|
|40. os.pathconf(path, name)|返回相关文件的系统配置信息。|
|41. os.pipe()|创建一个管道. 返回一对文件描述符(r, w) 分别为读和写|
|42. os.popen(command[, mode[, bufsize]])|从一个 command 打开一个管道|
|43. os.read(fd, n)|从文件描述符 fd 中读取最多 n 个字节，返回包含读取字节的字符串，文件描述符 fd对应文件已达到结尾, 返回一个空字符串。|
|44. os.readlink(path)|返回软链接所指向的文件|
|45. os.remove(path)|删除路径为path的文件。如果path 是一个文件夹，将抛出OSError; 查看下面的rmdir()删除一个 directory。|
|46. os.removedirs(path)|递归删除目录。|
|47. os.rename(src, dst)|重命名文件或目录，从 src 到 dst|
|48. os.renames(old, new)|递归地对目录进行更名，也可以对文件进行更名。|
|49. os.rmdir(path)|删除path指定的空目录，如果目录非空，则抛出一个OSError异常。|
|50. os.stat(path)|获取path指定的路径的信息，功能等同于C API中的stat()系统调用。|
|51. os.stat_float_times([newvalue])|決定stat_result是否以float对象显示时间戳|
|52. os.statvfs(path)|获取指定路径的文件系统统计信息|
|53. os.symlink(src, dst)|创建一个软链接|
|54. os.tcgetpgrp(fd)|返回与终端fd（一个由os.open()返回的打开的文件描述符）关联的进程组|
|55. os.tcsetpgrp(fd, pg)|设置与终端fd（一个由os.open()返回的打开的文件描述符）关联的进程组为pg。|
|59. os.ttyname(fd)|返回一个字符串，它表示与文件描述符fd 关联的终端设备。如果fd 没有与终端设备关联，则引发一个异常。|
|60. os.unlink(path)|删除文件路径|
|61. os.utime(path, times)|返回指定的path文件的访问和修改的时间。|
|62. os.walk(top[, topdown=True[, onerror=None[, followlinks=False]]])|输出在文件夹中的文件名通过在树中游走，向上或者向下。|
|63. os.write(fd, str)|写入字符串到文件描述符 fd中. 返回实际写入的字符串长度|
|64. os.path 模块|获取文件的属性信息。|
56-58已從python3刪除，分別是
|名稱|敘述|
|-|-|
|56. os.tempnam([dir[, prefix]])|Python3 中已删除。返回唯一的路径名用于创建临时文件。|
|57. os.tmpfile()|Python3 中已删除。返回一个打开的模式为(w+b)的文件对象 .这文件对象没有文件夹入口，没有文件描述符，将会自动删除。|
|58. os.tmpnam()|Python3 中已删除。为创建一个临时文件返回一个唯一的路径|




### 創建一个疊代器
>把一個class作为一个疊代器使用需要在class中實現兩個方法 `__iter__()` 和` __next__() `。
class都有一个構造函數，Python 的構造函數為 __init__(), 它會在對象初始化的時候執行。
更多内容查閱：Python3 面向對象
`__iter__()` 方法返回一个特殊的疊代器对象， 这个疊代器對象實現了 `__next__()` 方法並通過 StopIteration 異常標示迭代的完成。
`__next__()` 方法（Python 2 裡是 next()）會返回下一個迭代器對象。
創建一個返回數字的迭代器，初始值為 1，逐步遞增 1。
```python=
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self
 
  def __next__(self):
    x = self.a
    self.a += 1
    return x
 
myclass = MyNumbers()
myiter = iter(myclass)
 
print(next(myiter))
print(next(myiter))
print(next(myiter))
print(next(myiter))
print(next(myiter))
```
###### [Out] `1` `2` `3` `4` `5`
### StopIteration
>StopIteration 出現在在循環對象窮盡所有元素時的報錯，用於標識迭代的完成，防止出現無限循環的情況，在` __next__() `方法中我們可以設置在完成指定循環次數後觸發 StopIteration 異常來結束迭代。
```python=
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self
 
  def __next__(self):
    if self.a <= 20:
      x = self.a
      self.a += 1
      return x
    else:
      raise StopIteration
 
myclass = MyNumbers()
myiter = iter(myclass)
 
for x in myiter:
  print(x)
```


### while 和 for 循環語句
無限循環在服務器上客戶端的實時請求非常有用。for 循環可以遍歷任何序列的項目，如一個列表或者一個字符串 ; while 循環則需要注意有無給初始值以及True的條件。
使用while或是for循環語句時，另有兩個控制指令，`continue`和`break`，來跳過循環。
continue用於跳過該次循環，break則是用於退出循環。
各來一個while和for使用continue的例子：
```python=
for letter in 'Python':     # 第一個實例
   if letter == 'h':
      continue
   print ('當前字母 :', letter)
 
var = 10                    # 第二個實例
while var > 0:              
   var = var -1
   if var == 5:
      continue
   print ('當前變量值 :', var)
print "Good bye!"
```
最後，循環語句內還有一個跳過循環的控制指令`pass`，是空語句，只為了保持架構的完整性。
```python=13
def sample(n_samples):
    pass
```

該處的 pass 便是佔據一個位置，因為如果定義一個空函數程序會報錯，當你沒有想好函數的內容是可以用 pass 填充，使程序可以正常運行。
### Python 異常處理

|異常名稱|	描述|
|-|-|
|BaseException	|所有異常的基類|
|SystemExit|	解釋器請求退出|
|KeyboardInterrupt	|用戶中斷執行(通常是輸入^C)|
|Exception	|常規錯誤的基類|
|StopIteration|迭代器沒有更多的值|
|GeneratorExit	|生成器(generator)發生異常來通知退出|
|StandardError	|所有的內建標準異常的基類|
|ArithmeticError	|所有數值計算錯誤的基類|
|FloatingPointError|	浮點計算錯誤|
|OverflowError|	數值運算超出最大限制|
|ZeroDivisionError|	除(或取模)零(所有數據類型)|
|AssertionError|斷言語句失敗|
|AttributeError|	對像沒有這個屬性|
|EOFError|	沒有內建輸入,到達EOF 標記|
|EnvironmentError|	操作系統錯誤的基類|
|IOError	|輸入/輸出操作失敗||
||OSError|	操作系統錯誤|
|WindowsError	|系統調用失敗|
|ImportError	|導入模塊/對象失敗|
|LookupError	|無效數據查詢的基類|
|IndexError	|序列中沒有此索引(index)|
|KeyError	|映射中沒有這個鍵
|MemoryError	|內存溢出錯誤(對於Python 解釋器不是致命的)|
|NameError|	未聲明/初始化對象(沒有屬性)|
|UnboundLocalError	|訪問未初始化的本地變量|
|ReferenceError|	弱引用(Weak reference)試圖訪問已經垃圾回收了的對象|
|RuntimeError	|一般的運行時錯誤|
|NotImplementedError|尚未實現的方法|
|SyntaxError	Python |語法錯誤|
|IndentationError|	縮進錯誤|
|TabError	Tab|和空格混用|
|SystemError	|一般的解釋器系統錯誤|
||TypeError	|對類型無效的操作|
|ValueError	|傳入無效的參數|
|UnicodeError	Unicode| 相關的錯誤|
|UnicodeDecodeError	Unicode| 解碼時的錯誤|
|UnicodeEncodeError	Unicode| 編碼時錯誤|
|UnicodeTranslateError	Unicode| 轉換時錯誤|
|Warning	|警告的基類|
|DeprecationWarning	|關於被棄用的特徵的警告|
|FutureWarning	|關於構造將來語義會有改變的警告|
|OverflowWarning	|舊的關於自動提升為長整型(long)的警告|
|PendingDeprecationWarning	|關於特性將會被廢棄的警告|
|RuntimeWarning	|可疑的運行時行為(runtime behavior)的警告|
|SyntaxWarning	|可疑的語法的警告|
|UserWarning	|用戶代碼生成的警告||

>### 捕捉異常可以使用try/except語句。

`try`/`except`語句用來檢測`try`語句塊中的錯誤，從而讓`except`語句捕獲異常信息並處理。

如果你不想在異常發生時結束你的程序，只需在`try`裡捕獲它。

以下為簡單的try....except...else的語法：
```PYTHON
try:
<语句>        #运行别的代码
except <名字>：
<语句>        #如果在try部份引发了'name'异常
except <名字>，<数据>:
<语句>        #如果引发了'name'异常，获得附加的数据
else:
<语句>        #如果没有异常发生
```
>try的工作原理是，當開始一個try語句後，python就在當前程序的上下文中作標記，這樣當異常出現時就可以回到這裡，try子句先執行，接下來會發生什麼依賴於執行時是否出現異常。
>
>如果當try後的語句執行時發生異常，python就跳回到try並執行第一個匹配該異常的except子句，異常處理完畢，控制流就通過整個try語句（除非在處理異常時又引發新的異常）。
如果在try後的語句裡發生了異常，卻沒有匹配的except子句，異常將被遞交到上層的try，或者到程序的最上層（這樣將結束程序，並打印缺省的出錯信息）。
如果在try子句執行時沒有發生異常，python將執行else語句後的語句（如果有else的話），然後控制流通過整個try語句。

>#### 實例
下面是簡單的例子，它打開一個文件，在該文件中的內容寫入內容，且並未發生異常：

```python
#!/usr/bin/python # -*- coding: UTF-8 -*- try : 
    fh = open ( "testfile" , "w" ) 
    fh . write ( "這是一個測試文件，用於測試異常! !" ) except IOError : print "Error:沒有找到文件或讀取文件失敗" else : print "內容寫入文件成功" 
    fh . close ()
```
以上程序輸出結果：
```python
$ python test . py 
 內容寫入文件成功
$ cat testfile        #查看寫入的內容這是一個測試文件，用於測試異常!!
```
>可以在没有异常类型的状态下使用except
```python
try:
    正常的操作
   ......................
except:
    发生异常，执行这块代码
   ......................
else:
    如果没有异常执行这块代码
```
使用except而带多种异常类型
你也可以使用相同的except语句来处理多个异常信息，如下所示：
```python
try:
    正常的操作
   ......................
except(Exception1[, Exception2[,...ExceptionN]]]):
   发生以上多个异常中的一个，执行这块代码
   ......................
else:
    如果没有异常执行这块代码
```

### try-finally 语句
try-finally 语句无论是否发生异常都将执行最后的代码。
```python
try:
<语句>
finally:
<语句>    #退出try时总会执行
raise
```
实例
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
try:
    fh = open("testfile", "w")
    fh.write("这是一个测试文件，用于测试异常!!")
finally:
    print "Error: 没有找到文件或读取文件失败"
```
如果打开的文件没有可写权限，输出如下所示：
```python
$ python test.py 
Error: 没有找到文件或读取文件失败
```
同样的例子也可以写成如下方式：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

try:
    fh = open("testfile", "w")
    try:
        fh.write("这是一个测试文件，用于测试异常!!")
    finally:
        print "关闭文件"
        fh.close()
except IOError:
    print "Error: 没有找到文件或读取文件失败"
```
当在try块中抛出一个异常，立即执行finally块代码。

finally块中的所有语句执行后，异常被再次触发，并执行except块代码。

参数的内容不同于异常。

### 异常的参数
一个异常可以带上参数，可作为输出的异常信息参数。
你可以通过except语句来捕获异常的参数，如下所示：
```python
try:
    正常的操作
   ......................
except ExceptionType, Argument:
    你可以在这输出 Argument 的值...
```
变量接收的异常值通常包含在异常的语句中。在元组的表单中变量可以接收一个或者多个值。

元组通常包含错误字符串，错误数字，错误位置。

>### 实例
以下为单个异常的实例：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

# 定义函数
def temp_convert(var):
    try:
        return int(var)
    except ValueError, Argument:
        print "参数没有包含数字\n", Argument

# 调用函数
temp_convert("xyz");
```
以上程序执行结果如下：
```python
$ python test.py 
参数没有包含数字
invalid literal for int() with base 10: 'xyz'
```
### 触发异常
我们可以使用raise语句自己触发异常

raise语法格式如下：
```python
raise [Exception [, args [, traceback]]]
```
语句中 Exception 是异常的类型（例如，NameError）参数标准异常中任一种，args 是自已提供的异常参数。

最后一个参数是可选的（在实践中很少使用），如果存在，是跟踪异常对象。

>### 实例
一个异常可以是一个字符串，类或对象。 Python的内核提供的异常，大多数都是实例化的类，这是一个类的实例的参数。

定义一个异常非常简单，如下所示：
```python
def functionName( level ):
    if level < 1:
        raise Exception("Invalid level!", level)
        # 触发异常后，后面的代码就不会再执行
```
注意，为了能够捕获异常，"except"语句必须有用相同的异常来抛出类对象或者字符串。

例如我们捕获以上异常，"except"语句如下所示：
```python
try:
    正常逻辑
except Exception,err:
    触发自定义异常    
else:
    其余代码
```
### 实例
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

# 定义函数
def mye( level ):
    if level < 1:
        raise Exception,"Invalid level!"
        # 触发异常后，后面的代码就不会再执行
try:
    mye(0)            # 触发异常
except Exception,err:
    print 1,err
else:
    print 2
```
执行以上代码，输出结果为：
```python
$ python test.py 
1 Invalid level!
```
### 用户自定义异常
通过创建一个新的异常类，程序可以命名它们自己的异常。异常应该是典型的继承自Exception类，通过直接或间接的方式。

以下为与RuntimeError相关的实例,实例中创建了一个类，基类为RuntimeError，用于在异常触发时输出更多的信息。

在try语句块中，用户自定义的异常后执行except块语句，变量 e 是用于创建Networkerror类的实例。
```python
class Networkerror(RuntimeError):
    def __init__(self, arg):
        self.args = arg
```
在你定义以上类后，你可以触发该异常，如下所示：
```python
try:
    raise Networkerror("Bad hostname")
except Networkerror,e:
    print e.args
```
## Python2.x 与3.x 版本区别

Python的3.0版本，常被称为Python 3000，或简称Py3k。相对于Python的早期版本，这是一个较大的升级。
为了不带入过多的累赘，Python 3.0在设计的时候没有考虑向下相容。
许多针对早期Python版本设计的程式都无法在Python 3.0上正常执行。
为了照顾现有程式，Python 2.6作为一个过渡版本，基本使用了Python 2.x的语法和库，同时考虑了向Python 3.0的迁移，允许使用部分Python 3.0的语法与函数。
新的Python程式建议使用Python 3.0版本的语法。
除非执行环境无法安装Python 3.0或者程式本身使用了不支援Python 3.0的第三方库。目前不支援Python 3.0的第三方库有Twisted, py2exe, PIL等。
大多数第三方库都正在努力地相容Python 3.0版本。即使无法立即使用Python 3.0，也建议编写相容Python 3.0版本的程式，然后使用Python 2.6, Python 2.7来执行。
Python 3.0的变化主要在以下几个方面:
- print 函数
print语句没有了，取而代之的是print()函数。 Python 2.6与Python 2.7部分地支持这种形式的print语法。在Python 2.6与Python 2.7里面，以下三种形式是等价的：
print "fish"
print ("fish") #注意print后面有个空格
print("fish") #print()不能带有任何其它参数
然而，Python 2.6实际已经支持新的print()语法：
```
from __future__ import print_function
print("fish", "panda", sep=', ')
```

### Unicode
Python 2 有 ASCII str() 类型，unicode() 是单独的，不是 byte 类型。
现在， 在 Python 3，我们最终有了 Unicode (utf-8) 字符串，以及一个字节类：byte 和 bytearrays。
由于 Python3.X 源码文件默认使用utf-8编码，这就使得以下代码是合法的：
```python
>>> 中国 = 'china' 
>>>print(中国) 
china
```
Python 2.x
```python
>>> str = "我爱北京天安门"
>>> str
'\xe6\x88\x91\xe7\x88\xb1\xe5\x8c\x97\xe4\xba\xac\xe5\xa4\xa9\xe5\xae\x89\xe9\x97\xa8'
>>> str = u"我爱北京天安门"
>>> str
u'\u6211\u7231\u5317\u4eac\u5929\u5b89\u95e8'
```
Python 3.x
```python
>>> str = "我爱北京天安门"
>>> str
'我爱北京天安门'
```
### 除法运算
Python中的除法较其它语言显得非常高端，有套很复杂的规则。Python中的除法有两个运算符，/和//
首先来说/除法:
在python 2.x中/除法就跟我们熟悉的大多数语言，比如Java啊C啊差不多，整数相除的结果是一个整数，把小数部分完全忽略掉，浮点数除法会保留小数点的部分得到一个浮点数的结果。
在python 3.x中/除法不再这么做了，对于整数之间的相除，结果也会是浮点数。
Python 2.x:
```python
>>> 1 / 2
0
>>> 1.0 / 2.0
0.5
Python 3.x:
>>> 1/2
0.5
```
而对于//除法，这种除法叫做floor除法，会对除法的结果自动进行一个floor操作，**在python 2.x和python 3.x中是一致的。**
python 2.x:
```python
>>> -1 // 2
-1
```
```python
python 3.x:
>>> -1 // 2
-1
```
注意的是并不是舍弃小数部分，而是执行 floor 操作，如果要截取整数部分，那么需要使用 math 模块的 trunc 函数
python 3.x:
```python
>>> import math
>>> math.trunc(1 / 2)
0
>>> math.trunc(-1 / 2)
0
```
### 异常
在 Python 3 中处理异常也轻微的改变了，在 Python 3 中我们现在使用 as 作为关键词。
捕获异常的语法由 except exc, var 改为 except exc as var。
使用语法except (exc1, exc2) as var可以同时捕获多种类别的异常。 >Python 2.6已经支持这两种语法。
1. 在2.x时代，所有类型的对象都是可以被直接抛出的，在3.x时代，只有继承自BaseException的对象才可以被抛出。
2. 2.x raise语句使用逗号将抛出对象类型和参数分开，3.x取消了这种奇葩的写法，直接调用构造函数抛出对象即可。
在2.x时代，异常在代码中除了表示程序错误，还经常做一些普通控制结构应该做的事情，在3.x中可以看出，设计者让异常变的更加专一，只有在错误发生的情况才能去用异常捕获语句来处理。

### xrange
在 Python 2 中 xrange() 创建迭代对象的用法是非常流行的。比如： for 循环或者是列表/集合/字典推导式。
这个表现十分像生成器（比如。"惰性求值"）。但是这个 xrange-iterable 是无穷的，意味着你可以无限遍历。
由于它的惰性求值，如果你不得仅仅不遍历它一次，xrange() 函数 比 range() 更快（比如 for 循环）。尽管如此，对比迭代一次，不建议你重复迭代多次，因为生成器每次都从头开始。
在 Python 3 中，range() 是像 xrange() 那样实现以至于一个专门的 xrange() 函数都不再存在（在 Python 3 中 xrange() 会抛出命名异常）。
```python
import timeit

n = 10000
def test_range(n):
    return for i in range(n):
        pass

def test_xrange(n):
    for i in xrange(n):
        pass   
```
Python 2
```python
print 'Python', python_version()

print '\ntiming range()' 
%timeit test_range(n)

print '\n\ntiming xrange()' 
%timeit test_xrange(n)

Python 2.7.6

timing range()
1000 loops, best of 3: 433 µs per loop


timing xrange()
1000 loops, best of 3: 350 µs per loop
```
Python 3
```python
print('Python', python_version())

print('\ntiming range()')
%timeit test_range(n)

Python 3.4.1

timing range()
1000 loops, best of 3: 520 µs per loop
```
```python
print(xrange(10))
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-5-5d8f9b79ea70> in <module>()
----> 1 print(xrange(10))

NameError: name 'xrange' is not defined
```
### 八进制字面量表示
八进制数必须写成0o777，原来的形式0777不能用了；二进制必须写成0b111。
新增了一个bin()函数用于将一个整数转换成二进制字串。 Python 2.6已经支持这两种语法。
在Python 3.x中，表示八进制字面量的方式只有一种，就是0o1000。
python 2.x
```
>>> 0o1000
512
>>> 01000
512
```
python 3.x
```
>>> 01000
  File "<stdin>", line 1
    01000
        ^
SyntaxError: invalid token
>>> 0o1000
512
```
### 不等运算符
Python 2.x中不等于有两种写法 != 和 <>
Python 3.x中去掉了<>, 只有!=一种写法，还好，我从来没有使用<>的习惯
### 去掉了repr表达式``
Python 2.x 中反引号``相当于repr函数的作用
Python 3.x 中去掉了``这种写法，只允许使用repr函数，这样做的目的是为了使代码看上去更清晰么？不过我感觉用repr的机会很少，一般只在debug的时候才用，多数时候还是用str函数来用字符串描述对象。
```
def sendMail(from_: str, to: str, title: str, body: str) -> bool:
    pass
```
### 多个模块被改名（根据PEP8）

旧的名字	|新的名字|
|-|-|
_winreg	|winreg|
ConfigParser	|configparser|
copy_reg	|copyreg|
Queue|	queue|
SocketServer	|socketserver|
repr	|reprlib|

StringIO模块现在被合并到新的io模组内。 new, md5, gopherlib等模块被删除。 Python 2.6已经支援新的io模组。
httplib, BaseHTTPServer, CGIHTTPServer, SimpleHTTPServer, Cookie, cookielib被合并到http包内。
取消了exec语句，只剩下exec()函数。 Python 2.6已经支援exec()函数。
### 数据类型
1）Py3.X去除了long类型，现在只有一种整型——int，但它的行为就像2.X版本的long
2）新增了bytes类型，对应于2.X版本的八位串，定义一个bytes字面量的方法如下：
```
>>> b = b'china' 
>>> type(b) 
<type 'bytes'> 
```
str对象和bytes对象可以使用.encode() (str -> bytes) or .decode() (bytes -> str)方法相互转化。
```
>>> s = b.decode() 
>>> s 
'china' 
>>> b1 = s.encode() 
>>> b1 
b'china' 
```
3）dict的.keys()、.items 和.values()方法返回迭代器，而之前的iterkeys()等函数都被废弃。同时去掉的还有 dict.has_key()，用 in替代它吧 。

### 打开文件
原：
`file( ..... )`
或 
`open(.....)`
改为只能用
`open(.....)`
### 从键盘录入一个字符串
原:
`raw_input( "提示信息" )`
改为:
`input( "提示信息" )`

在python2.x中raw_input()和input( )，两个函数都存在，其中区别为：
- raw_input()---将所有输入作为字符串看待，返回字符串类型
- input()-----只能接收"数字"的输入，在对待纯数字输入时具有自己的特性，它返回所输入的数字的类型（int, float ）

在python3.x中raw_input()和input( )进行了整合，去除了raw_input()，仅保留了input()函数，其接收任意任性输入，将所有输入默认为字符串处理，并返回字符串类型。

### map、filter 和 reduce

这三个函数号称是函数式编程的代表。在 Python3.x 和 Python2.x 中也有了很大的差异。
首先我们先简单的在 Python2.x 的交互下输入 map 和 filter,看到它们两者的类型是 built-in function(内置函数):
```
>>> map
<built-in function map>
>>> filter
<built-in function filter>
>>>
```
它们输出的结果类型都是列表:
```
>>> map(lambda x:x *2, [1,2,3])
[2, 4, 6]
>>> filter(lambda x:x %2 ==0,range(10))
[0, 2, 4, 6, 8]
>>>
```
但是在Python 3.x中它们却不是这个样子了：
```
>>> map
<class 'map'>
>>> map(print,[1,2,3])
<map object at 0x10d8bd400>
>>> filter
<class 'filter'>
>>> filter(lambda x:x % 2 == 0, range(10))
<filter object at 0x10d8bd3c8>
>>>
```
首先它们从函数变成了类，其次，它们的返回结果也从当初的列表成了一个可迭代的对象, 我们尝试用 next 函数来进行手工迭代:
```
>>> f =filter(lambda x:x %2 ==0, range(10))
>>> next(f)
0
>>> next(f)
2
>>> next(f)
4
>>> next(f)
6
>>>
```
对于比较高端的 reduce 函数，它在 Python 3.x 中已经不属于 built-in 了，被挪到 functools 模块当中。

## Python JSON
本章节我们将为大家介绍如何使用 Python 语言来编码和解码 JSON 对象。
JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式，易于人阅读和编写。
### JSON 函数
使用 JSON 函数需要导入 json 库：import json。

函数	|描述|
|-|-|
json.dumps|	将 Python 对象编码成 JSON 字符串|
json.loads|	将已编码的 JSON 字符串解码为 Python 对象|
### json.dumps
json.dumps 用于将 Python 对象编码成 JSON 字符串。
语法
```
json.dumps(obj, skipkeys=False, ensure_ascii=True, check_circular=True, allow_nan=True, cls=None, indent=None, separators=None, encoding="utf-8", default=None, sort_keys=False, **kw)
```
实例
以下实例将数组编码为 JSON 格式数据：
```python
#!/usr/bin/python
import json

data = [ { 'a' : 1, 'b' : 2, 'c' : 3, 'd' : 4, 'e' : 5 } ]

json = json.dumps(data)
print json
```
以上代码执行结果为：
`[{"a": 1, "c": 3, "b": 2, "e": 5, "d": 4}]`
使用参数让 JSON 数据格式化输出：
```python
>>> import json
>>> print json.dumps({'a': 'Runoob', 'b': 7}, sort_keys=True, indent=4, separators=(',', ': '))
{
    "a": "Runoob",
    "b": 7
}
```
### python 原始类型向 json 类型的转化对照表：

|Python	|JSON|
|-|-|
dict	|object|
list, tuple	|array|
str, unicode	|string|
int, long, float	|number|
True	|true|
False	|false|
None|	null|
json.loads
json.loads 用于解码 JSON 数据。该函数返回 Python 字段的数据类型。
语法
json.loads(s[, encoding[, cls[, object_hook[, parse_float[, parse_int[, parse_constant[, object_pairs_hook[, **kw]]]]]]]])
实例
以下实例展示了Python 如何解码 JSON 对象：
```python=
#!/usr/bin/python
import json

jsonData = '{"a":1,"b":2,"c":3,"d":4,"e":5}';

text = json.loads(jsonData)
print text
```
以上代码执行结果为：
`{u'a': 1, u'c': 3, u'b': 2, u'e': 5, u'd': 4}`
### json 类型转换到 python 的类型对照表：

JSON|	Python|
|-|-|
object	|dict|
array	|list|
string	|unicode|
number (int)	|int, long|
number (real)	|float|
true	|True|
false	|False|
null	|None|


### JSON 函数

函数|	描述|
|-|-|
encode	|将 Python 对象编码成 JSON 字符串|
decode	|将已编码的 JSON 字符串解码为 Python 对象|

### encode
Python encode() 函数用于将 Python 对象编码成 JSON 字符串。
>语法
`demjson.encode(self, obj, nest_level=0)`

实例
以下实例将数组编码为 JSON 格式数据：
```python
#!/usr/bin/python
import demjson

data = [ { 'a' : 1, 'b' : 2, 'c' : 3, 'd' : 4, 'e' : 5 } ]

json = demjson.encode(data)
print json
```
以上代码执行结果为：
`[{"a":1,"b":2,"c":3,"d":4,"e":5}]`
### decode
Python 可以使用 demjson.decode() 函数解码 JSON 数据。该函数返回 Python 字段的数据类型。
语法
`demjson.decode(self, txt)`
实例
以下实例展示了Python 如何解码 JSON 对象：
```python=
#!/usr/bin/python
import demjson

json = '{"a":1,"b":2,"c":3,"d":4,"e":5}';

text = demjson.decode(json)
print  text
```
以上代码执行结果为：
`{u'a': 1, u'c': 3, u'b': 2, u'e': 5, u'd': 4}`

### Python内建函数
>### divmod(a, b)
>python divmod() 函数把除数和余数运算结果结合起来，返回一个包含商和余数的元组(a // b, a % b)。

>### open ( name [, mode [, buffering ]])
>在python I/O函数介绍理有一单元提到open函数之用法。

>### staticmethod(function)
>python staticmethod 返回函数的静态方法。
该方法不强制要求传递参数，如下声明一个静态方法：
>```python
>class C(object):
>    @staticmethod
>    def f(arg1, arg2, ...):
>```

>### all ( iterable )
>all() 函数用于判断给定的可迭代参数 iterable 中的所有元素是否都为 TRUE，如果是返回 True，否则返回 False。
元素除了是 0、空、None、False 外都算 True。

>### enumerate(sequence, [start=0])
>enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中。
Python 2.3. 以上版本可用，2.6 添加 start 参数。
>- sequence -- 一个序列、迭代器或其他支持迭代对象。
>- start -- 下标起始位置。

>
>### chr（i）
>chr() 用一个范围在 range（256）内的（就是0～255）整数作参数，返回一个对应的字符。i為16进位的数字。

>### ord(c)
>ord（）函數是chr（）函數（對於8位的ASCII字符串）或unichr（）函數（對於Unicode對象）的配對函數，它以一個字符（長度為1的字符串）作為參數，返回對應的ASCII數值，或者Unicode數值，如果所給的Unicode字符超出了你的Python定義範圍，則會引發一個TypeError的異常。
> c 是字符
> ```python
>>>>ord('a')
>97
>```

>### any(iterable)
>any() 函数用于判断给定的可迭代参数 iterable 是否全部为 False，则返回 False，如果有一个为 True，则返回 True。
>元素除了是 0、空、FALSE 外都算 TRUE。

>### eval ( expression [, globals [, locals ]])
>eval() 函數用來執行一個字符串表達式，並返回表達式的值。
>- expression -- 表達式。
>- globals -- 變量作用域，全局命名空間，如果被提供，則必須是一個字典對象。
>- locals -- 變量作用域，局部命名空間，如果被提供，可以是任何映射對象。
>```python
>>>> x = 7 
>>>> eval ( ' 3 * x ' ) 21 
>>>> eval ( ' pow(2,2) ' ) 4 
>>>> eval ( ' 2 + 2 ' ) 4 
>>>> n = 81 
>>>> eval ( " n + 4 " ) 85  
>```

>### isinstance(object, classinfo)
>object -- 实例对象。
classinfo -- 可以是直接或间接类名、基本类型或者由它们组成的元组。
>isinstance() 函数来判断一个对象是否是一个已知的类型，类似 type()。
>如果对象的类型与参数二的类型（classinfo）相同则返回 True，否则返回 False。。
>:::info
>isinstance() 与 type() 区别：
>type() 不会认为子类是一种父类类型，不考虑继承关系。
>isinstance() 会认为子类是一种父类类型，考虑继承关系。
>如果要判断两个类型是否相同推荐使用 isinstance()。
>```python
>class A:
>    pass 
>class B(A):
>    pass
> 
>isinstance(A(), A)    # returns True
>type(A()) == A        # returns True
>isinstance(B(), A)    # returns True
>type(B()) == A        # returns False
>Python 内置函数 Python 内置函数
>```
>:::
>```python
>>>>a = 2
>>>> isinstance (a,int)
>True
>>>> isinstance (a,str)
>False
>>>> isinstance (a,(str,int,list))  # 是元组中的一个返回 True
>True
>```

>### property : 
>`class property([fget[, fset[, fdel[, doc]]]])`
>property() 函数的作用是在新式类中返回属性值。
>fget -- 获取属性值的函数
>fset -- 设置属性值的函数
>fdel -- 删除属性值函数
>doc -- 属性描述信息
>返回新式类属性。
>实例：
```python
class C(object):
    def __init__(self):
        self._x = None
 
    def getx(self):
        return self._x
 
    def setx(self, value):
        self._x = value
 
    def delx(self):
        del self._x
 
    x = property(getx, setx, delx, "I'm the 'x' property.")
```
>如果c是C的實例化，c.x 將觸發 getter，c.x = value將觸發setter，del c.x觸發刪除。
如果給定doc參數，其將成為這個屬性值的docstring，否則屬性函數就會復制fget函數的docstring（如果有的話）。
將屬性函數用作裝飾器可以很方便的創建只讀屬性：
```python
class Parrot(object):
    def __init__(self):
        self._voltage = 100000
 
    @property
    def voltage(self):
        """Get the current voltage."""
        return self._voltage
```        
>上面的代碼將voltage（）方法轉化成同名只讀屬性的getter方法。
>property的getter，setter和deleter方法同樣可以用作裝飾器：
```python
class C(object):
    def __init__(self):
        self._x = None
 
    @property
    def x(self):
        """I'm the 'x' property."""
        return self._x
 
    @x.setter
    def x(self, value):
        self._x = value
 
    @x.deleter
    def x(self):
        del self._x
```
>這個代碼和第一個例子完全相同，但要注意這些額外函數的名字和屬性下的一樣，例如這裡的x。

>### pow( x, y [ , z ] )
>从 math 模块引入 pow()，pow() 方法返回 xy（x的y次方） 的值。


>### sum(iterable[, start])
>sum() 方法对系列进行求和计算。

>### basestring()
>无参数或返回值
>basestring（）方法是str和unicode的超類（父類），也是抽像類，因此不能被調用和實例化，但可以被用來判斷一個對像是否為str或者unicode的實例，isinstance（obj，basestring）等價於isinstance（obj，（str，unicode））

>### execfile(filename[, globals[, locals]])
>execfile() 函數可以用來執行一個文件。
>- filename -- 文件名。
>- globals -- 變量作用域，全局命名空間，如果被提供，則必須是一個字典對象。
>- locals -- 變量作用域，局部命名空間，如果被提供，可以是任何映射對象。
>
>假设有一个hello.py的文件，内有`print('runoob');`
>就可以使用execfile调用文件：
>```python
>>>> execfile ( ' hello.py ' ) runoob
>```


>### issubclass(class, classinfo)
>issubclass（）方法用於判斷參數類是否是類型參數classinfo的子類。
>如果類是classinfo的子類返回True，否則返回False。
>```python
>#!/usr/bin/python
># -*- coding: UTF-8 -*-
> 
>class A:
>    pass
>class B(A):
>    pass
>    
>print(issubclass(B,A))    # 返回 True
>```

>### super ( type [ , object-or-type] )
>- type -- 类。
>- object-or-type -- 类，一般是 self
>
>super() 函数是用于调用父类(超类)的一个方法。
>super 是用来解决多重继承问题的，直接用类名调用父类方法在使用单继承的时候没问题，但是如果使用多继承，会涉及到查找顺序（MRO）、重复调用（钻石继承）等种种问题。
>MRO 就是类的方法解析顺序表, 其实也就是继承父类方法时的顺序表。没有反回值。
>Python3.x 和 Python2.x 的一个区别是: Python 3 可以使用直接使用 super().xxx 代替 super(Class, self).xxx 
>例子：
>```python
>#!/usr/bin/python
># -*- coding: UTF-8 -*-
> 
>class A(object):   # Python2.x 记得继承 object
>    def add(self, x):
>         y = x+1
>         print(y)
>class B(A):
>    def add(self, x):
>        super(B, self).add(x)
>b = B()
>b.add(2)  # 3
>```
>
>
>
>### bin(x) 
>x 是 int or long int 数字
>bin() 返回一个整数 int 或者长整数 long int 的二进制表示。
>
>### iter ( object [ , sentinel ] )
>object -- 支持迭代的集合对象。
>sentinel -- 如果传递了第二个参数，则参数 object 必须是一个可调用的对象（如，函数），此时，iter 创建了一个迭代器对象，每次调用这个迭代器对象的__next__()方法时，都会调用 object。
>iter() 函数用来生成迭代器。返回迭代器对象

>### bool
>用法 class bool([x])
>bool() 函数用于将给定参数转换为布尔类型，如果没有参数，返回 False。
>bool 是 int 的子类。
>返回 True or False

>### bytearray()
>class bytearray([source[, encoding[, errors]]])
>- 如果 source 为整数，则返回一个长度为 source 的初始化数组；
>- 如果 source 为字符串，则按照指定的 encoding 将字符串转换为字节序列；
>- 如果 source 为可迭代类型，则元素必须为[0 ,255] 中的整数；
>- 如果 source 为与 buffer 接口一致的对象，则此对象也可以被用于初始化 bytearray。
>- 如果没有输入任何参数，默认就是初始化数组为0个元素。
>
>bytearray() 方法返回一个新字节数组。这个数组里的元素是可变的，并且每个元素的值范围: 0 <= x < 256。

>### row_imput()
>:::info
>注意：input（）和raw_input（）這兩個函數均能接收字符串，但raw_input（）直接讀取控制台的輸入（任何類型的輸入它都可以接收）。而對於input（），它希望能夠讀取一個合法的python表達式，即你輸入字符串的時候必須使用引號將它括起來，否則它會引發一個SyntaxError。
>
>除非對輸入（）有特別需要，否則一般情況下我們都是推薦使用raw_input（）來與用戶交互。
>
>注意：python3裡input（）默認接收到的是str類型。
>:::

>### unichr(i)
>unichr() 函数 和 chr()函数功能基本一样， 只不过是返回 unicode 的字符。返回 unicode 的字符。

>### frozenset()
>class frozenset([iterable])
>frozenset() 返回一个冻结的集合，冻结后集合不能再添加或删除任何元素。返回新的 frozenset 对象，如果不提供任何参数，默认会生成空集合。
>```python
>>>> a = frozenset(range(10))     # 生成一个新的不可变集合
>>>> a
>frozenset([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
>>>> b = frozenset('runoob') 
>>>> b
>frozenset(['b', 'r', 'u', 'o', 'n'])   # 创建不可变集合
>```

>### class long(x, base=10)
>long() 函数将数字或字符串转换为一个长整型。返回长整型数。
>- x -- 字符串或数字。
>- base -- 可选，进制数，默认十进制。

>### reload(module)
>module -- 模块对象。reload() 用于重新载入之前载入的模块。
>```python
>>>>import sys
>>>> sys.getdefaultencoding()            # 当前默认编码
>'ascii'
>>>> reload(sys)                         # 使用 reload
><module 'sys' (built-in)>
>>>> sys.setdefaultencoding('utf8')      # 设置编码
>>>> sys.getdefaultencoding()
>'utf8'
>```

>### callable(object)
>callable() 函数用于检查一个对象是否是可调用的。如果返回 True，object 仍然可能调用失败；但如果返回 False，调用对象 object 绝对不会成功。
>对于函数、方法、lambda 函式、 类以及实现了 __call__ 方法的类实例, 它都返回 True。
```python
>>>callable(0)
False
>>> callable("runoob")
False
 
>>> def add(a, b):
...     return a + b
... 
>>> callable(add)             # 函数返回 True
True
>>> class A:                  # 类
...     def method(self):
...             return 0
... 
>>> callable(A)               # 类返回 True
True
>>> a = A()
>>> callable(a)               # 没有实现 __call__, 返回 False
False
>>> class B:
...     def __call__(self):
...             return 0
... 
>>> callable(B)
True
>>> b = B()
>>> callable(b)               # 实现 __call__, 返回 True
True
```
callable()返回True or False.


>### format()
>Python2.6 开始，新增了一种格式化字符串的函数 str.format()，它增强了字符串格式化的功能。
>
>基本语法是通过 {} 和 : 来代替以前的 % 。
>
>format 函数可以接受不限个参数，位置可以不按顺序。
>```python
>>
>>>>"{} {}".format("hello", "world")    # 不设置指定位置，按默认顺序
>'hello world'
>>>> "{0} {1}".format("hello", "world")  # 设置指定位置
>'hello world'
>>>> "{1} {0} {1}".format("hello", "world")  # 设置指定位置
>'world hello world'
>```
>数字格式化:
>- `^`, `<`, `>` 分别是居中、左对齐、右对齐，后面带宽度， : 号后面带填充的字符，只能是一个字符，不指定则默认是用空格填充。
>- `+`表示在正数前显示 +，负数前显示 -；  （空格）表示在正数前加空格
>- b、d、o、x 分别是二进制、十进制、八进制、十六进制。

>|数字|格式|输出|描述|
>|-|-|-|-|
>|3.1415926|{:.2f}|3.14|保留小数点后两位|
>|3.1415926|{:+.2f}|+3.14|带符号保留小数点后两位|
>|-1|{:+.2f}|-1.00|带符号保留小数点后两位|
>|5|{:0>2d}|05|数字补零 (填充左边, 宽度为2)|
>|5|{:x<4d}|5xxx|数字补x (填充右边, 宽度为4)|
>|1000000|{:,}|1,000,000|以逗号分隔的数字格式|
>|13|{:10d}|13|右对齐 (默认, 宽度为10)|
>|13|{:<10d}|13|左对齐 (宽度为10)|
>|13|{:^10d}|13|中间对齐 (宽度为10)|

>### locals()
>locals() 函数会以字典类型返回当前位置的全部局部变量。
>对于函数, 方法, lambda 函式, 类, 以及实现了 __call__ 方法的类实例, 它都返回 True。
>没有参数，返回字典类型的局部变量

>### reduce(function, iterable[, initializer])
>reduce() 函数会对参数序列中元素进行累积。
函数将一个数据集合（链表，元组等）中的所有数据进行下列操作：用传给 reduce 中的函数 function（有两个参数）先对集合中的第 1、2 个元素进行操作，得到的结果再与第三个数据用 function 函数运算，最后得到一个结果。返回函数计算结果
>function -- 函数，有两个参数
>iterable -- 可迭代对象
>initializer -- 可选，初始参数


>### vars([object])
>vars() 函数返回对象object的属性和属性值的字典对象。返回对象object的属性和属性值的字典对象，如果没有参数，就打印当前调用位置的属性和属性值 类似 locals()。
>例子
>```python
>>>>print(vars())
>{'__builtins__': <module '__builtin__' (built-in)>, '__name__': '__main__', '__doc__': None, '__package__': None}
>>>> class Runoob:
>...     a = 1
>... 
>>>> print(vars(Runoob))
>{'a': 1, '__module__': '__main__', '__doc__': None}
>>>> runoob = Runoob()
>>>> print(vars(runoob))
>{}
>```

>### classmethod
>classmethod 修饰符对应的函数不需要实例化，不需要 self 参数，但第一个参数需要是表示自身类的 cls 参数，可以来调用类的属性，类的方法，实例化对象等。返回函数的类方法。

>### getattr(object, name[, default])
>getattr() 函数用于返回一个对象属性值。返回对象属性值。
>- object -- 对象。
>- name -- 字符串，对象属性。
>- default -- 默认返回值，如果不提供该参数，在没有对应属性时，将触发 AttributeError。

>### map() 
>map()根据提供的函数对指定序列做映射。
>第一个参数 function 以参数序列中的每一个元素调用 function 函数，返回包含每次 function 函数返回值的新列表。
>

### Python3 面向对象
Python从设计之初就已经是一门面向对象的语言，正因为如此，在Python中创建一个类和对象是很容易的。本章节我们将详细介绍Python的面向对象编程。
如果你以前没有接触过面向对象的编程语言，那你可能需要先了解一些面向对象语言的一些基本特征，在头脑里头形成一个基本的面向对象的概念，这样有助于你更容易的学习Python的面向对象编程。
接下来我们先来简单的了解下面向对象的一些基本特征。
### 面向对象技术简介
#### 类(Class): 用来描述具有相同的属性和方法的对象的集合。
它定义了该集合中每个对象所共有的属性和方法。对象是类的实例。
- 方法：类中定义的函数。
- 类变量：类变量在整个实例化的对象中是公用的。类变量定义在类中且在函数体之外。类变量通常不作为实例变量使用。
- 数据成员：类变量或者实例变量用于处理类及其实例对象的相关的数据。
- 方法重写：如果从父类继承的方法不能满足子类的需求，可以对其进行改写，这个过程叫方法的覆盖（override），也称为方法的重写。
- 局部变量：定义在方法中的变量，只作用于当前实例的类。
- 实例变量：在类的声明中，属性是用变量来表示的。这种变量就称为实例变量，是在类声明的内部但是在类的其他成员方法之外声明的。

#### 继承：即一个派生类（derived class）继承基类（base class）的字段和方法。
继承也允许把一个派生类的对象作为一个基类对象对待。例如，有这样一个设计：一个Dog类型的对象派生自Animal类，这是模拟"是一个（is-a）"关系（例图，Dog是一个Animal）。
#### 实例化：创建一个类的实例，类的具体对象。
对象：通过类定义的数据结构实例。对象包括两个数据成员（类变量和实例变量）和方法。
和其它编程语言相比，Python 在尽可能不增加新的语法和语义的情况下加入了类机制。
Python中的类提供了面向对象编程的所有基本功能：类的继承机制允许多个基类，派生类可以覆盖基类中的任何方法，方法中可以调用基类中的同名方法。
对象可以包含任意数量和类型的数据。
类定义
语法格式如下：
```python
class ClassName:
    <statement-1>
    .
    .
    .
    <statement-N>
```
类实例化后，可以使用其属性，实际上，创建一个类之后，可以通过类名访问其属性。
类对象
类对象支持两种操作：属性引用和实例化。
属性引用使用和 Python 中所有的属性引用一样的标准语法：obj.name。
类对象创建后，类命名空间中所有的命名都是有效属性名。所以如果类定义是这样:
实例(Python 3.0+)
```python
#!/usr/bin/python3
 
class MyClass:
    """一个简单的类实例"""
    i = 12345
    def f(self):
        return 'hello world'
 
# 实例化类
x = MyClass()
``` 
# 访问类的属性和方法
print("MyClass 类的属性 i 为：", x.i)
print("MyClass 类的方法 f 输出为：", x.f())
以上创建了一个新的类实例并将该对象赋给局部变量 x，x 为空的对象。
执行以上程序输出结果为：
MyClass 类的属性 i 为： 12345
MyClass 类的方法 f 输出为： hello world
类有一个名为 __init__() 的特殊方法（构造方法），该方法在类实例化时会自动调用，像下面这样：
def __init__(self):
    self.data = []
类定义了 __init__() 方法，类的实例化操作会自动调用 __init__() 方法。如下实例化类 MyClass，对应的 __init__() 方法就会被调用:
x = MyClass()
当然， __init__() 方法可以有参数，参数通过 __init__() 传递到类的实例化操作上。例如:
实例(Python 3.0+)
```python
#!/usr/bin/python3
 
class Complex:
    def __init__(self, realpart, imagpart):
        self.r = realpart
        self.i = imagpart
x = Complex(3.0, -4.5)
print(x.r, x.i)   # 输出结果：3.0 -4.5
```
self代表类的实例，而非类
类的方法与普通的函数只有一个特别的区别——它们必须有一个额外的第一个参数名称, 按照惯例它的名称是 self。
```python
class Test:
    def prt(self):
        print(self)
        print(self.__class__)
 
t = Test()
t.prt()
```
以上实例执行结果为：
<__main__.Test instance at 0x100771878>
__main__.Test
从执行结果可以很明显的看出，self 代表的是类的实例，代表当前对象的地址，而 self.class 则指向类。
self 不是 python 关键字，我们把他换成 runoob 也是可以正常执行的:
```python
class Test:
    def prt(runoob):
        print(runoob)
        print(runoob.__class__)
 
t = Test()
t.prt()
```
以上实例执行结果为：
<__main__.Test instance at 0x100771878>
__main__.Test
类的方法
在类的内部，使用 def 关键字来定义一个方法，与一般函数定义不同，类方法必须包含参数 self, 且为第一个参数，self 代表的是类的实例。
实例(Python 3.0+)
```python
#!/usr/bin/python3
 
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
# 实例化类
p = people('runoob',10,30)
p.speak()
执行以上程序输出结果为：
runoob 说: 我 10 岁。
继承
Python 同样支持类的继承，如果一种语言不支持继承，类就没有什么意义。派生类的定义如下所示:
class DerivedClassName(BaseClassName1):
    <statement-1>
    .
    .
    .
    <statement-N>
```
需要注意圆括号中基类的顺序，若是基类中有相同的方法名，而在子类使用时未指定，python从左至右搜索 即方法在子类中未找到时，从左到右查找基类中是否包含方法。
BaseClassName（示例中的基类名）必须与派生类定义在一个作用域内。除了类，还可以用表达式，基类定义在另一个模块中时这一点非常有用:
class DerivedClassName(modname.BaseClassName):
实例(Python 3.0+)
```python
#!/usr/bin/python3
 
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
#单继承示例
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
 
 
 
s = student('ken',10,60,3)
s.speak()
执行以上程序输出结果为：
ken 说: 我 10 岁了，我在读 3 年级
多继承
Python同样有限的支持多继承形式。多继承的类定义形如下例:
class DerivedClassName(Base1, Base2, Base3):
    <statement-1>
    .
    .
    .
    <statement-N>
```
需要注意圆括号中父类的顺序，若是父类中有相同的方法名，而在子类使用时未指定，python从左至右搜索 即方法在子类中未找到时，从左到右查找父类中是否包含方法。
实例(Python 3.0+)
```python
#!/usr/bin/python3
 
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
#单继承示例
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
 
#另一个类，多重继承之前的准备
class speaker():
    topic = ''
    name = ''
    def __init__(self,n,t):
        self.name = n
        self.topic = t
    def speak(self):
        print("我叫 %s，我是一个演说家，我演讲的主题是 %s"%(self.name,self.topic))
 
#多重继承
class sample(speaker,student):
    a =''
    def __init__(self,n,a,w,g,t):
        student.__init__(self,n,a,w,g)
        speaker.__init__(self,n,t)
 
test = sample("Tim",25,80,4,"Python")
test.speak()   #方法名同，默认调用的是在括号中排前地父类的方法
```
执行以上程序输出结果为：
我叫 Tim，我是一个演说家，我演讲的主题是 Python
方法重写
如果你的父类方法的功能不能满足你的需求，你可以在子类重写你父类的方法，实例如下：
实例(Python 3.0+)
```python
#!/usr/bin/python3
 
class Parent:        # 定义父类
   def myMethod(self):
      print ('调用父类方法')
 
class Child(Parent): # 定义子类
   def myMethod(self):
      print ('调用子类方法')
 
c = Child()          # 子类实例
c.myMethod()         # 子类调用重写方法
super(Child,c).myMethod() #用子类对象调用父类已被覆盖的方法
```
super() 函数是用于调用父类(超类)的一个方法。
执行以上程序输出结果为：
```python
调用子类方法
调用父类方法
```
更多文档：
### Python 子类继承父类构造函数说明
- 类属性与方法:
- 类的私有属性:
__private_attrs：两个下划线开头，声明该属性为私有，不能在类的外部被使用或直接访问。在类内部的方法中使用时 self.__private_attrs。
类的方法
在类的内部，使用 def 关键字来定义一个方法，与一般函数定义不同，类方法必须包含参数 self，且为第一个参数，self 代表的是类的实例。
self 的名字并不是规定死的，也可以使用 this，但是最好还是按照约定是用 self。

- 类的私有方法:
__private_method：两个下划线开头，声明该方法为私有方法，只能在类的内部调用 ，不能在类的外部调用。self.__private_methods。
实例
类的私有属性实例如下：
实例(Python 3.0+)
```python
#!/usr/bin/python3
 
class JustCounter:
    __secretCount = 0  # 私有变量
    publicCount = 0    # 公开变量
 
    def count(self):
        self.__secretCount += 1
        self.publicCount += 1
        print (self.__secretCount)
 
counter = JustCounter()
counter.count()
counter.count()
print (counter.publicCount)
print (counter.__secretCount)  # 报错，实例不能访问私有变量
执行以上程序输出结果为：
1
2
2
Traceback (most recent call last):
  File "test.py", line 16, in <module>
    print (counter.__secretCount)  # 报错，实例不能访问私有变量
AttributeError: 'JustCounter' object has no attribute '__secretCount'
```
类的私有方法实例如下：
```python
#!/usr/bin/python3
 
class Site:
    def __init__(self, name, url):
        self.name = name       # public
        self.__url = url   # private
 
    def who(self):
        print('name  : ', self.name)
        print('url : ', self.__url)
 
    def __foo(self):          # 私有方法
        print('这是私有方法')
 
    def foo(self):            # 公共方法
        print('这是公共方法')
        self.__foo()
 
x = Site('菜鸟教程', 'www.runoob.com')
x.who()        # 正常输出
x.foo()        # 正常输出
x.__foo()      # 报错
```
以上实例执行结果：

类的专有方法：
__init__ : 构造函数，在生成对象时调用
__del__ : 析构函数，释放对象时使用
__repr__ : 打印，转换
__setitem__ : 按照索引赋值
__getitem__: 按照索引获取值
__len__: 获得长度
__cmp__: 比较运算
__call__: 函数调用
__add__: 加运算
__sub__: 减运算
__mul__: 乘运算
__truediv__: 除运算
__mod__: 求余运算
__pow__: 乘方
运算符重载
Python同样支持运算符重载，我们可以对类的专有方法进行重载，实例如下：
实例(Python 3.0+)
```python
#!/usr/bin/python3
 
class Vector:
   def __init__(self, a, b):
      self.a = a
      self.b = b
 
   def __str__(self):
      return 'Vector (%d, %d)' % (self.a, self.b)
   
   def __add__(self,other):
      return Vector(self.a + other.a, self.b + other.b)
 
v1 = Vector(2,10)
v2 = Vector(5,-2)
print (v1 + v2)
```
以上代码执行结果如下所示:
Vector(7,8)


### Python3 标准库概览
操作系统接口
os模块提供了不少与操作系统相关联的函数。
```python
>>> import os
>>> os.getcwd()      # 返回当前的工作目录
'C:\\Python34'
>>> os.chdir('/server/accesslogs')   # 修改当前的工作目录
>>> os.system('mkdir today')   # 执行系统命令 mkdir 
0
```
建议使用 "import os" 风格而非 "from os import *"。这样可以保证随操作系统不同而有所变化的 os.open() 不会覆盖内置函数 open()。
在使用 os 这样的大型模块时内置的 dir() 和 help() 函数非常有用:
```python
>>> import os
>>> dir(os)
<returns a list of all module functions>
>>> help(os)
<returns an extensive manual page created from the module's docstrings>
```
针对日常的文件和目录管理任务，:mod:shutil 模块提供了一个易于使用的高级接口:
```python
>>> import shutil
>>> shutil.copyfile('data.db', 'archive.db')
>>> shutil.move('/build/executables', 'installdir')
```
#### 文件通配符
glob模块提供了一个函数用于从目录通配符搜索中生成文件列表:
```python
>>> import glob
>>> glob.glob('*.py')
['primes.py', 'random.py', 'quote.py']
```
#### 命令行参数
通用工具脚本经常调用命令行参数。这些命令行参数以链表形式存储于 sys 模块的 argv 变量。例如在命令行中执行 "python demo.py one two three" 后可以得到以下输出结果:
```python
>>> import sys
>>> print(sys.argv)
```
[Out] `['demo.py', 'one', 'two', 'three']`

#### 错误输出重定向和程序终止
sys 还有 stdin，stdout 和 stderr 属性，即使在 stdout 被重定向时，后者也可以用于显示警告和错误信息。
```python
>>> sys.stderr.write('Warning, log file not found starting a new one\n')
```
`Warning, log file not found starting a new one
大多脚本的定向终止都使用 "sys.exit()"。`

#### 字符串正则匹配
re模块为高级字符串处理提供了正则表达式工具。对于复杂的匹配和处理，正则表达式提供了简洁、优化的解决方案:
```python
>>> import re
>>> re.findall(r'\bf[a-z]*', 'which foot or hand fell fastest')
['foot', 'fell', 'fastest']
>>> re.sub(r'(\b[a-z]+) \1', r'\1', 'cat in the the hat')
'cat in the hat'
```
如果只需要简单的功能，应该首先考虑字符串方法，因为它们非常简单，易于阅读和调试:
```python
>>> 'tea for too'.replace('too', 'two')
'tea for two'
```
#### 数学
math模块为浮点运算提供了对底层C函数库的访问:
```python
>>> import math
>>> math.cos(math.pi / 4)
0.70710678118654757
>>> math.log(1024, 2)
10.0
```
random提供了生成随机数的工具。
```python
>>> import random
>>> random.choice(['apple', 'pear', 'banana'])
'apple'
>>> random.sample(range(100), 10)   # sampling without replacement
[30, 83, 16, 4, 8, 81, 41, 50, 18, 33]
>>> random.random()    # random float
0.17970987693706186
>>> random.randrange(6)    # random integer chosen from range(6)
4
```

#### 访问 互联网
有几个模块用于访问互联网以及处理网络通信协议。其中最简单的两个是用于处理从 urls 接收的数据的 urllib.request 以及用于发送电子邮件的 smtplib:
```python
>>> from urllib.request import urlopen
>>> for line in urlopen('http://tycho.usno.navy.mil/cgi-bin/timer.pl'):
...     line = line.decode('utf-8')  # Decoding the binary data to text.
...     if 'EST' in line or 'EDT' in line:  # look for Eastern Time
...         print(line)

<BR>Nov. 25, 09:43:32 PM EST

>>> import smtplib
>>> server = smtplib.SMTP('localhost')
>>> server.sendmail('soothsayer@example.org', 'jcaesar@example.org',
... """To: jcaesar@example.org
... From: soothsayer@example.org
...
... Beware the Ides of March.
... """)
>>> server.quit()
```
注意第二个例子需要本地有一个在运行的邮件服务器。

#### 日期和时间
datetime模块为日期和时间处理同时提供了简单和复杂的方法。
支持日期和时间算法的同时，实现的重点放在更有效的处理和格式化输出。
该模块还支持时区处理:
```python
>>> # dates are easily constructed and formatted
>>> from datetime import date
>>> now = date.today()
>>> now
datetime.date(2003, 12, 2)
>>> now.strftime("%m-%d-%y. %d %b %Y is a %A on the %d day of %B.")
'12-02-03. 02 Dec 2003 is a Tuesday on the 02 day of December.'

>>> # dates support calendar arithmetic
>>> birthday = date(1964, 7, 31)
>>> age = now - birthday
>>> age.days
14368
```
#### 数据压缩
以下模块直接支持通用的数据打包和压缩格式：zlib，gzip，bz2，zipfile，以及 tarfile。
```python
>>> import zlib
>>> s = b'witch which has which witches wrist watch'
>>> len(s)
41
>>> t = zlib.compress(s)
>>> len(t)
37
>>> zlib.decompress(t)
b'witch which has which witches wrist watch'
>>> zlib.crc32(s)
226805979
```

#### 性能度量
有些用户对了解解决同一问题的不同方法之间的性能差异很感兴趣。Python 提供了一个度量工具，为这些问题提供了直接答案。
例如，使用元组封装和拆封来交换元素看起来要比使用传统的方法要诱人的多,timeit 证明了现代的方法更快一些。
```python
>>> from timeit import Timer
>>> Timer('t=a; a=b; b=t', 'a=1; b=2').timeit()
0.57535828626024577
>>> Timer('a,b = b,a', 'a=1; b=2').timeit()
0.54962537085770791
```
相对于 timeit 的细粒度，:mod:profile 和 pstats 模块提供了针对更大代码块的时间度量工具。
#### 测试模块
开发高质量软件的方法之一是为每一个函数开发测试代码，并且在开发过程中经常进行测试
doctest模块提供了一个工具，扫描模块并根据程序中内嵌的文档字符串执行测试。
测试构造如同简单的将它的输出结果剪切并粘贴到文档字符串中。
通过用户提供的例子，它强化了文档，允许 doctest 模块确认代码的结果是否与文档一致:
```python
def average(values):
    """Computes the arithmetic mean of a list of numbers.

    >>> print(average([20, 30, 70]))
    40.0
    """
    return sum(values) / len(values)
```
```python
import doctest
doctest.testmod()   # 自动验证嵌入测试
```
unittest模块不像 doctest模块那么容易使用，不过它可以在一个独立的文件里提供一个更全面的测试集:
```python
import unittest

class TestStatisticalFunctions(unittest.TestCase):

    def test_average(self):
        self.assertEqual(average([20, 30, 70]), 40.0)
        self.assertEqual(round(average([1, 5, 7]), 1), 4.3)
        self.assertRaises(ZeroDivisionError, average, [])
        self.assertRaises(TypeError, average, 20, 30, 70)

unittest.main() # Calling from the command line invokes all tests
```

### Python3 正则表达式
正则表达式是一个特殊的字符序列，它能帮助你方便的检查一个字符串是否与某种模式匹配。
Python 自1.5版本起增加了re 模块，它提供 Perl 风格的正则表达式模式。
re 模块使 Python 语言拥有全部的正则表达式功能。
compile 函数根据一个模式字符串和可选的标志参数生成一个正则表达式对象。该对象拥有一系列方法用于正则表达式匹配和替换。
re 模块也提供了与这些方法功能完全一致的函数，这些函数使用一个模式字符串做为它们的第一个参数。
本章节主要介绍 Python 中常用的正则表达式处理函数，如果你对正则表达式不了解，可以查看我们的 正则表达式 - 教程。
#### re.match函数
re.match 尝试从字符串的起始位置匹配一个模式，如果不是起始位置匹配成功的话，match()就返回none。
函数语法：
```python
re.match(pattern, string, flags=0)
```
函数参数说明：

|参数	|描述|
|-|-|
|pattern	|匹配的正则表达式|
|string|	要匹配的字符串。|
flags|	标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。参见：正则表达式修饰符 - 可选标志|

匹配成功re.match方法返回一个匹配的对象，否则返回None。
我们可以使用group(num) 或 groups() 匹配对象函数来获取匹配表达式。

|匹配对象方法|	描述|
|----|----|
|group(num=0)	|匹配的整个表达式的字符串，group() 可以一次输入多个组号，在这种情况下它将返回一个包含那些组所对应值的元组。|
|-|-|
|groups()	|返回一个包含所有小组字符串的元组，从 1 到 所含的小组号。|

实例
```python
#!/usr/bin/python
 
import re
print(re.match('www', 'www.runoob.com').span())  # 在起始位置匹配
print(re.match('com', 'www.runoob.com'))         # 不在起始位置匹配
```
以上实例运行输出结果为：
(0, 3)
None
实例
```python
#!/usr/bin/python3
import re
 
line = "Cats are smarter than dogs"
# .* 表示任意匹配除换行符（\n、\r）之外的任何单个或多个字符
matchObj = re.match( r'(.*) are (.*?) .*', line, re.M|re.I)
 
if matchObj:
   print ("matchObj.group() : ", matchObj.group())
   print ("matchObj.group(1) : ", matchObj.group(1))
   print ("matchObj.group(2) : ", matchObj.group(2))
else:
   print ("No match!!")
```
以上实例执行结果如下：
```
matchObj.group() :  Cats are smarter than dogs
matchObj.group(1) :  Cats
matchObj.group(2) :  smarter
```
#### re.search方法
re.search 扫描整个字符串并返回第一个成功的匹配。
函数语法：
```python
re.search(pattern, string, flags=0)
```
函数参数说明：
pattern	：匹配的正则表达式
string	：要匹配的字符串。
flags	：标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。参见：正则表达式修饰符 - 可选标志


匹配成功re.search方法返回一个匹配的对象，否则返回None。
我们可以使用group(num) 或 groups() 匹配对象函数来获取匹配表达式。
group(num=0)	：匹配的整个表达式的字符串，group() 可以一次输入多个组号，在这种情况下它将返回一个包含那些组所对应值的元组。
groups()	：返回一个包含所有小组字符串的元组，从 1 到 所含的小组号。
```python
实例
#!/usr/bin/python3
 
import re
 
print(re.search('www', 'www.runoob.com').span())  # 在起始位置匹配
print(re.search('com', 'www.runoob.com').span())         # 不在起始位置匹配
```
以上实例运行输出结果为：
```
(0, 3)
(11, 14)
```
实例
```python
#!/usr/bin/python3
 
import re
 
line = "Cats are smarter than dogs";
 
searchObj = re.search( r'(.*) are (.*?) .*', line, re.M|re.I)
 
if searchObj:
   print ("searchObj.group() : ", searchObj.group())
   print ("searchObj.group(1) : ", searchObj.group(1))
   print ("searchObj.group(2) : ", searchObj.group(2))
else:
   print ("Nothing found!!")
```   
以上实例执行结果如下：
```
searchObj.group() :  Cats are smarter than dogs
searchObj.group(1) :  Cats
searchObj.group(2) :  smarter
```
re.match与re.search的区别
re.match只匹配字符串的开始，如果字符串开始不符合正则表达式，则匹配失败，函数返回None；而re.search匹配整个字符串，直到找到一个匹配。
实例
```python
#!/usr/bin/python3
 
import re
 
line = "Cats are smarter than dogs";
 
matchObj = re.match( r'dogs', line, re.M|re.I)
if matchObj:
   print ("match --> matchObj.group() : ", matchObj.group())
else:
   print ("No match!!")

matchObj = re.search( r'dogs', line, re.M|re.I)
if matchObj:
   print ("search --> matchObj.group() : ", matchObj.group())
else:
   print ("No match!!")
```
以上实例运行结果如下：
```
No match!!
search --> matchObj.group() :  dogs
```
#### 检索和替换
Python 的re模块提供了re.sub用于替换字符串中的匹配项。
语法：
```python
re.sub(pattern, repl, string, count=0, flags=0)
```
参数：
pattern : 正则中的模式字符串。
repl : 替换的字符串，也可为一个函数。
string : 要被查找替换的原始字符串。
count : 模式匹配后替换的最大次数，默认 0 表示替换所有的匹配。
flags : 编译时用的匹配模式，数字形式。
前三个为必选参数，后两个为可选参数。
实例
```python
#!/usr/bin/python3
import re
 
phone = "2004-959-559 # 这是一个电话号码"
 
# 删除注释
num = re.sub(r'#.*$', "", phone)
print ("电话号码 : ", num)
 
# 移除非数字的内容
num = re.sub(r'\D', "", phone)
print ("电话号码 : ", num)
```
以上实例执行结果如下：
```
电话号码 :  2004-959-559 
电话号码 :  2004959559
```
#### repl 参数是一个函数
以下实例中将字符串中的匹配的数字乘于 2：
实例
```python
#!/usr/bin/python
 
import re
 
# 将匹配的数字乘于 2
def double(matched):
    value = int(matched.group('value'))
    return str(value * 2)
 
s = 'A23G4HFD567'
print(re.sub('(?P<value>\d+)', double, s))
```
执行输出结果为：
```
A46G8HFD1134
```

#### compile 函数
compile 函数用于编译正则表达式，生成一个正则表达式（ Pattern ）对象，供 match() 和 search() 这两个函数使用。
语法格式为：
```python
re.compile(pattern[, flags])
```
参数：
pattern : 一个字符串形式的正则表达式
flags 可选，表示匹配模式，比如忽略大小写，多行模式等，具体参数为：
re.I 忽略大小写
re.L 表示特殊字符集 \w, \W, \b, \B, \s, \S 依赖于当前环境
re.M 多行模式
re.S 即为' . '并且包括换行符在内的任意字符（' . '不包括换行符）
re.U 表示特殊字符集 \w, \W, \b, \B, \d, \D, \s, \S 依赖于 Unicode 字符属性数据库
re.X 为了增加可读性，忽略空格和' # '后面的注释
实例
```python
>>>import re
>>> pattern = re.compile(r'\d+')                    # 用于匹配至少一个数字
>>> m = pattern.match('one12twothree34four')        # 查找头部，没有匹配
>>> print m
None
>>> m = pattern.match('one12twothree34four', 2, 10) # 从'e'的位置开始匹配，没有匹配
>>> print m
None
>>> m = pattern.match('one12twothree34four', 3, 10) # 从'1'的位置开始匹配，正好匹配
>>> print m                                         # 返回一个 Match 对象
<_sre.SRE_Match object at 0x10a42aac0>
>>> m.group(0)   # 可省略 0
'12'
>>> m.start(0)   # 可省略 0
3
>>> m.end(0)     # 可省略 0
5
>>> m.span(0)    # 可省略 0
(3, 5)
```
在上面，当匹配成功时返回一个 Match 对象，其中：
group([group1, …]) 方法用于获得一个或多个分组匹配的字符串，当要获得整个匹配的子串时，可直接使用 group() 或 group(0)；
start([group]) 方法用于获取分组匹配的子串在整个字符串中的起始位置（子串第一个字符的索引），参数默认值为 0；
end([group]) 方法用于获取分组匹配的子串在整个字符串中的结束位置（子串最后一个字符的索引+1），参数默认值为 0；
span([group]) 方法返回 (start(group), end(group))。
再看看一个例子：
实例
```python
>>>import re
>>> pattern = re.compile(r'([a-z]+) ([a-z]+)', re.I)   # re.I 表示忽略大小写
>>> m = pattern.match('Hello World Wide Web')
>>> print m                               # 匹配成功，返回一个 Match 对象
<_sre.SRE_Match object at 0x10bea83e8>
>>> m.group(0)                            # 返回匹配成功的整个子串
'Hello World'
>>> m.span(0)                             # 返回匹配成功的整个子串的索引
(0, 11)
>>> m.group(1)                            # 返回第一个分组匹配成功的子串
'Hello'
>>> m.span(1)                             # 返回第一个分组匹配成功的子串的索引
(0, 5)
>>> m.group(2)                            # 返回第二个分组匹配成功的子串
'World'
>>> m.span(2)                             # 返回第二个分组匹配成功的子串索引
(6, 11)
>>> m.groups()                            # 等价于 (m.group(1), m.group(2), ...)
('Hello', 'World')
>>> m.group(3)                 # 不存在第三个分组
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: no such group
```
#### findall

在字符串中找到正则表达式所匹配的所有子串，并返回一个列表，如果没有找到匹配的，则返回空列表。
注意： match 和 search 是匹配一次 findall 匹配所有。
语法格式为：
```python
findall(string[, pos[, endpos]])
```
参数：
string 待匹配的字符串。
pos 可选参数，指定字符串的起始位置，默认为 0。
endpos 可选参数，指定字符串的结束位置，默认为字符串的长度。
查找字符串中的所有数字：
实例
```python
import re
 
pattern = re.compile(r'\d+')   # 查找数字
result1 = pattern.findall('runoob 123 google 456')
result2 = pattern.findall('run88oob123google456', 0, 10)
 
print(result1)
print(result2)
```
输出结果：
```
['123', '456']
['88', '12']
```
#### re.finditer
和 findall 类似，在字符串中找到正则表达式所匹配的所有子串，并把它们作为一个迭代器返回。
re.finditer(pattern, string, flags=0)
参数：
参数	描述
pattern	匹配的正则表达式
string	要匹配的字符串。
flags	标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。参见：正则表达式修饰符 - 可选标志
实例
```python
import re
 
it = re.finditer(r"\d+","12a32bc43jf3") 
for match in it: 
    print (match.group() )
```
输出结果：
```
12 
32 
43 
3
```
#### re.split
split 方法按照能够匹配的子串将字符串分割后返回列表，它的使用形式如下：
re.split(pattern, string[, maxsplit=0, flags=0])
参数：
pattern:匹配的正则表达式
string	:要匹配的字符串。
maxsplit	:分隔次数，maxsplit=1 分隔一次，默认为 0，不限制次数。
flags	:标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。参见：正则表达式修饰符 - 可选标志
实例
```python
>>>import re
>>> re.split('\W+', 'runoob, runoob, runoob.')
['runoob', 'runoob', 'runoob', '']
>>> re.split('(\W+)', ' runoob, runoob, runoob.') 
['', ' ', 'runoob', ', ', 'runoob', ', ', 'runoob', '.', '']
>>> re.split('\W+', ' runoob, runoob, runoob.', 1) 
['', 'runoob, runoob, runoob.']
 
>>> re.split('a*', 'hello world')   # 对于一个找不到匹配的字符串而言，split 不会对其作出分割
['hello world']
```
#### 正则表达式对象
>### re.RegexObject
re.compile() 返回 RegexObject 对象。
>### re.MatchObject
group() 返回被 RE 匹配的字符串。
- start() 返回匹配开始的位置
- end() 返回匹配结束的位置
- span() 返回一个元组包含匹配 (开始,结束) 的位置
>### 正则表达式修饰符 - 可选标志
正则表达式可以包含一些可选标志修饰符来控制匹配的模式。修饰符被指定为一个可选的标志。多个标志可以通过按位 OR(|) 它们来指定。如 re.I | re.M 被设置成 I 和 M 标志：
re.I	: 使匹配对大小写不敏感
re.L	: 做本地化识别（locale-aware）匹配
re.M	: 多行匹配，影响 ^ 和 $
re.S	: 匹配包括换行在内的所有字符
re.U	: 根据Unicode字符集解析字符。这个标志影响 \w, \W, \b, \B.
re.X	: 该标志通过给予你更灵活的格式以便你将正则表达式写得更易于理解。

>### 正则表达式模式
模式字符串使用特殊的语法来表示一个正则表达式：
字母和数字表示他们自身。一个正则表达式模式中的字母和数字匹配同样的字符串。
多数字母和数字前加一个反斜杠时会拥有不同的含义。
标点符号只有被转义时才匹配自身，否则它们表示特殊的含义。
反斜杠本身需要使用反斜杠转义。
由于正则表达式通常都包含反斜杠，所以你最好使用原始字符串来表示它们。模式元素(如 r'\t'，等价于 \\t )匹配相应的特殊字符。
下表列出了正则表达式模式语法中的特殊元素。如果你使用模式的同时提供了可选的标志参数，某些模式元素的含义会改变。
>模式	/ 描述
^	: 匹配字符串的开头
$	: 匹配字符串的末尾。
.	: 匹配任意字符，除了换行符，当re.DOTALL标记被指定时，则可以匹配包括换行符的任意字符。
[...]	: 用来表示一组字符,单独列出：[amk] 匹配 'a'，'m'或'k'
[^...]	: 不在[]中的字符：[^abc] 匹配除了a,b,c之外的字符。
re*	: 匹配0个或多个的表达式。
re+	: 匹配1个或多个的表达式。
re?	: 匹配0个或1个由前面的正则表达式定义的片段，非贪婪方式
re{ n}	: 匹配n个前面表达式。例如，"o{2}"不能匹配"Bob"中的"o"，但是能匹配"food"中的两个o。
re{ n,}	: 精确匹配n个前面表达式。例如，"o{2,}"不能匹配"Bob"中的"o"，但能匹配"foooood"中的所有o。"o{1,}"等价于"o+"。"o{0,}"则等价于"o*"。
re{ n, m}	: 匹配 n 到 m 次由前面的正则表达式定义的片段，贪婪方式
a| b	: 匹配a或b
(re)	: 匹配括号内的表达式，也表示一个组
(?imx)	: 正则表达式包含三种可选标志：i, m, 或 x 。只影响括号中的区域。
(?-imx)	: 正则表达式关闭 i, m, 或 x 可选标志。只影响括号中的区域。
(?: re)	: 类似 (...), 但是不表示一个组
(?imx: re)	: 在括号中使用i, m, 或 x 可选标志
(?-imx: re)	: 在括号中不使用i, m, 或 x 可选标志
(?#...)	: 注释.
(?= re)	: 前向肯定界定符。如果所含正则表达式，以 ... 表示，在当前位置成功匹配时成功，否则失败。但一旦所含表达式已经尝试，匹配引擎根本没有提高；模式的剩余部分还要尝试界定符的右边。
(?! re)	: 前向否定界定符。与肯定界定符相反；当所含表达式不能在字符串当前位置匹配时成功。
(?> re)	: 匹配的独立模式，省去回溯。
\w	: 匹配数字字母下划线
\W	: 匹配非数字字母下划线
\s	: 匹配任意空白字符，等价于 [\t\n\r\f]。
\S	: 匹配任意非空字符
\d	: 匹配任意数字，等价于 [0-9]。
\D	: 匹配任意非数字
\A	: 匹配字符串开始
\Z	: 匹配字符串结束，如果是存在换行，只匹配到换行前的结束字符串。
\z	: 匹配字符串结束
\G	: 匹配最后匹配完成的位置。
\b	: 匹配一个单词边界，也就是指单词和空格间的位置。例如， 'er\b' 可以匹配"never" 中的 'er'，但不能匹配 "verb" 中的 'er'。
\B	: 匹配非单词边界。'er\B' 能匹配 "verb" 中的 'er'，但不能匹配 "never" 中的 'er'。
\n, \t, 等。	: 匹配一个换行符。匹配一个制表符, 等
\1...\9	: 匹配第n个分组的内容。
\10	: 匹配第n个分组的内容，如果它经匹配。否则指的是八进制字符码的表达式。
>### 正则表达式实例
>字符匹配
实例	/ 描述
python	: 匹配 "python".

>字符类
实例	/ 描述
[Pp]ython	: 匹配 "Python" 或 "python"
rub[ye]	: 匹配 "ruby" 或 "rube"
[aeiou]	: 匹配中括号内的任意一个字母
[0-9]	: 匹配任何数字。类似于 [0123456789]
[a-z]	: 匹配任何小写字母
[A-Z]	: 匹配任何大写字母
[a-zA-Z0-9]	: 匹配任何字母及数字
[^aeiou]	: 除了aeiou字母以外的所有字符
[^0-9]	: 匹配除了数字外的字符

>特殊字符类
实例	/ 描述
.	: 匹配除 "\n" 之外的任何单个字符。要匹配包括 '\n' 在内的任何字符，请使用象 '[.\n]' 的模式。
\d	: 匹配一个数字字符。等价于 [0-9]。
\D	: 匹配一个非数字字符。等价于 [^0-9]。
\s	: 匹配任何空白字符，包括空格、制表符、换页符等等。等价于 [ \f\n\r\t\v]。
\S	: 匹配任何非空白字符。等价于 [^ \f\n\r\t\v]。
\w	: 匹配包括下划线的任何单词字符。等价于'[A-Za-z0-9_]'。
\W	: 匹配任何非单词字符。等价于 '[^A-Za-z0-9_]'。

### CGI是什麼?

通用網關接口或CGI，是一組定義信息如何在Web服務器和自定義腳本之間交換的標準。
CGI規範目前保持是由NCSA 和 NCSA 維護和定義如下。
通用網關接口或CGI，是外部網關方案，如HTTP服務器的信息服務器的接口標準。
目前的版本是CGI/1.1，而CGI/1.2目前正在定製中。

### 網頁瀏覽
要了解CGI的概念，讓我們看看當點擊一個超鏈接，瀏覽某一個網頁或URL發生什麼情況。
瀏覽器觸發HTTP Web服務器和網址也就是文件名的請求。
Web服務器將解析URL，並尋找，如果找到該文件，然後將其發送回瀏覽器中的文件名，否則將表示請求了錯誤文件的錯誤消息。
Web瀏覽器需要從Web服務器和顯示器接收到的文件信息或錯誤信息的響應。
然而，也可以設置在HTTP服務器，以便每當在某個目錄中的文件被請求文件不被發送回;相反，它被執行的程序，無論該程序的輸出被發送回瀏覽器顯示。此函數被稱為公共網關接口CGI或與程序稱為CGI腳本。這些CGI程序可以是一個Python腳本，Perl腳本，Shell腳本，C或C++程序等等。![](https://i.imgur.com/4iA30Qj.png)
### Web 服务器支持及配置
在你进行 CGI 编程前，确保您的 Web 服务器支持 CGI 及已经配置了 CGI 的处理程序。
Apache 支持 CGI 配置：
设置好CGI目录：
`ScriptAlias /cgi-bin/ /var/www/cgi-bin/`
所有的HTTP服务器执行 CGI 程序都保存在一个预先配置的目录。这个目录被称为 CGI 目录，并按照惯例，它被命名为 /var/www/cgi-bin 目录。
CGI 文件的扩展名为 .cgi，python 也可以使用 .py 扩展名。
默认情况下，Linux 服务器配置运行的 cgi-bin 目录中为 /var/www。
如果你想指定其他运行 CGI 脚本的目录，可以修改 httpd.conf 配置文件，如下所示：
```python
<Directory "/var/www/cgi-bin">
   AllowOverride None
   Options +ExecCGI
   Order allow,deny
   Allow from all
</Directory>
```
在 AddHandler 中添加 `.py` 后缀，这样我们就可以访问 .py 结尾的 python 脚本文件：
`AddHandler cgi-script .cgi .pl .py`
### 第一个CGI程序
我们使用 Python 创建第一个 CGI 程序，文件名为 hello.py，文件位于 `/var/www/cgi-bin `目录中，内容如下：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

print "Content-type:text/html"
print                               # 空行，告诉服务器结束头部
print '<html>'
print '<head>'
print '<meta charset="utf-8">'
print '<title>Hello World - 我的第一个 CGI 程序！</title>'
print '</head>'
print '<body>'
print '<h2>Hello World! 我是来自菜鸟教程的第一CGI程序</h2>'
print '</body>'
print '</html>'
```
文件保存后修改 hello.py，修改文件权限为 755：
`chmod 755 hello.py `
以上程序在浏览器访问 http://localhost/cgi-bin/hello.py 显示结果如下：
`Hello World! 我是来自菜鸟教程的第一CGI程序`
这个的hello.py脚本是一个简单的Python脚本，脚本第一行的输出内容"Content-type:text/html"发送到浏览器并告知浏览器显示的内容类型为"text/html"。
用 print 输出一个空行用于告诉服务器结束头部信息。
### HTTP头部
hello.py文件内容中的" Content-type:text/html"即为HTTP头部的一部分，它会发送给浏览器告诉浏览器文件的内容类型。
HTTP头部的格式如下：
`HTTP 字段名: 字段内容`
例如：
`Content-type: text/html`
以下介绍了CGI程序中HTTP头部经常使用的信息：
`Content-type:`	 : 请求的与实体对应的MIME信息。例如: Content-type:text/html
`Expires: Date`:	响应过期的日期和时间
`Location: URL`:	用来重定向接收方到非请求URL的位置来完成请求或标识新的资源
`Last-modified: Date`:	请求资源的最后修改时间
`Content-length: N`:	请求的内容长度
`Set-Cookie: String	`:设置Http Cookie
### CGI环境变量
所有的CGI程序都接收以下的环境变量，这些变量在CGI程序中发挥了重要的作用：

|变量名|	描述|
|-|-|
CONTENT_TYPE|	这个环境变量的值指示所传递来的信息的MIME类型。目前，环境变量CONTENT_TYPE一般都是：application/x-www-form-urlencoded,他表示数据来自于HTML表单。|
CONTENT_LENGTH	|如果服务器与CGI程序信息的传递方式是POST，这个环境变量即使从标准输入STDIN中可以读到的有效数据的字节数。这个环境变量在读取所输入的数据时必须使用。|
HTTP_COOKIE|	客户机内的 COOKIE 内容。|
HTTP_USER_AGENT	|提供包含了版本数或其他专有数据的客户浏览器信息。|
PATH_INFO	|这个环境变量的值表示紧接在CGI程序名之后的其他路径信息。它常常作为CGI程序的参数出现。|
QUERY_STRING	|如果服务器与CGI程序信息的传递方式是GET，这个环境变量的值即使所传递的信息。这个信息经跟在CGI程序名的后面，两者中间用一个问号'?'分隔。|
REMOTE_ADDR|	这个环境变量的值是发送请求的客户机的IP地址，例如上面的192.168.1.67。这个值总是存在的。而且它是Web客户机需要提供给Web服务器的唯一标识，可以在CGI程序中用它来区分不同的Web客户机。|
REMOTE_HOST	|这个环境变量的值包含发送CGI请求的客户机的主机名。如果不支持你想查询，则无需定义此环境变量。|
REQUEST_METHOD	|提供脚本被调用的方法。对于使用 HTTP/1.0 协议的脚本，仅 GET 和 POST 有意义。|
SCRIPT_FILENAME	|CGI脚本的完整路径|
SCRIPT_NAME	|CGI脚本的的名称|
SERVER_NAME	|这是你的 WEB 服务器的主机名、别名或IP地址。|
SERVER_SOFTWARE	|这个环境变量的值包含了调用CGI程序的HTTP服务器的名称和版本号。例如，上面的值为Apache/2.2.14(Unix)|

以下是一个简单的CGI脚本输出CGI的环境变量：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
# filename:test.py

import os

print "Content-type: text/html"
print
print "<meta charset=\"utf-8\">"
print "<b>环境变量</b><br>";
print "<ul>"
for key in os.environ.keys():
    print "<li><span style='color:green'>%30s </span> : %s </li>" % (key,os.environ[key])
print "</ul>"
```
将以上点保存为 test.py ,并修改文件权限为 755，执行结果如下：
![](https://i.imgur.com/JBy3x3g.png)

### GET和POST方法
浏览器客户端通过两种方法向服务器传递信息，这两种方法就是 GET 方法和 POST 方法。
使用GET方法传输数据
GET方法发送编码后的用户信息到服务端，数据信息包含在请求页面的URL上，以"?"号分割, 如下所示：
```
http://www.test.com/cgi-bin/hello.py?key1=value1&key2=value2
```
有关 GET 请求的其他一些注释：
GET 请求可被缓存
GET 请求保留在浏览器历史记录中
GET 请求可被收藏为书签
GET 请求不应在处理敏感数据时使用
GET 请求有长度限制
GET 请求只应当用于取回数据
### 简单的url实例：GET方法
以下是一个简单的URL，使用GET方法向hello_get.py程序发送两个参数：
```python
/cgi-bin/test.py?name=菜鸟教程&url=http://www.runoob.com
```
以下为hello_get.py文件的代码：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

# filename：test.py

# CGI处理模块
import cgi, cgitb 

# 创建 FieldStorage 的实例化
form = cgi.FieldStorage() 

# 获取数据
site_name = form.getvalue('name')
site_url  = form.getvalue('url')

print "Content-type:text/html"
print
print "<html>"
print "<head>"
print "<meta charset=\"utf-8\">"
print "<title>菜鸟教程 CGI 测试实例</title>"
print "</head>"
print "<body>"
print "<h2>%s官网：%s</h2>" % (site_name, site_url)
print "</body>"
print "</html>"
```
文件保存后修改 hello_get.py，修改文件权限为 755：
`chmod 755 hello_get.py `

### 简单的表单实例：GET方法
以下是一个通过HTML的表单使用GET方法向服务器发送两个数据，提交的服务器脚本同样是hello_get.py文件，hello_get.html 代码如下：
```python
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<form action="/cgi-bin/hello_get.py" method="get">
站点名称: <input type="text" name="name">  <br />

站点 URL: <input type="text" name="url" />
<input type="submit" value="提交" />
</form>
</body>
</html>
```
默认情况下 cgi-bin 目录只能存放脚本文件，我们将 hello_get.html 存储在 test 目录下，修改文件权限为 755：
`chmod 755 hello_get.html`
### 使用POST方法传递数据
使用POST方法向服务器传递数据是更安全可靠的，像一些敏感信息如用户密码等需要使用POST传输数据。
以下同样是hello_get.py ，它也可以处理浏览器提交的POST表单数据:
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

# CGI处理模块
import cgi, cgitb 

# 创建 FieldStorage 的实例化
form = cgi.FieldStorage() 

# 获取数据
site_name = form.getvalue('name')
site_url  = form.getvalue('url')

print "Content-type:text/html"
print
print "<html>"
print "<head>"
print "<meta charset=\"utf-8\">"
print "<title>菜鸟教程 CGI 测试实例</title>"
print "</head>"
print "<body>"
print "<h2>%s官网：%s</h2>" % (site_name, site_url)
print "</body>"
print "</html>"
```
以下为表单通过POST方法（method="post"）向服务器脚本 hello_get.py 提交数据:
```python
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<form action="/cgi-bin/hello_get.py" method="post">
站点名称: <input type="text" name="name">  <br />

站点 URL: <input type="text" name="url" />
<input type="submit" value="提交" />
</form>
</body>
</html>
```
### 通过CGI程序传递checkbox数据
checkbox用于提交一个或者多个选项数据，HTML代码如下：
```python
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<form action="/cgi-bin/checkbox.py" method="POST" target="_blank">
<input type="checkbox" name="runoob" value="on" /> 菜鸟教程
<input type="checkbox" name="google" value="on" /> Google
<input type="submit" value="选择站点" />
</form>
</body>
</html>
```
以下为 checkbox.py 文件的代码：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

# 引入 CGI 处理模块 
import cgi, cgitb 

# 创建 FieldStorage的实例 
form = cgi.FieldStorage() 

# 接收字段数据
if form.getvalue('google'):
   google_flag = "是"
else:
   google_flag = "否"

if form.getvalue('runoob'):
   runoob_flag = "是"
else:
   runoob_flag = "否"

print "Content-type:text/html"
print
print "<html>"
print "<head>"
print "<meta charset=\"utf-8\">"
print "<title>菜鸟教程 CGI 测试实例</title>"
print "</head>"
print "<body>"
print "<h2> 菜鸟教程是否选择了 : %s</h2>" % runoob_flag
print "<h2> Google 是否选择了 : %s</h2>" % google_flag
print "</body>"
print "</html>"
```
修改 checkbox.py 权限：
`chmod 755 checkbox.py`

### 通过CGI程序传递Radio数据
Radio 只向服务器传递一个数据，HTML代码如下：
```python
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<form action="/cgi-bin/radiobutton.py" method="post" target="_blank">
<input type="radio" name="site" value="runoob" /> 菜鸟教程
<input type="radio" name="site" value="google" /> Google
<input type="submit" value="提交" />
</form>
</body>
</html>
```
radiobutton.py 脚本代码如下：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

# 引入 CGI 处理模块 
import cgi, cgitb 

# 创建 FieldStorage的实例 
form = cgi.FieldStorage() 

# 接收字段数据
if form.getvalue('site'):
   site = form.getvalue('site')
else:
   site = "提交数据为空"

print "Content-type:text/html"
print
print "<html>"
print "<head>"
print "<meta charset=\"utf-8\">"
print "<title>菜鸟教程 CGI 测试实例</title>"
print "</head>"
print "<body>"
print "<h2> 选中的网站是 %s</h2>" % site
print "</body>"
print "</html>"
```
修改 radiobutton.py 权限：
`chmod 755 radiobutton.py`
### 通过CGI程序传递 Textarea 数据
Textarea 向服务器传递多行数据，HTML代码如下：
```python
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<form action="/cgi-bin/textarea.py" method="post" target="_blank">
<textarea name="textcontent" cols="40" rows="4">
在这里输入内容...
</textarea>
<input type="submit" value="提交" />
</form>
</body>
</html>
```
textarea.py 脚本代码如下：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

# 引入 CGI 处理模块 
import cgi, cgitb 

# 创建 FieldStorage的实例 
form = cgi.FieldStorage() 

# 接收字段数据
if form.getvalue('textcontent'):
   text_content = form.getvalue('textcontent')
else:
   text_content = "没有内容"

print "Content-type:text/html"
print
print "<html>"
print "<head>";
print "<meta charset=\"utf-8\">"
print "<title>菜鸟教程 CGI 测试实例</title>"
print "</head>"
print "<body>"
print "<h2> 输入的内容是：%s</h2>" % text_content
print "</body>"
print "</html>"
```
修改 textarea.py 权限：
`chmod 755 textarea.py`
#### 通过CGI程序传递下拉数据。
HTML 下拉框代码如下：
```python
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<form action="/cgi-bin/dropdown.py" method="post" target="_blank">
<select name="dropdown">
<option value="runoob" selected>菜鸟教程</option>
<option value="google">Google</option>
</select>
<input type="submit" value="提交"/>
</form>
</body>
</html>
```
dropdown.py 脚本代码如下所示：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

# 引入 CGI 处理模块 
import cgi, cgitb 

# 创建 FieldStorage的实例 
form = cgi.FieldStorage() 

# 接收字段数据
if form.getvalue('dropdown'):
   dropdown_value = form.getvalue('dropdown')
else:
   dropdown_value = "没有内容"

print "Content-type:text/html"
print
print "<html>"
print "<head>"
print "<meta charset=\"utf-8\">"
print "<title>菜鸟教程 CGI 测试实例</title>"
print "</head>"
print "<body>"
print "<h2> 选中的选项是：%s</h2>" % dropdown_value
print "</body>"
print "</html>"
```
修改 dropdown.py 权限：
`chmod 755 dropdown.py`
### CGI中使用Cookie
在 http 协议一个很大的缺点就是不对用户身份的进行判断，这样给编程人员带来很大的不便， 而 cookie 功能的出现弥补了这个不足。
cookie 就是在客户访问脚本的同时，通过客户的浏览器，在客户硬盘上写入纪录数据 ，当下次客户访问脚本时取回数据信息，从而达到身份判别的功能，cookie 常用在身份校验中。
　
>### cookie的语法
http cookie的发送是通过http头部来实现的，他早于文件的传递，头部set-cookie的语法如下：
Set-cookie:name=name;expires=date;path=path;domain=domain;secure 
name=name: 需要设置cookie的值(name不能使用";"和","号),有多个name值时用 ";" 分隔，例如：name1=name1;name2=name2;name3=name3。
expires=date: cookie的有效期限,格式： expires="Wdy,DD-Mon-YYYY HH:MM:SS"
path=path: 设置cookie支持的路径,如果path是一个路径，则cookie对这个目录下的所有文件及子目录生效，例如： path="/cgi-bin/"，如果path是一个文件，则cookie指对这个文件生效，例如：path="/cgi-bin/cookie.cgi"。
domain=domain: 对cookie生效的域名，例如：domain="www.runoob.com"
secure: 如果给出此标志，表示cookie只能通过SSL协议的https服务器来传递。
cookie的接收是通过设置环境变量HTTP_COOKIE来实现的，CGI程序可以通过检索该变量获取cookie信息。
Cookie设置
Cookie的设置非常简单，cookie会在http头部单独发送。以下实例在cookie中设置了name 和 expires：
```pyrhon
#!/usr/bin/python
# -*- coding: UTF-8 -*-
# 
print 'Content-Type: text/html'
print 'Set-Cookie: name="菜鸟教程";expires=Wed, 28 Aug 2016 18:30:00 GMT'
print
print """
<html>
    <head>
        <meta charset="utf-8">
        <title>菜鸟教程(runoob.com)</title>
    </head>
    <body>
        <h1>Cookie set OK!</h1>
    </body>
</html>
"""
```
将以上代码保存到 cookie_set.py，并修改 cookie_set.py 权限：
`chmod 755 cookie_set.py`
以上实例使用了 Set-Cookie 头信息来设置Cookie信息，可选项中设置了Cookie的其他属性，如过期时间Expires，域名Domain，路径Path。这些信息设置在 "Content-type:text/html"之前。
检索Cookie信息
Cookie信息检索页非常简单，Cookie信息存储在CGI的环境变量HTTP_COOKIE中，存储格式如下：
`key1=value1;key2=value2;key3=value3....`
以下是一个简单的CGI检索cookie信息的程序：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

# 导入模块
import os
import Cookie

print "Content-type: text/html"
print

print """
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<h1>读取cookie信息</h1>
"""

if 'HTTP_COOKIE' in os.environ:
    cookie_string=os.environ.get('HTTP_COOKIE')
    c=Cookie.SimpleCookie()
    c.load(cookie_string)

    try:
        data=c['name'].value
        print "cookie data: "+data+"<br>"
    except KeyError:
        print "cookie 没有设置或者已过去<br>"
print """
</body>
</html>

"""
```
将以上代码保存到 cookie_get.py，并修改 cookie_get.py 权限：
`chmod 755 cookie_get.py`
以上 cookie 设置颜色 Gif 如下所示：

文件上传实例
HTML设置上传文件的表单需要设置 enctype 属性为 multipart/form-data，代码如下所示：
```python
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
 <form enctype="multipart/form-data" 
                     action="/cgi-bin/save_file.py" method="post">
   <p>选中文件: <input type="file" name="filename" /></p>
   <p><input type="submit" value="上传" /></p>
   </form>
</body>
</html>
```
save_file.py脚本文件代码如下：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import cgi, os
import cgitb; cgitb.enable()

form = cgi.FieldStorage()

# 获取文件名
fileitem = form['filename']

# 检测文件是否上传
if fileitem.filename:
   # 设置文件路径 
   fn = os.path.basename(fileitem.filename)
   open('/tmp/' + fn, 'wb').write(fileitem.file.read())

   message = '文件 "' + fn + '" 上传成功'
   
else:
   message = '文件没有上传'
   
print """\
Content-Type: text/html\n
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
   <p>%s</p>
</body>
</html>
""" % (message,)
```
将以上代码保存到 save_file.py，并修改 save_file.py 权限：
`chmod 755 save_file.py`
以上 cookie 设置颜色 Gif 如下所示：

如果你使用的系统是Unix/Linux，你必须替换文件分隔符，在window下只需要使用open()语句即可：
> fn = os.path.basename(fileitem.filename.replace("\\", "/" ))

### 文件下载对话框
我们先在当前目录下创建 foo.txt 文件，用于程序的下载。
文件下载通过设置HTTP头信息来实现，功能代码如下：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

# HTTP 头部
print "Content-Disposition: attachment; filename=\"foo.txt\"";
print
# 打开文件
fo = open("foo.txt", "rb")

str = fo.read();
print str

# 关闭文件
fo.close()
```
## Python 操作 MySQL 数据库
Python 标准数据库接口为 Python DB-API，Python DB-API为开发人员提供了数据库应用编程接口。
Python 数据库接口支持非常多的数据库，你可以选择适合你项目的数据库：
>GadFly
mSQL
MySQL
PostgreSQL
Microsoft SQL Server 2000
Informix
Interbase
Oracle
Sybase

你可以访问Python数据库接口及API查看详细的支持数据库列表。
不同的数据库你需要下载不同的DB API模块，例如你需要访问Oracle数据库和Mysql数据，你需要下载Oracle和MySQL数据库模块。
DB-API 是一个规范. 它定义了一系列必须的对象和数据库存取方式, 以便为各种各样的底层数据库系统和多种多样的数据库接口程序提供一致的访问接口 。
Python的DB-API，为大多数的数据库实现了接口，使用它连接各数据库后，就可以用相同的方式操作各数据库。
Python DB-API使用流程：
>引入 API 模块。
获取与数据库的连接。
执行SQL语句和存储过程。
关闭数据库连接。

### 什么是MySQLdb?
MySQLdb 是用于Python链接Mysql数据库的接口，它实现了 Python 数据库 API 规范 V2.0，基于 MySQL C API 上建立的。
### 如何安装MySQLdb?
为了用DB-API编写MySQL脚本，必须确保已经安装了MySQL。复制以下代码，并执行：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import MySQLdb
```
如果执行后的输出结果如下所示，意味着你没有安装 MySQLdb 模块：
```python
Traceback (most recent call last):
  File "test.py", line 3, in <module>
    import MySQLdb
ImportError: No module named MySQLdb
```
事先安装MySQLdb，请访问 (linux系統）https://pypi.python.org/pypi/MySQL-python
>相关资源下载链接如下：
>Python2.7（个人觉得这个版本语句兼容性高，适合入门）：
>https://blog.python.org/2018/05/python-2715-released.html
>Mysql8.0.12（请根据自己需要选择版本）：
>https://dev.mysql.com/downloads/installer/
>Mysql官方数据库连接器（请根据自己需要选择）：
>https://dev.mysql.com/downloads/connector/python/
从这里可选择适合您的平台的安装包，分为预编译的二进制文件和源代码安装包。
如果您选择二进制文件发行版本的话，安装过程基本安装提示即可完成。如果从源代码进行安装的话，则需要切换到MySQLdb发行版本的顶级目录，并键入下列命令:
```python
$ gunzip MySQL-python-1.2.2.tar.gz
$ tar -xvf MySQL-python-1.2.2.tar
$ cd MySQL-python-1.2.2
$ python setup.py build
$ python setup.py install
```
注意：请确保您有root权限来安装上述模块。
数据库连接
连接数据库前，请先确认以下事项：
您已经创建了数据库 TESTDB.
在TESTDB数据库中您已经创建了表 EMPLOYEE
EMPLOYEE表字段为 FIRST_NAME, LAST_NAME, AGE, SEX 和 INCOME。
连接数据库TESTDB使用的用户名为 "testuser" ，密码为 "test123",你可以可以自己设定或者直接使用root用户名及其密码，Mysql数据库用户授权请使用Grant命令。
在你的机子上已经安装了 Python MySQLdb 模块。
如果您对sql语句不熟悉，可以访问我们的 SQL基础教程
>实例：
以下实例链接Mysql的TESTDB数据库：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import MySQLdb

# 打开数据库连接
db = MySQLdb.connect("localhost", "testuser", "test123", "TESTDB", charset='utf8' )

# 使用cursor()方法获取操作游标 
cursor = db.cursor()

# 使用execute方法执行SQL语句
cursor.execute("SELECT VERSION()")

# 使用 fetchone() 方法获取一条数据
data = cursor.fetchone()

print "Database version : %s " % data

# 关闭数据库连接
db.close()
```
执行以上脚本输出结果如下：
`Database version : 5.0.45`
### 创建数据库表
如果数据库连接存在我们可以使用execute()方法来为数据库创建表，如下所示创建表EMPLOYEE：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import MySQLdb

# 打开数据库连接
db = MySQLdb.connect("localhost", "testuser", "test123", "TESTDB", charset='utf8' )

# 使用cursor()方法获取操作游标 
cursor = db.cursor()

# 如果数据表已经存在使用 execute() 方法删除表。
cursor.execute("DROP TABLE IF EXISTS EMPLOYEE")

# 创建数据表SQL语句
sql = """CREATE TABLE EMPLOYEE (
         FIRST_NAME  CHAR(20) NOT NULL,
         LAST_NAME  CHAR(20),
         AGE INT,  
         SEX CHAR(1),
         INCOME FLOAT )"""

cursor.execute(sql)

# 关闭数据库连接
db.close()
```
数据库插入操作
以下实例使用执行 SQL INSERT 语句向表 EMPLOYEE 插入记录：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import MySQLdb

# 打开数据库连接
db = MySQLdb.connect("localhost", "testuser", "test123", "TESTDB", charset='utf8' )

# 使用cursor()方法获取操作游标 
cursor = db.cursor()

# SQL 插入语句
sql = """INSERT INTO EMPLOYEE(FIRST_NAME,
         LAST_NAME, AGE, SEX, INCOME)
         VALUES ('Mac', 'Mohan', 20, 'M', 2000)"""
try:
   # 执行sql语句
   cursor.execute(sql)
   # 提交到数据库执行
   db.commit()
except:
   # Rollback in case there is any error
   db.rollback()

# 关闭数据库连接
db.close()
```
以上例子也可以写成如下形式：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import MySQLdb

# 打开数据库连接
db = MySQLdb.connect("localhost", "testuser", "test123", "TESTDB", charset='utf8' )

# 使用cursor()方法获取操作游标 
cursor = db.cursor()

# SQL 插入语句
sql = "INSERT INTO EMPLOYEE(FIRST_NAME, \
       LAST_NAME, AGE, SEX, INCOME) \
       VALUES (%s, %s, %s, %s, %s )" % \
       ('Mac', 'Mohan', 20, 'M', 2000)
try:
   # 执行sql语句
   cursor.execute(sql)
   # 提交到数据库执行
   db.commit()
except:
   # 发生错误时回滚
   db.rollback()

# 关闭数据库连接
db.close()
```

实例：
以下代码使用变量向SQL语句中传递参数:
:::info
user_id = "test123"
password = "password"

con.execute('insert into Login values(%s, %s)' % \
             (user_id, password))
:::
### 数据库查询操作
Python查询Mysql使用 fetchone() 方法获取单条数据, 使用fetchall() 方法获取多条数据。
>fetchone(): 该方法获取下一个查询结果集。结果集是一个对象
fetchall():接收全部的返回结果行.
rowcount: 这是一个只读属性，并返回执行execute()方法后影响的行数。

实例：
查询EMPLOYEE表中salary（工资）字段大于1000的所有数据：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import MySQLdb

# 打开数据库连接
db = MySQLdb.connect("localhost", "testuser", "test123", "TESTDB", charset='utf8' )

# 使用cursor()方法获取操作游标 
cursor = db.cursor()

# SQL 查询语句
sql = "SELECT * FROM EMPLOYEE \
       WHERE INCOME > %s" % (1000)
try:
   # 执行SQL语句
   cursor.execute(sql)
   # 获取所有记录列表
   results = cursor.fetchall()
   for row in results:
      fname = row[0]
      lname = row[1]
      age = row[2]
      sex = row[3]
      income = row[4]
      # 打印结果
      print "fname=%s,lname=%s,age=%s,sex=%s,income=%s" % \
             (fname, lname, age, sex, income )
except:
   print "Error: unable to fecth data"

# 关闭数据库连接
db.close()
```
以上脚本执行结果如下：
`fname=Mac, lname=Mohan, age=20, sex=M, income=2000`
### 数据库更新操作
更新操作用于更新数据表的的数据，以下实例将 EMPLOYEE 表中的 SEX 字段为 'M' 的 AGE 字段递增 1：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import MySQLdb

# 打开数据库连接
db = MySQLdb.connect("localhost", "testuser", "test123", "TESTDB", charset='utf8' )

# 使用cursor()方法获取操作游标 
cursor = db.cursor()

# SQL 更新语句
sql = "UPDATE EMPLOYEE SET AGE = AGE + 1 WHERE SEX = '%c'" % ('M')
try:
   # 执行SQL语句
   cursor.execute(sql)
   # 提交到数据库执行
   db.commit()
except:
   # 发生错误时回滚
   db.rollback()

# 关闭数据库连接
db.close()
```

### 删除操作
删除操作用于删除数据表中的数据，以下实例演示了删除数据表 EMPLOYEE 中 AGE 大于 20 的所有数据：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import MySQLdb

# 打开数据库连接
db = MySQLdb.connect("localhost", "testuser", "test123", "TESTDB", charset='utf8' )

# 使用cursor()方法获取操作游标 
cursor = db.cursor()

# SQL 删除语句
sql = "DELETE FROM EMPLOYEE WHERE AGE > %s" % (20)
try:
   # 执行SQL语句
   cursor.execute(sql)
   # 提交修改
   db.commit()
except:
   # 发生错误时回滚
   db.rollback()

# 关闭连接
db.close()
```
### 执行事务
事务机制可以确保数据一致性。
事务应该具有4个属性：原子性、一致性、隔离性、持久性。这四个属性通常称为ACID特性。
- 原子性（atomicity）。一个事务是一个不可分割的工作单位，事务中包括的诸操作要么都做，要么都不做。
- 一致性（consistency）。事务必须是使数据库从一个一致性状态变到另一个一致性状态。一致性与原子性是密切相关的。
- 隔离性（isolation）。一个事务的执行不能被其他事务干扰。即一个事务内部的操作及使用的数据对并发的其他事务是隔离的，并发执行的各个事务之间不能互相干扰。
- 持久性（durability）。持续性也称永久性（permanence），指一个事务一旦提交，它对数据库中数据的改变就应该是永久性的。接下来的其他操作或故障不应该对其有任何影响。
### Python DB API 2.0 的事务提供了两个方法 commit 或 rollback。
实例：
```python
# SQL删除记录语句
sql = "DELETE FROM EMPLOYEE WHERE AGE > %s" % (20)
try:
   # 执行SQL语句
   cursor.execute(sql)
   # 向数据库提交
   db.commit()
except:
   # 发生错误时回滚
   db.rollback()
```
对于支持事务的数据库， 在Python数据库编程中，当游标建立之时，就自动开始了一个隐形的数据库事务。
commit()方法游标的所有更新操作，rollback（）方法回滚当前游标的所有操作。每一个方法都开始了一个新的事务。
### 错误处理
DB API中定义了一些数据库操作的错误及异常，下表列出了这些错误和异常:

|异常	|描述|
|-|-|
Warning	|当有严重警告时触发，例如插入数据是被截断等等。必须是 StandardError 的子类。|
Error	|警告以外所有其他错误类。必须是 StandardError 的子类。|
InterfaceError	|当有数据库接口模块本身的错误（而不是数据库的错误）发生时触发。 必须是Error的子类。|
DatabaseError	|和数据库有关的错误发生时触发。 必须是Error的子类。|
DataError	|当有数据处理时的错误发生时触发，例如：除零错误，数据超范围等等。 必须是DatabaseError的子类。|
OperationalError	|指非用户控制的，而是操作数据库时发生的错误。例如：连接意外断开、 数据库名未找到、事务处理失败、内存分配错误等等操作数据库是发生的错误。 必须是DatabaseError的子类。|
IntegrityError	|完整性相关的错误，例如外键检查失败等。必须是DatabaseError子类。|
InternalError	|数据库的内部错误，例如游标（cursor）失效了、事务同步失败等等。 必须是DatabaseError子类。|
ProgrammingError	|程序错误，例如数据表（table）没找到或已存在、SQL语句语法错误、 参数数量错误等等。必须是DatabaseError的子类。|
NotSupportedError	|不支持错误，指使用了数据库不支持的函数或API等。例如在连接对象上 使用.rollback()函数，然而数据库并不支持事务或者事务已关闭。 必须是DatabaseError的子类。|

>关于Mysql的连接，经过摸索，建议正文修改一下，使用mysql官方提供的连接器，我目前安装的mysql是8.0.12版本，数据库安装完成后，可以安装“mysql-connector-python-8.0.12-py2.7-windows-x86-64bit”，当然了，要根据自己的操作系统和python版本以及位数进行选择，我是win10的64位，python2.7的64位，故选择的上述插件，安装完成后，直接使用以下代码进行测试：
>```python
># -*- coding:utf-8 -*-
>
>import mysql.connector
>
># 打开数据库连接（请根据自己的用户名、密码及数据库名称进行修改）
>cnn = mysql.connector.connect(user='root',passwd='root',database='testdb')
>
># 使用cursor()方法获取操作游标 
>cursor = cnn.cursor()
>
># 使用execute方法执行SQL语句
>cursor.execute("SELECT VERSION()")
>
># 使用 fetchone() 方法获取一条数据
>
>data = cursor.fetchone()
>print "Database version : %s " % data
>
># 执行sql语句
>cnn.close() 
>```
>显示的结果应该如下：
>`Database version : 8.0.12 `
>显示的结果应该如下：
>`Database version : 8.0.12`
### Python 网络编程
Python 提供了两个级别访问的网络服务：
- 低级别的网络服务支持基本的 Socket，它提供了标准的 BSD Sockets API，可以访问底层操作系统Socket接口的全部方法。
- 高级别的网络服务模块 SocketServer， 它提供了服务器中心类，可以简化网络服务器的开发。
#### 什么是 Socket?
Socket又称"套接字"，应用程序通常通过"套接字"向网络发出请求或者应答网络请求，使主机间或者一台计算机上的进程间可以通讯。
### socket()函数
Python 中，我们用 socket（）函数来创建套接字，语法格式如下：
`socket.socket([family[, type[, proto]]])`
>参数
family: 套接字家族可以使AF_UNIX或者AF_INET
type: 套接字类型可以根据是面向连接的还是非连接分为SOCK_STREAM或SOCK_DGRAM
protocol: 一般不填默认为0.

### Socket 对象(内建)方法
服务器端套接字

|函数	|描述|
|----|----|
s.bind()|	绑定地址（host,port）到套接字， 在AF_INET下,以元组（host,port）的形式表示地址。|
s.listen()	|开始TCP监听。backlog指定在拒绝连接之前，操作系统可以挂起的最大连接数量。该值至少为1，大部分应用程序设为5就可以了。|
s.accept()	|被动接受TCP客户端连接,(阻塞式)等待连接的到来
客户端套接字|
s.connect()	|主动初始化TCP服务器连接，。一般address的格式为元组（hostname,port），如果连接出错，返回socket.error错误。|
s.connect_ex()	|connect()函数的扩展版本,出错时返回出错码,而不是抛出异常|

公共用途的套接字函数

|函数	|描述|
|---|---|
s.recv()	|接收TCP数据，数据以字符串形式返回，bufsize指定要接收的最大数据量。flag提供有关消息的其他信息，通常可以忽略。|
s.send()	|发送TCP数据，将string中的数据发送到连接的套接字。返回值是要发送的字节数量，该数量可能小于string的字节大小。|
s.sendall()	|完整发送TCP数据，完整发送TCP数据。将string中的数据发送到连接的套接字，但在返回之前会尝试发送所有数据。成功返回None，失败则抛出异常。|
s.recvfrom()	|接收UDP数据，与recv()类似，但返回值是（data,address）。其中data是包含接收数据的字符串，address是发送数据的套接字地址。|
s.sendto()|	发送UDP数据，将数据发送到套接字，address是形式为（ipaddr，port）的元组，指定远程地址。返回值是发送的字节数。|
s.close()	|关闭套接字|
s.getpeername()|	返回连接套接字的远程地址。返回值通常是元组（ipaddr,port）。|
s.getsockname()|	返回套接字自己的地址。通常是一个元组(ipaddr,port)|
s.setsockopt(level,optname,value)	|设置给定套接字选项的值。|
s.getsockopt(level,optname[.buflen])	|返回套接字选项的值。|
s.settimeout(timeout)|	设置套接字操作的超时期，timeout是一个浮点数，单位是秒。值为None表示没有超时期。一般，超时期应该在刚创建套接字时设置，因为它们可能用于连接的操作（如connect()）|
s.gettimeout()	|返回当前超时期的值，单位是秒，如果没有设置超时期，则返回None。|
s.fileno()	|返回套接字的文件描述符。|
s.setblocking(flag)	|如果flag为0，则将套接字设为非阻塞模式，否则将套接字设为阻塞模式（默认值）。非阻塞模式下，如果调用recv()没有发现任何数据，或send()调用无法立即发送数据，那么将引起socket.error异常。|
s.makefile()	|创建一个与该套接字相关连的文件|

### 簡單實例
>### 服务端
>我们使用 socket 模块的 socket 函数来创建一个 socket 对象。socket 对象可以通过调用其他函数来设置一个 socket 服务。
现在我们可以通过调用 bind(hostname, port) 函数来指定服务的 port(端口)。
接着，我们调用 socket 对象的 accept 方法。该方法等待客户端的连接，并返回 connection 对象，表示已连接到客户端。

完整代码如下：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
# 文件名：server.py
 
import socket               # 导入 socket 模块
 
s = socket.socket()         # 创建 socket 对象
host = socket.gethostname() # 获取本地主机名
port = 12345                # 设置端口
s.bind((host, port))        # 绑定端口
 
s.listen(5)                 # 等待客户端连接
while True:
    c,addr = s.accept()     # 建立客户端连接
    print '连接地址：', addr
    c.send('欢迎访问菜鸟教程！')
    c.close()                # 关闭连接
```
>### 客户端
>接下来我们写一个简单的客户端实例连接到以上创建的服务。端口号为 12345。
socket.connect(hosname, port ) 方法打开一个 TCP 连接到主机为 hostname 端口为 port 的服务商。连接后我们就可以从服务端获取数据，记住，操作完成后需要关闭连接。

完整代码如下：

```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
# 文件名：client.py
 
import socket               # 导入 socket 模块
 
s = socket.socket()         # 创建 socket 对象
host = socket.gethostname() # 获取本地主机名
port = 12345                # 设置端口号
 
s.connect((host, port))
print s.recv(1024)
s.close()
```
现在我们打开两个终端，第一个终端执行 server.py 文件：
`$ python server.py`
第二个终端执行 client.py 文件：
```
$ python client.py 
欢迎访问菜鸟教程！
```
这时我们再打开第一个终端，就会看到有以下信息输出：
`连接地址： ('192.168.0.118', 62461)`

>#### 再多一點實例：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import sys
reload(sys)
sys.setdefaultencoding('utf8')
import socket
# 建立一个服务端
server = socket.socket(socket.AF_INET,socket.SOCK_STREAM)
server.bind(('localhost',9090)) #绑定要监听的端口
server.listen(5) #开始监听 表示可以使用五个链接排队
while True:# conn就是客户端链接过来而在服务端为期生成的一个链接实例
    conn,addr = server.accept() #等待链接,多个链接的时候就会出现问题,其实返回了两个值
    print(conn,addr)
    while True:
        data = conn.recv(1024)  #接收数据
        print('recive:',data.decode()) #打印接收到的数据
        conn.send(data.upper()) #然后再发送数据
    conn.close()
```
客户端：
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import sys
reload(sys)
sys.setdefaultencoding('utf8')
import socket# 客户端 发送一个数据，再接收一个数据
client = socket.socket(socket.AF_INET,socket.SOCK_STREAM) #声明socket类型，同时生成链接对象
client.connect(('localhost',9090)) #建立一个链接，连接到本地的6969端口
while True:
    # addr = client.accept()
    # print '连接地址：', addr
    msg = '欢迎访问菜鸟教程！'  #strip默认取出字符串的头尾空格
    client.send(msg.encode('utf-8'))  #发送一条信息 python3 只接收btye流
    data = client.recv(1024) #接收一个信息，并指定接收的大小 为1024字节
    print('recv:',data.decode()) #输出我接收的信息
client.close() #关闭这个链接
```


### Python Internet 模块
以下列出了 Python 网络编程的一些重要模块：

|协议	|功能用处	|端口号	|Python 模块|
|-----|----|----|----|
HTTP	|网页访问	|80|	httplib, urllib, xmlrpclib|
NNTP	|阅读和张贴新闻文章，俗称为"帖子"	|119|	nntplib|
FTP	|文件传输|	20|	ftplib, urllib|
SMTP	|发送邮件|	25	|smtplib|
POP3	|接收邮件	|110|	poplib|
IMAP4|	获取邮件|	143|	imaplib|
Telnet|	命令行|	23	|telnetlib|
Gopher	|信息查找|	70|	gopherlib, urllib|

### Python SMTP发送邮件
SMTP（Simple Mail Transfer Protocol）即简单邮件传输协议,它是一组用于由源地址到目的地址传送邮件的规则，由它来控制信件的中转方式。
python的smtplib提供了一种很方便的途径发送电子邮件。它对smtp协议进行了简单的封装。
Python创建 SMTP 对象语法如下：
```python
import smtplib

smtpObj = smtplib.SMTP( [host [, port [, local_hostname]]] )
```
>参数说明：
host: SMTP 服务器主机。 你可以指定主机的ip地址或者域名如: runoob.com，这个是可选参数。
port: 如果你提供了 host 参数, 你需要指定 SMTP 服务使用的端口号，一般情况下 SMTP 端口号为25。
local_hostname: 如果 SMTP 在你的本机上，你只需要指定服务器地址为 localhost 即可。

Python SMTP 对象使用 sendmail 方法发送邮件，语法如下：
`SMTP.sendmail(from_addr, to_addrs, msg[, mail_options, rcpt_options])``

>参数说明：
from_addr: 邮件发送者地址。
to_addrs: 字符串列表，邮件发送地址。
msg: 发送消息
:::info
这里要注意一下第三个参数，msg 是字符串，表示邮件。我们知道邮件一般由标题，发信人，收件人，邮件内容，附件等构成，发送邮件的时候，要注意 msg 的格式。这个格式就是 smtp 协议中定义的格式。
:::
实例
以下执行实例需要你本机已安装了支持 SMTP 的服务，如：sendmail。
以下是一个使用 Python 发送邮件简单的实例：
实例
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import smtplib
from email.mime.text import MIMEText
from email.header import Header
 
sender = 'from@runoob.com'
receivers = ['429240967@qq.com']  # 接收邮件，可设置为你的QQ邮箱或者其他邮箱
 
# 三个参数：第一个为文本内容，第二个 plain 设置文本格式，第三个 utf-8 设置编码
message = MIMEText('Python 邮件发送测试...', 'plain', 'utf-8')
message['From'] = Header("菜鸟教程", 'utf-8')   # 发送者
message['To'] =  Header("测试", 'utf-8')        # 接收者
 
subject = 'Python SMTP 邮件测试'
message['Subject'] = Header(subject, 'utf-8')
 
 
try:
    smtpObj = smtplib.SMTP('localhost')
    smtpObj.sendmail(sender, receivers, message.as_string())
    print "邮件发送成功"
except smtplib.SMTPException:
    print "Error: 无法发送邮件"
```
我们使用三个引号来设置邮件信息，标准邮件需要三个头部信息： From, To, 和 Subject ，每个信息直接使用空行分割。
我们通过实例化 smtplib 模块的 SMTP 对象 smtpObj 来连接到 SMTP 访问，并使用 sendmail 方法来发送信息。
执行以上程序，如果你本机安装 sendmail（邮件传输代理程序），就会输出：
$ python test.py 
邮件发送成功
查看我们的收件箱(一般在垃圾箱)，就可以查看到邮件信息：

如果我们本机没有 sendmail 访问，也可以使用其他邮件服务商的 SMTP 访问（QQ、网易、Google等）。
实例
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import smtplib
from email.mime.text import MIMEText
from email.header import Header
 
# 第三方 SMTP 服务
mail_host="smtp.XXX.com"  #设置服务器
mail_user="XXXX"    #用户名
mail_pass="XXXXXX"   #口令 
 
 
sender = 'from@runoob.com'
receivers = ['429240967@qq.com']  # 接收邮件，可设置为你的QQ邮箱或者其他邮箱
 
message = MIMEText('Python 邮件发送测试...', 'plain', 'utf-8')
message['From'] = Header("菜鸟教程", 'utf-8')
message['To'] =  Header("测试", 'utf-8')
 
subject = 'Python SMTP 邮件测试'
message['Subject'] = Header(subject, 'utf-8')
 
 
try:
    smtpObj = smtplib.SMTP() 
    smtpObj.connect(mail_host, 25)    # 25 为 SMTP 端口号
    smtpObj.login(mail_user,mail_pass)  
    smtpObj.sendmail(sender, receivers, message.as_string())
    print "邮件发送成功"
except smtplib.SMTPException:
    print "Error: 无法发送邮件"
```
使用Python发送HTML格式的邮件
Python发送HTML格式的邮件与发送纯文本消息的邮件不同之处就是将MIMEText中_subtype设置为html。具体代码如下：
实例
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import smtplib
from email.mime.text import MIMEText
from email.header import Header
 
sender = 'from@runoob.com'
receivers = ['429240967@qq.com']  # 接收邮件，可设置为你的QQ邮箱或者其他邮箱
 
mail_msg = """
<p>Python 邮件发送测试...</p>
<p><a href="http://www.runoob.com">这是一个链接</a></p>
"""
message = MIMEText(mail_msg, 'html', 'utf-8')
message['From'] = Header("菜鸟教程", 'utf-8')
message['To'] =  Header("测试", 'utf-8')
 
subject = 'Python SMTP 邮件测试'
message['Subject'] = Header(subject, 'utf-8')
 
 
try:
    smtpObj = smtplib.SMTP('localhost')
    smtpObj.sendmail(sender, receivers, message.as_string())
    print "邮件发送成功"
except smtplib.SMTPException:
    print "Error: 无法发送邮件"
```
执行以上程序，如果你本机安装sendmail，就会输出：
`$ python test.py 
邮件发送成功`
查看我们的收件箱(一般在垃圾箱)，就可以查看到邮件信息。

### Python 发送带附件的邮件
发送带附件的邮件，首先要创建MIMEMultipart()实例，然后构造附件，如果有多个附件，可依次构造，最后利用smtplib.smtp发送。
实例
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart
from email.header import Header
 
sender = 'from@runoob.com'
receivers = ['429240967@qq.com']  # 接收邮件，可设置为你的QQ邮箱或者其他邮箱
 
#创建一个带附件的实例
message = MIMEMultipart()
message['From'] = Header("菜鸟教程", 'utf-8')
message['To'] =  Header("测试", 'utf-8')
subject = 'Python SMTP 邮件测试'
message['Subject'] = Header(subject, 'utf-8')
 
#邮件正文内容
message.attach(MIMEText('这是菜鸟教程Python 邮件发送测试……', 'plain', 'utf-8'))
 
# 构造附件1，传送当前目录下的 test.txt 文件
att1 = MIMEText(open('test.txt', 'rb').read(), 'base64', 'utf-8')
att1["Content-Type"] = 'application/octet-stream'
# 这里的filename可以任意写，写什么名字，邮件中显示什么名字
att1["Content-Disposition"] = 'attachment; filename="test.txt"'
message.attach(att1)
 
# 构造附件2，传送当前目录下的 runoob.txt 文件
att2 = MIMEText(open('runoob.txt', 'rb').read(), 'base64', 'utf-8')
att2["Content-Type"] = 'application/octet-stream'
att2["Content-Disposition"] = 'attachment; filename="runoob.txt"'
message.attach(att2)
 
try:
    smtpObj = smtplib.SMTP('localhost')
    smtpObj.sendmail(sender, receivers, message.as_string())
    print "邮件发送成功"
except smtplib.SMTPException:
    print "Error: 无法发送邮件"
```
輸出結果：
```
$ python test.py 

邮件发送成功
```
查看我们的收件箱(一般在垃圾箱)，就可以查看到邮件信息。

### 在 HTML 文本中添加图片
邮件的 HTML 文本中一般邮件服务商添加外链是无效的，正确添加图片的实例如下所示：
实例
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import smtplib
from email.mime.image import MIMEImage
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
from email.header import Header
 
sender = 'from@runoob.com'
receivers = ['429240967@qq.com']  # 接收邮件，可设置为你的QQ邮箱或者其他邮箱
 
msgRoot = MIMEMultipart('related')
msgRoot['From'] = Header("菜鸟教程", 'utf-8')
msgRoot['To'] =  Header("测试", 'utf-8')
subject = 'Python SMTP 邮件测试'
msgRoot['Subject'] = Header(subject, 'utf-8')
 
msgAlternative = MIMEMultipart('alternative')
msgRoot.attach(msgAlternative)
 
 
mail_msg = """
<p>Python 邮件发送测试...</p>
<p><a href="http://www.runoob.com">菜鸟教程链接</a></p>
<p>图片演示：</p>
<p><img src="cid:image1"></p>
"""
msgAlternative.attach(MIMEText(mail_msg, 'html', 'utf-8'))
 
# 指定图片为当前目录
fp = open('test.png', 'rb')
msgImage = MIMEImage(fp.read())
fp.close()
 
# 定义图片 ID，在 HTML 文本中引用
msgImage.add_header('Content-ID', '<image1>')
msgRoot.attach(msgImage)
 
try:
    smtpObj = smtplib.SMTP('localhost')
    smtpObj.sendmail(sender, receivers, msgRoot.as_string())
    print "邮件发送成功"
except smtplib.SMTPException:
    print "Error: 无法发送邮件"
```
```
$ python test.py 
邮件发送成功
```
查看我们的收件箱(如果在垃圾箱可能需要移动到收件箱才可正常显示)，就可以查看到邮件信息。

### 使用第三方 SMTP 服务发送
这里使用了 QQ 邮箱(你也可以使用 163，Gmail等)的 SMTP 服务，需要做以下配置：

QQ 邮箱通过生成授权码来设置密码：

QQ 邮箱 SMTP 服务器地址：smtp.qq.com，ssl 端口：465。
以下实例你需要修改：发件人邮箱（你的QQ邮箱），密码，收件人邮箱（可发给自己）。 
### QQ SMTP
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import smtplib
from email.mime.text import MIMEText
from email.utils import formataddr
 
my_sender='429240967@qq.com'    # 发件人邮箱账号
my_pass = 'xxxxxxxxxx'              # 发件人邮箱密码
my_user='429240967@qq.com'      # 收件人邮箱账号，我这边发送给自己
def mail():
    ret=True
    try:
        msg=MIMEText('填写邮件内容','plain','utf-8')
        msg['From']=formataddr(["FromRunoob",my_sender])  # 括号里的对应发件人邮箱昵称、发件人邮箱账号
        msg['To']=formataddr(["FK",my_user])              # 括号里的对应收件人邮箱昵称、收件人邮箱账号
        msg['Subject']="菜鸟教程发送邮件测试"                # 邮件的主题，也可以说是标题
 
        server=smtplib.SMTP_SSL("smtp.qq.com", 465)  # 发件人邮箱中的SMTP服务器，端口是25
        server.login(my_sender, my_pass)  # 括号中对应的是发件人邮箱账号、邮箱密码
        server.sendmail(my_sender,[my_user,],msg.as_string())  # 括号中对应的是发件人邮箱账号、收件人邮箱账号、发送邮件
        server.quit()  # 关闭连接
    except Exception:  # 如果 try 中的语句没有执行，则会执行下面的 ret=False
        ret=False
    return ret
 
ret=mail()
if ret:
    print("邮件发送成功")
else:
    print("邮件发送失败")
```
```
$ python test.py 
邮件发送成功
```

## Python 多線程
>
多線程類似於同時執行多個不同程序，多線程運行有如下優點：
- 使用線程可以把佔據長時間的程序中的任務放到後台去處理。
- 用戶界面可以更加吸引人，這樣比如用戶點擊了一個按鈕去觸發某些事件的處理，可以彈出一個進度條來顯示處理的進度
- 程序的運行速度可能加快
- 在一些等待的任務實現上如用戶輸入、文件讀寫和網絡收發數據等，線程就比較有用了。在這種情況下我們可以釋放一些珍貴的資源如內存佔用等等。

線程在執行過程中與進程還是有區別的。每個獨立的進程有一個程序運行的入口、順序執行序列和程序的出口。但是線程不能夠獨立執行，必須依存在應用程序中，由應用程序提供多個線程執行控制。
每個線程都有他自己的一組CPU寄存器，稱為線程的上下文，該上下文反映了線程上次運行該線程的CPU寄存器的狀態。
指令指針和堆棧指針寄存器是線程上下文中兩個最重要的寄存器，線程總是在進程得到上下文中運行的，這些地址都用於標誌擁有線程的進程地址空間中的內存。
線程可以被搶占（中斷）。
在其他線程正在運行時，線程可以暫時擱置（也稱為睡眠） -- 這就是線程的退讓。

### 开始学习Python线程
Python中使用线程有两种方式：函数或者用类来包装线程对象。
函数式：调用thread模块中的start_new_thread()函数来产生新线程。语法如下:
`thread.start_new_thread ( function, args[, kwargs] )`

>参数说明:
function - 线程函数。
args - 传递给线程函数的参数,他必须是个tuple类型。
kwargs - 可选参数。
实例(Python 2.0+)
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import thread
import time
 
# 为线程定义一个函数
def print_time( threadName, delay):
   count = 0
   while count < 5:
      time.sleep(delay)
      count += 1
      print "%s: %s" % ( threadName, time.ctime(time.time()) )
 
# 创建两个线程
try:
   thread.start_new_thread( print_time, ("Thread-1", 2, ) )
   thread.start_new_thread( print_time, ("Thread-2", 4, ) )
except:
   print "Error: unable to start thread"
 
while 1:
   pass
```
执行以上程序输出结果如下：
```
Thread-1: Thu Jan 22 15:42:17 2009
Thread-1: Thu Jan 22 15:42:19 2009
Thread-2: Thu Jan 22 15:42:19 2009
Thread-1: Thu Jan 22 15:42:21 2009
Thread-2: Thu Jan 22 15:42:23 2009
Thread-1: Thu Jan 22 15:42:23 2009
Thread-1: Thu Jan 22 15:42:25 2009
Thread-2: Thu Jan 22 15:42:27 2009
Thread-2: Thu Jan 22 15:42:31 2009
Thread-2: Thu Jan 22 15:42:35 2009
```
线程的结束一般依靠线程函数的自然结束；也可以在线程函数中调用thread.exit()，他抛出SystemExit exception，达到退出线程的目的。
### 线程模块
Python通过两个标准库thread和threading提供对线程的支持。thread提供了低级别的、原始的线程以及一个简单的锁。
threading 模块提供的其他方法：
- threading.currentThread(): 返回当前的线程变量。
- threading.enumerate(): 返回一个包含正在运行的线程的list。正在运行指线程启动后、结束前，不包括启动前和终止后的线程。
- threading.activeCount(): 返回正在运行的线程数量，与len(threading.enumerate())有相同的结果。

除了使用方法外，线程模块同样提供了Thread类来处理线程，Thread类提供了以下方法:
>run(): 用以表示线程活动的方法。
start():启动线程活动。
join([time]): 等待至线程中止。这阻塞调用线程直至线程的join() 方法被调用中止-正常退出或者抛出未处理的异常-或者是可选的超时发生。
isAlive(): 返回线程是否活动的。
getName(): 返回线程名。
setName(): 设置线程名。

### 使用Threading模块创建线程
使用Threading模块创建线程，直接从threading.Thread继承，然后重写__init__方法和run方法：
实例(Python 2.0+)
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import threading
import time
 
exitFlag = 0
 
class myThread (threading.Thread):   #继承父类threading.Thread
    def __init__(self, threadID, name, counter):
        threading.Thread.__init__(self)
        self.threadID = threadID
        self.name = name
        self.counter = counter
    def run(self):                   #把要执行的代码写到run函数里面 线程在创建后会直接运行run函数 
        print "Starting " + self.name
        print_time(self.name, self.counter, 5)
        print "Exiting " + self.name
 
def print_time(threadName, delay, counter):
    while counter:
        if exitFlag:
            (threading.Thread).exit()
        time.sleep(delay)
        print "%s: %s" % (threadName, time.ctime(time.time()))
        counter -= 1
 
# 创建新线程
thread1 = myThread(1, "Thread-1", 1)
thread2 = myThread(2, "Thread-2", 2)
 
# 开启线程
thread1.start()
thread2.start()
 
print "Exiting Main Thread"
```

以上程序执行结果如下；
```
Starting Thread-1
Starting Thread-2
Exiting Main Thread
Thread-1: Thu Mar 21 09:10:03 2013
Thread-1: Thu Mar 21 09:10:04 2013
Thread-2: Thu Mar 21 09:10:04 2013
Thread-1: Thu Mar 21 09:10:05 2013
Thread-1: Thu Mar 21 09:10:06 2013
Thread-2: Thu Mar 21 09:10:06 2013
Thread-1: Thu Mar 21 09:10:07 2013
Exiting Thread-1
Thread-2: Thu Mar 21 09:10:08 2013
Thread-2: Thu Mar 21 09:10:10 2013
Thread-2: Thu Mar 21 09:10:12 2013
Exiting Thread-2
```
### 线程同步
如果多个线程共同对某个数据修改，则可能出现不可预料的结果，为了保证数据的正确性，需要对多个线程进行同步。
使用Thread对象的Lock和Rlock可以实现简单的线程同步，这两个对象都有acquire方法和release方法，对于那些需要每次只允许一个线程操作的数据，可以将其操作放到acquire和release方法之间。如下：
多线程的优势在于可以同时运行多个任务（至少感觉起来是这样）。但是当线程需要共享数据时，可能存在数据不同步的问题。
考虑这样一种情况：一个列表里所有元素都是0，线程"set"从后向前把所有元素改成1，而线程"print"负责从前往后读取列表并打印。
那么，可能线程"set"开始改的时候，线程"print"便来打印列表了，输出就成了一半0一半1，这就是数据的不同步。为了避免这种情况，引入了锁的概念。
锁有两种状态——锁定和未锁定。每当一个线程比如"set"要访问共享数据时，必须先获得锁定；如果已经有别的线程比如"print"获得锁定了，那么就让线程"set"暂停，也就是同步阻塞；等到线程"print"访问完毕，释放锁以后，再让线程"set"继续。
经过这样的处理，打印列表时要么全部输出0，要么全部输出1，不会再出现一半0一半1的尴尬场面。
实例(Python 2.0+)
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import threading
import time
 
class myThread (threading.Thread):
    def __init__(self, threadID, name, counter):
        threading.Thread.__init__(self)
        self.threadID = threadID
        self.name = name
        self.counter = counter
    def run(self):
        print "Starting " + self.name
       # 获得锁，成功获得锁定后返回True
       # 可选的timeout参数不填时将一直阻塞直到获得锁定
       # 否则超时后将返回False
        threadLock.acquire()
        print_time(self.name, self.counter, 3)
        # 释放锁
        threadLock.release()
 
def print_time(threadName, delay, counter):
    while counter:
        time.sleep(delay)
        print "%s: %s" % (threadName, time.ctime(time.time()))
        counter -= 1
 
threadLock = threading.Lock()
threads = []
 
# 创建新线程
thread1 = myThread(1, "Thread-1", 1)
thread2 = myThread(2, "Thread-2", 2)
 
# 开启新线程
thread1.start()
thread2.start()
 
# 添加线程到线程列表
threads.append(thread1)
threads.append(thread2)
 
# 等待所有线程完成
for t in threads:
    t.join()
print "Exiting Main Thread"
```

### 线程优先级队列（ Queue）
Python的Queue模块中提供了同步的、线程安全的队列类，包括FIFO（先入先出)队列Queue，LIFO（后入先出）队列LifoQueue，和优先级队列PriorityQueue。这些队列都实现了锁原语，能够在多线程中直接使用。可以使用队列来实现线程间的同步。
>### Queue模块中的常用方法:
>Queue.qsize() 返回队列的大小
Queue.empty() 如果队列为空，返回True,反之False
Queue.full() 如果队列满了，返回True,反之False
Queue.full 与 maxsize 大小对应
Queue.get([block[, timeout]])获取队列，timeout等待时间
Queue.get_nowait() 相当Queue.get(False)
Queue.put(item) 写入队列，timeout等待时间
Queue.put_nowait(item) 相当Queue.put(item, False)
Queue.task_done() 在完成一项工作之后，Queue.task_done()函数向任务已经完成的队列发送一个信号
Queue.join() 实际上意味着等到队列为空，再执行别的操作

实例(Python 2.0+)
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import Queue
import threading
import time
 
exitFlag = 0
 
class myThread (threading.Thread):
    def __init__(self, threadID, name, q):
        threading.Thread.__init__(self)
        self.threadID = threadID
        self.name = name
        self.q = q
    def run(self):
        print "Starting " + self.name
        process_data(self.name, self.q)
        print "Exiting " + self.name
 
def process_data(threadName, q):
    while not exitFlag:
        queueLock.acquire()
        if not workQueue.empty():
            data = q.get()
            queueLock.release()
            print "%s processing %s" % (threadName, data)
        else:
            queueLock.release()
        time.sleep(1)
 
threadList = ["Thread-1", "Thread-2", "Thread-3"]
nameList = ["One", "Two", "Three", "Four", "Five"]
queueLock = threading.Lock()
workQueue = Queue.Queue(10)
threads = []
threadID = 1
 
# 创建新线程
for tName in threadList:
    thread = myThread(threadID, tName, workQueue)
    thread.start()
    threads.append(thread)
    threadID += 1
 
# 填充队列
queueLock.acquire()
for word in nameList:
    workQueue.put(word)
queueLock.release()
 
# 等待队列清空
while not workQueue.empty():
    pass
 
# 通知线程是时候退出
exitFlag = 1
 
# 等待所有线程完成
for t in threads:
    t.join()
print "Exiting Main Thread"
```
以上程序执行结果：
```
Starting Thread-1
Starting Thread-2
Starting Thread-3
Thread-1 processing One
Thread-2 processing Two
Thread-3 processing Three
Thread-1 processing Four
Thread-2 processing Five
Exiting Thread-3
Exiting Thread-1
Exiting Thread-2
Exiting Main Thread
```
### Python 线程同步
以下代码可以直观展示加锁和不加锁时，对数据修改情况。
### 加锁时
```python=
# -*-* encoding:UTF-8 -*-
# author : shoushixiong
# date   : 2018/11/22
import threading
import time
list = [0,0,0,0,0,0,0,0,0,0,0,0]
class myThread(threading.Thread):
    def __init__(self,threadId,name,counter):
        threading.Thread.__init__(self)
        self.threadId = threadId
        self.name = name
        self.counter = counter
    def run(self):
        print "开始线程:",self.name
        # 获得锁，成功获得锁定后返回 True
        # 可选的timeout参数不填时将一直阻塞直到获得锁定
        # 否则超时后将返回 False
        threadLock.acquire()
        print_time(self.name,self.counter,list.__len__())
        # 释放锁
        threadLock.release()
    def __del__(self):
        print self.name,"线程结束！"
def print_time(threadName,delay,counter):
    while counter:
        time.sleep(delay)
        list[counter-1] += 1
        print "[%s] %s 修改第 %d 个值，修改后值为:%d" % (time.ctime(time.time()),threadName,counter,list[counter-1])
        counter -= 1
threadLock = threading.Lock()
threads = []
# 创建新线程
thread1 = myThread(1,"Thread-1",1)
thread2 = myThread(2,"Thread-2",2)
# 开启新线程
thread1.start()
thread2.start()
# 添加线程到线程列表
threads.append(thread1)
threads.append(thread2)
# 等待所有线程完成
for t in threads:
    t.join()
print "主进程结束！"
```
输出结果为：
```
开始线程: Thread-1
开始线程: Thread-2
[Thu Nov 22 16:04:13 2018] Thread-1 修改第 12 个值，修改后值为:1
[Thu Nov 22 16:04:14 2018] Thread-1 修改第 11 个值，修改后值为:1
[Thu Nov 22 16:04:15 2018] Thread-1 修改第 10 个值，修改后值为:1
[Thu Nov 22 16:04:16 2018] Thread-1 修改第 9 个值，修改后值为:1
[Thu Nov 22 16:04:17 2018] Thread-1 修改第 8 个值，修改后值为:1
[Thu Nov 22 16:04:18 2018] Thread-1 修改第 7 个值，修改后值为:1
[Thu Nov 22 16:04:19 2018] Thread-1 修改第 6 个值，修改后值为:1
[Thu Nov 22 16:04:20 2018] Thread-1 修改第 5 个值，修改后值为:1
[Thu Nov 22 16:04:21 2018] Thread-1 修改第 4 个值，修改后值为:1
[Thu Nov 22 16:04:22 2018] Thread-1 修改第 3 个值，修改后值为:1
[Thu Nov 22 16:04:23 2018] Thread-1 修改第 2 个值，修改后值为:1
[Thu Nov 22 16:04:24 2018] Thread-1 修改第 1 个值，修改后值为:1
[Thu Nov 22 16:04:26 2018] Thread-2 修改第 12 个值，修改后值为:2
[Thu Nov 22 16:04:28 2018] Thread-2 修改第 11 个值，修改后值为:2
[Thu Nov 22 16:04:30 2018] Thread-2 修改第 10 个值，修改后值为:2
[Thu Nov 22 16:04:32 2018] Thread-2 修改第 9 个值，修改后值为:2
[Thu Nov 22 16:04:34 2018] Thread-2 修改第 8 个值，修改后值为:2
[Thu Nov 22 16:04:36 2018] Thread-2 修改第 7 个值，修改后值为:2
[Thu Nov 22 16:04:38 2018] Thread-2 修改第 6 个值，修改后值为:2
[Thu Nov 22 16:04:40 2018] Thread-2 修改第 5 个值，修改后值为:2
[Thu Nov 22 16:04:42 2018] Thread-2 修改第 4 个值，修改后值为:2
[Thu Nov 22 16:04:44 2018] Thread-2 修改第 3 个值，修改后值为:2
[Thu Nov 22 16:04:46 2018] Thread-2 修改第 2 个值，修改后值为:2
[Thu Nov 22 16:04:48 2018] Thread-2 修改第 1 个值，修改后值为:2
主进程结束！
Thread-1 线程结束！
Thread-2 线程结束！
```
### 不加锁时
同样是上面实例的代码，注释以下两行代码：
```python=
threadLock.acquire()
threadLock.release()
```
输出结果为：
```
开始线程: Thread-1
开始线程: Thread-2
[Thu Nov 22 16:09:20 2018] Thread-1 修改第 12 个值，修改后值为:1
[Thu Nov 22 16:09:21 2018] Thread-2 修改第 12 个值，修改后值为:2
[Thu Nov 22 16:09:21 2018] Thread-1 修改第 11 个值，修改后值为:1
[Thu Nov 22 16:09:22 2018] Thread-1 修改第 10 个值，修改后值为:1
[Thu Nov 22 16:09:23 2018] Thread-1 修改第 9 个值，修改后值为:1
[Thu Nov 22 16:09:23 2018] Thread-2 修改第 11 个值，修改后值为:2
[Thu Nov 22 16:09:24 2018] Thread-1 修改第 8 个值，修改后值为:1
[Thu Nov 22 16:09:25 2018] Thread-2 修改第 10 个值，修改后值为:2
[Thu Nov 22 16:09:25 2018] Thread-1 修改第 7 个值，修改后值为:1
[Thu Nov 22 16:09:26 2018] Thread-1 修改第 6 个值，修改后值为:1
[Thu Nov 22 16:09:27 2018] Thread-2 修改第 9 个值，修改后值为:2
[Thu Nov 22 16:09:27 2018] Thread-1 修改第 5 个值，修改后值为:1
[Thu Nov 22 16:09:28 2018] Thread-1 修改第 4 个值，修改后值为:1
[Thu Nov 22 16:09:29 2018] Thread-2 修改第 8 个值，修改后值为:2
[Thu Nov 22 16:09:29 2018] Thread-1 修改第 3 个值，修改后值为:1
[Thu Nov 22 16:09:30 2018] Thread-1 修改第 2 个值，修改后值为:1
[Thu Nov 22 16:09:31 2018] Thread-2 修改第 7 个值，修改后值为:2
[Thu Nov 22 16:09:31 2018] Thread-1 修改第 1 个值，修改后值为:1
[Thu Nov 22 16:09:33 2018] Thread-2 修改第 6 个值，修改后值为:2
[Thu Nov 22 16:09:35 2018] Thread-2 修改第 5 个值，修改后值为:2
[Thu Nov 22 16:09:37 2018] Thread-2 修改第 4 个值，修改后值为:2
[Thu Nov 22 16:09:39 2018] Thread-2 修改第 3 个值，修改后值为:2
[Thu Nov 22 16:09:41 2018] Thread-2 修改第 2 个值，修改后值为:2
[Thu Nov 22 16:09:43 2018] Thread-2 修改第 1 个值，修改后值为:2
主进程结束！
Thread-1 线程结束！
Thread-2 线程结束！
```

## Python XML 解析
### 什么是 XML？

- XML 指可扩展标记语言（eXtensible Markup Language）。 
- XML 被设计用来传输和存储数据。
- XML 是一套定义语义标记的规则，这些标记将文档分成许多部件并对这些部件加以标识。
它也是元标记语言，即定义了用于定义其他与特定领域有关的、语义的、结构化的标记语言的句法语言。
### Python 对 XML 的解析
常见的 XML 编程接口有 DOM 和 SAX，这两种接口处理 XML 文件的方式不同，当然使用场合也不同。

### Python 有三种方法解析 XML，SAX，DOM，以及 ElementTree:
1.SAX (simple API for XML )
Python 标准库包含 SAX 解析器，SAX 用事件驱动模型，通过在解析XML的过程中触发一个个的事件并调用用户定义的回调函数来处理XML文件。
2.DOM(Document Object Model)
将 XML 数据在内存中解析成一个树，通过对树的操作来操作XML。
3.ElementTree(元素树)
ElementTree就像一个轻量级的DOM，具有方便友好的API。代码可用性好，速度快，消耗内存少。
注：因DOM需要将XML数据映射到内存中的树，一是比较慢，二是比较耗内存，而SAX流式读取XML文件，比较快，占用内存少，但需要用户实现回调函数（handler）。

本章节使用到的 XML 实例文件 movies.xml 内容如下：
```python=
movies.xml
<collection shelf="New Arrivals">
<movie title="Enemy Behind">
   <type>War, Thriller</type>
   <format>DVD</format>
   <year>2003</year>
   <rating>PG</rating>
   <stars>10</stars>
   <description>Talk about a US-Japan war</description>
</movie>
<movie title="Transformers">
   <type>Anime, Science Fiction</type>
   <format>DVD</format>
   <year>1989</year>
   <rating>R</rating>
   <stars>8</stars>
   <description>A schientific fiction</description>
</movie>
   <movie title="Trigun">
   <type>Anime, Action</type>
   <format>DVD</format>
   <episodes>4</episodes>
   <rating>PG</rating>
   <stars>10</stars>
   <description>Vash the Stampede!</description>
</movie>
<movie title="Ishtar">
   <type>Comedy</type>
   <format>VHS</format>
   <rating>PG</rating>
   <stars>2</stars>
   <description>Viewable boredom</description>
</movie>
</collection>
```
### python使用SAX解析xml
SAX是一种基于事件驱动的 API。
利用SAX解析XML文档牵涉到两个部分: 解析器和事件处理器。
解析器负责读取XML文档，并向事件处理器发送事件，如元素开始跟元素结束事件。
而事件处理器则负责对事件作出响应，对传递的XML数据进行处理。
1、对大型文件进行处理；
2、只需要文件的部分内容，或者只需从文件中得到特定信息。
3、想建立自己的对象模型的时候。

在python中使用sax方式处理xml要先引入xml.sax中的parse函数，还有xml.sax.handler中的ContentHandler。
ContentHandler类方法介绍
### characters(content)方法
调用时机：
从行开始，遇到标签之前，存在字符，content 的值为这些字符串。
从一个标签，遇到下一个标签之前， 存在字符，content 的值为这些字符串。
从一个标签，遇到行结束符之前，存在字符，content 的值为这些字符串。
标签可以是开始标签，也可以是结束标签。
### startDocument() 方法
文档启动的时候调用。
### endDocument() 方法
解析器到达文档结尾时调用。
### startElement(name, attrs)方法
遇到XML开始标签时调用，name是标签的名字，attrs是标签的属性值字典。
### endElement(name) 方法
遇到XML结束标签时调用。

### make_parser方法
以下方法创建一个新的解析器对象并返回。
`xml.sax.make_parser( [parser_list] )`

>参数说明:
parser_list - 可选参数，解析器列表
### parser方法
以下方法创建一个 SAX 解析器并解析xml文档：
xml.sax.parse( xmlfile, contenthandler[, errorhandler])

>参数说明:
xmlfile - xml文件名
contenthandler - 必须是一个ContentHandler的对象
errorhandler - 如果指定该参数，errorhandler必须是一个SAX ErrorHandler对象

### parseString方法
parseString方法创建一个XML解析器并解析xml字符串：
`xml.sax.parseString(xmlstring, contenthandler[, errorhandler])`
>参数说明:
xmlstring - xml字符串
contenthandler - 必须是一个ContentHandler的对象
errorhandler - 如果指定该参数，errorhandler必须是一个SAX ErrorHandler对象
Python 解析XML实例

实例
```python=
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import xml.sax
 
class MovieHandler( xml.sax.ContentHandler ):
   def __init__(self):
      self.CurrentData = ""
      self.type = ""
      self.format = ""
      self.year = ""
      self.rating = ""
      self.stars = ""
      self.description = ""
 
   # 元素开始事件处理
   def startElement(self, tag, attributes):
      self.CurrentData = tag
      if tag == "movie":
         print "*****Movie*****"
         title = attributes["title"]
         print "Title:", title
 
   # 元素结束事件处理
   def endElement(self, tag):
      if self.CurrentData == "type":
         print "Type:", self.type
      elif self.CurrentData == "format":
         print "Format:", self.format
      elif self.CurrentData == "year":
         print "Year:", self.year
      elif self.CurrentData == "rating":
         print "Rating:", self.rating
      elif self.CurrentData == "stars":
         print "Stars:", self.stars
      elif self.CurrentData == "description":
         print "Description:", self.description
      self.CurrentData = ""
 
   # 内容事件处理
   def characters(self, content):
      if self.CurrentData == "type":
         self.type = content
      elif self.CurrentData == "format":
         self.format = content
      elif self.CurrentData == "year":
         self.year = content
      elif self.CurrentData == "rating":
         self.rating = content
      elif self.CurrentData == "stars":
         self.stars = content
      elif self.CurrentData == "description":
         self.description = content
  
if ( __name__ == "__main__"):
   
   # 创建一个 XMLReader
   parser = xml.sax.make_parser()
   # turn off namepsaces
   parser.setFeature(xml.sax.handler.feature_namespaces, 0)
 
   # 重写 ContextHandler
   Handler = MovieHandler()
   parser.setContentHandler( Handler )
   
   parser.parse("movies.xml")
```
以上代码执行结果如下：
```
*****Movie*****
Title: Enemy Behind
Type: War, Thriller
Format: DVD
Year: 2003
Rating: PG
Stars: 10
Description: Talk about a US-Japan war
*****Movie*****
Title: Transformers
Type: Anime, Science Fiction
Format: DVD
Year: 1989
Rating: R
Stars: 8
Description: A schientific fiction
*****Movie*****
Title: Trigun
Type: Anime, Action
Format: DVD
Rating: PG
Stars: 10
Description: Vash the Stampede!
*****Movie*****
Title: Ishtar
Type: Comedy
Format: VHS
Rating: PG
Stars: 2
Description: Viewable boredom
```
### 使用xml.dom解析xml
文件对象模型（Document Object Model，简称DOM），是W3C组织推荐的处理可扩展置标语言的标准编程接口。
一个 DOM 的解析器在解析一个 XML 文档时，一次性读取整个文档，把文档中所有元素保存在内存中的一个树结构里，之后你可以利用DOM 提供的不同的函数来读取或修改文档的内容和结构，也可以把修改过的内容写入xml文件。
python中用xml.dom.minidom来解析xml文件，实例如下：
实例
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
from xml.dom.minidom import parse
import xml.dom.minidom
 
# 使用minidom解析器打开 XML 文档
DOMTree = xml.dom.minidom.parse("movies.xml")
collection = DOMTree.documentElement
if collection.hasAttribute("shelf"):
   print "Root element : %s" % collection.getAttribute("shelf")
 
# 在集合中获取所有电影
movies = collection.getElementsByTagName("movie")
 
# 打印每部电影的详细信息
for movie in movies:
   print "*****Movie*****"
   if movie.hasAttribute("title"):
      print "Title: %s" % movie.getAttribute("title")
 
   type = movie.getElementsByTagName('type')[0]
   print "Type: %s" % type.childNodes[0].data
   format = movie.getElementsByTagName('format')[0]
   print "Format: %s" % format.childNodes[0].data
   rating = movie.getElementsByTagName('rating')[0]
   print "Rating: %s" % rating.childNodes[0].data
   description = movie.getElementsByTagName('description')[0]
   print "Description: %s" % description.childNodes[0].data
```
以上程序执行结果如下：
```
Root element : New Arrivals
*****Movie*****
Title: Enemy Behind
Type: War, Thriller
Format: DVD
Rating: PG
Description: Talk about a US-Japan war
*****Movie*****
Title: Transformers
Type: Anime, Science Fiction
Format: DVD
Rating: R
Description: A schientific fiction
*****Movie*****
Title: Trigun
Type: Anime, Action
Format: DVD
Rating: PG
Description: Vash the Stampede!
*****Movie*****
Title: Ishtar
Type: Comedy
Format: VHS
Rating: PG
Description: Viewable boredom
```
## Python GUI编程(Tkinter)
Python 提供了多个图形开发界面的库，几个常用 Python GUI 库如下：
>- Tkinter： Tkinter 模块(Tk 接口)是 Python 的标准 Tk GUI 工具包的接口 .Tk 和 Tkinter 可以在大多数的 Unix 平台下使用,同样可以应用在 Windows 和 Macintosh 系统里。Tk8.0 的后续版本可以实现本地窗口风格,并良好地运行在绝大多数平台中。
>- wxPython：wxPython 是一款开源软件，是 Python 语言的一套优秀的 GUI 图形库，允许 Python 程序员很方便的创建完整的、功能健全的 GUI 用户界面。
>- Jython：Jython 程序可以和 Java 无缝集成。除了一些标准模块，Jython 使用 Java 的模块。Jython 几乎拥有标准的Python 中不依赖于 C 语言的全部模块。比如，Jython 的用户界面将使用 Swing，AWT或者 SWT。Jython 可以被动态或静态地编译成 Java 字节码。

### Tkinter 编程
Tkinter 是 Python 的标准 GUI 库。Python 使用 Tkinter 可以快速的创建 GUI 应用程序。
由于 Tkinter 是内置到 python 的安装包中、只要安装好 Python 之后就能 import Tkinter 库、而且 IDLE 也是用 Tkinter 编写而成、对于简单的图形界面 Tkinter 还是能应付自如。
:::info
注意：Python3.x 版本使用的库名为 tkinter,即首写字母 T 为小写。
`import tkinter`
:::
创建一个GUI程序
1、导入 Tkinter 模块
2、创建控件
3、指定这个控件的 master， 即这个控件属于哪一个
4、告诉 GM(geometry manager) 有一个控件产生了。
>实例
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import Tkinter
top = Tkinter.Tk()
# 进入消息循环
top.mainloop()
```
以上代码执行结果如下图:
![](https://i.imgur.com/wsWYrts.png)

### tkwindow
>实例
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
from Tkinter import *           # 导入 Tkinter 库
root = Tk()                     # 创建窗口对象的背景色
                                # 创建两个列表
li     = ['C','python','php','html','SQL','java']
movie  = ['CSS','jQuery','Bootstrap']
listb  = Listbox(root)          #  创建两个列表组件
listb2 = Listbox(root)
for item in li:                 # 第一个小部件插入数据
    listb.insert(0,item)
 
for item in movie:              # 第二个小部件插入数据
    listb2.insert(0,item)
 
listb.pack()                    # 将小部件放置到主窗口中
listb2.pack()
root.mainloop()                 # 进入消息循环
```
以上代码执行结果如下图:
![](https://i.imgur.com/QuDg1xo.png)


### Tkinter 组件
Tkinter的提供各种控件，如按钮，标签和文本框，一个GUI应用程序中使用。这些控件通常被称为控件或者部件。
目前有15种Tkinter的部件。，在下面的表有这些部件以及一个简短的介绍：

|控件	|描述|
|----|----|
Button	|按钮控件；在程序中显示按钮。|
Canvas	|画布控件；显示图形元素如线条或文本|
Checkbutton	|多选框控件；用于在程序中提供多项选择框|
Entry|	输入控件；用于显示简单的文本内容|
Frame|	框架控件；在屏幕上显示一个矩形区域，多用来作为容器|
Label	|标签控件；可以显示文本和位图|
Listbox|	列表框控件；在Listbox窗口小部件是用来显示一个字符串列表给用户|
Menubutton|	菜单按钮控件，由于显示菜单项。|
Menu	|菜单控件；显示菜单栏,下拉菜单和弹出菜单|
Message|	消息控件；用来显示多行文本，与label比较类似|
Radiobutton	|单选按钮控件；显示一个单选的按钮状态|
Scale	|范围控件；显示一个数值刻度，为输出限定范围的数字区间|
Scrollbar|	滚动条控件，当内容超过可视化区域时使用，如列表框。|.
Text	|文本控件；用于显示多行文本|
Toplevel	|容器控件；用来提供一个单独的对话框，和Frame比较类似|
Spinbox	|输入控件；与Entry类似，但是可以指定输入范围值|
PanedWindow	|PanedWindow是一个窗口布局管理的插件，可以包含一个或者多个子控件。|
LabelFrame	|labelframe 是一个简单的容器控件。常用与复杂的窗口布局。|
tkMessageBox	|用于显示你应用程序的消息框。|

### 标准属性
标准属性也就是所有控件的共同属性，如大小，字体和颜色等等。

|属性	|描述|
|----|----|
Dimension	|控件大小；|
Color	|控件颜色；|
Font	|控件字体；|
Anchor	|锚点；|
Relief	|控件样式；|
Bitmap	|位图；|
Cursor	|光标；|
### 几何管理

Tkinter控件有特定的几何状态管理方法，管理整个控件区域组织，一下是Tkinter公开的几何管理类：包、网格、位置

|几何方法	|描述|
|----|----|
pack()	|包装；|
grid()	|网格；|
place()	|位置；|

## open cv 讀取圖片
首先引入 NumPy 與 OpenCV 的 Python 模組：
```
import numpy as np
import cv2
```
OpenCV 本身就有提供讀取圖片檔的函數可用，讀取一般的圖片檔，只要呼叫 cv2.imread 即可將圖片讀取進來：
### 讀取圖檔
img = cv2.imread('image.jpg')
以 cv2.imread 讀進來的資料，會儲存成一個 NumPy 的陣列，我們可以用 type 檢查一下：
```python
type(img)
<class 'numpy.ndarray'>
```
此 NumPy 陣列的前兩個維度分別是圖片的高度與寬度，第三個維度則是圖片的 channel（RGB 彩色圖片的 channel 是 3，灰階圖片則為 1）。

以這個子來說，我們的原始圖片是一張 1920×1080 的彩色圖片，我們可以檢查一下這個 NumPy 陣列的大小：
```
img.shape
(1080, 1920, 3)
```
### 圖檔格式

OpenCV 的 cv2.imread 在讀取圖片時，可以在第二個參數指定圖片的格式，可用的選項有三種：

cv2.IMREAD_COLOR
此為預設值，這種格式會讀取 RGB 三個 channels 的彩色圖片，而忽略透明度的 channel。
cv2.IMREAD_GRAYSCALE
以灰階的格式來讀取圖片。
cv2.IMREAD_UNCHANGED
讀取圖片中所有的 channels，包含透明度的 channel。
這是讀取灰階圖片的範例：

以灰階的方式讀取圖檔:
```
img_gray = cv2.imread('image.jpg', cv2.IMREAD_GRAYSCALE)
```
### 顯示圖片

將圖片讀取進來之後，可以使用 OpenCV 所提供的 cv2.imshow 來顯示圖片：

顯示圖片:
```python
cv2.imshow('My Image', img)
# 按下任意鍵則關閉所有視窗
cv2.waitKey(0)
cv2.destroyAllWindows()
```
這裡 `cv2.waitKey `函數是用來等待與讀取使用者按下的按鍵，而其參數是等待時間（單位為毫秒），若設定為` 0` 就表示持續等待至使用者按下按鍵為止，這樣當我們按下`任意按鍵`之後，就會呼叫 cv2.destroyAllWindows 關閉所有 OpenCV 的視窗。
:::info
等待按鍵輸入
`int waitKey(int delay=0)`

delay：等待時間，這邊主要分兩大類使用方式，當delay<=0時，程式靜止，當delay>0時，函式會等待參數時間(ms)後，返回按鍵的ASCII碼，如果這段時間沒有按鍵按下，會返回-1。

waitKey()只有搭配OpenCV視窗才有效果，沒有視窗的話無此暫停程式功能。
可以使用這個特性搭配while迴圈，讓圖片不斷顯示，直到按下某特定按鍵後才停止。
由於esc鍵的ASCII碼為27，所以以下程式只有按下esc鍵，程式才會跳出迴圈：
```python
while(true){ 
    imshow("Display window", img);  
    if(cvWaitKey(10)==27){  
        break; 
    } 
}
```
:::

如果在程式中有許多的 OpenCV 視窗，而我們只要關閉特定的視窗時，可以改用 cv2.destroyWindow 加上視窗名稱，關閉指定的視窗：

關閉 'My Image' 視窗:
```
cv2.destroyWindow('My Image')
```
在預設的狀況下，以 cv2.imshow 所開啟的視窗會依據圖片來自動調整大小，但若是圖片太大、佔滿整個螢幕時，我們會希望可以自由縮放視窗的大小，這時候就可以使用 cv2.namedWindow 將視窗設定為 cv2.WINDOW_NORMAL：
```
#讓視窗可以自由縮放大小:
cv2.namedWindow('My Image', cv2.WINDOW_NORMAL)

cv2.imshow('My Image', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

### 寫入圖片檔案

若要將 NumPy 陣列中儲存的圖片寫入檔案，可以使用 OpenCV 的 cv2.imwrite：
```python=
# 寫入圖檔
cv2.imwrite('output.jpg', img)
cv2.imwrite 可透過圖片的副檔名來指定輸出的圖檔格式：

# 寫入不同圖檔格式
cv2.imwrite('output.png', img)
cv2.imwrite('output.tiff', img)
輸出圖片檔案時，也可以調整圖片的品質或壓縮率：

# 設定 JPEG 圖片品質為 90（可用值為 0 ~ 100）
cv2.imwrite('output.jpg', img, [cv2.IMWRITE_JPEG_QUALITY, 90])

# 設定 PNG 壓縮層級為 5（可用值為 0 ~ 9）
cv2.imwrite('output.png', img, [cv2.IMWRITE_PNG_COMPRESSION, 5])
```

### Matplotlib

Matplotlib 是 Python 之中很常被使用的繪圖工具，以下介紹如何以 Matplotlib 顯示 OpenCV 讀入或產生的圖片。

### 彩色圖片

Matplotlib 顯示圖片的方式也很簡單，只要呼叫 imshow 就可以了，但是由於 OpenCV 讀取進來的圖片會以 BGR 的方式儲存三個顏色的 channel，如果直接把 OpenCV 讀入的圖片放進 Matplotlib 來顯示，就會出現類似這樣的顏色錯誤問題：
![](https://i.imgur.com/x4swDIm.jpg)

遇到這樣的問題，只要將 OpenCV 讀入的 BGR 格式轉為 Matplotlib 用的 RGB 格式，再交給 Matplotlib 顯示就會得到正確的結果了。以下是使用 Matplotlib 顯示彩色圖片的範例：
```python
import numpy as np
import cv2
from matplotlib import pyplot as plt

# 使用 OpenCV 讀取圖檔
img_bgr = cv2.imread('image.jpg')

# 將 BGR 圖片轉為 RGB 圖片
img_rgb = img_bgr[:,:,::-1]

# 或是這樣亦可
# img_rgb = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2RGB)

# 使用 Matplotlib 顯示圖片
plt.imshow(img_rgb)
plt.show()
```
### 灰階圖片

而如果是以 OpenCV 讀取灰階的圖片時，由於 channel 只有一個，所以就不會有上述的色彩問題，直接把 OpenCV 讀入的 NumPy 陣列放進 Matplotlib 的 imshow 中即可顯示，但是 Matplotlib 在顯示一個 channel 的圖片時，會用預設的 colormap 上色，所以畫出來繪像這樣：

![](https://i.imgur.com/zC5eN5c.jpg)
如果想要以黑白的方式呈現灰階圖片，可以自己設定 colormap：
```python
# 使用 OpenCV 讀取灰階圖檔
img_gray = cv2.imread('image.jpg', cv2.IMREAD_GRAYSCALE)

# 使用 Matplotlib 顯示圖片
plt.imshow(img_gray, cmap = 'gray')
plt.show()
```
結果就會是灰色階的照片了。



## python處理照片
### 切割圖片
利用opencv將圖片切割成8X8的例子如下：
```python=
import cv2, numpy

img = cv2.imread('/home/eray/Desktop/crop/crop01.jpg')
h,w,c = img.shape   #讀取圖片的長寬高
a = int(h/8)
b = int(w/8)

x = [0, 1*a, 2*a, 3*a, 4*a, 5*a, 6*a, 7*a]
y = [0, 1*b, 2*b, 3*b, 4*b, 5*b, 6*b, 7*b]
k = 0

for i in range(8):
    for j in range(8):
        crop-img = img[x[i]:x[i]+a, y[j]:y[j]+b]
        # cv2.imshow('crop'+str(k),crop_img)
        # cv2.waitKey(0)
        cv2.imwrite('crop'+str(k)+'.jpg',crop_img)
        k += 1
cv2.destroyWindow()
```
儲存切割後的照片的位置，是python檔存放的檔案夾。


## python處理由jpg檔修改對應之xml檔
```python
import glob, os

gloves_xml = '/home/eray/Desktop/20190711/UDA_gloves20190708/xml/'
shoes_xml = '/home/eray/Desktop/20190711/UDA_shoes20190704/xml/'

all = os.listdir(gloves_xml)
all += os.listdir(shoes_xml_)
all.short()

a = len(all)

i = 0
while i < a-1:
    if all[i] == all[i+1]:
        del all[i]
    i += 1
print(len(all))
```

## python處理xml之讀取及寫入
```python
[1]
import os
f = open('/Users/irenehuang/desktop/labelImg.py','r+')
data = f.readlines()
print(data)
```

*f = open( ' /Users/irenehuang/desktop/capMask ' , ' r+' )中
因為open('r')讀完之後指標不會回到一開始，在讀取上會有Error，所以要把它存起來（例如存成data = f.readlines）或是再開一次*

```python
[2]
from os import walk
from os.path import join

f = open('/Users/irenehuang/desktop/label_20190705/UDA_newCap2')
data=os.listdir('/Users/irenehuang/desktop/label_20190705/UDA_newCap2')
#listdir是取得指定目錄中所有的檔案與子目錄名稱
print(data) 
#print出的data會是一個list，每一行data是一個string，用逗號隔開.
#
data.find('/Users/irenehuang/desktop/capMask')
for root, dirs, files in walk('/Users/irenehuang/desktop/capMask'):
    for f in files:
    fullpath = join(root, f)
print(fullpath)									
##fullpath 取得所有檔案的絕對路徑，讓程式逐一處理
root_pic = '/Users/irenehuang/desktop/capMask/'
root_xml1 = '/Users/irenehuang/desktop/label_20190705/UDA_newCap2'
root_xml = '/Users/irenehuang/desktop/label_20190705/UDA_newCap2/'


k1 = os.listdir('/Users/irenehuang/desktop/capMask/')
k2 = os.listdir('/Users/irenehuang/desktop/label_20190705/UDA_newCap2/')

#for i in k1:
#	print(i)


f = open('/Users/irenehuang/desktop/label_20190705/UDA_newCap2/20190604_1751__0.xml', 'r+')
f1 = open('/Users/irenehuang/desktop/label_20190705/training/20190604_1751__0.xml', 'w') 
#'w'寫，並存到新的folder,而檔名不要改（for辨識）


a = f.readlines()  
print(type(f))
print(type(a))
#print(k1)


#print(len(a)) #看整個檔案有幾行,來判斷要不要改他（因為只改一個name的)

#if len(a) < 30 :
#	for i in a:
#		if i.find('<name>') != -1:
			#print (i)
#			f1.write('\t\t<name>capMask</name>\n')  #write是寫一整行
#		else:
#			f1.write(i)
#	f.close()
#	f1.close()
'''
#print(i)

'''
#for j in range(0, len(k)):
	#print (i[j])
	
#	if ( os.path.isfile(root_xml+k[j][:-3]+'xml')):
		#print (i[j])
#		f = open(os.path.join(root_xml1, k[j][:-3]+'xml'), 'r+')
	#print(i.os.rename('.jpg','.xml'))






```





### os.path.splitext
>os.path.splitext(檔名)[-1]) 
照理來說是要印出副檔名

### 拍森的一些指令
>列出此目錄下所有文件：
>```
>$ import os
>$ os.listdir(' . ')
>```
>列出type：
>```
>$ type(os.listdir(' . '))   //<type 'list'>
>```
>列出此目錄下所有文件的數量：
>```
>$ len(os.listdir(' . '))
>```
>列出所有副檔名為*.text的文件
>```
>$ import glob
>$ glob.glob(' *.text ')
>```
>把檔名跟副檔名分開：
>```
>$ os.path.splitext(' abc.odt ')
>os.path.splitext(' abc.odt ')[0]   // ' abc '
>os.path.splitext(' abc.odt ')[1]   // ' .odt '
>```
>想要將list裡的字串連接起來便可以用join:
>```
>$ list = ['how', 'are', 'you']
>$print ', '.join(list)      // how, are, you
>$$print '--'.join(list)      // how--are--you
>```
>檢查指定資料夾內的所有檔案：
>```
>$ os.walk('path') //必須要用for in迴圈才能跑出來, 他的type是vgenerator(選擇器)
>```
>檢查是否有tmp資料夾：
>```
>$ os.path.isdir('tmp')
>```
>建立名稱為name的資料夾：
>```
>$ os.mkdir('name')
>```
>等同Pwd的指令,顯示目前所在位置的絕對路徑：
>```
>$ os.getcwd()
>```
>等同於cd指令,切換終端機視角所在的資料夾位置：
>```
>$ os.chdir()
>```
>List加入aaa字串的資料:
>```
>$ list.appent('aaa')
>```
>字串取代 replace:
>```
>$ print 'abcdefg'.replace( 'abc', '123' )     // 123defg
>```




## python讀取與寫入範例
```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import os
import xml.etree.cElementTree as ET
import glob
import math
import time
import datetime
import numpy as np
import cv2
import shutil
from os import walk
from os import listdir
from os.path import isfile, isdir, join

def sss():
    source = '/home/eray/programProject/'

if __name__=='__main__':
    source = '/home/eray/programCASE/yolov3-program/darknet-alex/VOCdevkit/VOC2007/Annotations/'
    listS = glob.glob(os.path.join(source, '*.xml'))
    print len(listS)
    print len(listS)*0.8
    print len(listS)*0.1
    
    f = open('/home/eray/Desktop/list.txt', 'w')
    f1 = open('/home/eray/Desktop/trainval.txt', 'w')
    f2 = open('/home/eray/Desktop/train.txt', 'w')
    f3 = open('/home/eray/Desktop/val.txt', 'w')
    f4 = open('/home/eray/Desktop/test.txt', 'w')
    
    for i in range(0, len(listS)):            
        regStr = listS[i].rpartition(".")[0]
        regStr = regStr.rpartition("/")[2]
        f.write(regStr)
        f1.write(regStr)
        if i < len(listS)*0.8:
            f2.write(regStr)
            f2.write('\n')
        else :
            f3.write(regStr)
            f3.write('\n')
        if i > len(listS)*0.9:
            f4.write(regStr)
            f4.write('\n')
        f.write('\n')
        f1.write('\n')
```

## NumPy 教程

NumPy（Numerical Python）是Python語言的一個擴展程序庫，支持大量的維度數組與矩陣運算，此外也針對數組運算提供大量的數學函數庫。
數字計算，包含：
一個強大的N維數組對象Ndarray，廣播功能函數，整合C / C ++ / Fortran代碼的工具，線性代數，傅里葉變換，隨機數生成等功能

NumPy通常與SciPy（科學Python）和Matplotlib（繪圖庫）一起使用，這種組合廣泛用於替代MatLab，是一個強大的科學計算環境，有助於我們通過Python學習數據科學或者機器學習。
- SciPy是一個開源的Python算法庫和數學工具包。
SciPy包含的模塊有最優化，線性代數，積分，插值，特殊函數，快速傅里葉變換，信號處理和圖像處理，常微分方程求解和其他科學與工程中常用的計算。
- Matplotlib是Python編程語言及其數值數學擴展包NumPy的可視化操作界面。它為利用通用的圖形用戶界面工具包，如Tkinter，wxPython，Qt或GTK +向應用程序嵌入式繪圖提供了應用程序接口（API）

### NumPy Ndarray 对象
NumPy 最重要的一个特点是其 N 维数组对象 ndarray，它是一系列同类型数据的集合，以 0 下标为开始进行集合中元素的索引。

- ndarray 对象是用于存放同类型元素的多维数组。
- ndarray 中的每个元素在内存中都有相同存储大小的区域。
- ndarray 内部由以下内容组成：
-- 一个指向数据（内存或内存映射文件中的一块数据）的指针。
-- 数据类型或 dtype，描述在数组中的固定大小值的格子。
-- 一个表示数组形状（shape）的元组，表示各维度大小的元组。
-- 一个跨度元组（stride），其中的整数指的是为了前进到当前维度下一个元素需要"跨过"的字节数。 跨度可以是负数，这样会使数组在内存中后向移动，切片中 obj[::-1] 或 obj[:,::-1] 就是如此。

NumPy 的 Array 函數：
`numpy.array(object, dtype = None, copy = True, order = None, subok = False, ndmin = 0)`
參數說明：

|名稱|描述|
|----|----|
|object	|数组或嵌套的数列|
dtype	|数组元素的数据类型，可选|
copy|	对象是否需要复制，可选|
order|	创建数组的样式，C为行方向，F为列方向，A为任意方向（默认）|
subok|	默认返回一个与基类类型一致的数组|
ndmin|	指定生成数组的最小维度|
