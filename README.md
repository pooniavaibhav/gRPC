# gRPC
simple  python gRPC implementation
### We require installation of two packages to run grpc-
#### grpcio
#### grpcio-tools
Python’s gRPC tools include the protocol buffer compiler protoc and the special plugin for generating server and client code from .proto service definitions.

#### By default, gRPC uses Protocol Buffers, Google’s mature open source mechanism for serializing structured data (although it can be used with other data formats such as JSON).
### HOW PROTOBUFFS(PROTOCOLBUFFERS) WORKS?
##### Step1-
create a .proto file
### .proto FILE-
It has two main methods-
#### package
The .proto file starts with a package declaration, which helps to prevent naming conflicts between different projects. In Python, packages are normally determined by directory structure, so the package you define in your .proto file will have no effect on the generated code. However, you should still declare one to avoid name collisions in the Protocol Buffers name space as well as in non-Python languages. 
#### message definitions-
The definitions in a .proto file are simple: you add a message for each data structure you want to serialize, then specify a name and a type for each field in the message.
#### Things to rememeber-
The " = 1", " = 2" markers on each element identify the unique "tag" that field uses in the binary encoding. Tag numbers 1-15 require one less byte to encode than higher numbers, so as an optimization you can decide to use those tags for the commonly used or repeated elements, leaving tags 16 and higher for less-commonly used optional elements. Each element in a repeated field requires re-encoding the tag number, so repeated fields are particularly good candidates for this optimization.
### Compiling Your Protocol Buffers
Now that you have a .proto, the next thing you need to do is generate the classes. To do this, you need to run the protocol buffer compiler protoc on your .proto:
#### $ python -m grpc_tools.protoc -I../../protos --python_out=. --grpc_python_out=. ../../protos/helloworld.proto
This generates python file in your specified destination directory.
