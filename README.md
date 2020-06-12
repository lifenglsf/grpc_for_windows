# 这是一个grpc+protobuf的windows版本
项目使用 [vcpkg](https://github.com/microsoft/vcpkg)编译，仅供大家测试使用，请勿用于正式环境


朋友需要在windows下进行php+grpc的相关开发，然后发现官方的grpc未提供windows下的php plugin的exe文件，故建立此项目，希望能够帮助更多的以windows为开发环境的开发者。 

# 版本日志
- 2020.1.14 grpc 1.26,protoc 3.11.2
- 2020.6.12 grpc 1.28.1 protoc 3.12.0

# 使用方法
### 生成php文件的参考命令

`protoc.exe --proto_path=. --php_out=. --grpc_out=. --plugin=protoc-gen-grpc=grpc_php_plugin.exe helloworld.proto`

参考[protocbuf使用](https://developers.google.com/protocol-buffers/docs/proto3#generating)

可以把exe的目录添加到系统的path变量下
    
     
