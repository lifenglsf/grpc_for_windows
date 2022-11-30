### 朋友需要在windows下进行php+grpc的相关开发，然后发现官方的grpc未提供windows下的php plugin的exe文件，故建立此项目，希望能够帮助更多的以windows为开发环境的开发者。 

# 这是一个grpc+protobuf的windows版本
项目使用 [vcpkg](https://github.com/microsoft/vcpkg)编译，仅供大家测试使用，请勿用于正式环境

### 安装命令
- clone [vcpkg](https://github.com/microsoft/vcpkg) 项目到本地
- 安装最新的vcpkg。 
	bootstrap-vcpkg.bat
- 安装grpc 
	vcpkg install grpc
- x86文件位置
	installed\x86-windows\tools\protobuf
	installed\x86-windows\tools\grpc
- x64文件位置
	installed\x64-windows\tools\protobuf
	installed\x64-windows\tools\grpc




# 版本日志
- 2020.1.14 grpc 1.26,protoc 3.11.2
- 2020.6.12 grpc 1.28.1 protoc 3.12.0
- 2022.11.30 grpc 1.50.1 protoc 3.21.8

# 使用方法
### 生成php文件的参考命令

`protoc.exe --proto_path=. --php_out=. --grpc_out=. --plugin=protoc-gen-grpc=grpc_php_plugin.exe helloworld.proto`

参考[protocbuf使用](https://developers.google.com/protocol-buffers/docs/proto3#generating)

可以把exe的目录添加到系统的path变量下
    
# 特别说明
-  使用vcpkg 2022-11-10-5fdee72bc1fceca198fb1ab7589837206a8b81ba这个版本安装grpc会出现安装x86的grpc，安装完成后出现类似
`grpc provides CMake targets:
    # this is heuristically generated, and may not be correct
    find_package(gRPC CONFIG REQUIRED)
    # note: 7 additional targets are not displayed.
    target_link_libraries(main PRIVATE gRPC::gpr gRPC::grpc gRPC::grpc++ gRPC::grpc++_alts)
    find_package(modules CONFIG REQUIRED)
    target_link_libraries(main PRIVATE re2::re2 c-ares::cares)`
  这样的错误，然后发现grpc的plugin都没有生成，发现grpc少了个grpc[codegen]这个工具没有自动安装，安装这个工具即可`vcpkg install grpc[codegen]:x86-windows --recurse`这个命令会重新安装grpc
  - 正常情况grpc目录下的libprotobuf.dll,libprotoc.dll和protobuf目录下的应该是一样的，但是vcpkg 2022-11-10-5fdee72bc1fceca198fb1ab7589837206a8b81ba 安装的会不一致，需要使用protobuf下的dll文件，否则protoc生成proto程序文件会失败
