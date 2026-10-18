# 编辑日志

## 2026-10-18

**项目启动**

- 建立翻译项目：确定书名《UNIX 生活：写给每个人的指南》（*Life With UNIX: A Guide For Everyone*，Don Libes、Sandy Ressler 著，Prentice Hall 1989）。
- 改写 `AGENTS.md`，替换原 FreeBSD 手册模板，适配本书翻译项目（PDF 原文提取、GitBook 结构、四类信息框、术语表）。
- 新增原文提取工具 `script/extract_pdf.py`（按坐标剔除页眉页脚、重组跨行连字符）、切分工具 `script/split_en.py`（按印刷目录切成 20 个英文源文件，输出到 `en/`）、目录生成工具 `script/gen_mulu.py`（由 `SUMMARY.md` 生成 `mu-lu.md`，并可按目录建占位页）。
- 提取正文插图 3 张到 `.gitbook/assets/`。
- 建立完整 GitBook 目录结构：4 部分 12 章共 111 节，另前言两篇、附录 A，共页面 126 个；`SUMMARY.md` 与 `mu-lu.md` 同步生成。
- 编写 `README.md` 项目首页与 `yi-zhe-shuo-ming.md` 术语对照表。
- 原书页码与中文章节对应关系：原书正文第 1 页 = PDF 第 21 页（偏移 +20）。

**待办**

- 各章翻译与逐句校对（三轮 + 一轮复查）。
- 附录 A 地址名录：公司名保留英文，条目说明文字翻译。
- 原书 Index（索引）不翻译，改为说明页或省略（索引页码无对应意义）。
