# Projects

## [docker-machine-driver-xhyve](https://github.com/zchee/docker-machine-driver-xhyve)

docker-machine/minikube driver plugin for xhyve/hyperkit. (native macOS hypervisor.framework)

[nathanleclaire/docker-machine-xhyve#2](https://github.com/nathanleclaire/docker-machine-xhyve/issues/2)

## [nvim-go](https://github.com/zchee/nvim-go)

Go development plugin for Neovim written in pure Go.

## [clang-server](https://github.com/zchee/clang-server)

A C/C++ AST index server using libclang written in Go.

## [go-qcow2](https://github.com/zchee/go-qcow2)

Manage the QEMU qcow2 disk image written in Go.

## [go-mmal](https://github.com/zchee/go-mmal)

Raspberry Pi's libmmal bindings for Go.

## deoplete.nvim sources

- [deoplete-go](https://github.com/zchee/deoplete-go)
- [deoplete-jedi](https://github.com/zchee/deoplete-jedi)
- [deoplete-clang](https://github.com/zchee/deoplete-clang)

---

# Organizations

- [vim-jp](https://github.com/vim-jp)
- [fsnotify](https://github.com/fsnotify)

---

# Contributions

## [docker/machine](https://github.com/docker/machine)

- [Support --google-disk-type flag for google driver](https://github.com/docker/machine/issues/687)
  - First contribution: : 2015-03-02
- [docs: Update each drivers flag](https://github.com/docker/machine/issues/1167)
- [(closed) New Driver: xhyve](https://github.com/docker/machine/issues/1358)
  - Move to [docker-machine-driver-xhyve](#docker-machine-driver-xhyve)
- [etc...](https://github.com/docker/machine/pulls?q=is%3Apr+is%3Aclosed+author%3Azchee)

## [nsf/gocode](https://github.com/nsf/gocode)

- [package_bin: Fix callback arg to package path instead of alias name](https://github.com/nsf/gocode/issues/357)
- [package_bin: Add bimport v1. backport https://golang.org/cl/24648/](https://github.com/nsf/gocode/issues/360)
- [import: Support gb mode in candidates of package import](https://github.com/nsf/gocode/issues/365)
- [package_bin: Support go1.8 upstream](https://github.com/nsf/gocode/issues/372)
- [backport of golang.org/x/tools/9deed8c](https://github.com/nsf/gocode/issues/376)
- [package_bin: backport of golang.org/x/tools/6d7cee0](https://github.com/nsf/gocode/issues/402)
- [package_bin: support type alias](https://github.com/nsf/gocode/issues/417)
- [test/0019: add HuffmanOnly constants for zlib](https://github.com/nsf/gocode/issues/425)
- [typealias: add go1.8.typealias build tag for dev.typealias branch](https://github.com/nsf/gocode/issues/432)
- [declcache: support '-race' build when gb mode](https://github.com/nsf/gocode/issues/438)
- [decl/type_dealias: add handle the nil of decl](https://github.com/nsf/gocode/issues/439)
- [package_bin: backport interface embedding support](https://github.com/nsf/gocode/issues/441)
- [package_bin: improve efficiency of binary export position encoding](https://github.com/nsf/gocode/issues/451)

## [boot2docker/boot2docker](https://github.com/boot2docker/boot2docker)

- [Add support virtio-9p](https://github.com/boot2docker/boot2docker/issues/1139) 

## [coreos/minikube-iso](https://github.com/coreos/minikube-iso)

- [xhyve/virtio-blk: enable virtio-blk block devices driver for xhyve](https://github.com/coreos/minikube-iso/issues/28)

## [moby/hyperkit](https://github.com/moby/hyperkit)

- [kexec: fix wrong calculation method of ramdisk_start](https://github.com/moby/hyperkit/issues/66)
  - backport to [mist64/xhyve#119 (open)](https://github.com/mist64/xhyve/issues/119)

## Miscellaneous

- [go-clang/bootstrap](https://github.comgo-clang/bootstrap)
  - [Fix error handle for clang.FromDirectory()](https://github.com/go-clang/bootstrap/issues/9)
- [constabulary/gb](https://github.com/constabulary/gb)
  - [internal/vendor: Add newline to end of file](https://github.com/constabulary/gb/issues/631)
- [derekparker/delve](https://github.com/derekparker/delve)
  - [Fix typo](https://github.com/derekparker/delve/pull/112)
  - [cmd: Support space separate flags for build-flags](https://github.com/derekparker/delve/issues/619)
  - [pkg/proc: fix struct methods to unexported name & format by goimports](https://github.com/derekparker/delve/issues/728)
- [google/kati](https://github.com/google/kati)
  - [Fix can't the build kati binary](https://github.com/google/kati/issues/106)
  - [Fix kati instead of glog](https://github.com/google/kati/issues/108)
- [golang/dep](https://github.com/golang/dep)
  - [fix '|&' pipe on travis osx vm](https://github.com/golang/dep/issues/156)
  - [remove osx from ci badge and add '-u' flag for install](https://github.com/golang/dep/issues/190)
- [fsnotify/fsevents](https://github.com/fsnotify/fsevents)
  - [ci: Re-enable CircleCI test](https://github.com/fsnotify/fsevents/issues/23)
  - [example: fix lacking '%v' for go vet testing](https://github.com/fsnotify/fsevents/issues/24)
  - [ci/travis: add xcode8.1(macOS 10.12) test](https://github.com/fsnotify/fsevents/issues/25)
  - [ci/travis: fix 10.11 and 10.10 xcode images version](https://github.com/fsnotify/fsevents/issues/26)
- [tmux/tmux](https://github.com/tmux/tmux)
  - [Add missing wchar.h header when enable-utf8proc(HAVE_UTF8PROC)](https://github.com/tmux/tmux/issues/752)
- [cweill/gotests](https://github.com/cweill/gotests)
  - [Support some comments before 'package'](https://github.com/cweill/gotests/issues/40)
- [neovim/neovim](https://github.com/neovim/neovim)
  - [terminal: Fix terminal color to "correct" black color](https://github.com/neovim/neovim/issues/6160)
- [google/flatbuffers](https://github.com/google/flatbuffers)
  - [go: fix unknown field 'UOffset' to 'Pos'](https://github.com/google/flatbuffers/issues/4146)
  - [sample: update auto-generated monster_generated.h](https://github.com/google/flatbuffers/issues/4219)
  - [tests: update monster_test.bfbs binary file with generate_code.sh](https://github.com/google/flatbuffers/issues/4220)
  - [Go: Fix gRPC generated code format based on gofmt spec](https://github.com/google/flatbuffers/issues/4121)
- [neovim/go-client](https://github.com/neovim/go-client)
  - [nvim/apitool: ignore nvim_call_{atomic,function} when compare](https://github.com/neovim/go-client/issues/10)
  - [nvim: add new BufferChangedTick(nvim_buf_get_changedtick) function](https://github.com/neovim/go-client/issues/11)
  - [nvim: change get_api_info to new 'nvim_' suffix API](https://github.com/neovim/go-client/issues/12)
- [mercari/gaurun](https://github.com/mercari/gaurun)
  - [gcm: rename Client method receiver to c](https://github.com/mercari/gaurun/issues/67)
