workspace(name = "build_stack_rules_proto")

# gazelle:repo bazel_gazelle

# ----------------------------------------------------
# Toolchain-Related
# ----------------------------------------------------

register_toolchains("//toolchain:standard")

# ----------------------------------------------------
# Top-Level Dependency Trees
# ----------------------------------------------------

load("//deps:core_deps.bzl", "core_deps")

core_deps()

load("//deps:protobuf_core_deps.bzl", "protobuf_core_deps")

protobuf_core_deps()

load("//deps:prebuilt_protoc_deps.bzl", "prebuilt_protoc_deps")

prebuilt_protoc_deps()

load("//deps:grpc_core_deps.bzl", "grpc_core_deps")

grpc_core_deps()

load("//deps:grpc_java_deps.bzl", "grpc_java_deps")

grpc_java_deps()


# ----------------------------------------------------
# Go Tools
# ----------------------------------------------------

load(
    "@io_bazel_rules_go//go:deps.bzl",
    "go_register_toolchains",
    "go_rules_dependencies",
)

go_rules_dependencies()

go_register_toolchains(version = "1.16.2")

# ----------------------------------------------------
# Gazelle
# ----------------------------------------------------

load("@bazel_gazelle//:deps.bzl", "gazelle_dependencies")

gazelle_dependencies()

load("//:go_deps.bzl", "go_deps")

# gazelle:repository_macro go_deps.bzl%go_deps
go_deps()

# ----------------------------------------------------
# Core gRPC
# ----------------------------------------------------

load(
    "@com_github_grpc_grpc//bazel:grpc_deps.bzl",
    "grpc_deps",
)

grpc_deps()

# ----------------------------------------------------
# Java
# ----------------------------------------------------

load(
    "@rules_jvm_external//:defs.bzl",
    "maven_install",
)
load(
    "@io_grpc_grpc_java//:repositories.bzl",
    "IO_GRPC_GRPC_JAVA_ARTIFACTS",
    "IO_GRPC_GRPC_JAVA_OVERRIDE_TARGETS",
    "grpc_java_repositories",
)

maven_install(
    artifacts = IO_GRPC_GRPC_JAVA_ARTIFACTS,
    generate_compat_repositories = True,
    override_targets = IO_GRPC_GRPC_JAVA_OVERRIDE_TARGETS,
    repositories = [
        "https://repo.maven.apache.org/maven2/",
    ],
)

load(
    "@maven//:compat.bzl",
    "compat_repositories",
)

compat_repositories()

grpc_java_repositories()

# ----------------------------------------------------
# Golang
# ----------------------------------------------------

load("//deps:go_core_deps.bzl", "go_core_deps")

go_core_deps()
