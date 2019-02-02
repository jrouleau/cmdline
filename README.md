# cmdline

A simple tool to generate a kernel cmdline string from `/etc/cmdline` and `/etc/cmdline.d/`.

## Requirements

* Requires `bash`, `cat`, `realpath`, and `sed`

## Installation

### Arch Linux

* Install AUR package from https://aur.archlinux.org/packages/cmdline/

### From source

* Run `make install` as root

## Usage

`gencmdline` reads `/etc/cmdline` first and then any files in `/etc/cmdline.d/` removing any comments or empty lines and outputs a single space concatenated string.

Optionally reads from an alternate root directory with `gencmdline <dir>`

Comments must start with `#`

Example:
```sh
# /etc/cmdline.d/zswap

# Activate and configure zswap
zswap.enabled=1
zswap.compressor=lz4
zswap.max_pool_percent=20
zswap.zpool=z3fold
```

Output
```sh
$ gencmdline
... zswap.enabled=1 zswap.compressor=lz4 zswap.max_pool_percent=20 zswap.zpool=z3fold ...
```

## License

MIT License

Copyright (c) 2019 Jonathan Rouleau
