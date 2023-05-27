# thztools
>author:Sen
>>e-mail:tianhuzong@qq.com 
>>Github:https://github.com/tianhuzong
>>Gitee:https://gitee.com/thzsen
>>QQ:1485319167
- - -
>Tianhuzong开发的工具，方便在开发中使用
1.0.2加入了加密解密内容：<kbd>RSA</kbd>,<kbd>AES</kbd>，<kbd>凯撒加密</kbd>
- - -
>1.0.3版本中，修复了维吉尼亚密码的错误，引入了与ip地址有关的类<kbd>IP</kbd>
- - -
>1.0.4版本中，新增了检测ip是否为合法的IPv4
- - -
- - -
>1.0.5中，修复一个命名冲突
- - -
##使用方法：
- - -
####安装模块
```bash
pip install thztools
```
安装完模块之后接下来就是引用了

下面是引用jiami模块的类的用法

```python
from  thztools.jiami import *
#-----RSA-----
rsa = RSA()
#生成密钥对
(gongyao,siyao) = rsa.newkeys(1024)#返回生成的密钥对
#加密
mingwen = "这是一段中文字符串"
miwen = rsa.jiami(gongyao,mingwen)#返回密文
#解密
res = rsa.jiemi(siyao,miwen)#返回明文
#数字签名
sign = rsa.sign(siyao,"这是被签名的文本")#返回签名文本
#签名验证
res = rsa.qmyz("这是被签名的文本",sign,gongyao)#返回布尔值

#-----凯撒密码-----
kaisa = KaiSa()
#加密
miwen = kaisa.jiami("Hello,world",3)
#第一个参数为欲加密的文字，除英文字母外的都不会被加密
#第二个参数是偏移量，正数表示向右偏移，负数表示向左偏移

#解密
mingwen = kaisa.jiemi(mingwen,3)
#第一个参数是密文
#第二个参数是偏移量，与加密时的偏移量相同

#-----AES-----
aes = AES
#生成AES秘钥
key = aes.newkey()#自动生成随机秘钥，bytes
#加密
miwen,suijishu,tag = aes.jiami('这是被加密的内容',key)
# 第一个参数是被加密的内容，第二个参数是秘钥
# 返回值第一个是密文
# 第二个是加密时生成的随机数
# 第三个是加密时生成的验证标签

#解密
mingwen = aes.jiemi(miwen,key,suijishu,tag)
# 第一个参数是密文
# 第二个参数是密钥
# 第三个参数是加密时生成的随机数
# 第四个参数是加密时生成的验证标签

#-----维吉尼亚密码-----
wjny = Weijiniya()
#加密
miwen = wjny.jiami("这是被加密的文字",'thisisakey')
#返回密文

#解密
mingwen = wjny.jiemi("这是被解密的文字",'thisisakey')
#返回明文
```

下面是使用ip模块的类的用法

```python
from thztools.ip import *
ip = IP()
#请注意，输入的ip应为IPv4地址
#IP地址的基本信息
infomation = ip.jbxx(ip = '192.0.2.0')
#ip地理位置
geo = ip.geo(ip = '8.8.8.8')
```