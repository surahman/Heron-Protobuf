# _**Heron Protocol Buffers Migration to Native Bazel Rules**_

 We need to generate the [Python protobuf](https://thethoughtfulkoala.com/posts/2020/05/08/py-protobuf-bazel.html) and use Bazel's native [rules](https://docs.bazel.build/versions/main/be/overview.html#rules) for [Java and CC](https://github.com/bazelbuild/rules_proto). Java and CC examples are [here](https://blog.bazel.build/2017/02/27/protocol-buffers.html).

Working on assembling the Protobuf in isolation on this repository for [PR #3768](https://github.com/apache/incubator-heron/pull/3768).

![Heron Protocol Buffer Diagram](protobuf_diagram.png "Apache Heron Protocol Buffer")

<br>

### **_Automated BUILD file generation using Gazelle_**

Protocol Buffer `BUILD` files are located in the [`proto/`](proto/) directory.

To generate/update the `BUILD` files run `bazel run //:gazelle -- proto` from the repository root directory.

<br>

### Directory Tree

```bash
├── proto
│   ├── api
│   │   ├── BUILD.bazel
│   │   └── topology.proto
│   ├── ckptmgr
│   │   ├── BUILD.bazel
│   │   └── ckptmgr.proto
│   ├── scheduler
│   │   ├── BUILD.bazel
│   │   └── scheduler.proto
│   ├── stmgr
│   │   ├── BUILD.bazel
│   │   └── stmgr.proto
│   ├── system
│   │   ├── BUILD.bazel
│   │   ├── common.proto
│   │   ├── execution_state.proto
│   │   ├── metrics.proto
│   │   ├── packing_plan.proto
│   │   ├── physical_plan.proto
│   │   ├── stats.proto
│   │   └── tuple.proto
│   ├── testing
│   │   ├── BUILD.bazel
│   │   └── networktests.proto
│   └── tmanager
│       ├── BUILD.bazel
│       └── tmanager.proto
```