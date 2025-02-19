# Copyright (c) 2009-2021, Google LLC
# All rights reserved.
#
# Use of this source code is governed by a BSD-style
# license that can be found in the LICENSE file or at
# https://developers.google.com/open-source/licenses/bsd

load(
    "//upb/bazel:build_defs.bzl",
    "UPB_DEFAULT_CPPOPTS",
)

package(default_applicable_licenses = ["//:license"])

licenses(["notice"])

cc_binary(
    name = "protoc-gen-upb-protos",
    srcs = [
        "protoc-gen-upb-protos.cc",
    ],
    copts = UPB_DEFAULT_CPPOPTS,
    visibility = ["//visibility:public"],
    deps = [
        ":gen_utils",
        ":generator",
        ":names",
        ":output",
        "//:protobuf",
        "//src/google/protobuf",
        "//src/google/protobuf/compiler:code_generator",
        "//src/google/protobuf/compiler:plugin",
        "//upb_generator:file_layout",
    ],
)

cc_library(
    name = "generator",
    srcs = [
        "gen_accessors.cc",
        "gen_enums.cc",
        "gen_extensions.cc",
        "gen_messages.cc",
        "gen_repeated_fields.cc",
    ],
    hdrs = [
        "gen_accessors.h",
        "gen_enums.h",
        "gen_extensions.h",
        "gen_messages.h",
        "gen_repeated_fields.h",
    ],
    visibility = ["//visibility:private"],
    deps = [
        ":gen_utils",
        ":keywords",
        ":names",
        ":output",
        "//:protobuf",
        "//src/google/protobuf",
        "//upb_generator:common",
        "//upb_generator:file_layout",
        "//upb_generator/c:names",
        "//upb_generator/minitable:names",
        "@com_google_absl//absl/container:flat_hash_set",
        "@com_google_absl//absl/strings",
    ],
)

cc_library(
    name = "keywords",
    srcs = ["keywords.cc"],
    hdrs = ["keywords.h"],
    visibility = ["//visibility:private"],
    deps = [
        "@com_google_absl//absl/container:flat_hash_set",
        "@com_google_absl//absl/strings",
    ],
)

cc_library(
    name = "output",
    srcs = ["output.cc"],
    hdrs = ["output.h"],
    visibility = ["//visibility:private"],
    deps = [
        "//:protobuf",
        "//src/google/protobuf/io",
        "//upb_generator/c:names",
        "//upb_generator/minitable:names",
        "@com_google_absl//absl/log:absl_log",
        "@com_google_absl//absl/strings",
    ],
)

cc_library(
    name = "gen_utils",
    srcs = ["gen_utils.cc"],
    hdrs = ["gen_utils.h"],
    visibility = ["//visibility:public"],
    deps = [
        "//:protobuf",
        "//src/google/protobuf",
        "//src/google/protobuf/compiler:code_generator",
        "@com_google_absl//absl/strings",
    ],
)

cc_library(
    name = "names",
    srcs = ["names.cc"],
    hdrs = ["names.h"],
    visibility = ["//visibility:private"],
    deps = [
        ":keywords",
        ":output",
        "//src/google/protobuf",
        "//src/google/protobuf/compiler:code_generator",
        "@com_google_absl//absl/strings:string_view",
    ],
)
