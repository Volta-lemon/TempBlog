

ChatGPT很火，但是身边人总是对他不以为然，甚至因为门槛（魔法或账号）高，懒的去，我就偏要让他们用上GPT，装好这个AC中间的字母。——总而言之，让亲朋好友使上GPT！

经过在github长时间的混迹，我曾见人起高楼（微信接入ChatGPT，我一开始的想法），又见人楼塌了（给微信号封了！！！）。深知这建高楼的方式不适合我，于是打起了QQ的主意。

发现了ChatGPT for Bot这个项目，在踩坑*3的基础上，用了一晚上的时间就搭建完成。（当然，你看我的教程，我觉得只需要emmmm，30分钟！！！）PS：只需要一台window电脑即可。

## 

## 1. 演示效果：



## 2. 部署方式



详细文档在这里：https://chatgpt-qq.lss233.com/

这个机器人不只可以接入GPT，还能接入newbing、bard、文心一言等模型！

感恩作者写了这么好的项目以及这么丰富的文档。

并且我前天提的issue，今天就得到回复了！

文档中还有一键部署到Linux，不过那还是比较有门槛的，推荐大家先在本机搞一搞和朋友一起玩一玩。

碎碎念太多，总之这个作者真的是个很强并且很好的人。



准备：

1. 一个api_key:从platform.openai.com【碎碎念，前1000个都有号，我就晚了那么一点号就没了，还这么用心写教程，我觉得闪客大佬应该给我奖励】
2. 一个window电脑
3. 如果你想更快速的响应可以先准备登录腾讯云（不是必须）
4. 一个马上就要拥有一个自己的chatgpt机器人的激动内心
5. 首先去github上下载部署包：**https://github.com/lss233/chatgpt-mirai-qq-bot/releases/tag/v2.3.4**

如果下载有问题的话也可以下载我上传百度云上的：是作者4月9日更新的（作者太勤奋了！）



链接: https://pan.baidu.com/s/15QeQzORSSiZY0i1kB3TXNw?pwd=cmda 提取码: cmda 复制这段内容后打开百度网盘手机App，操作更方便哦



上面的文件夹里包含所有的压缩包（部署包+ffmpeg+proxy）



1. 将部署包拷贝在不含中文，不含空格的文件夹中
2. 解压部署包，可以看到有一个初始化.cmd——没错点击他！
3. 之后按回车即可，再之后就会弹出一个记事本文件，填写配置

> 这里很重要，我就是在这里弄了好长时间，一方面是因为我自己的号，额度已经过期了，一时间找不到地方去买号，最后才找到一个地方买的号。另一方面就是我是凌晨时候弄得，晚上漂亮国用的人多，服务太卡，我一度以为是配置问题，弄了好长时间。

作者大大给的样例：



![img](https://article-images.zsxq.com/FuzEXwyYmufztwOSPf2TnBK1kG_T)

其他部分按规则填自己的就行，一定要把我圈起来的地方改成：

 api_key = "你的api_key"

通常是以sk开头的字符串！【我在这踩坑好长时间~~~~】

然后那个proxy代理规则，填自己客户端上的端口（你懂得）

尊贵的GPTplus用户也可以使用更好的模型哟！大概需要通过验证吧？我不尊贵所以不知道。

![img](https://article-images.zsxq.com/FnX52aTxE0niJdul4nw-9V-nBF4a)



你如果想让服务更快，需要加一个配置【不收费，并且搭起来很快，利用腾讯云函数】：

[[openai.accounts]]

 api_key = "sk-xxxxxx"

api_endpoint = "填一个节点"

这个节点的搭建方法（地址来源：https://github.com/Ice-Hazymoon/openai-scf-proxy）：

在https://cloud.tencent.com/注册账号

进入云数控制台：https://console.cloud.tencent.com/scf/list

依次点击【新建】->【从头开始】，然后按照下面配置，没写出来的就不用管了，使用默认设置

函数类型：Web函数

任数名称：openai-proxy（也可以随手取个名称）

地域：香港（也可以是中国以外的任何国家）

运行环境：Nodejs 16.13（或更高版本）

高级配置：

内存：64M

执行超时时间：900秒

请多并发：2个并发

日志配置 -> 日志投递：启用（可选择不开，开的话一个月应几分钱）

函数代码：本地上传zip包（点我下载ZIP包）

触发器配置（这里可能要创建一个新的触发器）：

默认触发器

触发别名/版本：默认流量

请申请方法：ANY

发布环境：发布

鉴权方法：免鉴权

之后点击“完成”按钮，进入【任数字管理】，点击【任数字管理】，往下拉，找到【访问路径】，这里就是你的代理地址

使用的时候需要把 "/release" 部分删除

例如：https://service-aaaaa.hk.apigw.tencentcs.com/release/

改为：https://service-aaaaa.hk.apigw.tencentcs.com/

![img](https://article-images.zsxq.com/FnyOpf0Wc__wDuJ3hifmfSWCv6Oq)

PS:我填的漂亮g，但是这样需要我的window电脑上也是漂亮g才可以。



1. 填写完文件后，保存，需要按回车按一下，不需要的话等待即可！
2. 目录中多了两个cmd脚本，你已经成功了大半！
3. 我们先双击 启动 ChatGPT.cmd ，如果你的运气爆棚，你会看见类似这样的提示：





![img](https://article-images.zsxq.com/FrU4k0OI9plg05escI5-6hoqOZRz)

【但是我当时运气没有爆棚。。。】



保持窗口不要关，打开另一个 Mirai.cmd，然后等待程序启动完毕。【在这段时间里，你可以先在电脑上登上自己的qq小号，防止出现登录验证，增加操作成本】



如果你看见了红色的错误提示，无需理会。





![img](https://article-images.zsxq.com/FsiDpBLWHogBvs8Kc1cUO2flhV-5)

出现

\>

之后就登陆一下你想作为机器人的小号qq即可！

login 你机器人的QQ号 你机器人的密码 MACOS

顺利的话，你可以直接看到successful提示，之后你就可以给小号发消息看看效果了！

![img](https://article-images.zsxq.com/FtiEF6HnrctqAHggXn2hImnNNfc6)







不顺利的话，可能你需要验证，但不用慌，也很简单（虽然我没验证哈哈哈）——这部分我就是直接抄官方文档了，大家可以自己去官方文档查看。



> 接下来，Mirai 很有可能会要求你提供验证码。这个验证码其实就和你平时登录 QQ 时做的验证码是一样的。 
>
> 我们用鼠标选中 Mirai 提供的那一段链接，然后按一下 鼠标右键，这段链接就会被复制。

![img](https://article-images.zsxq.com/Fqd3DvRP3DGS5jlcd6h8XE06pj3u)

我们用鼠标选中 Mirai 提供的那一段链接，然后按一下 **鼠标右键**，这段链接就会被复制。

打开浏览器，在地址栏中粘贴你复制的链接并回车，你会看见一个这样的页面：



![img](https://article-images.zsxq.com/FkWRCIO9xNcPEwiXWMls9SpPy0Fh)







接下来，我们对着页面的空白处按下 F12，打开 **开发人员工具**。



切换到 Network（网络） 选项卡，然后在这个框中输入 verify







![img](https://article-images.zsxq.com/FnPDKqLfU0mYB2x6MaMVWSvADua3)



我们放着这个窗口不管，回到刚刚那个网页，把所有的滑动验证完成，直到它不再出现新的验证码。

这个时候，回到**开发人员工具**的窗口，你会发现多出了几个 cap_union_new_verify。



我们选中最后一个，然后点击右边的 **Preview**（或者叫预览） 。



然后右键 ticket 后面的那串代码，点击复制。





![img](https://article-images.zsxq.com/FlbMzRfx_KA3Mwm2r6xzF1CC3nuJ)





















回到  启动 Mirai.cmd的那个黑色窗口，按下鼠标右键，那串代码就会被粘贴到里面。

我们按下回车，继续。



接下来，Mirai 很有可能会让你进行短信验证。通常到了这一步的时候，你离整个项目顺利运行已经不远了。



随后你的手机上将会收到一条短信验证码，把验证码中的数字输入到窗口中，然后回车。

然后你就会看到！



![img](https://article-images.zsxq.com/FtiEF6HnrctqAHggXn2hImnNNfc6)







好，现在去测试你的机器人吧！！！

现在的功能不够，就去官方文档里探索更多吧！







碎碎念：希望我踩过的坑大家不要踩，所以再说一遍！

1. 一定要修改access_token为api_key再用官网的api_key！
2. 不要在凌晨部署！！
3. 多看文档多解决问题



PS：如果有和我一样的倒霉蛋，没有号也想尝试部署的话，我买了几个备用的，可以私聊我（5美金额度，所以比其他地方便宜点）

之后如果有时间有机会我会尝试部署到Linux上，不过估计得再买一台服务器了，还挺贵，最近学校事多+考研比较忙，看看大家的反馈，希望能帮到大家！！！



加入星球第一天，输出3500字！！！