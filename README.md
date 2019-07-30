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

>
>### 字串 / 字符串也有運算：
>S.find（substring，[start [，end]]）＃可指範圍查找子串，返回索引值，否則返回-1
S.rfind（substring，[start [，end]]）＃反向查找
S.index（substring，[start [，end]]）＃同找，只是找不到產生ValueError異常
S.rindex（substring，[start [，end]]）＃同上反向查找
S.count（substring，[start [，end]]）＃返回找到子串的個數
>
>S.lowercase（）
>S.capitalize（）＃首字母大寫
>S.lower（）＃轉小寫
>S.upper（）＃轉大寫
>S.swapcase（）＃大小寫互換
>
>S.split（str，''）＃將字符串轉錄，以空格切分
>S.join（list，''）＃將list轉string，以空格連接
>
>處理字符串的內置函數
>len（str）＃串長度
>cmp（“我的朋友”，str）＃字符串比較。第一個大，返回1
>max（'abcxyz'）＃尋找字符串中最大的字符
>min（'abcxyz'）＃尋找字符串中最小的字符

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
|-|-|
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
out_exp_res:　　列表生成元素表示式，可以是有返回值的函式。
for out_exp in input_list：　　迭代input_list將out_exp傳入out_exp_res表示式中。
if out_exp == 2：　　根據條件過濾哪些值可以。
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
:::info
### 生成器
>在Python中，使用了yield的函數被稱為生成器（generator）。
跟普通函數不同的是，生成器是一個返回迭代器的函數，只能用於迭代操作，更簡單點理解生成器就是一個迭代器。
在調用生成器運行的過程中，每次遇到yield時函數會暫停並保存當前所有的運行信息，返回yield的值，並在下一次執行next（）方法時從當前位置繼續運行。
調用一個生成器函數，返回的是一個迭代器對象。
:::
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
