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
