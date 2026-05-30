ai 方向的笔记，使用 [Quartz](https://quartz.jzhao.xyz/) 发布网页。

### Website

https://plerks.github.io/ai-notes/

### 配置流程

```shell
# 1. Clone the Quartz repository
git clone https://github.com/jackyzha0/quartz.git <repo-name>
cd quartz
 
# 2. Install dependencies
npm i
 
# 3. Initialize your site (choose a template, set your base URL, import content)
npx quartz create
 
# 4. Install plugins referenced by your chosen template
# 此时有 Default, Obsidian, TTRPG, Blog 四个选项，选 Default ，实测选 Obsidian 公式渲染会有问题
npx quartz plugin install --from-config
 
# 5. Preview your site locally
# 本地 preview 地址为 <http://localhost:8080>
npx quartz build --serve
```

markdown 笔记内容要置于 `content/` 文件夹下，本地写笔记可以用 [Obsidian](https://obsidian.md/)。

此时要把 `.git` 文件夹删掉，因为一开始是 clone 的 quartz 官方仓库，不需要那个 commit 记录。

### 网页自动发布

在仓库的 Settings -> Pages -> Build and deployment -> Source 下，选择 **Github Actions** 。

创建 `.github/workflows/deploy.yml` ，内容见[链接](https://quartz.jzhao.xyz/hosting#github-pages) ，不过要改下 on-push 触发构建的分支名为自己的分支（官网配置的分支叫 v5）。

在 [quartz.config.yaml](https://quartz.jzhao.xyz/configuration) 中，设置 baseUrl 为仓库链接（重要！不然 quartz 生成的链接会不对）

后续写好笔记后直接用 git 提交即可。