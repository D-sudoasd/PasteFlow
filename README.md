<p align="center">
  <img src="assets/readme/hero.png" width="100%" alt="PasteFlow — Clean clipboard tables and export them for your next tool / 整理剪贴板表格并导出到后续软件. Conceptual illustration / 概念插图。">
</p>

# PasteFlow

**Clean clipboard tables and export them for your next tool**

**整理剪贴板表格并导出到后续软件**

[Overview / 项目概览](#overview--项目概览) · [Start / 开始使用](#start--开始使用) · [Reference / 详细说明](#reference--详细说明)

## Overview / 项目概览

Turn copied columns into a consistent table. Review delimiters, headers and column order, then export CSV, TXT or TSV with the encoding required by your workflow.

将复制的列数据整理为规则表格，检查分隔符、表头和列顺序，再按后续流程所需编码导出 CSV、TXT 或 TSV。

- **Preserve source text** — 保留表头、单位、科学计数法与原始文本。
- **Arrange columns** — 删除或调整列顺序，并可恢复原始解析结果。
- **Export presets** — 提供 Excel、Origin、pandas、MATLAB 和 GBK 预设。

## Start / 开始使用

Run with Python and Tkinter / 使用 Python 与 Tkinter 启动：

```powershell
py csv_paste_exporter.py
```

[Windows downloads / Windows 下载](https://github.com/D-sudoasd/PasteFlow/releases/latest)

The first row is data unless the header option is enabled. The preview helps check table organization; it does not perform scientific fitting.

默认第一行为数据，启用表头选项后才作为表头；预览用于检查表格整理结果。

*Cover: AI-generated conceptual illustration. 封面为 AI 生成的概念插图。*

## Reference / 详细说明

**粘贴数据 → 预览整理 → 导出表格**（面向 Origin / Excel / Python / MATLAB）

PasteFlow 是一款轻量 Windows 工具：把仪器软件、Origin、Excel 与脚本之间的剪贴板数据整理成规整表格，再导出为适合目标软件的格式。

English summary: PasteFlow turns pasted scientific data into clean tables and exports CSV / TXT / TSV with presets for Excel, Origin, pandas, MATLAB, or legacy GBK instruments.

```text
复制列  →  粘贴  →  预览  →  导出
```

常见场景：拉伸应力–应变列、XRD `2theta`/强度、光谱表、宽 Origin 工作表拆给绘图脚本。

## 能力

- 自动识别制表符、逗号、分号或空白分隔
- 去掉空行/空列，补齐参差不齐的行
- 保留表头、单位、科学计数法与原始文本
- 列删除 / 重排；可恢复原始解析结果
- 快速 X/Y 图预览与导出就绪检查
- 目标预设：Excel、Origin、Python/pandas、MATLAB、旧仪器/GBK
- 编码：UTF-8 BOM、UTF-8、GBK

窗口标题为 **「CSV 列数据整理导出」**。设置保存在 `%APPDATA%\CsvPasteExporter\settings.json`。默认：**第一行是数据**，勾选「第一行是表头」后才当表头。

## 目标软件与格式

与应用内 **目标软件** 预设一致。TSV 可从 **格式**（或 **自定义**）选择。

| 目标 | 格式 | 编码 |
| --- | --- | --- |
| Excel | CSV | UTF-8 BOM |
| Origin | TXT（制表符） | UTF-8 BOM |
| Python / pandas | CSV | UTF-8 |
| MATLAB | CSV | UTF-8 |
| 旧仪器/GBK | TXT（制表符） | GBK |

## 下载

**[Latest Release](https://github.com/D-sudoasd/PasteFlow/releases/latest)** — Windows EXE，无需安装 Python。带标签的安装包可能落后于 `main`；要当前 GUI / 预设 / 图表，请用下方源码运行。

## 使用 GUI

1. 从 Origin / Excel / 仪器软件复制若干列  
2. 点 **粘贴剪贴板**（或粘贴到 **粘贴区**）  
3. 可选：**第一行是表头**、**目标软件**  
4. 看 **预览**；改粘贴区后用 **整理预览**  
5. 可选：**删除选中列** / **上移列** / **下移列** / **恢复原始数据**  
6. **导出** → CSV / TXT / TSV（UTF-8 BOM / UTF-8 / GBK）

**清空** 会清掉粘贴区与预览。

## 范围与边界

| 做 | 不做 |
| --- | --- |
| 剪贴板表格解析与矩形化 | 科学计算、拟合、单位换算 |
| 导出给下游软件的干净分隔文件 | 读取专有 Origin / Excel 工程文件 |
| 简易 X/Y 预览 | 出版级作图或批处理管线 |
| 本地桌面工具 | 网络服务或云同步 |

解析启发式（分隔符优先级、空行处理等）面向常见科研剪贴板；极端混乱文本仍可能需要人工整理。工具不修改剪贴板来源文件。

## 从源码开发

运行时只需 **Python 标准库 + Tkinter**。开发依赖见 `requirements-dev.txt`：

```powershell
py -m pip install -r requirements-dev.txt
py csv_paste_exporter.py
py -m pytest -q
```

打包无边框 EXE：

```powershell
py -m PyInstaller --noconfirm --clean --onefile --windowed --name "CSV列数据整理导出" --distpath "dist" --workpath "build" --specpath "build" "csv_paste_exporter.py"
```

单文件入口：`csv_paste_exporter.py`。测试：`tests/test_csv_paste_exporter.py`。

## License

[MIT](LICENSE)
