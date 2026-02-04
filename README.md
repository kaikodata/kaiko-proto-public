# Kaiko Public Protocol Buffers

This repository contains the public Protocol Buffer definitions for Kaiko's gRPC APIs.

## Available Services

### Equities Service (`kaiko.equities`)

Real-time and historical streaming access to index equities data.

- `StreamIndex` - Real-time stream of index updates
- `ReplayIndex` - Historical replay of index data within a time range

## Generating Client Code

Use `protoc` to generate client code for your language. For detailed instructions, see the [Protocol Buffers Reference](https://protobuf.dev/reference/).

### Prerequisites

1. Install the [Protocol Buffer Compiler (protoc)](https://protobuf.dev/downloads/)
2. Install the language-specific plugin for your target language

### Go

```bash
# Install plugins
go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest

# Generate
protoc --go_out=gen/go --go_opt=paths=source_relative \
       --go-grpc_out=gen/go --go-grpc_opt=paths=source_relative \
       -I proto proto/kaiko/equities/equities.proto
```

See: [Go Generated Code Guide](https://protobuf.dev/reference/go/go-generated/)

### Python

```bash
# Install
pip install grpcio grpcio-tools

# Generate
python -m grpc_tools.protoc -I proto \
       --python_out=gen/python \
       --grpc_python_out=gen/python \
       proto/kaiko/equities/equities.proto
```

See: [Python Generated Code Guide](https://protobuf.dev/reference/python/python-generated/)

### Java

```bash
protoc --java_out=gen/java \
       --plugin=protoc-gen-grpc-java=/path/to/protoc-gen-grpc-java \
       --grpc-java_out=gen/java \
       -I proto proto/kaiko/equities/equities.proto
```

See: [Java Generated Code Guide](https://protobuf.dev/reference/java/java-generated/)

### C#

```bash
protoc --csharp_out=gen/csharp \
       --grpc_out=gen/csharp \
       --plugin=protoc-gen-grpc=/path/to/grpc_csharp_plugin \
       -I proto proto/kaiko/equities/equities.proto
```

See: [C# Generated Code Guide](https://protobuf.dev/reference/csharp/csharp-generated/)

### Other Languages

For C++, Ruby, PHP, Kotlin, Dart, and other languages, refer to the [Protocol Buffers Reference](https://protobuf.dev/reference/).

## Alternative: Using Buf

For a simpler workflow, you can use the [Buf CLI](https://buf.build/docs/installation):

```bash
# Default (Go)
buf generate

# Other languages - use --template flag
buf generate --template buf/buf.gen.python.yaml
buf generate --template buf/buf.gen.java.yaml
buf generate --template buf/buf.gen.csharp.yaml
buf generate --template buf/buf.gen.typescript.yaml
buf generate --template buf/buf.gen.ruby.yaml
buf generate --template buf/buf.gen.php.yaml
```

Generated code will be in `gen/<language>/`.

## Support

- Documentation: https://docs.kaiko.com
- Email: support@kaiko.com

## License

Copyright (c) Kaiko. All rights reserved.
