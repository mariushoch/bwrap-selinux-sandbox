## bwrap-selinux-sandbox

For using the SELinux sandbox types (`sandbox_*_t`) with [`bwrap`](https://github.com/containers/bubblewrap) (instead of having to use the very limited suid [`seunshare`](http://man7.org/linux/man-pages/man8/seunshare.8.html)). This is a very lightweight, yet powerful, sandboxing mechanism (without suid binaries).  
`bwrap-sandbox` is SELinux's [`sandbox`](http://man7.org/linux/man-pages/man8/sandbox.8.html) modified to use `bwrap` (with the SELinux module described below), instead of `seunshare`.

### Example

This make things possible like:  

`$ bwrap --dev-bind / / --bind /etc/hostname /etc/passwd ./bwrap-sandbox -t sandbox_min_t sh -i`  

`/etc/passwd` now contains the hostname (due to the bwrap bind).  

`sh-5.0$ cat /etc/passwd  `  
`marius-latitude`

`/mnt/` can't be accessed, per the SELinux restrictions on `sandbox_min_t`.

`sh-5.0$ ls /mnt/`  
`ls: cannot open directory '/mnt/': Permission denied`  

## Usage

### Setup

Run `semodule -i ./bwrap-selinux-sandbox/bwrap-selinux-sandbox.pp` as root.  
The module can be removed using `semodule -r bwrap-selinux-sandbox`.

### Usage
`bwrap-sandbox` can be used as a drop-in replacement for SELinux's [`sandbox`](http://man7.org/linux/man-pages/man8/sandbox.8.html).


## Build
Use `make` in `bwrap-selinux-sandbox/` to build the SELinux module.
