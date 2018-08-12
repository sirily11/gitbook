# [Chalice](https://github.com/aws/chalice) 架设[Lambda Function](/lambda-function.md)的库

## 第一步

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



