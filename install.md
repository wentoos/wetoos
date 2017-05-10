# 命令行安装插件  

### 1. git 和 curl atom安装  
    在命令行中书写 sudo apt-pet install git curl atom 就ok了，如没有软件包，
    输入sudo apt-get update获取一下软件列表就行了  
  ***
### 2. 安装 nvm nodejs管理工具  
 安装 nvm 命令行  
 - curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash  
 - 官网网址  https://github.com/creationix/nvm#install-script  

### 3. 安装nodejs  
 - 用nvm获取nodejs版本  
  在终端输入命令：nvm ls-remote  
- 使用命令nvm install [node版本号]  
安装完成  
- 切换版本  
使用 nvm use [node版本号]切换版本  
****
### 使用Facebook的create-react-app快速构建React开发环境
- 安装create-react-app的方式也非常简单，可以直接使用npm命令进行全局安装。

- npm install -g create-react-app  
- create-react-app my-app  
- cd my-app/  
- npm start  
执行完上述命令之后，你可以直接打开http://localhost:3000，即可以看到你React APP的运行效果。此时也是处于开发模式下，如果你要进行发布，则使用npm run build进行编译。
