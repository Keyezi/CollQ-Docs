---
description: 某些功能是需要Pro的……
---

# \[CQ码\]如何发送图片语音表情?

## 前提

请查看[酷Q air 与 Pro 之间的区别](kuqair-yu-pro-zhi-jian-de-qu-bie.md)，明确你的机器人支持哪些CQ码。

## 图片发送

### 如果你懒得看……

 请试试[这个](https://cqp.cc/t/47996)插件，可以快速帮你配置图片CQ码 ![](../.gitbook/assets/uxd_zc7k-_h34w-e4-05h.png) 

### 准备

 既然要发送图片，我们就需要发送的图片 🖼 、酷Q Pro 👨🏫   
还有一个我们用来进行消息发送的插件 🔌 plugin\(

![](../.gitbook/assets/image%20%2877%29.png)

我这里准备了一张很有寓意的图片。 ![](../.gitbook/assets/llu6-2z6ltvuf2v-txu55gn.png) 

![](../.gitbook/assets/you-yang-nv-zhuang-zhao-.png)

### 导入图片

 前面我们已经说过了酷Q目录的用处  
我们所存放图片的地方是data/app文件夹

 把我们的图片丢进去

![](../.gitbook/assets/image%20%2873%29.png)

 为了不出什么岔子，我们把这里的文件名改成我们想要的文件名：

![](../.gitbook/assets/image%20%2869%29.png)

{% hint style="info" %}
这里记得记住我们的文件名:**`悠扬女装照.png`**
{% endhint %}

 这里我们打开一个可以编辑发送文本的插件，我用的是 **语言库**

![](../.gitbook/assets/image%20%2878%29.png)

   **你看到这段消息由两个部分组成：**

```text
Emm…… 
[CQ:image,file=悠扬女装照.png]
```

上面的`Emm……`是我们的文字信息  
下面`[CQ:image.file=悠扬女装照.png]`就是我们的CQ码了

 其中，`CQ:image`指定了这是一个**图片CQ码**。  
`file=悠扬女装照.png`则指定我们的图片名称。

![](../.gitbook/assets/image%20%2868%29.png)

我们在群内测试一下：

![](../.gitbook/assets/image%20%2881%29.png)

#### 可以看到，图片已经成功发送了。

### 使用文件夹进行图片分类

当然，你有时候会发现cqimg缓存文件太多了。  
阻碍了我们查询图片  
肿么办？

 这时候不要急，用~~灰指甲（~~ 一个文件夹就能解决难题

 依旧转到image文件夹。  
这里我们新建一个文件夹，名称自己取  
然后顺手把图片丢进去，如图所示

![](../.gitbook/assets/image%20%2882%29.png)

 这时候我们的CQ码得这么~~`屑`~~写

```text
Emm…… 
[CQ:image,file=悠扬女装照合集\悠扬女装照.png]
```

 发出来的效果是一样的，并没有啥区别,我就不贴图了。

## 语音发送

语音发送也是使用CQ码。

像上面一样， 我们这里找到`record`文件夹，把我们要发送的语音放进去~

![](../.gitbook/assets/image%20%2872%29.png)

同样的，我们也选用语言库来进行设置



 这里我们将上面的图片CQ码替换成了这样子：

```text
Emm…… 
[CQ:record,file=悠扬不女装.mp3]
```

