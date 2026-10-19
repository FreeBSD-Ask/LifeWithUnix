# 检查点

> 本文件是唯一验收标准，命令均在仓库根目录执行。最后更新：2026-10-20。

## 0. 使用规则

* 每完成一个单元，至少运行 CP-G1、CP-G2 与该单元的检查点。
* 全书完成后，运行 CP-G1 至 CP-G8 全部检查。
* 结果必须原样记入 `PROJECT-PROGRESS.md` 的“最近检查结果”，不得只写“通过”。
* 检查点的预期值会随文件增减变化；变化时同步更新本文件与基线。

## 1. 全局检查点

### CP-G1 引号

```sh
python script/check_quotes.py
```

预期：最后一行输出 `total problems: 0`。

失败处理：按报告的文件与行号逐个手动修正，禁止批量替换。

### CP-G2 markdownlint

```sh
npx --no-install markdownlint-cli2 "**/*.md" "!en/**" "!node_modules/**" "!script/**" --config .github/.markdownlint.json
```

预期：输出 `Summary: 0 error(s)`。2026-10-20 的基线为 132 个文件；新增任务文档后文件数会变化，错误数必须为 0。

失败处理：逐条修复，不得关闭规则或修改配置掩盖问题。

### CP-G3 H1 与 SUMMARY 一致

```sh
python - <<'EOF'
import re, pathlib
lines = pathlib.Path('SUMMARY.md').read_text(encoding='utf-8').splitlines()
bad = []
n = 0
for ln in lines:
    m = re.match(r'\* \[(.+?)\]\((.+?)\)', ln.strip())
    if not m:
        continue
    title, path = m.group(1), m.group(2)
    p = pathlib.Path(path)
    if not p.exists():
        bad.append((path, 'MISSING'))
        continue
    n += 1
    first = next((x[2:].strip() for x in p.read_text(encoding='utf-8').splitlines() if x.startswith('# ')), '')
    if first != title:
        bad.append((path, 'H1 mismatch'))
print('entries', n, 'mismatches', len(bad))
for b in bad[:10]:
    print(b)
EOF
```

预期：`entries 129 mismatches 0`。SUMMARY 条目增减时，`entries` 随之变化，`mismatches` 必须为 0。

### CP-G4 章节结构

```sh
python script/compare_structure.py
```

预期：差异为 0。

当前状态：该脚本在 2026-10-20 检查时不存在（`AGENTS.md` 有引用）。暂以 CP-G3 加人工核对节号代替：逐章检查 `X.1` 至 `X.N` 是否连续、H2 是否保留原书节号。补建脚本后，把实际输出写回本节。

### CP-G5 中文与英文、数字间距

```sh
python - <<'EOF'
import re, glob, pathlib
dirs = ['qian-yan', 'di-yi-bu-fen-guo-qu-xian-zai-yu-wei-lai', 'di-er-bu-fen-unix-xin-xi',
        'di-san-bu-fen-unix-nei-bu', 'di-si-bu-fen-unix-zhi-wai']
bad = []
for d in dirs:
    for f in glob.glob(d + '/*.md'):
        for i, ln in enumerate(pathlib.Path(f).read_text(encoding='utf-8').splitlines(), 1):
            if ln.startswith('```') or '`' in ln or 'http' in ln:
                continue
            if re.search(r'[\u4e00-\u9fff][A-Za-z0-9]|[A-Za-z0-9][\u4e00-\u9fff]', ln):
                bad.append((f, i, ln[:60]))
print('CJK no-space lines:', len(bad))
for b in bad[:10]:
    print(b)
EOF
```

预期：`CJK no-space lines: 0`。含行内代码或网址的行已跳过，需人工抽查这些行。

### CP-G6 禁止项扫描

```sh
python - <<'EOF'
import re, glob, pathlib
dirs = ['qian-yan', 'di-yi-bu-fen-guo-qu-xian-zai-yu-wei-lai', 'di-er-bu-fen-unix-xin-xi',
        'di-san-bu-fen-unix-nei-bu', 'di-si-bu-fen-unix-zhi-wai']
counts = {'您': 0, '仓库': 0, 'asciidoc': 0, 'text_fence': 0, 'html': 0}
for d in dirs:
    for f in glob.glob(d + '/*.md'):
        t = pathlib.Path(f).read_text(encoding='utf-8')
        body = re.sub(r'```.*?```', '', t, flags=re.S)
        body = re.sub(r'`[^`]*`', '', body)
        counts['您'] += body.count('您')
        counts['仓库'] += body.replace('硬拷贝', '').count('仓库')
        counts['asciidoc'] += len(re.findall(r'\b(?:xref|link):', body))
        counts['text_fence'] += t.count('```text')
        counts['html'] += len(re.findall(r'</?[a-zA-Z][^>]*>', body))
print(counts)
EOF
```

预期：`{'您': 0, '仓库': 0, 'asciidoc': 0, 'text_fence': 0, 'html': 0}`。

说明：`硬拷贝终端` 是固定术语，扫描时已排除；是否改写由术语表统一决定。HTML 计数已剔除代码块与行内代码。

### CP-G7 图片引用

```sh
python - <<'EOF'
import re, glob, pathlib
dirs = ['qian-yan', 'di-yi-bu-fen-guo-qu-xian-zai-yu-wei-lai', 'di-er-bu-fen-unix-xin-xi',
        'di-san-bu-fen-unix-nei-bu', 'di-si-bu-fen-unix-zhi-wai']
missing = []
total = 0
files = [f for d in dirs for f in glob.glob(d + '/*.md')] + ['fu-lu-a-di-zhi.md']
for f in files:
    base = pathlib.Path(f).parent
    for m in re.finditer(r'!\[[^\]]*\]\(([^)]+)\)', pathlib.Path(f).read_text(encoding='utf-8')):
        p = m.group(1)
        if p.startswith('http'):
            continue
        total += 1
        if not (base / p).exists():
            missing.append((f, p))
print('total image refs', total, 'missing', len(missing))
for x in missing:
    print(x)
EOF
```

预期：`missing 0`。`AGENTS.md` 中的 `xxx.png` 是写法示例，不在扫描范围内。

### CP-G8 空页与存根页

```sh
python - <<'EOF'
import glob, pathlib
dirs = ['qian-yan', 'di-yi-bu-fen-guo-qu-xian-zai-yu-wei-lai', 'di-er-bu-fen-unix-xin-xi',
        'di-san-bu-fen-unix-nei-bu', 'di-si-bu-fen-unix-zhi-wai']
stubs = []
for d in dirs:
    for f in glob.glob(d + '/*.md'):
        lines = [l for l in pathlib.Path(f).read_text(encoding='utf-8').splitlines() if l.strip()]
        if len(lines) < 2:
            stubs.append((f, len(lines)))
print('stub pages', len(stubs))
for s in stubs:
    print(s)
EOF
```

预期：`stub pages 0`。

## 2. 单元检查点

每个单元完成后，除四轮全部勾选外，还要运行下面两类命令：

* 引号：`python script/check_quotes.py <该单元目录>`
* lint：`npx --no-install markdownlint-cli2 "<该单元目录>/*.md" --config .github/.markdownlint.json`

| ID | 单元 | 附加检查 |
| -- | ---- | -------- |
| CP-U00 | 前言与如何阅读 | 两条命令均须通过 |
| CP-U01 | 第 1 章 UNIX 历史 | 两条命令均须通过；时间线表格列数完整 |
| CP-U02 | 第 2 章 UNIX 现状 | 两条命令均须通过 |
| CP-U03 | 第 3 章 UNIX 未来 | 两条命令均须通过；合并趋势图引用可解析 |
| CP-U04 | 第 4 章 印刷资料 | 两条命令均须通过；书名、刊名保持原文 |
| CP-U05 | 第 5 章 非印刷资料 | 两条命令均须通过 |
| CP-U06 | 第 6 章 用户环境 | 两条命令均须通过；终端提示符与代码块原样 |
| CP-U07 | 第 7 章 程序员环境 | 两条命令均须通过；代码只译注释 |
| CP-U08 | 第 8 章 管理员环境 | 两条命令均须通过；配置文件内容原样 |
| CP-U09 | 第 9 章 UNIX 地下世界 | 两条命令均须通过；公共机房图片图注准确 |
| CP-U10 | 第 10 章 UNIX 服务 | 两条命令均须通过 |
| CP-U11 | 第 11 章 UNIX 应用 | 两条命令均须通过；作者屏幕图片引用可解析 |
| CP-U12 | 第 12 章 走进现实世界 | 两条命令均须通过；中文字形图片引用可解析 |
| CP-U13 | 附录 A 地址 | 两条命令均须通过；337 条地址数据未改动 |

## 3. 交接检查点

交接或换会话前逐项确认：

* [ ] `git status --short` 为空。
* [ ] `PROJECT-PROGRESS.md` 顶部的“最近内容提交”存在于 `git log` 中；其后的提交只应是进度书自身的更新。
* [ ] `PROJECT-PROGRESS.md` 的“当前任务”“当前轮次”“下一步”均非空。
* [ ] 没有仍在运行、尚未回收的子代理。
* [ ] 最近检查结果已按实际输出记录。
* [ ] 未完成的轮次没有被勾选。
* [ ] 本轮失败或取消的尝试已记入“阻塞与风险”。
