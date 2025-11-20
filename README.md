# -Opensssl3.x-ubuntu-openssl1.1.1
针对anygrasp教程中下载Ubuntu 24.04 中缺少 libssl.so.1.1.1的方法
详细操作步骤
1. 下载并解压 openssl 1.1.1 源码
   wget https://www.openssl.org/source/openssl-1.1.1.tar.gz
   tar -xzvf openssl-1.1.1.tar.gz
   cd openssl-1.1.1

2. 配置并编译安装（推荐家目录/临时目录）
   ./config --prefix=$HOME/openssl-1.1.1 --openssldir=$HOME/openssl-1.1.1 shared
    make -j$(nproc)
    make install
#这会在 ~/openssl-1.1.1/lib 下生成 libcrypto.so.1.1、libssl.so.1.1 等文件
3. 临时指定动态库优先路径运行 license_checker
   export LD_LIBRARY_PATH=$HOME/openssl-1.1.1/lib:$LD_LIBRARY_PATH
