# 实验复测记录

复测日期：2026-10-07（Asia/Shanghai）。使用隔离副本，未修改本地原仓库或实验实现。环境：Ubuntu、RISC-V GCC 13.3.0、QEMU 8.2.2。以下是本地评分脚本结果，不是课程提交成绩。

为避免 QEMU 调试端口冲突，各测试使用独立 GDBPORT。首次发生端口冲突的结果未采纳。部分实验的扣分来自缺失 `time.txt` 或问答文件，需与功能失败分别看待。

## pgtbl

原始分支提交：`5797060e86a7d516be0a2d68d74641b10ea47138`。命令：`make grade`；退出码：`2`。

```text
  pgtbltest: ugetpid: OK
  pgtbltest: pgaccess: OK
pte printout: OK (0.4s)
answers-pgtbl.txt: OK
  usertests: all tests: FAIL
time: OK
Score: 36/46
```

[完整评分输出](verification/pgtbl.log)。

## syscall

原始分支提交：`588449e1f3689e4cc8bc750e17d30ede0cb05dcb`。命令：`make grade GDBPORT=26102`；退出码：`0`。

```text
answers-syscall.txt: OK
trace 32 grep: OK (1.5s)
trace all grep: OK (0.4s)
trace nothing: OK (0.8s)
trace children: OK (11.2s)
sysinfotest: OK (1.7s)
time: OK
Score: 40/40
```

[完整评分输出](verification/syscall.log)。

## thread

原始分支提交：`99e5821f20b50a67c82c3ea912140aaa3f6fa6a6`。命令：`make grade GDBPORT=26104`；退出码：`2`。

```text
uthread: OK (5.1s)
answers-thread.txt: FAIL
ph_safe: OK (6.9s)
ph_fast: OK (14.3s)
barrier: OK (3.6s)
time: FAIL
Score: 54/60
```

[完整评分输出](verification/thread.log)。

## traps

原始分支提交：`6b4126e6e20e4d78b8581759e0bc7f72636d8292`。命令：`make grade GDBPORT=26103`；退出码：`2`。

```text
answers-traps.txt: FAIL
backtrace test: OK (3.2s)
  alarmtest: test0: OK
  alarmtest: test1: OK
  alarmtest: test2: OK
  alarmtest: test3: OK
usertests: FAIL (4.3s)
time: FAIL
Score: 70/95
```

[完整评分输出](verification/traps.log)。

## 2023 上游基线对照

`pgtbl` 与 `traps` 的 `usertests` 在 `copyout` 测试失败。对未修改的 `upstream/traps`（`f379c1c4c80947365eb6c4046c3ab165629dc8cd`）在相同环境单独运行 `python3 grade-lab-traps usertests`，也在相同位置失败。该结果不能单独归因于个人实验实现。历史 `pgtbl` 提交的 `usertests failed` 标记仍保留。[上游对照日志](verification/upstream-traps-usertests.log)。
