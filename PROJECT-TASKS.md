# 任务书

> 本文件是《UNIX 生活：写给每个人的指南》简体中文版校对工作的唯一任务书。最后更新：2026-10-20。

## 0. 三份文档的分工

| 文档 | 作用 | 唯一性 |
| ---- | ---- | ------ |
| `PROJECT-TASKS.md` | 任务书：目标、范围、工作单元、验收标准、执行协议 | 任务范围的唯一来源 |
| `PROJECT-CHECKPOINTS.md` | 检查点：可复现的验收命令与预期结果 | 验收标准的唯一来源 |
| `PROJECT-PROGRESS.md` | 进度书：实时状态、修改记录、下一步 | 进度状态的唯一来源 |

发生冲突时：翻译与格式规则以 `AGENTS.md` 为准，任务范围以本文件为准，实时状态以 `PROJECT-PROGRESS.md` 为准，验收口径以 `PROJECT-CHECKPOINTS.md` 为准。

`script/review-progress.md` 是 2026-10-20 之前的历史记录，已冻结，不再更新；其中内容与新进度书不一致时，以 `PROJECT-PROGRESS.md` 为准。

## 1. 目标与完成定义

目标：在初译完成的基础上，对全书 126 个内容页逐句执行三轮校对（R1 准确性、R2 语言、R3 术语与格式）加一轮完整复查（F），消除事实错误、漏译、欧化汉语、术语不一致与格式违规，同时保留原书 1989 年的视角和调侃口吻。

全书完成的定义（DoD）：

1. `PROJECT-PROGRESS.md` 中 U00 至 U13 全部标记为已完成。
2. `PROJECT-CHECKPOINTS.md` 中的全局检查点全部通过。
3. 工作树干净，每个单元都有对应的中文提交。
4. `CHANGELOG.md` 记录本轮逐句回校的完成情况。

## 2. 工作单元

| ID | 单元 | 文件范围 | 页数 | 英文原文 |
| -- | ---- | -------- | ---- | -------- |
| U00 | 前言与如何阅读 | `qian-yan/*.md` | 2 | `en/01-preface.txt`、`en/02-how-to-read-this-book.txt` |
| U01 | 第 1 章 UNIX 历史 | `di-yi-bu-fen-guo-qu-xian-zai-yu-wei-lai/1.*.md` | 13 | `en/04-ch01-unix-history.txt` |
| U02 | 第 2 章 UNIX 现状 | `di-yi-bu-fen-guo-qu-xian-zai-yu-wei-lai/2.*.md` | 15 | `en/05-ch02-unix-present.txt` |
| U03 | 第 3 章 UNIX 未来 | `di-yi-bu-fen-guo-qu-xian-zai-yu-wei-lai/3.*.md` | 12 | `en/06-ch03-unix-future.txt` |
| U04 | 第 4 章 印刷资料 | `di-er-bu-fen-unix-xin-xi/4.*.md` | 7 | `en/08-ch04-printed-information.txt` |
| U05 | 第 5 章 非印刷资料 | `di-er-bu-fen-unix-xin-xi/5.*.md` | 5 | `en/09-ch05-nonprinted-information.txt` |
| U06 | 第 6 章 用户环境 | `di-san-bu-fen-unix-nei-bu/6.*.md` | 6 | `en/11-ch06-users-environment.txt` |
| U07 | 第 7 章 程序员环境 | `di-san-bu-fen-unix-nei-bu/7.*.md` | 5 | `en/12-ch07-programmers-environment.txt` |
| U08 | 第 8 章 管理员环境 | `di-san-bu-fen-unix-nei-bu/8.*.md` | 8 | `en/13-ch08-administrators-environment.txt` |
| U09 | 第 9 章 UNIX 地下世界 | `di-si-bu-fen-unix-zhi-wai/9.*.md` | 6 | `en/15-ch09-unix-underground.txt` |
| U10 | 第 10 章 UNIX 服务 | `di-si-bu-fen-unix-zhi-wai/10.*.md` | 11 | `en/16-ch10-unix-services.txt` |
| U11 | 第 11 章 UNIX 应用 | `di-si-bu-fen-unix-zhi-wai/11.*.md` | 21 | `en/17-ch11-unix-applications.txt` |
| U12 | 第 12 章 走进现实世界 | `di-si-bu-fen-unix-zhi-wai/12.*.md` | 14 | `en/18-ch12-unix-meets-the-real-world.txt` |
| U13 | 附录 A 地址 | `fu-lu-a-di-zhi.md` | 1 | `en/19-appendix-a-addresses.txt` |

合计 126 个内容页。

补充说明：

* 各章章首页（`X.-*.md`）计入该章页数。
* 原书索引（`en/20-index.txt`）按既定决定不翻译，不在单元表内。
* 各分部页只有标题、没有正文，不单列单元。
* `en/` 只用于定位与对照，PDF 是唯一权威源。

## 3. 四轮校对内容

### R1 准确性

* 人名、公司、机构、产品、版本号、日期、数字、价格、地址是否与原书一致。
* 事件时序、因果、指代是否正确。
* 是否漏译句子、信息框、脚注、表格行、图注。
* 人名首次出现时，身份交代是否充分。
* 可疑处回 PDF 核对，禁止以既有中文译文作为修改依据。

### R2 语言

* 欧化汉语：“进行、作出、加以 + 动词”、滥用“被”字句、长定语堆叠。
* 后置、倒装、偷换主语。
* 虚词冗余：的、了、着、是、被、所、会、将。
* 机翻腔与官腔；保留原书的调侃、讽刺、俚语。
* 每个段落写在同一行，不跨行拼接。

### R3 术语与格式

* 术语以 `yi-zhe-shuo-ming.md` 为准。常用约定：人名保留英文；shell 不译；daemon 译“守护进程”；kernel 译“内核”；source 译“源码”；public-domain 译“公有领域”；timesharing 译“分时”；port 译“移植”；repository 译“存储库”（禁止“仓库”）；copy 译“复制”（禁止“拷贝”，固定词“硬拷贝终端”暂列例外，待术语表统一时决定）。
* 正文使用中文弯引号，必须成对且方向正确；禁止英文直引号与 `「」『』`，代码块与行内代码除外，英文词内撇号不算引号。
* 正文中的路径加粗，命令与选项用反引号，两者不得混用。
* 代码块与终端输出保持原样，只把英文注释译成中文。
* 禁止 HTML、禁止 AsciiDoc 残留（`xref:`、`link:`、行尾软换行）、禁止 `text` 代码块标记。
* 避免滥用“已”字；一律用“你”；中文与英文、数字之间加半角空格。
* 表格居中，表头声明几列，数据行就要有几列。

### F 复查

完整通读该单元，只找前三轮遗漏的新问题。不得重复修改已经确认无误的内容，不得以“复查”为名重做已完成的轮次。

## 4. 执行协议

### 4.1 默认方式：手工串行

逐文件对照英文原文，逐处手动修改。每次修改前确认问题真实存在，修改后确认改动准确且未引入新错误。禁止 `sed`、脚本或任何形式的批量替换。

### 4.2 可选方式：滚动子代理

* 最多 10 路并发，一个单元只派一个代理，各代理的文件集不得重叠。
* 每个代理的任务书必须包含第 3 节的四轮要求与 `AGENTS.md` 的硬性约束，并声明不改 H1、`SUMMARY.md`、`mu-lu.md`、`yi-zhe-shuo-ming.md`、`en/`，不执行 git 提交。
* 代理返回后，主代理必须核对 `git diff`，确认修改真实、范围正确、没有相互覆盖；核对通过才计入进度。
* 代理被取消、超时、报错（包括余额不足）时，该单元视为未开始，改用手工；不得把未验证的代理结果计入进度。

### 4.3 提交

* 完成一个单元或一批相关修改后立即提交，只提交相关的 `.md` 文件。
* 提交信息用中文一行，例如“校对第 1 章 UNIX 历史（三轮+复查）”。
* 直接提交 `main`；未经用户要求不 push、不 force。

### 4.4 进度同步

以下时点必须更新 `PROJECT-PROGRESS.md`：

1. 开始一个单元之前，写明当前任务与计划。
2. 每完成一轮（R1、R2、R3、F）。
3. 每次提交之后，更新 HEAD 与修改数。
4. 遇到阻塞、失败或方案改变。
5. 会话结束或交接之前。

更新时必须如实记录；未执行的轮次不得勾选。

## 5. 禁止事项

完整清单见 `AGENTS.md`。核心几条：

* 不修改、不翻译 `en/`。
* 不以中文版既有译文作为修改依据。
* 不用今天的现状改写原书 1989 年的表述；确需补充，只用克制的“（译注：……）”，单独成段。
* 不臆造译名；新术语先登记再使用。
* 不手动编辑 `mu-lu.md`，不改 `SUMMARY.md` 首行。
* 不新增与 CI 工作流冲突的本地规则。

## 6. 接手流程

1. 读 `PROJECT-PROGRESS.md` 顶部的“当前任务”“当前轮次”“下一步”。
2. 读本文件第 2、3 节，确认范围与四轮要求。
3. 读 `PROJECT-CHECKPOINTS.md`，确认验收命令与预期结果。
4. 运行 `git status` 与 `git log --oneline -5`，确认工作树与进度书记录一致。
5. 从“下一步”继续。未完成的轮次不得跳轮，已完成的轮次不得重做。

## 7. 变更管理

* 新增、拆分或合并工作单元，或改变验收标准，先改本文件，再在 `PROJECT-PROGRESS.md` 记录变更。
* 临时脚本、截图与日志放在 `script/`，该目录不纳入版本控制。
* 本文件只规定任务，不记录实时状态。
