# remote-cache-bench

Open benchmark of remote build caches for Bazel.

Workload: abseil-cpp 20250814.1, 194 cc_library targets (~520 compile actions), Bazel 9.

Per provider: cold build that fills the remote cache, then `bazel clean --expunge` and two warm builds that read only from the remote cache (full download and `--remote_download_minimal`). Metrics: wall time, remote cache hit count, errors.

Providers: BuildFetch, BuildBuddy, Depot, Blacksmith, local baseline.
