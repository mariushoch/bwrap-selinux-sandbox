## bwrap-selinux-sandbox

For using the SELinux sandbox types (`sandbox_*_t`) with [`bwrap`](https://github.com/containers/bubblewrap) (instead of having to use the very limited `seunshare`). This is a very lightweight, yet very powerful, sandboxing mechanism (without suid binaries).

### Example

This make things possible like:  

`$ bwrap --dev-bind / / --bind /etc/hostname /etc/passwd ./bwrap-sandbox -t sandbox_min_t sh -i`  

`/etc/passwd` not contains the hostname (per the bwrap bind).  

`sh-5.0$ cat /etc/passwd  `  
`marius-latitude`

`/mnt/` can't be accessed, per the SELinux restrictions on `sandbox_min_t`.

`sh-5.0$ ls /mnt/`  
`ls: cannot open directory '/mnt/': Permission denied`  

## Usage

### Setup

Run `semodule -i bwrap-selinux-sandbox.pp` as root.  
The module can be removed using `semodule -r bwrap-selinux-sandbox`.

### Usage
`bwrap-sandbox` can be used as a drop-in replacement to SELinux's `sandbox`.


## Build
Use `make` to build the SELinux module.
