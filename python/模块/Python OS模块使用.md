## OS模块的使用
[相关笔记](http://note.youdao.com/noteshare?id=7600f8d8194a243b6436f4881e5556d5)

#### 例1、用python脚本写出testdir路径下目录的绝对路径
```testdir/
├── f1
├── f2
├── f3      
└── jpg
    ├── getjpg.py
```
实现脚本：
```python
import os
def dirlist(path):
    filelist = os.listdir(path)         #使用os.listdir遍历“path”目录下所有的文件
    for filename in filelist:
        filepath = os.path.join(path,filename) # 在某个目录下创建一个新目录，首先把新目录的完整路径表示出来
        
        if os.path.isdir(filepath):     #使用os.path.isdir()判断是否是文件夹
            dirlist(filepath)
        print filepath           
allfile = dirlist(".")
```

---
#### 例2、使用os.walk()模块写出文件绝对路径
    函数声明：os.walk(path)
	该函数返回一个元组，该元组有3个元素，这3个元素分别表示每次遍历的路径名，目录列表和文件列表
    #dirpath 是一个string，代表目录的路径，
    #dirnames 是一个list，包含了dirpath下所有子目录的名字。
    #filenames 是一个list，包含了非目录文件的名字。
```python
import os
for dirpath,dirnames,filenames in os.walk('.'):
    for filename in filenames:
        PATH = os.path.join(dirpath,filename)
    print PATH
```    

---

#### 例3、编写一个程序，能在当前目录以及当前目录的所有子目录下查找文件名包含指定字符串的文件，并打印出相对路径。


```python
import os
class OS_Advance(object):
    """docstring for OS_Advance"""

    def dir_1(self, directory):
        directory = os.path.split(directory)    #os.path.split路径拆分
        return directory[0]

    def find_path(self, dirname):
        results= []
        for root, dirs, files in os.walk('/Users/boxfish-edu/Downloads'):  #例2中查看os.walk模块的使用
            results += [os.path.relpath(os.path.join(root, x), start = '.') #os.path.relpath下面有对该模块的解释
            for x in files if dirname in x]
        for result in results:
            print(result)

osa = OS_Advance()
osa.find_path('py')
print(osa.dir_1('Practice/Chain.py'))
```

对该模块的解释os.path.relpath：
```
p = 'a/b/c/d'
print os.path.relpath(p) #默认当前目录开始 相当于 ./a/b/c/d
print os.path.relpath(p,'a/b')# 以a/b/目录开始 c/d

```

    