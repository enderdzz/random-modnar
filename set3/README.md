Set3中需要额外安装的库函数：pycrypto

>在以下提到的脚本中，均在py文件内写有注释，以下部分仅供参考

# Challenge17

题目要求使用pkcs7的方式，在给出的10个字符串中随机选取一个，对该字符串进行padding后加密，并解密后验证padding

其中定义class：AESCipher 主要包含两个函数及两个self变量。

*	其中``GetRandomStr``函数的主要功能为随机选取字符串，并对这个字符串进行padding，最终对padding结果使用AES的CBC模式加密，并按照题目要求返回msg和iv值
*	其中``DecryptCheckPadding``函数的主要功能为对密文进行解密，并且检验padding的方式是否正确，检验padding的方式主要由上文中提到的``pkcs7unpad``函数提供。

演示输出结果：第一个为正确结果，第二个对padding进行了篡改，因此输出的为False结果

# Challenge18

题目要求为对给出的字符串，并按照题中所给出的参数，使用AES的CTR模式对字符串进行解密。

演示输出结果：Yo, VIP Let's kick it Ice, Ice, baby Ice, Ice, baby

# Challenge19

题目要求，按照上一题中使用的方法，生成随机的AES密钥，并将题目中给出的message进行base64解码，在进行AES的CTR模式加密，并将并通过语义分析的方法进行猜测密钥，将原文恢复。

按照题目中给出的方法，由于该方法为基于对语义的尝试的方法，因此需要尝试多次才能够得出正确的结果，存在一定误差率，但本脚本使用的方法使误差仅存在于大小写之间，只需尝试几次便可得到正确结果。

验证方法：脚本中已提供