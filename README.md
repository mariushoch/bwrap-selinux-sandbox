## bwrap-selinux-sandbox

For using the SELinux sandbox types (`sandbox_*_t`) with [`bwrap`](https://github.com/containers/bubblewrap) (instead of having to use the very limited `seunshare`).

## Use

Run `semodule -i bwrap-selinux-sandbox.pp` as root.  
The module can be removed using `semodule -r bwrap-selinux-sandbox`.

## Build
Use `make` to build the module.
