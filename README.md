# OsPreferences

|方面|名称|链接|描述|
| -------------------------| -----------------------------| -----------------| -----------------|
|Font|`Ubuntu Mono`|[https://design.ubuntu.com/font](https://design.ubuntu.com/font)||
|Font|字魂正文宋楷|||
|Font|`OPPO Sans 4.0`|[https://www.coloros.com/article/A00000074](https://www.coloros.com/article/A00000074)||
|Gtk|`Andromeda`|[https://www.pling.com/p/2039961](https://www.pling.com/p/2039961)||
|Icons|`Azure Glassy Dark Icons`|[https://www.pling.com/p/2154036](https://www.pling.com/p/2154036)||
|Icons|`Elysia`|[https://www.pling.com/p/2167806](https://www.pling.com/p/2167806)|*cursor*|
|Python|`Poetry`|[https://python-poetry.org](https://python-poetry.org)||
|Terminal|`Murex`|[https://murex.rocks](https://murex.rocks)||
|Terminal|`Rio`|[https://github.com/raphamorim/rio](https://github.com/raphamorim/rio)||
|Terminal|`Contour`|[https://github.com/contour-terminal/contour](https://github.com/contour-terminal/contour)||
|Terminal|`G`|[https://github.com/equationzhao/g](https://github.com/equationzhao/g)||
|Terminal|`Lf`|[https://github.com/gokcehan/lf](https://github.com/gokcehan/lf)||

### Rio

#### Q&A

- `ssh`连接退格异常：写`export TERM=xterm-256color`到`.bashrc`中

### Poetry

#### Configuration

**PATH**: `$HOME/.config/pypoetry/config.toml`

- `cache-dir`: `Poetry`缓存路径，*默认*`"$HOME/.cache/pypoetry"`
- `data-dir`: `Poetry`数据路径，*默认*`"$HOME/.local/share/pypoetry"`
- `virtualenvs`
  - `create`: 是否自动创建虚拟环境，*默认*`true`
  - `in-project`: 是否在项目根目录下建立虚拟环境`.venv`，*默认*`None`，表示`{cache-dir}/virtualenvs`
    > 如果设置为`false`，`Poetry`将忽略**任何**项目下的`.venv`文件夹。
  - `options`
    - `no-pip`: 创建虚拟环境的时候不下载`pip`，*默认*`false`
  - `path`: 虚拟环境目录，*默认*`"{cache-dir}/virtualenvs"`
  - `prompt`: 虚拟环境的提示词，*默认*`{project_name}-py{python_version}`

#### Environment

- `poetry new <PROJECT>`: 创建新项目`<PROJECT>`
  - `--flat`: *平铺*项目
  - `-i`(`--interactive`): 使用*交互模式*
  - `--python <PYTHON>`: 指定Python版本或路径
  - `--name <NAME>`: 指定项目名称
  - `--author <AUTHOR>`: 指定作者
  - `--description <DESCRIPTION>`: 项目描述
- `poetry init`: 初始化当前文件夹为`Poetry`项目
  - `--python <PYTHON>`: 指定Python版本或路径
  - `--name <NAME>`: 指定项目名称
  - `--author <AUTHOR>`: 指定作者
  - `--description <DESCRIPTION>`: 项目描述
- `poetry build [OPTIONS]`: 构建项目
  - `-o <DIR>`(`--output <DIR>`): 指定构建目录`<DIR>`，不指定*默认**`dist`*
  - `--clean`: 构建之前清除输出目录
  - `--format <sdist|wheel>`: 指定构建格式`sdist|wheel`
- `poetry env <COMMANDS>`: 管理虚拟环境
  - `activate`: 输出执行激活脚本的*SHELL*命令，**不激活脚本**
  - `use <PYTHON>`: 创建虚拟环境，通过*版本数字*或者*Python解释器的路径*指定`<PYTHON>`
  - `info`: 输出本虚拟环境的 信息
  - `list`: 输出与本项目相关的所有虚拟环境
  - `remove [--all] <ENV>`: 移除虚拟环境`<ENV>`
    - `[--all]`: 移除所有虚拟环境
- `poetry source <COMMAND>`: 管理仓库镜像，**影响范围为当前项目**
  - `add [--priority (primary|supplemental|explicit)] <SOURCE_NAME> <SOURCE_URL>`: 指定优先级为`priority`的镜像，其中 **`<SOURCE_NAME> != pypi`**
  - `show [<SOURCE_NAME>]`: 展示`[<SOURCE_NAME>]`的信息
  - `remove <SOURCE_NAME>`: 删除镜像`<SOURCE_NAME>`

#### Dependency

- `poetry add [OPTIONS] <PACKAGES>`: 添加依赖`<PACKAGES>`并下载
  - `<PACKAGES>`
    - `<PACKAGE>[EXTRAS][(==|>=|<=)<VERSION>]`: 特定版本
    - `<LOCAL_PACKAGE_PATH>`: 本地安装，*模式*必须符合`^(\.)+/.+`
    - `git+https://github.com/<USER>/<REPOSITORY>.git`: `GITHUB`发布页安装
  - `[OPTIONS]`
    - `-D`(`--dev`): 添加依赖到`DEV`环境
    - `-G <GROUP>`(`--group <GROUP>`): 添加依赖到组
    - `--optional`:
    - `--lock`: 只更新`.lock`文件，**不安装**
- `poetry update [OPTIONS] [<PACKAGES>]`: 更新依赖`[<PACKAGES>]`
  - `--with <GROUPS>`: 更新组中的依赖，多个组的写法有
  - `--without <GROUPS>`: 更新组之外的依赖
  - `--only`: **激活后忽略** **`--with`****和** **`--without`**
  - `--lock`: 只更新`.lock`文件，**不更新**
  - `--dry-run`(`--outdated`): 只列出依赖的变化，而不修改`.lock`
- `poetry remove [OPTIONS] <PACKAGES>`: 删除依赖`<PACKAGES>`
  - `-D`(`--dev`): 从`DEV`环境中删除依赖
  - `-G <GROUP>`(`--group <GROUP>`): 从组中删除依赖
  - `--dry-run`: 只列出依赖的变化，而不修改`.lock`
  - `--lock`: 只更新`.lock`文件，**不删除**
- `poetry install [OPTIONS]`: 从`.lock`文件中下载依赖，如果没有`.lock`则隐式执行`poetry lock`
  - `--with <GROUPS>`: 安装组中的依赖
  - `--without <GROUPS>`: 安装组之外的依赖
  - `--all-groups`: 安装全部组中的依赖
  - `--no-root`: 不安装组`default`中的依赖
  - `--dry-run`: 只列出依赖的变化，而不修改`.lock`
- `poetry show [OPTIONS] [<PACKAGES>]`: 列出当前工作空间中的依赖，可指定包`[<PACKAGES>]`
  - `-o`(`--outdated`): 展示过时依赖
  - `--tree`: 按树状结构展示依赖
  - `--with <GROUPS>`: 展示组中的依赖
  - `--without <GROUPS>`: 展示组之外的依赖
  - `--top-level`: 只输出顶层依赖
- `poetry lock [OPTIONS]`: 生成锁文件
  - `--regenerate`: 忽略已有的`.lock`，重新生成
- `poetry sync [OPTIONS]`: 同步当前环境依赖和锁文件，自动移除`.lock`中不存在的依赖
  - `--with <GROUPS>`: 下载组中的依赖
  - `--without <GROUPS>`: 忽略组中的依赖
  - `--all-groups`: 下载所有组中的依赖
  - `--no-root`: 不下载组`default`中的依赖
  - `--dry-run`: 只列出操作，而不修改`.lock`
- `poetry export [OPTIONS]`: 导出项目元数据为其他格式
  > *插件:*  *`poetry-plugin-export`*
  >
  > 当使用`pip`安装由`poetry export`导出的`requirements.txt`时，应该加上`--no-deps`参数，因为Poetry已经完成了所有依赖的解析工作。
  - `-o <FILENAME>`(`--output <FILENAME>`): 指定导出内容文件，不设置则输出到`stdout`
  - `-f <FORMAT>`(`--format <FORMAT>`): 指明文件格式，可选`requirements.txt`、`pylock.toml`
  - `--without-hashes`: 导出文件不包含哈希值
  - `--with <GROUPS>`: 包含组中的依赖
- `poetry cache <COMMAND>`: 管理项目依赖缓存
  - `clear --all`: 删除缓存
  - `list`: 列出构建的`wheel`缓存

#### Plugin

- [`poetry-plugin-export`](https://github.com/python-poetry/poetry-plugin-export): 导出`pyproject.toml`为`requirements.txt`或`pylock.toml`
- [`poetry-plugin-sort`](https://github.com/andrei-shabanski/poetry-plugin-sort): 在`poetry add`后*自动*排序`pyproject.toml`中的`dependencies`。提供`poetry sort`命令手动触发排序。

## Use

```shell
ln -s ~/Lokalius/OsPreferences/config/g ~/.config/g
ln -s ~/Lokalius/OsPreferences/config/trae/settings.json ~/.config/Trae/User/settings.json
ln -s ~/Lokalius/OsPreferences/config/pypoetry ~/.config/pypoetry
ln -s ~/Lokalius/OsPreferences/murex_profile ~/.murex_profile
ln -s ~/Lokalius/OsPreferences/profile ~/.profile
```
