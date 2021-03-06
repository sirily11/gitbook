# [Chalice](https://github.com/aws/chalice) 架设[Lambda Function](/lambda-function.md)的库

## 第一步 安装[虚拟环境](/python-virtual-environments.md)

安装Python 虚拟环境 pipenv

```shell
pip install --user pipenv
```

接下来就是通过pipenv虚拟环境进行安装chalice了。

```
pipenv install chalice
```

这会在你当前目录下创建一个Pipfile。

内容大概长得就像这样：

```
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"

[packages]
chalice = "*"
"boto3" = "*"
pyinstaller = "*"

[dev-packages]
"autopep8" = "*"

[requires]
python_version = "3.6"
```

之后为了方便我们直接使用Chalice这个库，我们可以进入这个虚拟环境。

```
pipenv shell
```

你可以通过以下命令验证安装成功与否（来自Github）：

```
chalice --help
Usage: chalice [OPTIONS] COMMAND [ARGS]...
...
```

## 第二步 创建你的项目

下一步要做的事情便是用chalice命令来创建新的项目了:

```
$ chalice new-project helloworld
```

这条命令会创建一个名为`helloworld`的文件夹。你可以看见已经有几个文件为你创建好了。

```
$ cd helloworld
$ ls -la
drwxr-xr-x   .chalice
-rw-r--r--   app.py
-rw-r--r--   requirements.txt
```

## 第三步 编辑你的app.py

```py
from chalice import Chalice
app = Chalice(app_name='helloworld')
app.debug = True

@app.route('/')
def index():
    return {'hello': 'world'}
```

**接下来运行**

```
chalice local
```

你就可以打开命令提示符里的ip地址，之后你会在你的屏幕上显示：

```
{'hello': 'world'}
```

{% hint style='info' %}
注意！因为添加了debug功能，所以如果此时更改app.py，页面内容也会随之改动。

{% endhint %}

最后，如果我们对结果满意，就可以提交了

```
chalice deploy
```
{% hint style='danger' %}
在提交前，请务必确认你已经安装了[AWS CLI](https://aws.amazon.com/cn/cli/)。
{% endhint %}

## 第四步 进行更高阶的尝试
到此，我们已经知道了如何进行基础的访问，接下来我们是如何进行Http request。我们可以在URL的Parm中添加一些数值，之后打印到我们的页面上。方式如下。我们在URL的地址处填写/resource/123

```python
@app.route('/resource/{value}', methods=['PUT'],cors=True)
def put_test(value):
    return {"value": value}
```
之后我们屏幕上便会出现{"value":123}了。为了方便我们的其他程序调用这个函数，我们需要添加cors。
有关cors的更多详情，请阅读[这篇文章。](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Access_control_CORS)



