load("@build_bazel_rules_swift//swift:swift.bzl", "swift_library")

objc_import(
    name = "libsignal_ffi_lib",
    archives = ["@libsignal//:libsignal_ffi"],
)

objc_library(
    name = "SignalFfi",
    module_name = "SignalFfi",
    enable_modules = True,
    hdrs = glob(["SignalFfi/*.h"]),
    deps = [":libsignal_ffi_lib"],
)

swift_library(
    name = "LibSignalClient",
    module_name = "LibSignalClient",
    srcs = glob(["LibSignalClient/**/*.swift"]),
    deps = [":SignalFfi"],
    visibility = ["//visibility:public"],
)


