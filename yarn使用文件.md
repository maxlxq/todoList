## Yarn

####为什么需要Yarn？

1. 当跨机器或用户安装依赖时，拉取依赖包消耗的时间较长（依赖网络）。
2. 在版本管理没用锁定的情况下一个小升级就有可能导致项目出错。
3. 在协作开发时，npm安装依赖到  node_modules 目录时顺序不是固定的，不能保证不同终端中的开发环境一致。
4. node_modules里的依赖有很多重复的，即占用了硬盘资源，又拉长了拉取的时间和网络资源

#### Yarn说明

- 新特性
  1. 离线模式（Offline Mode）：如果你之前安装过某个包，那么你可以在没有互联网连接的情况下，对这个包进行重新安装。
  2. 确定性（Deterministic）：不管安装顺序如何，相同的依赖在每台机器上会以完全相同的方式进行安装。
  3. 网络性能：Yarn会对请求进行高效地排队，避免出现请求瀑布（waterfall），便于将网络的使用效率达到最大化。
  4. 网络弹性（Network Resilience）：单个请求的失败不会导致整个安装的失败，请求会基于故障进行重试。
  5. 扁平模式（Flat Mode）：将不匹配的依赖版本都会解析为同一个版本，避免重复创建

#### Yarn安装

- macOS
  1. 官方推荐的是homebrew：brew install yarn
  2. 或者用npm也可以： npm install -g yarn
- windows
  1. 下载.msi文件安装 ([下载传送门]( https://link.jianshu.com/?t=https://yarnpkg.com/latest.msi) )，不过需要先装个node ( [下载传送门](https://link.jianshu.com/?t=https://nodejs.org/) ).
- Linux
  1. apt-get :  *sudo apt-get update* && *sudo apt-get install yarn*
  2. yum: *sudo yum install yarn*



查看版本号：

```yarn --version```

yarn的配置

```yarn config list                            //显示所有配置项```

```yarn config get <key>                       //显示某配置项```

```yarn config delete <key>                    //删除某配置项```

```yarn config set <key> <value> [-g|--global] //设置配置项```

####Yarn使用简介

```markdown
// 生成package.json文件
yarn init === npm init 

// 安装模块
yarn [global] add [package]
yarn add [package]@[version]
yarn add [package]@[tag]

// 安装package.json中的所有包,并将包及它的所有依赖项保存进yarn.lock
yarn install === npm install  
yarn install --flat            // 安装一个包的单一版本
yarn install --force           // 强制重新下载所有包
yarn install --production      // 只安装dependencies里的包
yarn install --no-lockfile     // 不读取或生成yarn.lock
yarn install --pure-lockfile   // 不生成yarn.lock

// 升级/移除单个包（均会更新package.json和yarn.lock）
yarn upgrade [package]
yarn upgrade [package]@[version]
yarn upgrade [package]@[tag]

yarn remove [package]
// yarn会将安装的包缓存起来
yarn cache ls         //列出所有本地缓存了的包
yarn cache dir      //列出本地缓存的位置
yarn cache clean    //清除本地缓存

// 类似于npm命令
yarn run
yarn login/logout
yarn owner add  
yarn owner rm  
yarn publish
yarn version
```

#### END Yarn

