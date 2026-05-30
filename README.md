ai 相关笔记，使用 [Quartz](https://quartz.jzhao.xyz/) 发布网页。大致流程为：

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

创建 `.github/workflows/deploy.yml` ，内容见[链接](https://quartz.jzhao.xyz/hosting#github-pages) 。

然后直接用 git 提交即可。