---
title:  iterm2 配置字体
tags: Iterm2
date: 2019-05-21 17:31:29
---

##### 1. 首先安装`iTerm2`
- [GitHub](https://github.com/gnachman/iTerm2)
##### 2. 安装powerline
```ruby
 // 没有安装pip先安装pip
 sudo easy_install pip
 
 // 之后安装powerline（这里可能会报错， 可以参考问题解决）
 pip install powerline-status
```
##### 3.安装oh-my-zsh
```ruby
curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```
##### 6.安装字体库[fonts](https://github.com/powerline/fonts)
``````ruby
// 克隆字体库到本地
git clone https://github.com/powerline/fonts.git

// 安装字体
cd fonts 
./install.sh
``````
安装成功之后输出：
``````ruby
copying fonts...
Powerline fonts installed to /Users/slash/Library/Fonts
``````
##### 7.导入配色
- 首先下载[solarized](https://github.com/altercation/solarized)
``````ruby
git clone https://github.com/altercation/solarized
``````
- 解压zip文件， 进入solarized、iterm2-colors-solarized文件， 双击Solarized
  Dark.itermcolors和Solarized Light.itermcolors进行安装导入，如下图所示
  ![1637e1a0a8980e6e?imageslim](https://user-gold-cdn.xitu.io/2018/5/20/1637e1a0a8980e6e?imageslim)
- 进入系统偏好设置， profiles->Colors选择刚刚导入的配色方案即可
  ![1](https://user-gold-cdn.xitu.io/2018/5/20/1637e1a0a8c30214?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
##### 8.主题设置
- 使用agnoster， 下载安装：
``````ruby
// 克隆主题到本地
git clone  https://github.com/fcamblor/oh-my-zsh-agnoster-fcamblor


//安装主题
cd oh-my-zsh-agnoster-fcamblor
./install

``````
- 安装成功之后， open ~/.zshrc文件， 将ZSH_THEME改为agnoster
`````` ruby
# Set name of the theme to load. Optionally, if you set this to "random"
# it'll load a random theme each time that oh-my-zsh is loaded.
# See https://github.com/robbyrussell/oh-my-zsh/wiki/Themes
ZSH_THEME="agnoster"
``````
- 更改完成之后需要保存
`````` ruby
chsh -s /bin/zsh
``````
##### 9. 添加指令高亮效果[zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
- 下载文件
`````` ruby 
// 克隆项目到本地
git clone git://github.com/zsh-users/zsh-syntax-highlighting.git
``````

- open ~/.zshrc文件，在最后添加如下内容
`````` ruby
source /Users/slash（替换成自己的名称）/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
plugins=(zsh-syntax-highlighting)
``````
- 最后别忘了要保存修改的内容
`````` ruby
chsh -s /bin/zsh
``````