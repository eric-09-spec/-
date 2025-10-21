# 健康金融游戏 - 多设备访问指南

本文档提供了多种方法，让你可以在多台电脑上展示和访问这个健康金融游戏程序。

## 方法一：文件共享

最简单的方法是直接共享HTML文件：

1. **通过电子邮件/云存储分享**
   - 将`index.html`文件通过电子邮件发送给他人
   - 上传到百度网盘、阿里云盘等云存储服务，分享链接
   - 接收方下载后，双击文件即可在浏览器中打开

2. **局域网文件共享（Windows）**
   - 右键点击`游戏`文件夹 → 属性 → 共享选项卡
   - 点击「共享」按钮，添加要共享的用户
   - 设置权限为「读取」或「读取/写入」
   - 其他局域网内的电脑可以通过「网络」访问共享文件夹

## 方法二：使用本地服务器

使用简单的HTTP服务器可以让同一网络内的多台设备访问：

### 选项1：使用Python内置服务器（推荐）

1. 确保你的电脑已安装Python
2. 打开命令提示符（CMD）
3. 导航到游戏文件夹：
   ```
   cd c:\Users\王誉\Desktop\游戏
   ```
4. 运行以下命令启动服务器：
   ```
   # Python 3.x
   python -m http.server 8000
   ```
5. 查看你的电脑IP地址（运行`ipconfig`命令）
6. 其他设备在浏览器中输入：`http://你的IP地址:8000`

### 选项2：使用Node.js的http-server

1. 安装Node.js
2. 打开命令提示符，运行：
   ```
   npm install -g http-server
   ```
3. 导航到游戏文件夹并启动服务器：
   ```
   cd c:\Users\王誉\Desktop\游戏
   http-server -p 8000
   ```

## 方法三：部署到云服务

### 选项1：GitHub Pages（免费）

1. 在GitHub上创建一个新仓库
2. 将`index.html`文件上传到仓库
3. 在仓库设置中启用GitHub Pages
4. GitHub会提供一个公开URL，任何人都可以访问

### 选项2：使用GitHub Pages（免费）

GitHub Pages是GitHub提供的免费静态网站托管服务，非常适合托管我们的游戏页面：

1. **准备工作**：
   - 确保你有GitHub账号
   - 在电脑上安装Git

2. **创建GitHub仓库**：
   - 登录GitHub，点击右上角的「+」按钮，选择「New repository」
   - 填写仓库名称（例如：health-finance-game）
   - 设置仓库可见性（公开或私有都可以）
   - 点击「Create repository」

3. **将本地代码上传到GitHub**：
   - 在游戏文件夹中右键点击，选择「Git Bash Here」
   - 运行以下命令：
     ```bash
     git init
     git add .
     git commit -m "Initial commit"
     git remote add origin https://github.com/你的用户名/health-finance-game.git
     git push -u origin master
     ```

4. **启用GitHub Pages**：
   - 进入GitHub仓库页面
   - 点击「Settings」→「Pages」
   - 在「Build and deployment」部分，选择「Source」为「Deploy from a branch」
   - 选择「Branch」为「master」（或「main」），点击「Save」
   - 稍等几分钟，页面会显示你的网站URL

5. **访问你的游戏**：
   - 复制GitHub Pages提供的URL
   - 在任何电脑的浏览器中粘贴访问

### 解决GitHub Actions依赖锁文件问题

如果你在GitHub Actions中遇到"找不到依赖关系锁文件"的错误，这是因为我们的项目是纯静态HTML/CSS/JS项目，不需要npm/yarn依赖，以下是解决方案：

1. **已创建GitHub Actions配置**：我已经为你创建了一个特殊配置的工作流文件 `.github/workflows/pages.yml`，它会：
   - 跳过依赖安装步骤
   - 直接部署静态文件
   - 使用GitHub Pages的官方部署工具

2. **创建了.gitignore文件**：添加了标准的.gitignore文件，确保不会提交不必要的文件

3. **部署步骤**：
   - 确保你已经将所有文件（包括`.github`文件夹）推送到GitHub仓库
   - 在GitHub仓库设置中启用GitHub Pages
   - 当你推送到master/main分支时，Actions会自动部署你的网站

4. **手动部署选项**：如果你不想使用Actions，也可以通过GitHub页面的"Deploy from a branch"选项直接部署，无需依赖锁文件

### 选项3：使用Netlify（免费）

1. 访问[Netlify官网](https://www.netlify.com/)
2. 创建账户并登录
3. 拖拽`游戏`文件夹到Netlify界面
4. Netlify会自动部署并提供一个公开URL

### 选项3：使用云服务器（如阿里云、腾讯云）

1. 购买云服务器并设置
2. 将文件上传到服务器
3. 安装Web服务器（如Nginx、Apache）
4. 配置服务器指向游戏文件夹
5. 配置域名（可选）

## 方法四：使用在线HTML编辑器分享

一些在线HTML编辑器支持分享功能：

1. 将`index.html`的内容复制到在线编辑器（如JSFiddle、CodePen）
2. 使用编辑器的分享功能生成链接
3. 通过链接与他人分享

## 注意事项

1. **安全性**：使用本地服务器或云部署时，注意数据安全和访问权限
2. **性能**：在多设备同时访问时，可能需要考虑服务器性能
3. **兼容性**：确保各设备浏览器支持HTML5和CSS3特性
4. **离线访问**：如果需要离线使用，建议采用文件共享方法

## 最佳推荐

如果只是临时在几台电脑上展示，推荐使用「方法二：使用Python内置服务器」，简单快速。

如果需要长期稳定访问，推荐使用「方法三：部署到云服务」中的GitHub Pages或Netlify。

---

希望这份指南对你有所帮助！如果有任何问题，请随时咨询。