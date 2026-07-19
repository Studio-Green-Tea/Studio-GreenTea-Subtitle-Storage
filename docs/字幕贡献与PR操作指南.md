# 绿茶字幕组：字幕贡献与 Pull Request 操作指南

本文面向第一次使用 GitHub 的字幕组成员，所有步骤都可以在 GitHub 网页中完成，不需要安装 Git，也不需要输入命令。

适用仓库：[Studio-GreenTea-Subtitle-Storage](https://github.com/Studio-Green-Tea/Studio-GreenTea-Subtitle-Storage)

## 一、先理解几个词

| 名称 | 简单解释 | 在本仓库中的作用 |
| --- | --- | --- |
| 仓库（Repository） | 存放文件和修改记录的项目 | 保存字幕、README 和反馈模板 |
| `main` | 仓库的正式主分支 | 这里的内容视为当前正式版本 |
| 分支（Branch） | 从 `main` 复制出来的一条临时修改线 | 新增或修改字幕时，在自己的分支中操作，不直接碰正式版本 |
| 提交（Commit） | 保存一次修改并写下说明 | 类似“保存一个有说明的版本” |
| Pull Request（PR） | 请求把分支中的修改合并到 `main` | 让其他成员检查字幕、文件名和修改内容 |
| 审核（Review） | 其他成员检查 PR | 可以批准、提出修改要求或留言讨论 |
| 合并（Merge） | 把通过审核的修改加入 `main` | 合并后才成为正式版本 |

可以把整个过程理解为：

```text
正式版本 main
    ↓ 创建临时分支
在分支中上传或修改字幕
    ↓ 提交 Pull Request
另一名成员审核
    ↓ 审核通过并合并
修改进入 main，成为正式版本
```

需要特别注意：这是公开仓库，因此分支和 PR 也能被公众看到；“临时分支”表示内容尚未进入正式 `main`，不表示内容是私密的。

## 二、为什么不能直接修改 `main`

两个仓库的 `main` 都已经受到保护。日常修改必须通过 PR，原因包括：

- 防止误删或覆盖正式字幕；
- 让另一名成员检查错字、错译、时间轴和文件路径；
- 保留清楚的修改原因和讨论记录；
- 出现问题时更容易找到是哪一次修改造成的。

两位 Owner 拥有紧急绕过权限，但只应在严重且紧急、无法正常走 PR 的情况下使用。普通上传和修正仍然必须走 PR。

## 三、开始前的准备

1. 登录自己的 GitHub 账号，并确认自己仍是 `Studio-Green-Tea` 组织成员。
2. 打开[字幕存储仓库](https://github.com/Studio-Green-Tea/Studio-GreenTea-Subtitle-Storage)。
3. 阅读仓库根目录的 [README](../README.md) 和组织的[贡献指南](https://github.com/Studio-Green-Tea/.github/blob/main/CONTRIBUTING.md)。
4. 在本地准备好要上传或修改的 `.ass` 文件。
5. 确认不会上传视频、封装成品、未经授权的字体、图片或其他第三方文件。
6. 一次 PR 尽量只处理一部作品或一类问题。不同作品、不同目的的修改应分别建立分支和 PR。

## 四、每次操作都先创建分支

无论是上传新字幕还是修改旧字幕，都建议先创建分支。

### 1. 打开分支选择器

进入仓库首页后，在文件列表上方找到显示 `main` 的按钮。这个按钮就是分支选择器。

### 2. 输入新分支名称

点击 `main`，在搜索框中输入新的分支名称。建议使用英文、数字、短横线和斜线，不要使用空格。

推荐格式：

```text
add/作品英文名-集数
fix/作品英文名-集数-问题
docs/说明内容
```

例如：

```text
add/example-anime-03
fix/example-anime-03-timing
fix/example-anime-05-translation
```

### 3. 从 `main` 创建分支

点击类似下面的选项：

```text
Create branch: 分支名称 from 'main'
```

创建完成后，检查文件列表上方的分支按钮。它必须显示刚刚创建的分支名称，而不是 `main`。

> 每个新任务都应创建新分支。PR 合并后，不要继续使用旧分支处理下一项任务。

## 五、上传一部作品的新字幕

下面假设要把某部 2026 年 TV 动画的第 03 集字幕上传到仓库。

### 情况 A：作品目录已经存在

1. 确认当前选中的是刚创建的 `add/...` 分支。
2. 依次进入 `TV`、年份和作品目录，例如：

   ```text
   TV/2026/Example Anime/
   ```

3. 点击右上方的 `Add file`。
4. 选择 `Upload files`。
5. 把准备好的 `.ass` 文件拖入网页，或者点击 `choose your files` 选择文件。
6. 等待文件上传完毕，检查页面列出的文件名和目标目录。
7. 在 `Commit message` 中写清楚本次操作，例如：

   ```text
   Add Example Anime episode 03 subtitles
   ```

8. 确认提交目标是当前分支，然后点击 `Commit changes`。

### 情况 B：作品目录还不存在

GitHub 不能保存空目录，因此先用作品说明文件建立目录：

1. 确认当前选中的是刚创建的 `add/...` 分支。
2. 进入正确的类型和年份目录，例如 `TV/2026/`。
3. 点击 `Add file` → `Create new file`。
4. 在文件名输入框中填写：

   ```text
   Example Anime/README.md
   ```

   输入斜线后，GitHub 会自动创建 `Example Anime` 目录。

5. 在 README 中简单填写作品名称、字幕类型或其他必要说明。
6. 填写提交说明，例如：

   ```text
   Add Example Anime directory
   ```

7. 点击 `Commit changes`，并确认提交到当前分支。
8. 打开刚建立的作品目录，再按照“情况 A”的方法上传字幕文件。

同一个分支可以有多次 Commit；这些提交会自动出现在同一个 PR 中。

### 上传后必须检查

- 年份和作品目录是否正确；
- 文件名是否符合仓库 README 中的命名规范；
- 集数是否正确，例如 `[03]`，不要误写成 `[3]`；
- `JPSC` 和 `JPTC` 是否标记正确；
- 是否误传了视频、字体、压制成品、临时文件或备份文件；
- 简繁字幕都应发布时，是否遗漏其中一个版本；
- 文件内容、编码、字体名称和时间轴是否保持正常。

## 六、修改已经存在的字幕

修改前同样需要创建新的 `fix/...` 分支，并确认当前分支不是 `main`。

### 方法 A：在 GitHub 网页中直接修改少量文字

适合修改一两个错字、标点或短句。

1. 在正确的 `fix/...` 分支中打开字幕文件。
2. 点击右上方的铅笔图标 `Edit this file`。
3. 找到需要修改的字幕行并完成修改。
4. 不要顺便调整无关内容，也不要让编辑器自动改写整个文件。
5. 点击 `Commit changes`。
6. 填写明确的提交说明，例如：

   ```text
   Fix episode 03 translation at 00:12:34
   ```

7. 确认提交到当前 `fix/...` 分支。

如果页面没有铅笔图标，或者文件太大不方便编辑，请使用方法 B。

### 方法 B：在本地修改后上传替换

适合使用 Aegisub 修改翻译、时间轴、样式或大量字幕行。

1. 下载仓库中当前版本的字幕，或者确认本地文件是从当前 `main` 版本修改而来。
2. 使用 Aegisub 等工具完成修改并保存。
3. 尽量保留原文件名、编码、样式和目录位置。
4. 在 GitHub 中切换到自己的 `fix/...` 分支。
5. 进入原字幕所在目录。
6. 点击 `Add file` → `Upload files`。
7. 上传与原文件同名的新版本。GitHub 会把它识别为对现有文件的修改。
8. 填写提交说明并点击 `Commit changes`。

### 如果需要重命名或移动文件

- 重命名文本文件时，可以点击铅笔图标，然后修改页面上方的文件名；
- 也可以在同一个分支中删除旧文件，再把文件上传到新位置；
- 提交 PR 前必须确认旧文件已经删除，避免仓库中同时留下两个版本；
- PR 说明中必须写明旧路径和新路径。

### 修改后必须检查

- PR 的 `Files changed` 页面是否只出现计划修改的文件；
- 是否因为编码或换行符变化，导致整份字幕都显示为被修改；
- 修改前后的台词是否写在 PR 说明中；
- 时间轴问题是否标明时间点；
- 翻译修改是否附上理由或参考来源；
- 同一问题是否也影响简体或繁体的另一份字幕。

如果只修改了一句话，却看到整份文件几乎每一行都变成红色和绿色，请先不要提交 PR。这通常表示编码、换行符或保存方式发生了变化，应检查后重新保存。

## 七、创建 Pull Request

完成上传或修改后，需要申请把分支合并到 `main`。

### 方法 A：使用仓库顶部提示

推送 Commit 后，仓库顶部通常会出现黄色或绿色提示条。点击 `Compare & pull request`。

### 方法 B：从 Pull requests 页面创建

1. 点击仓库顶部的 `Pull requests`。
2. 点击 `New pull request`。
3. 确认方向如下：

   ```text
   base: main  ←  compare: 你的分支
   ```

   `base` 必须是 `main`，`compare` 必须是你刚才修改字幕的分支。

4. 点击 `Create pull request`。

### 填写 PR 标题

标题应让审核者一眼看懂目的。例如：

```text
[新增字幕] Example Anime 第03集
[字幕修正] Example Anime 第03集 00:12:34 错译
[时间轴修正] Example Anime 第05集
[目录调整] Example Anime 文件命名
```

### 填写 PR 内容

仓库会自动显示 PR 模板。请完整填写：

- 改动类型；
- 作品与集数；
- 文件路径；
- 时间点；
- 原内容和修改后内容；
- 修改理由或参考来源；
- 提交前确认选项。

不要只写“修复字幕”“更新文件”之类无法判断内容的说明。

填写完成后点击 `Create pull request`。此时只是创建审核请求，内容还没有进入 `main`。

## 八、其他成员如何审核 PR

当前保护规则要求至少一名其他成员批准，PR 作者不能批准自己的 PR。

审核者应执行以下步骤：

1. 打开 PR。
2. 阅读 `Conversation` 中的修改说明。
3. 点击 `Files changed` 检查实际变化。
4. 可以点击具体字幕行旁边的 `+` 留言。
5. 点击右上方的 `Review changes`。
6. 选择一种审核结果：

   - `Comment`：只留言，不批准也不拒绝；
   - `Approve`：确认修改可以合并；
   - `Request changes`：要求修改后再审核。

7. 填写审核意见并提交 Review。

### 作者收到修改意见后怎么办

作者不需要关闭 PR，也不需要创建新 PR。只要继续在原来的分支中修改或上传文件，新 Commit 会自动加入现有 PR。

需要注意当前仓库规则：

- 新 Commit 会使之前的批准失效，需要重新审核；
- 最后一次推送必须由另一名没有进行该次推送的成员批准；
- 所有审核讨论都必须解决，PR 才能合并；
- 修改完成后，可以在对应讨论中回复，并由合适的成员点击 `Resolve conversation`。

## 九、审核通过后合并

当 PR 至少获得一名其他成员批准、没有未解决讨论，并且没有冲突时，合并按钮会变为可用。

建议使用：

```text
Squash and merge
```

它会把分支中的多次小 Commit 整理成 `main` 中的一次完整修改，历史更容易阅读。

合并步骤：

1. 点击合并按钮右侧的小箭头。
2. 选择 `Squash and merge`。
3. 检查最终标题和说明。
4. 点击确认合并。
5. 合并完成后点击 `Delete branch` 删除已经使用完的临时分支。

删除已合并分支不会删除进入 `main` 的字幕。

如果合并按钮不可用，请查看页面提示，常见原因包括：

- 还没有其他成员批准；
- 新 Commit 导致旧批准失效；
- 仍有未解决的讨论；
- 分支与 `main` 存在冲突；
- PR 仍处于 Draft 状态。

## 十、完整示例：上传新字幕

目标：上传 `Example Anime` 第 03 集简繁字幕。

1. 打开仓库并从 `main` 创建分支 `add/example-anime-03`。
2. 确认分支选择器显示 `add/example-anime-03`。
3. 进入 `TV/2026/Example Anime/`。
4. 上传：

   ```text
   [Studio GreenTea] Example Anime [03][WebRip][1080p].JPSC.ass
   [Studio GreenTea] Example Anime [03][WebRip][1080p].JPTC.ass
   ```

5. Commit message 填写 `Add Example Anime episode 03 subtitles`。
6. 创建 PR，标题填写 `[新增字幕] Example Anime 第03集`。
7. 在 PR 模板中填写作品、路径、字幕类型和检查结果。
8. 请另一名成员检查 `Files changed` 并选择 `Approve`。
9. 使用 `Squash and merge` 合并。
10. 删除 `add/example-anime-03` 分支。

## 十一、完整示例：修正现有字幕

目标：修正第 03 集 `00:12:34` 的错译。

1. 从 `main` 创建分支 `fix/example-anime-03-translation`。
2. 打开第 03 集字幕，用网页编辑器修改，或使用 Aegisub 修改后上传同名文件。
3. Commit message 填写 `Fix episode 03 translation at 00:12:34`。
4. 创建 PR，标题填写 `[字幕修正] Example Anime 第03集 00:12:34 错译`。
5. 在 PR 中写明：

   ```text
   修改前：原台词
   修改后：新台词
   修改原因：翻译理由或参考来源
   ```

6. 请另一名成员审核并批准。
7. 解决所有讨论后，使用 `Squash and merge` 合并。
8. 删除临时分支。

## 十二、常见问题

### 1. 我不会修改文件，只发现了问题

不需要创建 PR，直接提交[问题反馈](https://github.com/Studio-Green-Tea/Studio-GreenTea-Subtitle-Storage/issues/new?template=problem-feedback.yml)，写明作品、集数、文件路径和时间点即可。

### 2. 我不小心选中了 `main`

不要继续上传。返回仓库首页，按照本文第四节创建新分支，再在新分支中操作。受保护的 `main` 通常会阻止直接修改。

### 3. PR 创建后又发现错误

继续修改同一个分支即可，现有 PR 会自动更新。不要重复创建第二个 PR。更新后需要请其他成员重新审核。

### 4. 为什么别人已经批准，还是不能合并

检查批准后是否又有新 Commit。新提交会使旧批准失效；请另一名成员重新检查并批准。还要确认所有讨论已经解决。

### 5. GitHub 显示冲突（Conflicts）

说明你的分支和最新 `main` 修改了相同位置。不要随意选择保留某一边，以免覆盖字幕。请联系 Owner 或熟悉 GitHub 的成员处理。

### 6. 上传后发现路径或文件名错误

在同一分支中移动、重命名或重新上传文件，然后再创建 PR；如果 PR 已经创建，修改会自动进入该 PR。

### 7. PR 为什么所有人都能看到

字幕仓库是公开仓库，因此分支、Commit、PR 和讨论都是公开的。请勿在文件或说明中填写密码、Cookie、访问令牌、私人联系方式等敏感信息。

## 十三、提交前最终检查表

### 新字幕

- [ ] 当前分支不是 `main`
- [ ] 年份、作品目录和集数正确
- [ ] 文件名符合仓库规范
- [ ] `JPSC`、`JPTC` 标记正确
- [ ] 没有上传视频、字体、压制成品或临时文件
- [ ] 简繁版本没有遗漏
- [ ] PR 标题和说明完整

### 字幕修正

- [ ] 当前分支不是 `main`
- [ ] 只修改了计划中的字幕和内容
- [ ] PR 中写明时间点、修改前后内容和理由
- [ ] 没有因编码或换行符导致整份文件无意义变化
- [ ] 已检查对应的简体或繁体字幕是否也需要同步修正
- [ ] PR 已由另一名成员审核
- [ ] 所有讨论都已解决

## 十四、相关入口

- [字幕存储仓库](https://github.com/Studio-Green-Tea/Studio-GreenTea-Subtitle-Storage)
- [提交问题反馈](https://github.com/Studio-Green-Tea/Studio-GreenTea-Subtitle-Storage/issues/new?template=problem-feedback.yml)
- [查看 Pull Requests](https://github.com/Studio-Green-Tea/Studio-GreenTea-Subtitle-Storage/pulls)
- [贡献指南](https://github.com/Studio-Green-Tea/.github/blob/main/CONTRIBUTING.md)
