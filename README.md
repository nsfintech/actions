# nsfintech/actions

组织自维护 GitHub Actions **setup action** 集散地:给 CI 环境装工具链/工具的
composite action 集中放这里,一个仓库一条版本线(v1 浮动 tag),各项目仓库
`uses: nsfintech/actions/actions/<name>@v1` 消费。

> 与 `nsfintech/.github` 的分工:`.github` 放可复用 workflow(reusable workflows);
> 本仓库放 action(composite actions,被 workflow 引用的步骤级组件)。
> fork 来的独立 action(如 setup-yq)仍单独成仓——fork 要跟上游,不混入。

## 设计约定

- **预编译二进制优先**:直接下载官方 release 产物 + sha256 校验,不依赖 runner
  上有 cargo/uv/npm(组织 runner 是裸机,环境全靠 setup action 供给)
- **缓存走 `$RUNNER_TOOL_CACHE`**:self-hosted runner 上该目录持久,与
  setup-node / dtolnay 的 `Found in cache` 同机制——首次下载,之后秒级命中
- **版本显式**:每个工具版本是 action 的 input 默认值,升级 = 改默认值 + `feat:`/
  `fix:` commit(走 release-please 发版,与组织其他仓库同节奏)
- **公开仓库**:与 `.github` 同策略(workflow 逻辑本就公开,setup 脚本无新增暴露面;
  且免开 org 级私有共享设置)

## 目录

| action | 用途 |
|---|---|
| [`actions/setup-cross-tools`](actions/setup-cross-tools/) | Rust 交叉编译工具链:zig + cargo-zigbuild + cargo-xwin。linux runner 上交叉出 darwin(darwin-arm64/x64)与 windows msvc 产物 |

## 版本管理

release-please(simple 类型,同 `nsfintech/.github` 模式):推 `feat:`/`fix:` 到
main → 开 release PR → 合并自动打 `vX.Y.Z` tag → update-major-tag 把 `v1` 前移。
消费方永远引 `@v1`,非破坏性更新自动跟进;破坏性改动升 `v2`。

## 索引

| 工具 | 版本(默认) | 来源 | 锁版本原因 |
|---|---|---|---|
| zig | 0.15.2 | ziglang.org 官方 tarball | 0.16.x darwin 链接 bug(exported symbols list 误读,实测 FileNotFound) |
| cargo-zigbuild | 0.23.4 | rust-cross GitHub release | — |
| cargo-xwin | 0.23.1 | rust-cross GitHub release | — |

升级工具版本时:改 `action.yml` 里 input 默认值 + `fetch` 的 sha256 + README
索引表,commit 用 `feat:`(如 `feat: zig 0.15.3`)。
