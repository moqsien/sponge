## English | [简体中文](assets/readme-cn.md)

<p align="center">
<img width="500px" src="https://raw.githubusercontent.com/zhufuyi/sponge/main/assets/logo.png">
</p>

<div align=center>

[![Go Report](https://goreportcard.com/badge/github.com/zhufuyi/sponge)](https://goreportcard.com/report/github.com/zhufuyi/sponge)
[![codecov](https://codecov.io/gh/zhufuyi/sponge/branch/main/graph/badge.svg)](https://codecov.io/gh/zhufuyi/sponge)
[![Go Reference](https://pkg.go.dev/badge/github.com/zhufuyi/sponge.svg)](https://pkg.go.dev/github.com/zhufuyi/sponge)
[![Go](https://github.com/zhufuyi/sponge/workflows/Go/badge.svg?branch=main)](https://github.com/zhufuyi/sponge/actions)
[![License: MIT](https://img.shields.io/github/license/zhufuyi/sponge)](https://img.shields.io/github/license/zhufuyi/sponge)

</div>

[Sponge](https://github.com/zhufuyi/sponge) is a powerful golang productivity tool that integrates `automatic code generation`, `web and microservices frameworks`, `basic development framework`. sponge has a wealth of generating code commands, generating different functional code can be combined into a complete service (similar to the way that artificially broken sponge cells can automatically recombine into a new sponge). The code is decoupled and modularly designed, it is easy to build a complete project from development to deployment, so that you develop web or microservices project easily, golang can also be "low-code development".

<br>

If you are developing a RESTful web or microservice with a simple CRUD API interface, you don't need to write a single line of golang code to compile and deploy to servers, dockers, k8s, and the complete service code is generated by sponge.

If you develop a generic RESTful web or microservice, you need to manually write code in addition to defining the data table, defining the api interface in the proto file, and filling in the specific business logic code in the generated template file. Other golang codes are generated by sponge.

<br>

### sponge generates the code framework

sponge is mainly based on **SQL** and **Protobuf** two ways to generate code, each way has to generate code for different functions.

**Generate code framework:**

<p align="center">
<img width="1500px" src="https://raw.githubusercontent.com/zhufuyi/sponge/main/assets/sponge-framework.png">
</p>

<br>

**Generate code framework corresponding UI interface:**

<p align="center">
<img width="1200px" src="https://raw.githubusercontent.com/zhufuyi/sponge/main/assets/en_sponge-ui.png">
</p>

<br>

### Services framework

sponge generated microservice code framework is shown in the figure below, which is a typical microservice hierarchical structure, with high performance, high scalability, contains commonly used service governance features, you can easily replace or add their own service governance features.

<p align="center">
<img width="1000px" src="https://raw.githubusercontent.com/zhufuyi/sponge/main/assets/microservices-framework.png">
</p>

<br>

### Egg model of a web service code generated by sponge

The sponge separates the two major parts of code during the process of generating web service code. It isolates the business logic from the non-business logic. For example, consider the entire web service code as an egg. The eggshell represents the web service framework code, while both the albumen and yolk represent the business logic code. The yolk is the core of the business logic (manually written code). It includes defining MySQL tables, defining API interfaces, and writing specific logic code.On the other hand, the albumen acts as a bridge connecting the core business logic code to the web framework code (automatically generated, no manual writing needed). This includes the registration of route code generated from proto files, handler method function code, parameter validation code, error codes, Swagger documentation, and more.

Egg model profiling diagram for `⓷Web services created based on protobuf`:

<p align="center">
<img width="1200px" src="https://raw.githubusercontent.com/zhufuyi/sponge_examples/main/assets/en_web-http-pb-anatomy.png">
</p>

This is the egg model for web service code, and there are egg models for microservice (grpc) code, and grpc gateway service code described in [sponge documentation](https://go-sponge.com/learn-about-sponge?id=%f0%9f%8f%b7project-code-egg-model).

<br>

### Key Features

- User-friendly UI for code generation commands.
- Automatic merging of template code for "low-code development" of API interfaces.
- Modular and decoupled code design with rich functional components readily available, you can also easily use their own components.
- Web framework [gin](https://github.com/gin-gonic/gin)
- RPC framework [grpc](https://github.com/grpc/grpc-go)
- Configuration parsing [viper](https://github.com/spf13/viper)
- Configuration center [nacos](https://github.com/alibaba/nacos)
- Logging component [zap](https://github.com/uber-go/zap)
- Database ORM component [gorm](https://github.com/go-gorm/gorm)
- Cache component [go-redis](https://github.com/go-redis/redis), [ristretto](https://github.com/dgraph-io/ristretto)
- Automated API documentation [swagger](https://github.com/swaggo/swag), [protoc-gen-openapiv2](https://github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-openapiv2)
- Authentication [jwt](https://github.com/golang-jwt/jwt)
- Message Queue [rabbitmq](https://github.com/rabbitmq/amqp091-go)
- Distributed Transaction Manager [dtm](https://github.com/dtm-labs/dtm)
- Parameter validation [validator](https://github.com/go-playground/validator)
- Adaptive rate limiting [ratelimit](https://github.com/zhufuyi/sponge/tree/main/pkg/shield/ratelimit)
- Adaptive circuit breaking [circuitbreaker](https://github.com/zhufuyi/sponge/tree/main/pkg/shield/circuitbreaker)
- Distributed Tracing [opentelemetry](https://github.com/open-telemetry/opentelemetry-go)
- Metrics monitoring [prometheus](https://github.com/prometheus/client_golang/prometheus), [grafana](https://github.com/grafana/grafana)
- Service registration and discovery [etcd](https://github.com/etcd-io/etcd), [consul](https://github.com/hashicorp/consul), [nacos](https://github.com/alibaba/nacos)
- Adaptive collecting [profile](https://go.dev/blog/pprof)
- Resource statistics [gopsutil](https://github.com/shirou/gopsutil)
- Code quality checking [golangci-lint](https://github.com/golangci/golangci-lint)
- Continuous integration and deployment [jenkins](https://github.com/jenkinsci/jenkins), [docker](https://www.docker.com/), [kubernetes](https://github.com/kubernetes/kubernetes)

<br>

### Project Code Directory Structure

The project code directory structure created by sponge follows the [project-layout](https://github.com/golang-standards/project-layout) convention and is structured as follows:

```bash
.
├── api            # Directory for exposing external API interfaces, typically containing proto files and generated *.pb.go files. The directory structure is typically in the form `api/xxx/v1`, where v1 indicates the version.
├── assets         # Store various static resources, such as images, markdown files, etc.
├── cmd            # Program entry directory
│    └── serviceName
│         ├── initial     # Program initialization, consisting of three files: initApp initializes configurations, registerServers registers services (HTTP or grpc), and registerClose registers resource cleanup.
│         └── main.go     # Program entry file
├── configs        # Directory for configuration files
├── deployments    # Directory for deployment scripts, supporting binary, Docker, and Kubernetes deployments.
├─ docs            # Directory for API interface Swagger documentation.
├── internal       # Directory for code of private applications and libraries.
│    ├── cache        # Cache directory wrapped around business logic.
│    ├── config       # Directory for Go structure configuration files.
│    ├── dao          # Data access directory, e.g., interfaces for CRUD operations on MySQL tables.
│    ├── ecode        # Directory for system error codes and custom business error codes.
│    ├── handler      # Directory for implementing HTTP business functionality (specific to web services).
│    ├── model        # Database model directory.
│    ├── routers      # HTTP routing directory.
│    ├── rpcclient    # Directory for client-side code that connects to grpc services.
│    ├── server       # Directory for creating services, including HTTP and grpc.
│    ├── service      # Directory for implementing grpc business functionality (specific to microservices).
│    └── types        # Directory for defining request and response parameter structures for HTTP.
├── pkg            # Directory for shared libraries.
├── scripts        # Directory for scripts, including compilation, execution, code generation, and deployment scripts.
├── test           # Directory for scripts required for testing services, such as scripts to start dependencies (e.g., MySQL, Redis) and test data (SQL).
└── third_party    # Directory for external helper programs, forked code, and other third-party tools.
```

<br>

### Quick start

#### Installation sponge

sponge can be installed on Windows, macOS, Linux and Docker environments. Click here for [instructions on installing sponge](https://github.com/zhufuyi/sponge/blob/main/assets/install-en.md).

#### Starting UI service

After installing the sponge, start the UI service:

```bash
sponge run
```

Access `http://localhost:24631` in a local browser and manipulate the generated code on the UI page.

> If you want to access it on a cross-host browser, you need to specify the host ip or domain name when starting the UI, example `sponge run -a http://your_host_ip:24631`. It is also possible to start the UI service on docker to support cross-host access, Click for instructions on [starting the sponge UI service in docker](https://github.com/zhufuyi/sponge/blob/main/assets/install-en.md#docker-environment).

<br>

### Sponge Development Documentation

Detailed instructions for operating, configuring, and deploying a project using sponge development, Click here to view the [sponge development documentation](https://go-sponge.com/)

<br>

### Examples of use

#### Simple examples

No specific business logic code is included.

- [1_web-gin-CRUD](https://github.com/zhufuyi/sponge_examples/tree/main/1_web-gin-CRUD)
- [2_micro-grpc-CRUD](https://github.com/zhufuyi/sponge_examples/tree/main/2_micro-grpc-CRUD)
- [3_web-gin-protobuf](https://github.com/zhufuyi/sponge_examples/tree/main/3_web-gin-protobuf)
- [4_micro-grpc-protobuf](https://github.com/zhufuyi/sponge_examples/tree/main/4_micro-grpc-protobuf)
- [5_micro-gin-rpc-gateway](https://github.com/zhufuyi/sponge_examples/tree/main/5_micro-gin-rpc-gateway)
- [6_micro-cluster-demo](https://github.com/zhufuyi/sponge_examples/tree/main/6_micro-cluster)

#### Complete project examples

- [7_community-single](https://github.com/zhufuyi/sponge_examples/tree/main/7_community-single)
- [8_community-cluster](https://github.com/zhufuyi/sponge_examples/tree/main/8_community-cluster)

#### Distributed transaction examples

- [9_order-system](https://github.com/zhufuyi/sponge_examples/tree/main/9_order-grpc-distributed-transaction)

<br>

### License

See the [LICENSE](LICENSE) file for licensing information.

<br>

### How to contribute

You are more than welcome to join us, raise an Issue or Pull Request.

Pull Request instructions.

1. Fork the code
2. Create your own branch: `git checkout -b feat/xxxx`
3. Commit your changes: `git commit -am 'feat: add xxxxx'`
4. Push your branch: `git push origin feat/xxxx`
5. Commit your pull request

<br>

**If it's help to you, give it a star ⭐.**

<br>
