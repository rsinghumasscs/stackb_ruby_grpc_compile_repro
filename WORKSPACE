load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

http_archive(
    name = "build_stack_rules_proto",
    sha256 = "7f7fc55f1cfe8b28f95f1feb8ea42f21310cbbf3c1ee5015dfc15c604f6593f1",
    strip_prefix = "rules_proto-78d64b7317a332ee884ad7fcd0506d78f2a402cb",
    urls = ["https://github.com/stackb/rules_proto/archive/78d64b7317a332ee884ad7fcd0506d78f2a402cb.tar.gz"],
)

http_archive(
    name = "io_grpc_grpc_java",
    sha256 = "d1e4323520a151f4768a3b22a5caf4b622d10a5a17710077e32275c5163a870f",
    strip_prefix = "grpc-java-1.22.0",
    urls = ["https://github.com/grpc/grpc-java/archive/v1.22.0.tar.gz"],
)

load("@build_stack_rules_proto//ruby:deps.bzl", "ruby_grpc_compile", "ruby_grpc_library", "ruby_proto_compile", "ruby_proto_library")

ruby_proto_library()

ruby_proto_compile()

ruby_grpc_compile()

ruby_grpc_library()

load("@com_github_grpc_grpc//bazel:grpc_deps.bzl", "grpc_deps")

grpc_deps()

load("@com_github_yugui_rules_ruby//ruby:def.bzl", "ruby_register_toolchains")

ruby_register_toolchains()

load("@com_github_yugui_rules_ruby//ruby/private:bundle.bzl", "bundle_install")

bundle_install(
    name = "test_gems_bundle",
    gemfile = "//ruby:Gemfile",
    gemfile_lock = "//ruby:Gemfile.lock",
)
