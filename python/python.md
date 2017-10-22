# PEP8

全部内容请参考[Python官网](https://www.python.org/dev/peps/pep-0008/)。以下为需要关注的几点。

## 缩进

使用 4 格缩进，只能使用空格，不能用 Tab。

## 空行的使用

1.  最外层函数定义前后需要加两个空格。

```python
(blank_line)
(another_blank_line)
def top_level_function():
	pass
(blank_line)
(another_blank_line)
```

2.  类的定义前后需要加两个空格。

```python
(blank_line)
(another_blank_line)
class SomeClass(object):
	pass
(blank_line)
(another_blank_line)
```

3.  类中的方法前后加一个空格。

```python
class SomeClass(object):

	def method_one():
      	pass
    
    def method_two():
      	pass

```

4.  适度地使用空格对代码进行**逻辑分区**。

##  `import` 语句

1.  使用 `import ...` 语法，一次只能导入一个模块：

```python
# bad
import sys, os

# good
import os
import sys
```

而 `from ... import ...` 语法则应在一行中导入所有需要的语法元素：

```python
from subprocess import Popen, PIPE
```

2.  多个 `import` 的组织顺序：**标准库 - 相关的第三方库 - 本地应用/特定库引入**。这三组 `import` 语句之间应当用一行空格隔开。对照以上规则，来看一个 Django 项目中的一个文件中 `import` 的使用。

```python
import uuid
from os.path import abspath

from django.db import models 
from django.utils.translation import ugettext_lazy as _

from django_extensions.db.models import TimeStampedModel

from users.models import Profile
from home.models import Post
```

