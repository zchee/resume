# Projects

## [docker-machine-driver-xhyve](https://github.com/zchee/docker-machine-driver-xhyve) (Go)

docker-machine/minikube driver plugin for xhyve/hyperkit. (native macOS hypervisor.framework)

macOSのHypervisor.framework(GUN/Linuxでのkvmに近いもの)を使った [mist64/xhyve](https://github.com/mist64/xhyve) をcgoでラップし、docker-machineのプラグインとして動くもの。  
[kubernetes/minikube](https://github.com/kubernetes/minikube)からの打診もあり、minikubeのバックエンドもサポート。  
内部構造は後にリリースされたDocker for Macとほぼ同じ。(クローズドソースのため、個人的なバイナリ解析の結果)  

qcow2ファイルのサポート、9p(plan9)プロトコル上のhost/guest間のフォルダシェアなど。

現在はGoogleの[@dlorenc](https://github.com/dlorenc)、[@r2d4](https://github.com/r2d4) (共にminikube)、Red Hatの[@praveenkumar](https://github.com/praveenkumar)、Shopifyの[@dalehamel](https://github.com/dalehamel)と保守。

## [nvim-go](https://github.com/zchee/nvim-go) (Go)

Go development plugin for Neovim written in pure Go.

VimのGo開発プラグインである[fatih/vim-go](https://github.com/fatih/vim-go)を、Neovim専用に書き直したもの。  
NeovimのMsgpack-RPCプラグイン機構を使用して、Vim scriptではなくGoで記述。  
vim-goとの完全互換を目指し、またオリジナルにはない[derekparker/delve](https://github.com/derekparker/delve)のTUIインターフェイスを実装しつつ開発中。

## [clang-server](https://github.com/zchee/clang-server) (Go)

A C/C++ AST index server using libclang written in Go.

LLVM libclangのGoバインディングである[go-clang](https://github.com/go-clang)を使い、

- C/C++のソースコードからASTを解析
- flatbuffersで全構造体をシリアライズ
- NoSQLであるLevelDBに保存
- Msgpack-RPCまたはgRPCでクライアントと通信

を経て、コード補完や各種コード解析(definition等)を提供するGoで記述したRPCサーバー。  
現在はflatbuffersのgRPCサポートにPythonが入っていないため、一時開発中断。

## [go-qcow2](https://github.com/zchee/go-qcow2) (Go)

Manage the QEMU qcow2 disk image written in Go.

QEMUのディスクイメージであるqcow2フォーマットを、仕様書に沿った形でバイナリレベルで構築するもの。  
現在はファイル作成・書き込みのみサポート。  
[docker-machine-driver-xhyve](https://github.com/zchee/docker-machine-driver-xhyve) の内部で使用している [moby/hyperkit](https://github.com/moby/hyperkit) がqcow2形式をサポートしているため、cgoでのバインディング・GPLライセンスを避けるために開発。

## [go-mmal](https://github.com/zchee/go-mmal) (Go)

Raspberry Pi's libmmal bindings for Go.

Raspberry Pi独自のMulti-Media Abstraction Layer (MMAL) を扱うためのGoのcgoバインディング。  
Goのみでカメラを操作可能。

## deoplete.nvim sources (Python)

Neovimの補完エンジンである [Shougo/deoplete.nvim](https://github.com/Shougo/deoplete.nvim) の言語別プラグイン。  
主にDocker社のVimユーザーのプロダクション環境で使用して頂いている。

- [deoplete-go](https://github.com/zchee/deoplete-go)
  - [nsf/gocode](https://github.com/nsf/gocode) を使用し提供
- [deoplete-jedi](https://github.com/zchee/deoplete-jedi)
  - Pythonの解析エンジンで有名なjediを使用しつつ、高速化のため内部でthreadingを使いサーバーを起動し補完を提供
- [deoplete-clang](https://github.com/zchee/deoplete-clang)
  - libclangのPythonバインディングを使用し、C/C++を解析し補完を提供
  - 当時はLLVMでPython3のサポートが無かった為、libclang-python3としてポートし開発。

---

# Organizations

- [vim-jp](https://github.com/vim-jp)
- [fsnotify](https://github.com/fsnotify)

---

# Contributions

## Go core, etc

### Go core
- [build: fix darwin/arm broken on macOS 10.12 with Xcode 8.0](https://go-review.googlesource.com/c/34673/)

### golang.org/x/tools
- [go/gcexportdata: fix unnecessary plural type definitions of arg](https://go-review.googlesource.com/c/42890/)
- [imports: fix LocalPrefix document prefix](https://go-review.googlesource.com/c/46432/)
- [cmd/git-contrib-init: support http.cookiefile config for gitcookies](https://go-review.googlesource.com/c/46235/)
- [cmd/go-contrib-init: fix get GOPATH env logic](https://go-review.googlesource.com/c/46234/)
- [cover: backport handle multiple samples from the same location (open)](https://go-review.googlesource.com/c/37550/)
- [cmd/guru: fix typo of 'hyphen' to rename to 'comma'](https://go-review.googlesource.com/c/35770/)

## [docker/machine](https://github.com/docker/machine)

主にAmazon EC2/GCPドライバへのオプション追加・ドキュメント整備など。

- [Support --google-disk-type flag for google driver](https://github.com/docker/machine/issues/687)
  - First contribution: : 2015-03-02
- [docs: Update each drivers flag](https://github.com/docker/machine/issues/1167)
- [(closed) New Driver: xhyve](https://github.com/docker/machine/issues/1358)
  - Move to [docker-machine-driver-xhyve](#docker-machine-driver-xhyve-go)
- [etc...](https://github.com/docker/machine/pulls?q=is%3Apr+is%3Aclosed+author%3Azchee)

## [nsf/gocode](https://github.com/nsf/gocode)

主にGoのtipでの言語仕様・バイナリ仕様の変更に追従するためのパーサーの修正。

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

## [moby/hyperkit](https://github.com/moby/hyperkit)

ハイパーバイザー起動時のkernelとinitrdファイルのロードにて、メモリ上で双方がオーバーラップする為にdebian testingやminikubeのカーネルが動作しない問題を修正。

- [kexec: fix wrong calculation method of ramdisk_start](https://github.com/moby/hyperkit/issues/66)
  - backport to [mist64/xhyve#119 (open)](https://github.com/mist64/xhyve/issues/119)

## [boot2docker/boot2docker](https://github.com/boot2docker/boot2docker)

[docker-machine-driver-xhyve](https://github.com/zchee/docker-machine-driver-xhyve) で使用している9pプロトコルサポートのkernel configの追加。

- [Add support virtio-9p](https://github.com/boot2docker/boot2docker/issues/1139) 

## [coreos/minikube-iso](https://github.com/coreos/minikube-iso)

[docker-machine-driver-xhyve](https://github.com/zchee/docker-machine-driver-xhyve) で使用している9pプロトコルサポートのkernel configの追加。

- [xhyve/virtio-blk: enable virtio-blk block devices driver for xhyve](https://github.com/coreos/minikube-iso/issues/28)

## [gperftools/gperftools](https://github.com/gperftools/gperftools)

macOS Sierraにおけるシステムライブラリlibsystem_malloc.dylibの仕様変更で動作しない問題をレポート、修正パッチを投稿。  
[jemalloc/jemalloc](https://github.com/jemalloc/jemalloc) で既に修正済みであったものをポート。

- [*** malloc_zone_unregister() failed on macOS 10.12 Sierra](https://github.com/gperftools/gperftools/issues/827) (issue)
  - [Fix finding default zone on macOS sierra](https://github.com/gperftools/gperftools/commit/acac6af26b0ef052b39f61a59507b23e9703bdfa) (commit)

## [tmux/tmux](https://github.com/tmux/tmux)

tmuxへの [@choppsv1氏の非公式パッチ](https://gist.github.com/choppsv1/dd00858d4f7f356ce2cf) にてTrue(24bit) color サポートが可能になったが、その後のtmuxの変更でapplyできなくなった為、[最新に追従するように変更したパッチ](https://gist.github.com/zchee/9f6f2ca17acf49e04088)を作成。  
以下の[@sunaku](https://github.com/sunaku) 氏のpull requestのベースとなり、その後tmux本体に正式にマージされる。

- [add support for 24-bit RGB color escape sequences](https://github.com/tmux/tmux/pull/112)


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
