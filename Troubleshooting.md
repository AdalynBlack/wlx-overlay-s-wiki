## Check logs

Wlx-S will often show troubleshooting tips in the logs, so it's good to always check them first.

By default, Wlx-S logs into `/tmp/wlx.log`.

You may also change where to log to, there are 2 methods:
- Pass the argument `--log-to=/path/to/wlx.log`
- Set the env var `WLX_LOGFILE=/path/to/wlx.log`

Argument takes precedence over env var.

Setting either to `""` will disable logging to file.

## Troubleshooting segmentation faults (SIGSEGV)

Run Wlx-S in `rust-gdb` (or even regular `gdb`) to get more info about the segfault.

Attach this with the other logs that you have.

```
rust-gdb -ex run target/debug/wlx-overlay-s
```