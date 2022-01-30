load("@rules_proto//proto:defs.bzl", "proto_library")
load("@rules_cc//cc:defs.bzl", "cc_proto_library")
load("@rules_java//java:defs.bzl", "java_proto_library")
load("@com_google_protobuf//:protobuf.bzl", "py_proto_library")
load("@rules_java//java:defs.bzl", "java_library")
load("@rules_cc//cc:defs.bzl", "cc_library")

package(default_visibility = ["//visibility:public"])

filegroup(
    name = "proto-srcs",
    srcs = glob(["**/*.proto"]),
)

# Configuring Protocol Buffer libraries.
proto_library(
    name = "proto_common",
    srcs = ["common.proto"],
)

proto_library(
    name = "proto_execution_state",
    srcs = ["execution_state.proto"],
)

proto_library(
    name = "proto_networktests",
    srcs = ["networktests.proto"],
)

proto_library(
    name = "proto_stats",
    srcs = ["stats.proto"],
)

proto_library(
    name = "proto_topology",
    srcs = ["topology.proto"],
)

proto_library(
    name = "proto_scheduler",
    srcs = ["scheduler.proto"],
    import_prefix = "~/Heron-Protobuf/src/",
    deps = [
        ":proto_common",
        ":proto_packing_plan",
    ],
)

proto_library(
    name = "proto_physical_plan",
    srcs = ["physical_plan.proto"],
    deps = [":proto_topology"],
)

proto_library(
    name = "proto_packing_plan",
    srcs = ["packing_plan.proto"],
)

proto_library(
    name = "proto_tuple",
    srcs = ["tuple.proto"],
    deps = [":proto_topology"],
)

proto_library(
    name = "proto_tmanager",
    srcs = ["tmanager.proto"],
    deps = [
        ":proto_ckptmgr",
        ":proto_common",
        ":proto_physical_plan",
        ":proto_stats",
        ":proto_topology",
    ],
)

proto_library(
    name = "proto_metrics",
    srcs = ["metrics.proto"],
    deps = [
        ":proto_common",
        ":proto_tmanager",
    ],
)

proto_library(
    name = "proto_stmgr",
    srcs = ["stmgr.proto"],
    deps = [
        ":proto_common",
        ":proto_packing_plan",
        ":proto_physical_plan",
        ":proto_stats",
        ":proto_topology",
        ":proto_tuple",
    ],
)

proto_library(
    name = "proto_ckptmgr",
    srcs = ["ckptmgr.proto"],
    deps = [
        ":proto_common",
        ":proto_physical_plan",
    ],
)

# Generate Protocol Libraries for Java, C++, and Python.
java_proto_library(
    name = "proto-java",
    deps = [
        ":proto_networktests",
        ":proto_execution_state",
        ":proto_common",
        ":proto_packing_plan",
        ":proto_stats",
        ":proto_topology",
        ":proto_ckptmgr",
        ":proto_metrics",
        ":proto_physical_plan",
        ":proto_scheduler",
        ":proto_stmgr",
        ":proto_tmanager",
        ":proto_tuple",
    ],
)

cc_proto_library(
    name = "proto-cxx",
    deps = [
        ":proto_networktests",
        ":proto_execution_state",
        ":proto_common",
        ":proto_packing_plan",
        ":proto_stats",
        ":proto_topology",
        ":proto_ckptmgr",
        ":proto_metrics",
        ":proto_physical_plan",
        ":proto_scheduler",
        ":proto_stmgr",
        ":proto_tmanager",
        ":proto_tuple",
    ],
)

py_proto_library(
    name = "proto-py",
    deps = [
        ":proto_networktests",
        ":proto_execution_state",
        ":proto_common",
        ":proto_packing_plan",
        ":proto_stats",
        ":proto_topology",
        ":proto_ckptmgr",
        ":proto_metrics",
        ":proto_physical_plan",
        ":proto_scheduler",
        ":proto_stmgr",
        ":proto_tmanager",
        ":proto_tuple",
    ],
)

filegroup(
    name = "srcs",
    srcs = glob(["**"]),
)
