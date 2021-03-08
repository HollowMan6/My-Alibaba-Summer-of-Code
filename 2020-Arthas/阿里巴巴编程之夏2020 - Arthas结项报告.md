# 阿里巴巴编程之夏2020 - Arthas结项报告

## 项目信息介绍

### 项目名称

Arthas在线教程重新编排，每个命令一个小教程

### 项目任务描述

 [Issue](https://github.com/alibaba/arthas/issues/847)

 旧版在线教程有两部分：`基础` 和 `进阶`。

 * https://arthas.aliyun.com/doc/arthas-tutorials.html?language=cn&id=arthas-basics
 * https://arthas.aliyun.com/doc/arthas-tutorials.html?language=cn&id=arthas-advanced
 
 一些调查结果： [#742](https://github.com/alibaba/arthas/issues/742)
 
 * 每个小教程都是比较长，再增加新的内容会导致教程越来越长
 * 用户容易失去耐心
 * 不好找到需要的内容
 * 更多的用户是想直接看某个命令的用法
 
 所以考虑

 * 每个命令一个教程，比如`watch`命令单独一个教程，这样子很多小技巧都可以写进去
 * 每一个案例一个教程，方便用户对应问题学习
 
 需要做的事情：

 * 把教程git仓库https://github.com/hengyunabc/katacoda-scenarios 放在arthas本身
 * 拆分教程，为单个命令提PR到： https://github.com/alibaba/arthas/tree/master/tutorials/katacoda
 * 修改现有的web页面 ： https://github.com/alibaba/arthas/blob/master/site/src/site/sphinx/_include_html/arthas-tutorials.html
 * 为每个官方文档页首增加到在线教程的链接: https://github.com/alibaba/arthas/tree/master/site/src/site/sphinx/*.md

### 实现方案描述

1. 把教程git仓库https://github.com/hengyunabc/katacoda-scenarios 放在arthas本身：

在阅读了Katacoda的官方文档后，我在Arthas仓库根目录下增加了[katacoda.yaml](https://github.com/alibaba/arthas/blob/master/katacoda.yaml)，其中指明了Katacoda教程的存放位置。然后将https://github.com/hengyunabc/katacoda-scenarios 所有教程迁移到了[/tutorials/katacoda/](https://github.com/alibaba/arthas/tree/master/tutorials/katacoda)目录下。

2. 拆分教程，为单个命令编写教程

参考https://arthas.aliyun.com/doc/commands.html 文档中的用法，同时将原有教程中的命令和用户案例进行整合和分类，编写新版Arthas教程。每个命令和案例教程的结构如下：

启动demo ->启动arthas-boot ->...[每个Command具体用法教程]...

同时整合同命令相关的用户案例至命令教程中，同时将其放在单独案例教程里，便于用户查询。

我另外整合了一些相关特殊用法，并且参考了https://github.com/alibaba/arthas/issues?q=label%3Auser-case 额外制作了一些案例。

3. 修改现有的web页面

   * 新版在线教程中包含了老版在线教程中的“Arthas基础教程”和“Arthas进阶教程”，放置在“入门教程”菜单栏中。
   * 命令教程按类放置在相关菜单中，用户案例在线教程放置在对应“用户案例”菜单栏中。
   
新版菜单设计如下：

![](https://user-images.githubusercontent.com/43995067/89858799-175ff080-dbd2-11ea-8fec-0af5f35d5c43.png)


 4. 为每个官方文档页首增加到在线教程的链接

 ![image](https://user-images.githubusercontent.com/43995067/84760649-3ec68280-afc0-11ea-904a-db205ac54cd9.png)

 5. 用户使用指南

 Katacoda 是一个面向软件工程师的交互式学习和培训平台，可在浏览器中使用真实环境学习和测试新技术，帮助开发人员学习，并掌握最佳实践。

 Katacoda 可以快速的提供一套完整的临时环境，并在使用后将其回收。用户可以根据设计好的引导步骤，通过浏览器上的终端界面操作一套完整的环境，一步步的学习和实践。

 Arthas新版在线教程使用Katacoda，提供了非常便利的学习方式，你只需要打开相应课程，就可以跟着课程说明，按照设计好的步骤一步步完成学习。

1. 首先访问在线教程：https://arthas.aliyun.com/doc/arthas-tutorials.html?language=cn ，从菜单中选择你想要学习的课程：
![](https://images.gitee.com/uploads/images/2020/0814/211330_e71ef0ca_7637131.png)

2. 课程介绍页面会标明课程的难度和需要的时间，帮助你了解该课程的基本信息。点击`START SCENARIO`开始学习。
![](https://images.gitee.com/uploads/images/2020/0814/212507_4a02d8aa_7637131.png)

3. 进入课程，左侧是该步骤说明，右侧是一个已经准备好的终端，直接可以使用。点击左侧黑块部分就可以在右侧执行：
![](https://images.gitee.com/uploads/images/2020/0814/213005_62d85818_7637131.png)

4. 点击右侧标签可以切换终端。之后就是跟着步骤说明，一步步的完成学习即可：
![](https://images.gitee.com/uploads/images/2020/0814/213458_43bb4e3f_7637131.png)

### 里程碑节点回顾

7月31日前实现了半数命令和用户教程合并进主仓库的任务，8月14日实现了所有命令和用户教程合并进主仓库的任务，并开始上线测试。

由于项目较庞大，完成每个命令的编写都可以算作一个里程碑节点。

项目进行期间向Arthas项目提起了超过80个PRs，总增减量超过两万六千行。

 ![image](https://images.gitee.com/uploads/images/2020/0903/191310_d7ff2cf1_7637131.png)

 测试期间，教程访问量激增，并且受到了用户的一致好评！

 * 用户的好评：

 ![image](https://images.gitee.com/uploads/images/2020/0827/133654_e1f2c3ea_7637131.png)

 * 教程使用人数和时长统计。可见8月14日新版教程测试上线之后，用户和时长都出现了大幅度的增加：

 ![image](https://images.gitee.com/uploads/images/2020/0827/133818_fb0c66c7_7637131.png)

## 项目总结

### 项目交付成果

#### 迁移现有教程

[#1229](https://github.com/alibaba/arthas/pull/1229)

[修复链接问题 link issues (#1235)](https://github.com/alibaba/arthas/pull/1235)

- [修复#1235中问题 issues in #1235 (#1236)](https://github.com/alibaba/arthas/pull/1236)

- [修复#1235中问题 issues in #1235 (#1237)](https://github.com/alibaba/arthas/pull/1237)

#### 教程编写

##### 案例

- [X] Web Console
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1332](https://github.com/alibaba/arthas/pull/1332)
- [X] HTTP API
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1423](https://github.com/alibaba/arthas/pull/1423)
- [X] arthas-boot支持的参数
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1344](https://github.com/alibaba/arthas/pull/1344)
- [X] 排查函数调用异常现象
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1335](https://github.com/alibaba/arthas/pull/1335)
- [X] 热更新代码
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1339](https://github.com/alibaba/arthas/pull/1339)
- [X] 动态更新应用
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1337](https://github.com/alibaba/arthas/pull/1337)
- [X] 排查logger冲突问题
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1338](https://github.com/alibaba/arthas/pull/1338)
- [X] 获取 Spring Context
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1342](https://github.com/alibaba/arthas/pull/1342)
- [X] 排查HTTP请求返回401
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1341](https://github.com/alibaba/arthas/pull/1341)
- [X] 排查HTTP请求返回404
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1340](https://github.com/alibaba/arthas/pull/1340)
- [X] 理解Spring Boot应用的ClassLoader结构
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1343](https://github.com/alibaba/arthas/pull/1343)
- [X] 查找Top N线程
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1336](https://github.com/alibaba/arthas/pull/1336)
- [X] 执行结果存日志
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1334](https://github.com/alibaba/arthas/pull/1334)
- [X] 后台异步任务
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1354](https://github.com/alibaba/arthas/pull/1354)

##### 命令

- [X] cls
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1312](https://github.com/alibaba/arthas/pull/1312)
- [X] session
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1313](https://github.com/alibaba/arthas/pull/1313)
- [X] reset
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1314](https://github.com/alibaba/arthas/pull/1314)
- [X] version
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1315](https://github.com/alibaba/arthas/pull/1315)
- [X] history
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1316](https://github.com/alibaba/arthas/pull/1316)
- [X] quit-stop
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1317](https://github.com/alibaba/arthas/pull/1317)
- [X] keymap
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1318](https://github.com/alibaba/arthas/pull/1318)
- [X] cat
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1319](https://github.com/alibaba/arthas/pull/1319)
- [X] echo
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1320](https://github.com/alibaba/arthas/pull/1320)
- [X] grep
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1321](https://github.com/alibaba/arthas/pull/1321)
- [X] tee
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1322](https://github.com/alibaba/arthas/pull/1322)
- [X] pwd
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1323](https://github.com/alibaba/arthas/pull/1323)
- [X] wc
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1384](https://github.com/alibaba/arthas/pull/1384)
- [X] plaintext
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1383](https://github.com/alibaba/arthas/pull/1383)
- [x] dashboard
 - - [x] 中文
 - - [x] English
 - - [X] PR [#1326](https://github.com/alibaba/arthas/pull/1326)
- [x] thread
 - - [x] 中文
 - - [x] English
 - - [X] PR [#1328](https://github.com/alibaba/arthas/pull/1328)
- [x] jvm
 - - [x] 中文
 - - [x] English
 - - [X] PR [#1329](https://github.com/alibaba/arthas/pull/1329)
- [X] sysprop
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1331](https://github.com/alibaba/arthas/pull/1331)
- [X] sysenv
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1330](https://github.com/alibaba/arthas/pull/1330)
- [X] vmoption
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1347](https://github.com/alibaba/arthas/pull/1347)
- [X] perfcounter
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1352](https://github.com/alibaba/arthas/pull/1352)
- [X] logger
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1365](https://github.com/alibaba/arthas/pull/1365)
- [X] mbean
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1357](https://github.com/alibaba/arthas/pull/1357)
- [X] getstatic
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1368](https://github.com/alibaba/arthas/pull/1368)
- [X] ognl
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1327](https://github.com/alibaba/arthas/pull/1327)
- [X] sc
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1370](https://github.com/alibaba/arthas/pull/1370)
- [X] sm
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1371](https://github.com/alibaba/arthas/pull/1371)
- [X] dump
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1372](https://github.com/alibaba/arthas/pull/1372)
- [X] heapdump
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1373](https://github.com/alibaba/arthas/pull/1373)
- [X] jad
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1374](https://github.com/alibaba/arthas/pull/1374)
- [X] classloader
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1375](https://github.com/alibaba/arthas/pull/1375)
- [X] mc-redefine
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1376](https://github.com/alibaba/arthas/pull/1376)
- [X] monitor
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1377](https://github.com/alibaba/arthas/pull/1377)
- [X] watch
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1378](https://github.com/alibaba/arthas/pull/1378)
- [X] trace
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1379](https://github.com/alibaba/arthas/pull/1379)
- [X] stack
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1380](https://github.com/alibaba/arthas/pull/1380)
- [X] tt
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1381](https://github.com/alibaba/arthas/pull/1381)
- [X] options
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1382](https://github.com/alibaba/arthas/pull/1382)
- [X] profiler
 - - [X] 中文
 - - [X] English
 - - [X] PR [#1421](https://github.com/alibaba/arthas/pull/1421)

#### 网页更新

 - [X] Part1 PR [#1364](https://github.com/alibaba/arthas/pull/1364)

 - [X] Part2 PR [#1385](https://github.com/alibaba/arthas/pull/1385)

 - [X] 将'命令'菜单栏拆分 PR [#1414](https://github.com/alibaba/arthas/pull/1414)

#### 增加链接

此部分包含在`教程编写`部分PR中。

#### 增加使用和贡献指南

[增加使用和贡献指南 (#1455)](https://github.com/alibaba/arthas/pull/1455)

#### 修复错误

[修复 intro.md 问题 (#1367)](https://github.com/alibaba/arthas/pull/1367)

[删除所有 arthas-boot.md 中的启动参数'--target-ip 0.0.0.0' (#1359)](https://github.com/alibaba/arthas/pull/1359)

[修复 classloaderhash 问题 (#1417)](https://github.com/alibaba/arthas/pull/1417)

[修复拼写错误 (#1418)](https://github.com/alibaba/arthas/pull/1418)

[修复拼写错误 (#1419)](https://github.com/alibaba/arthas/pull/1419)

[修复拼写错误 (#1434)](https://github.com/alibaba/arthas/pull/1434)

[修复网页 (#1435)](https://github.com/alibaba/arthas/pull/1435)

[修复显示问题 (#1436)](https://github.com/alibaba/arthas/pull/1436)

[为 --classLoaderClass 更新 sc/sm 在线教程 (#1443)](https://github.com/alibaba/arthas/pull/1443)

[修复 ID 在 T4 中不存在 (#1451)](https://github.com/alibaba/arthas/pull/1451)

[修复链接, 拼写错误, 'intro.md', 'finish.md' (#1453)](https://github.com/alibaba/arthas/pull/1453)

[为增强命令教程增加按 Q 或 Ctrl+C 退出的提示 (#1454)](https://github.com/alibaba/arthas/pull/1454)

[Classloader 在高级教程中使用 --classLoaderClass (#1456)](https://github.com/alibaba/arthas/pull/1456)

[修复拼写错误和访问问题 #847 (#1460)](https://github.com/alibaba/arthas/pull/1460)

#### 增加 Add --classLoaderClass Param 参数 PRs

[Classloader 命令支持使用 class name 匹配 ClassLoader (#1428)](https://github.com/alibaba/arthas/pull/1428)

[优化 --classLoaderClass #1428 (#1431)](https://github.com/alibaba/arthas/pull/1431)

[为sc/sm增加 --classLoaderClass参数 (#1433)](https://github.com/alibaba/arthas/pull/1433)

[为logger增加 --classLoaderClass参数 (#1445)](https://github.com/alibaba/arthas/pull/1445)

[为dump/getstatic/jad/mc/redifine增加 --classLoaderClas参数 (#1447)](https://github.com/alibaba/arthas/pull/1447)

#### 其它未合并 Other Unmerged PRs

[Split arthas-advanced to arthas-command/在线教程重新编排，每个命令一个小教程 (#2)](https://github.com/hengyunabc/katacoda-scenarios/pull/2)

[Arthas 在线教程整理和编写补充 (#5)](https://github.com/hengyunabc/katacoda-scenarios/pull/5)

[Arthas 在线教程整理和编写补充 (#1239)](https://github.com/alibaba/arthas/pull/1239)

[Arthas 在线教程整理和编写补充 —— 页面更新 (#1241)](https://github.com/alibaba/arthas/pull/1241)

[Arthas基础命令教程 (#1303)](https://github.com/alibaba/arthas/pull/1303)

[Fix typos in #1292 (#1446)](https://github.com/alibaba/arthas/pull/1446)

### 项目亮点介绍

1. 直白方便的教程选择菜单设计。命令和用户案例分类排放，方便用户就某种问题或者某个具体使用方法而检索。

2. 在官方相关文档处介绍在线教程，方便用户直接点击链接查看。

3. 在线教程可在浏览器中使用真实环境学习和测试新技术，帮助开发人员学习，并掌握最佳实践。

4. 在线教程可以快速的提供一套完整的临时环境，并在使用后将其回收。用户可以根据设计好的引导步骤，通过浏览器上的终端界面操作一套完整的环境，一步步的学习和实践。

5. 解决了用户自己配环境太麻烦，没有配套环境试用和文档操作性差，动手实践难度高的痛点。

6. 把教程git仓库放在arthas本身，方便后续Arthas贡献者找到在线教程源代码位置并为其继续贡献。

7. 主动为classloader/sc/sm/logger/dump/getstatic/jad/mc/redifine增加 --classLoaderClas参数，通过其可以直接指定某个无重复名称的ClassLoader而无需使用c参数指定动态变化的ClassLoader的Hash值，方便在线教程的编写。

### 心得体会

此次参与阿里巴巴编程之夏2020极大地锻炼了我的团队协作和沟通能⼒，拓宽了我的视野，收获十分丰厚。

在项目进行期间，两位导师同时给了我许多指导性的意见，在此我要感谢他们的辛勤指导😀！

因而，同学们，如果你对开源有足够的热情，推荐你参加未来的阿里巴巴编程之夏活动！
