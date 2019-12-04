### openssl 实现Android jni 加解密

#### 借鉴 

https://github.com/GitPhoenix/OpenSSL

https://github.com/leenjewel/openssl_for_ios_and_android

#### 环境说明

- 替换openssl版本至1.1.0f

- NDK 16 （支持 armeabi）

- CMake 3.10.2

#### 代码说明

基本没有修改 `GitPhoenix/OpenSSL`中算法实现，只修改了openssl版本可以编译通过和使用

生成的 so 文件有点大，需要精简库。这里只学习不做这个工作了，请自己动手吧。

#### 缺点

加解密错误在jni内部没有通过 java Exception抛出

没有 64 位支持，需要自己在linux下去编译生成



#### 参考学习原文

#### 安全加密C语言库OpenSSL，在Android中服务器和客户端之间的签名验证和数据加密通信等。

### OpenSSL系列文章：
##### 一、[Android CMake轻松实现基于OpenSSL的HmacSHA1签名](http://www.jianshu.com/p/07df7626b4ee)
##### 二、[Android CMake轻松实现基于OpenSSL的SHA(1-512)签名](http://www.jianshu.com/p/4804f176daaf)
##### 三、[Android CMake轻松实现基于OpenSSL的MD5信息摘要&异或加解密](http://www.jianshu.com/p/768d8be14b93)
##### 四、[Android CMake轻松实现基于OpenSSL的AES加解密](http://www.jianshu.com/p/3f09a048a2cc)
##### 五、[Android CMake轻松实现基于OpenSSL的RSA加解密](http://www.jianshu.com/p/04eba47f7c07)
##### 六、[Android CMake轻松实现基于OpenSSL的RSA签名和验证](http://www.jianshu.com/p/18f1380e7922)
##### 七、[在Retrofit的基础上结合OpenSSL实现服务器和客户端之间数据加密通信](http://www.jianshu.com/p/970a8331143f)

