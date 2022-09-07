load("//swift:swift.bzl", "swift_c_module", "swift_library")
load("//test/fixtures:common.bzl", "FIXTURE_TAGS")

package(
    default_visibility = ["//test:__subpackages__"],
)

licenses(["notice"])

###############################################################################
# Fixtures for testing explicit clang module compilation.

config_setting(
    name = "linux",
    constraint_values = [
        "@platforms//os:linux",
    ],
)

swift_library(
    name = "simple",
    srcs = ["Empty.swift"],
    tags = FIXTURE_TAGS,
    deps = [":shims"],
)

swift_c_module(
    name = "shims",
    module_name = "SwiftShims",
    system_module_map = select({
        ":linux": "$SWIFT_HOME/usr/lib/swift/shims/module.modulemap",
        "//conditions:default": "__BAZEL_XCODE_SDKROOT__/usr/lib/swift/shims/module.modulemap",
    }),
    tags = FIXTURE_TAGS,
)
