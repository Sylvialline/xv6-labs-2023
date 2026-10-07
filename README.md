# xv6-labs-2023

我的 MIT 6.1810 2023 年实验代码，个人提交集中在 2025 年 3–4 月。系统调用、页表、traps 和多线程分别保存在独立分支。

## 分支与进度

| 分支 | 内容与状态 |
| --- | --- |
| `syscall` | 2025-03-02–03：trace、sysinfo 和 freelist 计数优化；评分 40/40 |
| `pgtbl` | 2025-03-13：USYSCALL、vmprint、pgaccess；专项测试通过，历史提交记录 `usertests failed` |
| `traps` | 2025-03-17–18：backtrace、sigalarm、sigreturn；专项测试通过 |
| `thread` | 2025-04-15：uthread、ph、barrier；功能测试全部通过 |
| `debugging-demo` | 2025-03-02 的调试试验 |
| `util / lock / net` | 与对应官方初始分支一致，没有本年份的个人实验实现 |

[对应年份课程网站](https://pdos.csail.mit.edu/6.1810/2023/)。

## 复测摘要（2026-10-07）

| 分支 | 评分 | 说明 |
| --- | --- | --- |
| `syscall` | 40/40 | 全部通过 |
| `pgtbl` | 36/46 | 专项测试通过；usertests 的 copyout 失败，上游基线也复现 |
| `traps` | 70/95 | backtrace / alarmtest 通过；缺少问答和时间文件，copyout 失败上游亦复现 |
| `thread` | 54/60 | 功能全部通过，缺少问答和时间文件 |

## 查看代码

默认分支 `codex/archive` 放置留档说明和当时的工作区快照。切换到实验分支查看各实验实现：

```bash
git clone https://github.com/Sylvialline/xv6-labs-2023.git
cd xv6-labs-2023
git switch pgtbl
```

实验依赖 RISC-V 工具链、QEMU、make 和 Python 3。实验分支通常使用 `make qemu` 运行、`make grade` 评分；切换不同实验后先执行 `make clean`。参考仓库和 xv6 基础仓库不保证包含每个实验的评分脚本。

## 留档说明

2026-10-07 整理自本地 `~/xv6/xv6-labs-2023`。原始提交的作者和日期保留；`upstream/*` 是当时本地保存的上游分支快照，`archive/reflog-*` 保存仅在 reflog 中残留的版本。原有 `README` 和许可证保留。

[完整备份和恢复说明](docs/ARCHIVE.md) · [2026-10-07 复测记录](docs/VERIFICATION.md)。本次留档未修复实验实现。
