### npm运行报错如下

```bash
(node:internal/fs/read_file_context:68:3) {
  opensslErrorStack: [ 'error:03000086:digital envelope routines::initialization error' ],
  library: 'digital envelope routines',
  reason: 'unsupported',
  code: 'ERR_OSSL_EVP_UNSUPPORTED'
}
```

**原因：主要是nodeJs V17版本发布了OpenSSL3.0对算法和秘钥大小增加了更为严格的限制，nodeJs v17之前版本没影响，但V17和之后版本会出现这个错误**

解决方法：

1. 更换nodejs为**v17**之前的版本

2. 设置临时环境变量 ，**Windows下使用cmd命令**直接输入以下代码

```bash
$env:NODE_OPTIONS="--openssl-legacy-provider" 
```

有的**Windows系统**无法使用上面的命令可尝试这个：

```bash
set NODE_OPTIONS=--openssl-legacy-provider
```



**linux下输入**

```bash
export NODE_OPTIONS=--openssl-legacy-provider
```

3. 在构建命令前加入

```bash
"scripts": {
   "serve": "set NODE_OPTIONS=--openssl-legacy-provider && vue-cli-service serve",
   "build": "set NODE_OPTIONS=--openssl-legacy-provider && vue-cli-service build"
},
```


