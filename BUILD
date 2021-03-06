# Copyright 2017-present The Material Motion Authors. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
# Description:
# Motion interchange format.

load("@bazel_ios_warnings//:strict_warnings_objc_library.bzl", "strict_warnings_objc_library")
load("@build_bazel_rules_apple//apple:swift.bzl", "swift_library")
load("@build_bazel_rules_apple//apple:ios.bzl", "ios_unit_test")

licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

strict_warnings_objc_library(
    name = "MotionInterchange",
    srcs = glob([
        "src/*.m",
        "src/private/*.m",
    ]),
    hdrs = glob([
        "src/*.h",
        "src/private/*.h",
    ]),
    sdk_frameworks = [
        "CoreGraphics",
        "Foundation",
        "QuartzCore",
        "UIKit",
    ],
    enable_modules = 1,
    includes = ["src"],
    visibility = ["//visibility:public"],
)

swift_library(
    name = "UnitTestsSwiftLib",
    srcs = glob([
        "tests/unit/*.swift",
    ]),
    deps = [":MotionInterchange"],
    visibility = ["//visibility:private"],
)

objc_library(
    name = "UnitTestsLib",
    srcs = glob([
        "tests/unit/*.m",
    ]),
    deps = [":MotionInterchange"],
    visibility = ["//visibility:private"],
)

ios_unit_test(
    name = "UnitTests",
    deps = [
      ":UnitTestsLib",
      ":UnitTestsSwiftLib"
    ],
    minimum_os_version = "8.0",
    timeout = "short",
    visibility = ["//visibility:private"],
)
