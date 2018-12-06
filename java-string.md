# java-string
[TOC]

从概念上讲，Java字符串就是Unicode字符序列，每个用双引号括起来的字符串都是一个String类的实例。每个用双引号括起来的字符串都是String类型的一个实例。
## 子串
String类的substring类型可以从一个较大的字符串提取出一个子串。
```
String greeting = "Hello";
//第一个参数表示开始的位置，第二个参数表示不想包含的第一个位置
String s = greeting.substring(0,3);
```

## 拼接
Java中允许使用+号来连接两个字符串
```
String expletive = "Expletive";
String PG13 = "deleted";
String message = expletive + PG13;
```
在Java中，任何一个Java对象都可以转换成为字符串，例如：
```
int age = 13;
String rating = "PC" + age;
```
如果需要把多个字符串放在一起，并且用一个界定符来分割，那么就可以使用join方法。
```
String all = String.join(" / ", "S", "M", "L", "XL");
// all is the string "S / H / L / XL"
```
## 不可变字符串
Java中的字符串类型是**不可变的**，如果需要修改字符串，可以通过提取、拼接的方式来替换

## 检测字符串是否相等
字符串之间不能直接使用`==`来判断两个字符串是否相等,只能用于判断两个字符串是否在同一个位置上面；如果要判断值是否相同，需要使用`equals`来进行检测
```
String all = "hello";
all.equals("hello");
//如果需要不区分大小写来判断两个字符串是否相等，则可以使用如下方法：
"hello".equals.(all);
```
## 空串与null串
空串是长度为0的字符串，`""`表示一个空串，可以使用一下代码来判断字符串是否为空
```
if(str.length()==0)
if(str.equals(""))
```
空串也是一个Java对象，可以使用Java.String的各种方法。
但是String中还可以存放一个特殊值，名为null，这表示目前没有任何对象与该变量关联。需要使用`if(str==null)`来判断是否为null
在一起进行判断的时候，需要判断str是否为null，因为如果在一个null值上面调用方法，会出现错误。
```
if (str != null && str.lengthO != 0)
```
## 码点与代码单元
Java的字符串是由char值序列组成，char数据类型是一个采用UTF-16编码表示的Unicode码点的代码单元，大多数的Unicode使用一个代码单元就可以表示，而辅助字符需要一对代码单元来表示。因此最好不要使用char类型，因为这个类型太底层了。最好使用以下语句：
```
int cp = sentence.codePointAt(i);
if (Character.isSupplementaryCodePoint(cp))
i += 2;
else
i++;
```
显然，上述问题太过麻烦，因此使用codePoints方法
```
int[] codePointer=str.codePointer().toArray();
String str = new String(codePoints, 0, codePoints.length);
```

## String API
- `char charAt (int index)`
返回给定位置的代码单元。
- `int codePointAt(int Index)`
返回从给定位置开始的码点。
- `int offsetByCodePoints(int startlndex, int cpCount)`
返回从startlndex代码点开始，位移cpCount后的码点索引。
- `int compareTo(String other)`
按照字典顺序，如果字符串位于 other 之前，返回一个负数；如果字符串位于other之后，返回一个正数；如果两个字符串相等，返回0
- `IntStream codePoints()`
将这个字符串的码点作为一个流返回。
- `new String(int[] codePoints, int offset, int count)`
用数组中从 offset 开始的count个码点构造一个字符串。
- `boolean equals(0bject other)`
如果字符串与other相等， 返回true
- `boolean equalsIgnoreCase(String other)`
如果字符串与other相等(忽略大小写)返回true。
- `boolean startsWith( String prefix )`
如果字符串以suffix开头， 则返回true。
- ` boolean endsWith( String suffix )`
如果字符串以suffix结尾， 则返回true。
- `int indexOf(String str)`
- `int indexOf(String str,int fromlndex)`
- `int indexOf(int cp)`
- `int indexOf(int cp,int fromlndex)`
返回与字符串str或代码点cp匹配的第一个子串的开始位置。这个位置从索引0或fromlndex开始计算。如果在原始串中不存在str，返回-1。
- `int 1astIndexOf(String str)`
- `Int 1astIndexOf(String str, int fromlndex)`
- `int lastindexOf(int cp)`
- `int 1astindexOf(int cp, int fromlndex)`
返回与字符串str或代码点cp匹配的最后一个子串的开始位置。这个位置从原始串尾端fromlndex开始计算。
- `int 1ength()`
返回字符串的长度。
- `int codePointCount(int startlndex, int endlndex)`
返回startlndex和endludex-l之间的代码点数量。没有配成对的代用字符将计入代码点。
- `String replace(CharSequence oldString,CharSequence newString)`
返回一个新字符串。这个字符串用newString代替原始字符串中所有的oldString。
- `String substring(int beginlndex)`
- `String substring(int beginlndex, int endlndex)`
返回一个新字符串。
- `String toLowerCase( )`
- `String toUpperCase( )`
表示把字符串中的字母全部改为小写，或者大写
- `String trim()`
返回一个新字符串。这个字符串将删除了原始字符串头部和尾部的空格。
- `String join(CharSequence delimiter, CharSequence... elements)`
返回一个新字符串，用给定的定界符连接所有元素。

## 构建字符串
每次连接字符，不仅需要新建一个String对象，而且十分浪费资源和时间，使用StringBuilder就可以避免这个问题的发生。
```
StringBuilder builder = new StringBuilder();
builder.append(ch); // appends a single character
bui1der.append(str); // appends a string
String completedString = builder.toString();
```

```
\\构造一个空的字符串构建器。
StringBuilder()

\\返回构建器或缓冲器中的代码单元数量。
int length()

\\追加一个字符串并返回 this 。
StringBuilder append(String str)

\\追加一个代码单元并返回 this。
StringBuilder append(char c)

\\追加一个代码点，并将其转换为一个或两个代码单元并返回 this 。
StringBuilder appendCodePoint(int cp)

\\将第i个代码单元设置为c。
void setCharAt(int i ,char c)

\\在offset位置插入一个字符串并返回 this。
StringBuilder insert(int offset,String str)

\\在 offset 位置插入一个代码单元并返回 this。
StringBuilder insert(int offset,Char c)

\\删除偏移量从 startindex 到-endlndex-1 的代码单元并返回 this。
StringBuilder delete(int startindex,int endlndex)

\\返回一个与构建器或缓冲器内容相同的字符串
String toString()

```