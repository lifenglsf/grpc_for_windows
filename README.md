# 这是一个grpc+protobuf的windows版本
项目使用 [vcpkg](https://github.com/microsoft/vcpkg)编译，仅供大家测试使用，请勿用于正式环境

### 安装命令
使用 `vcpkg install grpc`  进行grpc安装，本地测试会自动安装x86和x64版本的grpc和protoc，grpc的exe在vcpkg项目的下的installed/x86-windows/tools/grpc和installed/x64-windows/tools/grpc目录下，protoc的exe在vcpkg项目的下的installed/x86-windows/tools/protobuf和installed/x64-windows/tools/protobuf目录下


朋友需要在windows下进行php+grpc的相关开发，然后发现官方的grpc未提供windows下的php plugin的exe文件，故建立此项目，希望能够帮助更多的以windows为开发环境的开发者。 

# 版本日志
- 2020.1.14 grpc 1.26,protoc 3.11.2
- 2020.6.12 grpc 1.28.1 protoc 3.12.0

# 使用方法
### 生成php文件的参考命令

`protoc.exe --proto_path=. --php_out=. --grpc_out=. --plugin=protoc-gen-grpc=grpc_php_plugin.exe helloworld.proto`

参考[protocbuf使用](https://developers.google.com/protocol-buffers/docs/proto3#generating)

可以把exe的目录添加到系统的path变量下
    
     
