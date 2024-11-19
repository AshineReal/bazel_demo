load("@build_bazel_rules_apple//apple:ios.bzl", "ios_application")
load("@build_bazel_rules_swift//swift:swift.bzl", "swift_library")
load("@rules_xcodeproj//xcodeproj:defs.bzl", "top_level_target", "xcodeproj")

swift_library(
    name = "MyLibrary",
    srcs = glob(["App/**/*.swift"]),
    deps = [
        "//libsignal:LibSignalClient",
        # "//ObjcModule:ObjcModule",
    ],
    visibility = ["//visibility:public"],
)


ios_application(
    name = "App",
    bundle_id = "com.example.app",
    families = [
        "iphone",
        "ipad",
    ],
    infoplists = [":Info.plist"],
    minimum_os_version = "15.0",
    deps = [":MyLibrary"],
    visibility = ["//visibility:public"],
)


xcodeproj(
    name = "xcodeproj",
    project_name = "App",
    tags = ["manual"],
    top_level_targets = [
        top_level_target(":App", target_environments = ["simulator"]),
    ],
)
