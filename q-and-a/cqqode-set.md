---
description: 某些功能是需要Pro的……
---

# \[CQ码\]如何发送图片语音表情?

## 前提

请查看[酷Q air 与 Pro 之间的区别](kuqair-yu-pro-zhi-jian-de-qu-bie.md)，明确你的机器人支持哪些CQ码。

官方文档：[https://docs.cqp.im/manual/cqcode/](https://docs.cqp.im/manual/cqcode/)

emoji list: [https://cqp.cc/t/15827](https://cqp.cc/t/15827)

##  官方部分说明

### 结构 <a id="&#x7ED3;&#x6784;"></a>

CQ码的结构为 `[CQ:function,key=value,...]`

其中 `function` 为功能名，`key` 为参数名，`value` 为参数值，`key=value` 称为一组参数。

一个CQ码可以包含零组、一组或多组参数，功能名与每组参数之间用半角逗号 `,` 分割。

### 规范 <a id="&#x89C4;&#x8303;"></a>

* CQ码是**大小写敏感**的，使用时请注意大小写。
* 对于不在CQ码内的消息（即文本消息），为了防止解析混淆，需要进行**转义**。  
  转义规则如下：

  ```text
  & -> &amp;
  [ -> &#91;
  ] -> &#93;
  ```

* CQ码中的 `function`（功能名）与 `key`（参数名），仅支持大小写字母、数字、短横线（-）、下划线（\_）及点号（.）。
* 对于CQ码中的 `value`（参数值），为了防止解析混淆，需要进行**转义**。  
  转义规则如下：

  ```text
  & -> &amp;
  [ -> &#91;
  ] -> &#93;
  , -> &#44;
  ```

## 图片发送

### 如果你懒得看……

 请试试[这个](https://cqp.cc/t/47996)插件，可以快速帮你配置图片CQ码 ![](../.gitbook/assets/uxd_zc7k-_h34w-e4-05h.png) 

### 准备

 既然要发送图片，我们就需要发送的图片 🖼 、酷Q Pro 👨🏫   
还有一个我们用来进行消息发送的插件 🔌 plugin\(

![](../.gitbook/assets/image%20%2879%29.png)

我这里准备了一张很有寓意的图片。 ![](../.gitbook/assets/llu6-2z6ltvuf2v-txu55gn.png) 

![](../.gitbook/assets/you-yang-nv-zhuang-zhao-.png)

### 导入图片

 前面我们已经说过了酷Q目录的用处  
我们所存放图片的地方是data/app文件夹

 把我们的图片丢进去

![](../.gitbook/assets/image%20%2875%29.png)

 为了不出什么岔子，我们把这里的文件名改成我们想要的文件名：

![](../.gitbook/assets/image%20%2870%29.png)

{% hint style="info" %}
这里记得记住我们的文件名:**`悠扬女装照.png`**
{% endhint %}

 这里我们打开一个可以编辑发送文本的插件，我用的是 **语言库**

![](../.gitbook/assets/image%20%2880%29.png)

   **你看到这段消息由两个部分组成：**

```text
Emm…… 
[CQ:image,file=悠扬女装照.png]
```

上面的`Emm……`是我们的文字信息  
下面`[CQ:image.file=悠扬女装照.png]`就是我们的CQ码了

 其中，`CQ:image`指定了这是一个**图片CQ码**。  
`file=悠扬女装照.png`则指定我们的图片名称。

![](../.gitbook/assets/image%20%2869%29.png)

我们在群内测试一下：

![](../.gitbook/assets/image%20%2883%29.png)

#### 可以看到，图片已经成功发送了。

### 使用文件夹进行图片分类

当然，你有时候会发现cqimg缓存文件太多了。  
阻碍了我们查询图片  
肿么办？

 这时候不要急，用~~灰指甲（~~ 一个文件夹就能解决难题

 依旧转到image文件夹。  
这里我们新建一个文件夹，名称自己取  
然后顺手把图片丢进去，如图所示

![](../.gitbook/assets/image%20%2884%29.png)

 这时候我们的CQ码得这么~~`屑`~~写

```text
Emm…… 
[CQ:image,file=悠扬女装照合集\悠扬女装照.png]
```

 发出来的效果是一样的，并没有啥区别,我就不贴图了。

## 语音发送

语音发送也是使用CQ码。

像上面一样， 我们这里找到`record`文件夹，把我们要发送的语音放进去~

![](../.gitbook/assets/image%20%2873%29.png)

同样的，我们也选用语言库来进行设置

 这里我们将上面的图片CQ码替换成了这样子：

```text
Emm…… 
[CQ:record,file=悠扬不女装.mp3]
```

两处改动：

```kotlin
CQ:image -> CQ:record //声明这是一个语音CQ码
悠扬女装照.png -> 悠扬不女装.mp3 //修改文件名称
```

发出来的效果：

![](../.gitbook/assets/image%20%2868%29.png)

 你可以看到，`emm……`这段被忽略了。  
这种`独占CQ码` 不支持与其他消息发送，默认以离消息文本起始位置最近的CQ码为准。

 如果你想同时发送语音和消息，可以询问对应的插件作者如何做到这种操作。

### 魔法语音

![](../.gitbook/assets/image%20%2874%29.png)

 如题所示，你可以看到前面的语音标识变成了膜法语音  
这里我们仅需稍作修改:

```kotlin
Emm…… 
[CQ:record,file=悠扬不女装.mp3,magic=true]
```

其中我们添加了这么一个参数：

```kotlin
,magic=true  //使用,分割参数，magic为参数名，true表示魔法语音模式为开启
/*
如果指定为false，就跟普通语音一样
你之前不用输入的原因是因为默认模式就是普通语音
*/
```

## 其他的CQ码

 上面我们介绍了几个常用的CQ码，但是CQ码种类有很多。

具体你可以看官方文档：[https://docs.cqp.im/manual/cqcode/](https://docs.cqp.im/manual/cqcode/)  
emoji 对应list:[https://cqp.cc/t/15827](https://cqp.cc/t/15827)  
但是用法大同小异，这里我介绍其中几个CQ码的特殊之处

### 只支持接收、不支持发送的CQ码

```kotlin
[CQ:sign,location={1},title={2},image={3}] //CQ:sign
[CQ:dice,type={1}] //CQ:dice,type不支持自定义
[CQ:rps,type={1}] //CQ:rps,type不支持自定义
[CQ:hb] //CQ:hb 红包消息，无法发送。
[CQ:rich] //rich(富文本)消息，通常游戏、链接分享会收到这个，恶意xml消息也会收到
//如果其他酷Q发送share消息就会收到rich消息
```

###  仅支持发送的CQ码

```kotlin
[CQ:share,url={1},title={2},content={3},image={4}]
//链接分享消息
[CQ:bface,id={1}] //原创表情
```

### @全体成员

```kotlin
[CQ:at,qq=123456] //这个CQ码会At QQ为123456的群成员
[CQ:at,qq=all]  //这个CQ码会AT全体成员
```

