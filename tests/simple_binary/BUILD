# Copyright 2023 The Bazel Authors. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load("//cc:cc_binary.bzl", "cc_binary")

licenses(["notice"])

cc_binary(
    name = "foo",
    srcs = ["foo.cc"],
)

cc_binary(
    name = "libfoo.so",
    srcs = ["foo.cc"],
    linkshared = 1,
)

# Regression test for building C code
# https://github.com/bazelbuild/rules_cc/pull/440#issuecomment-3075519628
cc_binary(
    name = "bar",
    srcs = ["bar.c"],
    copts = select({
        "@platforms//os:windows": ["/std:c11"],
        "//conditions:default": [],
    }),
)
