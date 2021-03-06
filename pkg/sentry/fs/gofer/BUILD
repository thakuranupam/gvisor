package(licenses = ["notice"])  # Apache 2.0

load("@io_bazel_rules_go//go:def.bzl", "go_library", "go_test")
load("//tools/go_stateify:defs.bzl", "go_stateify")

go_stateify(
    name = "gofer_state",
    srcs = [
        "file.go",
        "file_state.go",
        "fs.go",
        "inode.go",
        "inode_state.go",
        "session.go",
        "session_state.go",
    ],
    out = "gofer_state.go",
    package = "gofer",
)

go_library(
    name = "gofer",
    srcs = [
        "attr.go",
        "cache_policy.go",
        "context_file.go",
        "device.go",
        "file.go",
        "file_state.go",
        "fs.go",
        "gofer_state.go",
        "handles.go",
        "inode.go",
        "inode_state.go",
        "path.go",
        "session.go",
        "session_state.go",
        "socket.go",
        "util.go",
    ],
    importpath = "gvisor.googlesource.com/gvisor/pkg/sentry/fs/gofer",
    visibility = ["//pkg/sentry:internal"],
    deps = [
        "//pkg/abi/linux",
        "//pkg/amutex",
        "//pkg/fd",
        "//pkg/log",
        "//pkg/metric",
        "//pkg/p9",
        "//pkg/refs",
        "//pkg/secio",
        "//pkg/sentry/context",
        "//pkg/sentry/device",
        "//pkg/sentry/fs",
        "//pkg/sentry/fs/fdpipe",
        "//pkg/sentry/fs/fsutil",
        "//pkg/sentry/fs/host",
        "//pkg/sentry/fs/lock",
        "//pkg/sentry/kernel/auth",
        "//pkg/sentry/kernel/time",
        "//pkg/sentry/memmap",
        "//pkg/sentry/platform",
        "//pkg/sentry/safemem",
        "//pkg/sentry/uniqueid",
        "//pkg/sentry/usermem",
        "//pkg/state",
        "//pkg/syserror",
        "//pkg/tcpip",
        "//pkg/tcpip/transport/unix",
        "//pkg/unet",
        "//pkg/waiter",
    ],
)

go_test(
    name = "gofer_test",
    size = "small",
    srcs = ["gofer_test.go"],
    embed = [":gofer"],
    deps = [
        "//pkg/log",
        "//pkg/p9",
        "//pkg/p9/p9test",
        "//pkg/sentry/context",
        "//pkg/sentry/context/contexttest",
        "//pkg/sentry/fs",
        "//pkg/sentry/kernel/time",
        "//pkg/sentry/usermem",
        "//pkg/unet",
    ],
)
