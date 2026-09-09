# Changelog

## 1.0.0 (2026-09-09)


### Features

* 初始 setup-cross-tools action(交叉编译工具链供给) ([5a8cdb0](https://github.com/nsfintech/actions/commit/5a8cdb084915cbd65d05f5749b61faffde4c9113))


### Bug Fixes

* dtolnay@v1 必须显式传 toolchain([@v1](https://github.com/v1) 无默认值,[@stable](https://github.com/stable) 分支版才有) ([89a9951](https://github.com/nsfintech/actions/commit/89a9951ba830d577e129d77220d78e7274019d91))
* fetch 下载去掉 -s,保留 curl 进度表(百分比/速度) ([e12f68e](https://github.com/nsfintech/actions/commit/e12f68e784438abbc7ed3184bea8661f367f8433))
* PE32+ 断言对齐实际 file 输出((GUI) + x86-64 连字符) ([2cfccad](https://github.com/nsfintech/actions/commit/2cfccadbb6781fef762ba51f86c0381fcf77d22a))
* SDK 预下载入 TOOL_CACHE;自测改 cdylib 真验证链接 ([aa62785](https://github.com/nsfintech/actions/commit/aa627856a37809b44ae0aaf821b28cf261e45045))
* zig PATH 指向 mv 后的实际目录 ([6e69f1b](https://github.com/nsfintech/actions/commit/6e69f1b0ceaa17217276d44f19227b24e6ea8686))
* zig PATH 指向 mv 后的实际目录(二进制在 zig-&lt;ver&gt;/ 根) ([3da4d58](https://github.com/nsfintech/actions/commit/3da4d58e483d0bc222efdcbaa2ec5286e3819c33))
* zig 下载改社区镜像 zig.linus.dev(官方推荐 CI 用镜像) ([14b96c6](https://github.com/nsfintech/actions/commit/14b96c62461d5e73df6cc143b4d1dc175599fbbb))
* 断言匹配实际产物名与新版 file 描述 ([726e606](https://github.com/nsfintech/actions/commit/726e606cae752fa5cb98114b9338f6a0caa4a501))
* 自检命令改 --help(zigbuild 无 --version 参数);rust 改 dtolnay@v1 ([fed04f2](https://github.com/nsfintech/actions/commit/fed04f238f2cab52b30d3bcbed6316c9fbd417ae))
* 补回被误删的 cargo-xwin PATH 写入 ([9f0cb53](https://github.com/nsfintech/actions/commit/9f0cb53272dcc3915282361961dc6256a693bdac))

## Changelog
