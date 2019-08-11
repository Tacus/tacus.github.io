---
textarea: lua string

---
**Chapter 4. Strings**

Strings represent text. A string in Lua can contain a single letter or an entire book. Programs that manip- ulate strings with 100K or 1M characters are not unusual in Lua.

Strings in Lua are sequences of bytes. The Lua core is agnostic about how these bytes encode text. Lua is eight-bit clean and its strings can contain bytes with any numeric code, including embedded zeros. This means that we can store any binary data into a string. We can also store Unicode strings in any representation (UTF-8, UTF-16, etc.); however, as we will discuss, there are several good reasons to use UTF-8 whenever possible. The standard string library that comes with Lua assumes one-byte characters, but it can handle UTF-8 strings quite reasonably. Moreover, since version 5.3, Lua comes with a small library to help the use of UTF-8 encoding.

Strings in Lua are immutable values. We cannot change a character inside a string, as we can in C; instead, we create a new string with the desired modifications, as in the next example:

                  a = "one string"
                  b = string.gsub(a, "one", "another")  -- change string parts
                  print(a)       --> one string
                  print(b)       --> another string

Strings in Lua are subject to automatic memory management, like all other Lua objects (tables, functions, etc.). This means that we do not have to worry about allocation and deallocation of strings; Lua handles it for us.

Strings 代表文本。在lua中一个string 可以包含一个字母，或者整本书。在程序里面维护一个100k或者1m的字符是非常常用的。

Strings在lua中是字节序列。lua 核心并不知道这个字节怎么编码成文本。lua是完整的8比特位并且它的字符串可以存储任何二进制数据。我们同样可以存储unicode 以任何形式表示方法。就像我们之前讨论的，这里有n多理由让我们尽可能使用utf8方式编码。lua自带的标准string 库都假设lua是单字节字符，但是它也可以合理的处理utf8字符串。除此之外，5.3版本之后lua自带一个string 库用以处理utf8的编码。

lua中的字符串是不可变的值。我们不能像在c中一样改变一个字符串的字符，我们创建一个新的来达到我们想要的修改。就像下面的例子一样

strings的内存在lua中是自动管理，就像其他的类型。这意味着，我们不用去担心它的内存分配和释放。lua替我们处理它。

We can get the length of a string using the _length operator_ (denoted by #):

                  a = "hello"
                  print(#a)             --> 5
                  print(#"good bye")    --> 8
    
我们可以获取string的长度通过长度操作符#

This operator always counts the length in bytes, which is not the same as characters in some encodings.

We can concatenate two strings with the concatenation operator .. (two dots). If any operand is a number, Lua converts this number to a string:

                  > "Hello " .. "World"     --> Hello World
                  > "result is " .. 3       --> result is 3
    
#操作符按照字节来计算string的长度，这和某个编码的字符个数是不同的。
我们可以用两个点..连接两个string。如果某一个操作数是数字，lua会将数字转成string。
(Some languages use the plus sign for concatenation, but 3 + 5 is different from 3 .. 5.)  
 Remember that strings in Lua are immutable values. The concatenation operator always creates a new

string, without any modification to its operands:

    			> a = "Hello"  
    			> a .. " World" --> Hello World >a --> Hello

 