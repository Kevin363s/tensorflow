# Description:
#   Run sample models with TensorRT through TF-TRT bridge. Test TensorRT
#   numerics and latency.

package(
    default_visibility = ["//visibility:public"],
    licenses = ["notice"],  # Apache 2.0
)

exports_files(glob([
    "models/*",
]))

py_library(
    name = "model_handler",
    srcs = ["model_handler.py"],
    srcs_version = "PY3",
    deps = [
        "//tensorflow/core:protos_all_py",
        "//tensorflow/python:dtypes",
        "//tensorflow/python:framework",
        "//tensorflow/python:framework_ops",
        "//tensorflow/python:random_ops",
        "//tensorflow/python:session",
        "//tensorflow/python/compiler/tensorrt:trt_convert_py",
        "//tensorflow/python/saved_model:loader",
        "//tensorflow/python/saved_model:signature_constants",
        "//tensorflow/python/saved_model:tag_constants",
        "//third_party/py/attr",
        "//third_party/py/numpy",
        "@absl_py//absl/logging",
    ],
)

py_binary(
    name = "run_models",
    srcs = ["run_models.py"],
    data = ["sample_model/saved_model.pb"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [
        ":model_handler",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_ops",
        "//tensorflow/python/compiler/tensorrt:trt_convert_py",
        "@absl_py//absl:app",
        "@absl_py//absl/logging",
    ],
)
