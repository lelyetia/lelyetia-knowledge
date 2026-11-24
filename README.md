# Lelyetia's Knowledge Base

欢迎来到 **lelyetia 的个人知识库**！本项目使用 **MkDocs + Material for MkDocs** 搭建，主要记录我在学习过程中积累的知识、资源与笔记。记录方向包括：**计算机基础**、**计算机视觉**、**人工智能（传统机器学习与深度学习）**、**计算机图形学**、**大模型技术**以及**实用工具与科研工具**等，一切内容随我的学习历程持续更新。愿我们保持进步，to~ 屏幕前的你。

- **在线阅读**：<https://lelyetia.github.io/lelyetia-knowledge/>
- **个人主页**：<https://lelyetia.github.io/>
- **问题反馈**：<https://github.com/lelyetia/lelyetia-knowledge/issues>

## 关于我

中国普通大学本科生，目前**大三**在读，喜欢研究**计算机科学、人工智能、计算机图形学**等领域的知识。更多关于我的介绍见[个人主页](https://lelyetia.github.io/)。

- Q&A：喜欢玩的游戏？答：**Minecraft**、城市天际线。

## 本知识库的主要目的

互联网上的技术教程已经数不胜数。对于 Git、Markdown、Linux 管理等已有大量优质教程的内容，从零重写一份“知识点教学”往往事倍功半：一方面本科阶段对许多领域的理解远不及一线专家；另一方面，学习过程中最让人困扰的往往是 **“我究竟要学什么”** ——尤其在 AI 浪潮与信息焦虑并存的当下（2025–2026），每天充斥着各种夸大与唱衰。

因此，本知识库更希望承担 **“索引”** 与 **“导言”** 的角色：把相关领域的知识脉络整理清楚，并附上优质的学习资源链接，帮助大家更好地站在巨人的肩膀上。

## 阅读与维护说明

1. **更新节奏**：本知识库由我个人维护，受升学与课业精力所限，无法保证在本科期间做到面面俱到，但只要还在继续学习就会持续更新 >_<。
2. **原创与 AI 标记**：AI 时代让“产出”变得廉价，因此本知识库的大多数内容（尤其是知识点部分）坚持由我个人手写完成；**由 AI 完全生成的内容会在标题上标注 `*`**，仅作索引参考。内容难免存在疏漏或局限，欢迎通过 [Issues](https://github.com/lelyetia/lelyetia-knowledge/issues) 指正或补充。
3. **排版风格**：由于绝大部分内容为纯手敲，正文中的 Markdown 修饰（如加粗等）会相对克制，仅在必要时使用。
4. **交流与支持**：如果本知识库对你有帮助，欢迎关注[我的 GitHub](https://github.com/lelyetia) 并给本项目点个 [Star](https://github.com/lelyetia/lelyetia-knowledge)。计算机社区的开源精神让许多优质学习资源得以免费获取；如果觉得内容有帮助，也欢迎通过下方方式交流或打赏支持。

| 微信联系方式 | 微信收款码 | 支付宝收款码 |
| :---: | :---: | :---: |
| <a href="docs/assets/images/main_page/微信联系方式.jpg"><img src="docs/assets/images/main_page/微信联系方式.jpg" alt="微信联系方式" width="160"></a> | <a href="docs/assets/images/main_page/微信收款码.jpg"><img src="docs/assets/images/main_page/微信收款码.jpg" alt="微信收款码" width="160"></a> | <a href="docs/assets/images/main_page/支付宝收款码.jpg"><img src="docs/assets/images/main_page/支付宝收款码.jpg" alt="支付宝收款码" width="160"></a> |

---

## 本地预览与维护

### 首次启动

先安装 Python 3（需包含 `pip` 和 `venv`），然后在终端进入本仓库根目录（包含 `mkdocs.yml` 的目录）。

#### Linux / macOS

```bash
cd /你的路径/Lelyetia-knowledge
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m mkdocs serve
```

#### Windows（PowerShell）

```powershell
cd C:\你的路径\Lelyetia-knowledge
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python -m mkdocs serve
```

启动后，在浏览器打开 **<http://127.0.0.1:8000/lelyetia-knowledge/>**（具体地址以终端的 `Serving on` 输出为准）。修改并保存 `docs/` 下的笔记后，预览页面会自动刷新。终端需保持运行，按 **Ctrl+C** 停止服务。

如果 Windows 阻止执行激活脚本，可以直接使用虚拟环境中的 Python：

```powershell
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m mkdocs serve
```

### 以后每次启动

依赖安装过后，只需进入仓库、激活虚拟环境并启动：

```bash
cd /你的路径/Lelyetia-knowledge
source .venv/bin/activate
python -m mkdocs serve
```

Windows 将激活命令替换为 `.\.venv\Scripts\Activate.ps1`，也可直接运行 `.\.venv\Scripts\python.exe -m mkdocs serve`。只有新建环境或更新 `requirements.txt` 后，才需要重新执行 `python -m pip install -r requirements.txt`。

### 目录结构与添加笔记

```text
Lelyetia-knowledge/
├── .github/workflows/deploy.yml  # GitHub Actions 自动测试与部署工作流
├── README.md                     # 项目介绍与本地维护说明
├── requirements.txt              # Python 依赖
├── mkdocs.yml                    # 网站名称、主题、导航和扩展配置
├── hooks/                        # MkDocs 钩子（笔记版本记录解析）
├── templates/                    # 笔记模板
├── tests/                        # 版本记录规则单元测试
└── docs/
    ├── main_page.md              # 知识库介绍与首页正文
    ├── index.html                # 根目录入口，自动跳转至介绍页
    ├── practical-tools/          # 实用工具与软件索引
    ├── research-tools/           # 科研工具
    ├── llm_application/          # 大模型技术与应用
    ├── learning-resources/       # 按学科归类的学习资源与课程笔记
    ├── assets/                   # 图片等静态资源
    ├── stylesheets/              # 自定义样式
    └── javascripts/              # MathJax 数学公式配置
```

- 修改首页：编辑 `docs/main_page.md`。
- 添加笔记：在 `docs/` 对应目录下创建 Markdown 文件。
- 添加导航：在 `mkdocs.yml` 的 `nav` 中加入新页面，路径相对于 `docs/`，不需要写 `docs/` 前缀。例如：

```yaml
- 计算机科学基础:
    - (课程)CS50x: learning-resources/fundamentals-of-computer/CS50x.md
```

- 图片等资源放在 `docs/assets/`，在笔记中使用相对路径引用。

### 文内引用与参考资料

已启用 Markdown 脚注及悬停预览，无需安装额外的引用插件。正文中使用 `[^标识符]`，在文末统一写来源：

```markdown
这里是根据课程整理的内容。[^cs50]
同一来源可以再次引用。[^cs50]

## 参考资料

[^cs50]: Harvard University. [CS50x](https://cs50.harvard.edu/x/) [在线课程]. 访问日期：2026-11-03。
```

页面会显示上标 `[1]`，悬停或聚焦可查看来源，点击可跳到文末；文末的返回箭头可回到引用处。同一标识符复用同一个编号。编号按文末定义的顺序生成，建议按正文首次引用的顺序排列定义。

网页记录作者或机构、标题、链接与访问日期；书籍补充版本、章节或页码，论文补充 DOI 或公开链接。逐字摘录可放入 `>` 引用块并附来源，转述则在对应句子或段落末尾标注。可复用 `templates/note-with-references.md`，现有示例位于 `docs/learning-resources/fundamentals-of-computer/CS50x.md`。

### 笔记版本与更新记录

每篇笔记的文末保留一个“版本记录”表格，记录版本号、更新日期和更新概述。网站会自动读取其中的最新版本，在笔记标题下显示当前版本和最后更新日期，无需另外维护页首信息。

```markdown
## 版本记录 {#version-history}

| 版本号 | 更新日期 | 更新概述 |
| --- | --- | --- |
| v0.2.0 | 2026-11-03 | 补充示例并修正术语。 |
| v0.1.0 | 2026-11-03 | 建立笔记。 |
```

更新笔记后，在表格最上方新增一行，保留旧记录。版本号使用 `v主版本.次版本.修订号`，例如 `v0.1.1`、`v0.2.0`、`v1.0.0`；系统按三个数字比较版本，新版本的日期不得早于旧版本。同一天可以更新多个版本。表格放在正文与参考资料之后，概述中的竖线写成 `\|`。

新笔记可以复制 `templates/note.md`，需要引用的笔记使用 `templates/note-with-references.md`，并将模板中的 `YYYY-MM-DD` 替换为实际日期。缺失记录、无效日期、重复版本号或缺少概述会在构建时提示具体文件与原因。

### 代码块样式

所有代码块统一使用左上角红、黄、绿三个圆点的窗口样式，并支持语法高亮和复制按钮。继续使用普通围栏代码块即可，也可填写文件名：

````markdown
```python title="example.py"
print("Hello, world!")
```
````

修改 `hooks/note_versions.py` 后需重新启动 `python -m mkdocs serve` 才会生效。

### 构建与自动部署

在已激活虚拟环境的仓库根目录运行：

```bash
python -m mkdocs build
```

生成的网站位于 `site/`（已加入 `.gitignore`）。版本规则的自动检查可运行 `python -m unittest discover -s tests`，完整严格检查可运行 `python -m mkdocs build --strict`。

`mkdocs.yml` 中的 `site_url` 用于配置网站正式地址，本地预览仍使用终端输出的地址。推送到 `main` 分支后，会由 `.github/workflows/deploy.yml` 自动运行测试、严格构建并部署到 GitHub Pages（需在仓库 **Settings → Pages** 中将部署来源设为 **GitHub Actions**）；本地启动和构建不受部署配置影响。

### 常见问题

| 情况 | 处理方法 |
| --- | --- |
| 提示 `No module named mkdocs` 或缺少 `material` 主题 | 确认已激活 `.venv`，然后执行 `python -m pip install -r requirements.txt`。 |
| 提示找不到 `mkdocs.yml` | 先进入仓库根目录，再运行启动命令。 |
| 默认端口被占用 | 使用 `python -m mkdocs serve -a 127.0.0.1:8001`，然后访问 <http://127.0.0.1:8001/lelyetia-knowledge/>。 |
| Linux 创建虚拟环境时提示缺少 `venv` 或 `ensurepip` | 安装系统对应的 Python venv 软件包后重试，例如 Ubuntu / Debian 的 `python3-venv`。 |
| 数学公式没有渲染 | 当前配置从 `unpkg.com` 加载 MathJax，检查浏览器能否访问该地址。 |

退出虚拟环境可运行 `deactivate`。
