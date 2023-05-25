### thztools
Tianhuzong开发的工具，方便在开发中使用
目前版本加入了加密解密内容：RSA,AES，凯撒加密
使用方法：
#安装模块
```bash
pip install thztools
```
安装完模块之后接下来就是引用了
```python
#RSA
from  thztools.jiami import rsa
#生成密钥对
(gongyao,siyao) = rsa.newkeys(1024)
#加密
mingwen = "这是要加密的明文"
miwen = rsa.jiami(gongyao,mingwen)
#解密
res = rsa.jiemi(siyao,miwen)
b'\xe8\xbf\x99\xe6\x98\xaf\xe4\xb8\x80\xe6\xae\xb5\xe4\xb8\xad\xe6\x96\x87\xe5\xad\x97\xe7\xac\xa6\xe4\xb8\xb2'
