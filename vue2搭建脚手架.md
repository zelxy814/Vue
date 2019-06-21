## 首先要先安装node.js。  
- 因为是window系统所以，直接在官网下载安装包直接安装完即可在命令行输入 node -v如果有一下显示则安装成功：  `node -v`
## 现在node自带npm
`所以这里输入npm -v 也可以直接看到npm版本`
## 接下来安装cnpm,淘宝镜像
- 因为我们接下来需要安装很多依赖和插件都是需要从国外服务器下载。所以我们安装淘宝的镜像，这样可以提升速度。  
` npm install -g cnpm --registry=https://registry.npm.taobao.org`
-  安装淘宝镜像如果出现：if using 2.x branch,please upgrade to at least 2.1.6 to avoid a serious bug with socket..  
- 这里需要降低npm版本 具体命令： `npm install npm@4.6.1 -g`
- 然后在更新npm 版本  ：`npm update -d `
- 再重新安装镜像：`npm install -g cnpm --registry=https://registry.npm.taobao.org`
- 再重新输入 `cnpm -v`  如果出现以下提示则cnpm安装完毕：  
## 安装 webpack  命令  
`npm install webpack -g`
`webpack -v`
## 安装vue-cli  命令
`npm install vue-cli -g`
`vue -V` V是大写  
## 用vue-cli 来构建我们的项目
- `vue init webpack myproject`       --------------  myproject 是自定义的项目名称  
- `Project name (myproject )` ---------------------项目名称  
- `Project name myproject` 
- `Project description (A Vue.js project)` ---------------------项目描述  
- `Project description A Vue.js project`
- `Author Datura` --------------------- 项目创建者  
- `Author Datura`
- `Vue build (Use arrow keys)`
- `Vue build standalone`
- `Install vue-router? (Y/n)` --------------------- 是否安装Vue路由   
- `Install vue-router? Yes`
- `Use ESLint to lint your code? (Y/n) n` ---------------------是否启用eslint检测规则，这里个人建议选no  
- `Use ESLint to lint your code? No`
- `Setup unit tests with Karma + Mocha? (Y/n)`
- `Setup unit tests with Karma + Mocha? Yes`
- `Setup e2e tests with Nightwatch? (Y/n)`
- `Setup e2e tests with Nightwatch? Yes`
## 启动项目
cd到当前项目下 `npm dev run`
