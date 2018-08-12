# 在文本中设定提示风格文字 {#styled-hint-blocks-in-your-docs}

此插件需要 gitbook版本`>=2.0.0`.

### 安装 {#install}

添加以下内容到`book.json`,文件，之后运行`gitbook install`:

```
{
    "plugins": ["hints-istex"]
}
```

### 使用方法 {#usage}

你现在可以通过添加hint来使用了

```
{% hint style='info' %}
重要信息，以下内容会被当作提示内容。
{% endhint %}
```

The above example will produce a styled alert, with an icon:

```html
<div class="alert alert-info hints-alert">
    <div class="hints-icon">
        <i class="fa fa-info"></i>
    </div>
    <div class="hints-container">
        <p>Important info: this note needs to be highlighted</p>
    </div>
</div>
```

效果如下

{% hint style='info' %}

重要信息如下

{% endhint %}

Available styles are:

* `info`
  \(default\)
* `tip`
* `danger`
* `working`

### 设置 {#configuration}

你可以在`book.json`设置你自己的class：

```js
{
    "plugins": ["hints-istex"],
    "pluginsConfig": {
        "hints": {
            "info": "fa fa-info-circle",
            "success": "fa fa-check-circle",
            "danger": "fa fa-exclamation-triangle",
            "warning": "fa fa-exclamation-circle"
        }
    }
}
```



