# 完整历史备份

[Release](https://github.com/Sylvialline/xv6-labs-2023/releases/tag/archive-2026-10-07) 中的 [`xv6-labs-2023-original-2026-10-07.tar.gz`](https://github.com/Sylvialline/xv6-labs-2023/releases/download/archive-2026-10-07/xv6-labs-2023-original-2026-10-07.tar.gz) 保留原始 Git 历史和本地未提交内容。

原始远程来源：`git://g.csail.mit.edu/xv6-labs-2023`。

SHA-256：`f89e1a8cdc3987a9f53b216ce1009fda700298e5249807838bf6356ce343c255`。已核对 GitHub 返回的附件摘要。

附件包含：

- `original.bundle`：所有原始分支、远程分支、标签及 stash 可达的 Git 对象；额外保存 reflog 残留提交。
- `inventory.json`：留档时的 HEAD、分支、远程来源、状态和原始 ref / SHA 对照。
- `staged.patch`、`unstaged.patch`：已暂存和未暂存的修改。
- `untracked.tar.gz`：未跟踪文件。

被 `.gitignore` 忽略且未纳入 Git 的编译产物未上传；已提交的生成文件完整保留在 bundle 中。

## 恢复

在新目录中解压附件后，可以完整恢复原始 refs：

```bash
git clone --mirror original.bundle restored.git
git clone restored.git restored
cd restored
git switch pgtbl
```

如需恢复当时未提交的内容，在 `restored` 目录按顺序应用非空补丁，并解压未跟踪文件（附件解压于上一级目录）：

```bash
if test -s ../staged.patch; then git apply --index ../staged.patch; fi
if test -s ../unstaged.patch; then git apply ../unstaged.patch; fi
tar -xzf ../untracked.tar.gz
```

原始 stash 位于镜像的 `refs/stash`；`archive/stash-0` 分支用于浏览同一提交。stash 的第二个父提交为 index 快照；存在第三个父提交时，其保存未跟踪文件。可以从 bundle 恢复这些原始对象。

## 原始引用与公开分支

| 原始引用 | 原始 SHA | 公开分支 / 标签 |
| --- | --- | --- |
| `refs/heads/debugging-demo` | `5f9c2381129cfaa0688249a7fbd93bcef778e791` | `debugging-demo` |
| `refs/heads/lock` | `0de5ac779602f562a038e5ad27163d85bc71638b` | `lock` |
| `refs/heads/net` | `cfae93475dfb4cb5cfe264f4c029136e1447c262` | `net` |
| `refs/heads/pgtbl` | `5797060e86a7d516be0a2d68d74641b10ea47138` | `pgtbl` |
| `refs/heads/syscall` | `588449e1f3689e4cc8bc750e17d30ede0cb05dcb` | `syscall` |
| `refs/heads/thread` | `99e5821f20b50a67c82c3ea912140aaa3f6fa6a6` | `thread` |
| `refs/heads/traps` | `6b4126e6e20e4d78b8581759e0bc7f72636d8292` | `traps` |
| `refs/heads/util` | `77da51a3c309a4e41a7514982a34f064a44001a9` | `util` |
| `refs/remotes/origin/HEAD` | `77da51a3c309a4e41a7514982a34f064a44001a9` | `上游 HEAD 指向，详见 inventory.json` |
| `refs/remotes/origin/cow` | `5ce1f630132d8b7b35b9dc46b4a55f860eb85d5c` | `upstream/cow` |
| `refs/remotes/origin/debugging-demo` | `af77fb457c5fabb9a7d4346db45d4a60a513fb9c` | `upstream/debugging-demo` |
| `refs/remotes/origin/fs` | `a6af72924b115c1177d18d9b1eaba56623e4248b` | `upstream/fs` |
| `refs/remotes/origin/lock` | `0de5ac779602f562a038e5ad27163d85bc71638b` | `upstream/lock` |
| `refs/remotes/origin/mmap` | `b20ef9d0210fd7d9403acde1857eed1b9880c0b2` | `upstream/mmap` |
| `refs/remotes/origin/net` | `cfae93475dfb4cb5cfe264f4c029136e1447c262` | `upstream/net` |
| `refs/remotes/origin/pgtbl` | `66e11db2fabe4d0330b09f46bdd70b8ba7564d3f` | `upstream/pgtbl` |
| `refs/remotes/origin/riscv` | `74c1eba516fdb0ec1a17b16be7e76613ccba92bf` | `upstream/riscv` |
| `refs/remotes/origin/syscall` | `e3b3f8f9b0b1dc9c9e42622b90e2155ff7f7b40a` | `upstream/syscall` |
| `refs/remotes/origin/thread` | `0d65be5d1d880afafbf08c2adb605cf9f72216e2` | `upstream/thread` |
| `refs/remotes/origin/traps` | `f379c1c4c80947365eb6c4046c3ab165629dc8cd` | `upstream/traps` |
| `refs/remotes/origin/util` | `77da51a3c309a4e41a7514982a34f064a44001a9` | `upstream/util` |

仅在 reflog 中残留的原始提交：`81b3376d9aff7821e9cef773afa71f3f2f6e7b73`。
