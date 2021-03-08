# Alibaba Summer of Code 2020 - Arthas Final Report

## Project information

### Project name

Provide a separate tutorial for each Arthas command

### Project task description

 [Issue](https://github.com/alibaba/arthas/issues/847)

 There are two parts in the old online tutorial: `basic` and `advanced`

* https://arthas.aliyun.com/doc/arthas-tutorials.html?language=en&id=arthas-basics
* https://arthas.aliyun.com/doc/arthas-tutorials.html?language=en&id=arthas-advanced

Research about the online tutorial: [#742](https://github.com/alibaba/arthas/issues/742)

 * Each little tutorial is a little longer, and adding new content will cause the tutorial to get longer and longer.
 * Users tend to lose patience.
 * It's hard to find what you need.
 * More users want to see the usage of a command directly

So consider:

 * Provide a separate tutorial for each command, such as a separate tutorial for the `watch` command, so that many tips can be written in.
 * One tutorial per case to make it easier for users to learn to use Arthas.

What we need to:

 *  Move tutorial git Repository https://github.com/hengyunabc/katacoda-scenarios to Arthas itself.
 *  Seperate the tutorial, then send the PR merge to https://github.com/alibaba/arthas/tree/master/tutorials/katacoda
 *  Update the web page： https://github.com/alibaba/arthas/blob/master/site/src/site/sphinx/_include_html/arthas-tutorials.html
 *  Add links to the online tutorials for the official documents: https://github.com/alibaba/arthas/tree/master/site/src/site/sphinx/*.md

### Implementation plan

1. Move tutorial git Repository https://github.com/hengyunabc/katacoda-scenarios  to Arthas itself：

After reading katacoda's official documentation, I added the [katacoda.yaml](https://github.com/alibaba/arthas/blob/master/katacoda.yaml) at root in Arthas repository where I specified the katacoda tutorial is located. Then all tutorials https://github.com/hengyunabc/katacoda-scenarios have been migrated to [/tutorials/katacoda/](https://github.com/alibaba/arthas/tree/master/tutorials/katacoda) directory.

2. Seperate the tutorial, provide a separate tutorial for each Arthas command

Refer to https://arthas.aliyun.com/doc/commands.html . At the same time, the command and user cases in the original tutorial are integrated and classified, and the new version of Arthas tutorial is made. The structure of each command and case tutorial is as follows:

Start demo ->Start arthas-boot ->...[details on how to use each command]...

At the same time, the user case related to the command is integrated into the command tutorial, and it is placed in a separate case tutorial for users to query.

In addition, I have integrated some related special usages. Referring to https://github.com/alibaba/arthas/issues?q=label%3Auser-case , some additional cases have been produced.

3. Update the web page

   * The new online tutorials include "Arthas Basics" and "Arthas Advanced" from the old online tutorials, which are placed in the "Tutorials" menu bar.
   * Each related command tutorial is placed in the menu by it's classification. I also place typical user cases online tutorials in the "User Cases" menu bar.

New version menu design：

![](https://user-images.githubusercontent.com/43995067/90713496-0735c880-e2d8-11ea-818a-2c89120a7dc0.png)


 4. Add links to the online tutorials for the official documents

 ![image](https://user-images.githubusercontent.com/43995067/84760649-3ec68280-afc0-11ea-904a-db205ac54cd9.png)

 5. Usages

Katacoda is an interactive learning and training platform for software engineers. It can use real-world environment to learn and test new technologies in the browser to help developers learn and master best practices.

Katacoda can quickly provide a temporary environment and recycle it after use. Users can operate a complete set of environment through the browser terminal interface according to the designed guidance steps, and learn and practice step by step.

The new Arthas online tutorials provide a very convenient way to learn. You just need to open the corresponding courses, and you can follow the course instructions and complete the learning step by step according to the designed steps.

1. First visit the online tutorial: https://arthas.aliyun.com/doc/arthas-tutorials.html?language=en , select the course you want to study from the menu:
![](https://user-images.githubusercontent.com/43995067/90310125-2a9bf480-df21-11ea-819d-2713f22f4145.png)

2. The course introduction page will indicate the difficulty of the course and the time required to help you understand the basic information of the course. click `START SCENARIO` to start learning.
![](https://user-images.githubusercontent.com/43995067/90310168-9ed69800-df21-11ea-93cf-a01b4a41c66b.png)

3. Enter the course, the left side is the description of this step, and the right side is a ready terminal, which can be used directly. Click the black blocks on the left to execute commands in the right:
![](https://user-images.githubusercontent.com/43995067/90310223-3d62f900-df22-11ea-936c-deb950e61f9e.png)

4. Click the tab on the right to switch between terminals. Then follow the step-by-step instructions to complete the learning step by step:
![](https://user-images.githubusercontent.com/43995067/90310282-b8c4aa80-df22-11ea-8052-3799277b748e.png)

### Milestone review

Half of the commands and user tutorials were merged into the upstream before July 31, and all commands and user tutorials were merged into the upstream on August 14, and then it was online for testing.

Due to the large scale of this project, the completion of each command online tutorial can be regarded as a milestone node.

During the project, more than 80 PRs were sent to Arthas project, with a total increase or decrease of more than 26k lines.

 ![image](https://images.gitee.com/uploads/images/2020/0903/191310_d7ff2cf1_7637131.png)

 During the test, the number of visits to the tutorial increased dramatically, and was well received by all the users!

  * Well received by users:

 ![image](https://user-images.githubusercontent.com/43995067/91398554-e7ba1500-e86e-11ea-98da-77f50546197c.png)

 * Statistics of the visit and engagement duration of the tutorials. It can be seen that after the new version of the tutorial test was launched on August 14, users and engagement duration have increased significantly:

 ![image](https://images.gitee.com/uploads/images/2020/0827/133818_fb0c66c7_7637131.png)

## Project summary

### Project deliverables

#### Move Current Tutorial

[#1229](https://github.com/alibaba/arthas/pull/1229)

[fix link issues (#1235)](https://github.com/alibaba/arthas/pull/1235)

- [fix issues in #1235 (#1236)](https://github.com/alibaba/arthas/pull/1236)

- [fix issues in #1235 (#1237)](https://github.com/alibaba/arthas/pull/1237)

#### Adding Tutorial

##### User Cases

- [X] Web Console
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1332](https://github.com/alibaba/arthas/pull/1332)
- [X] HTTP API
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1423](https://github.com/alibaba/arthas/pull/1423)
- [X] Arthas boot supported options
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1344](https://github.com/alibaba/arthas/pull/1344)
- [X] Troubleshooting method invoke exception
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1335](https://github.com/alibaba/arthas/pull/1335)
- [X] Hotswap code
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1339](https://github.com/alibaba/arthas/pull/1339)
- [X] Change Logger Level
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1337](https://github.com/alibaba/arthas/pull/1337)
- [X] Troubleshoot logger conflicts
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1338](https://github.com/alibaba/arthas/pull/1338)
- [X] Get Spring Context
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1342](https://github.com/alibaba/arthas/pull/1342)
- [X] Troubleshooting HTTP request returns 401
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1341](https://github.com/alibaba/arthas/pull/1341)
- [X] Troubleshooting HTTP request returns 404
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1340](https://github.com/alibaba/arthas/pull/1340)
- [X] The ClassLoaders in Spring Boot application
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1343](https://github.com/alibaba/arthas/pull/1343)
- [X] Find CPU usage Top N threads
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1336](https://github.com/alibaba/arthas/pull/1336)
- [X] Log the output
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1334](https://github.com/alibaba/arthas/pull/1334)
- [X] Async in Background
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1354](https://github.com/alibaba/arthas/pull/1354)

##### Command

- [X] cls
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1312](https://github.com/alibaba/arthas/pull/1312)
- [X] session
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1313](https://github.com/alibaba/arthas/pull/1313)
- [X] reset
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1314](https://github.com/alibaba/arthas/pull/1314)
- [X] version
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1315](https://github.com/alibaba/arthas/pull/1315)
- [X] history
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1316](https://github.com/alibaba/arthas/pull/1316)
- [X] quit-stop
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1317](https://github.com/alibaba/arthas/pull/1317)
- [X] keymap
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1318](https://github.com/alibaba/arthas/pull/1318)
- [X] cat
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1319](https://github.com/alibaba/arthas/pull/1319)
- [X] echo
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1320](https://github.com/alibaba/arthas/pull/1320)
- [X] grep
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1321](https://github.com/alibaba/arthas/pull/1321)
- [X] tee
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1322](https://github.com/alibaba/arthas/pull/1322)
- [X] pwd
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1323](https://github.com/alibaba/arthas/pull/1323)
- [X] wc
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1384](https://github.com/alibaba/arthas/pull/1384)
- [X] plaintext
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1383](https://github.com/alibaba/arthas/pull/1383)
- [x] dashboard
 - - [x] Chinese
 - - [x] English
 - - [X] PR [#1326](https://github.com/alibaba/arthas/pull/1326)
- [x] thread
 - - [x] Chinese
 - - [x] English
 - - [X] PR [#1328](https://github.com/alibaba/arthas/pull/1328)
- [x] jvm
 - - [x] Chinese
 - - [x] English
 - - [X] PR [#1329](https://github.com/alibaba/arthas/pull/1329)
- [X] sysprop
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1331](https://github.com/alibaba/arthas/pull/1331)
- [X] sysenv
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1330](https://github.com/alibaba/arthas/pull/1330)
- [X] vmoption
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1347](https://github.com/alibaba/arthas/pull/1347)
- [X] perfcounter
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1352](https://github.com/alibaba/arthas/pull/1352)
- [X] logger
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1365](https://github.com/alibaba/arthas/pull/1365)
- [X] mbean
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1357](https://github.com/alibaba/arthas/pull/1357)
- [X] getstatic
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1368](https://github.com/alibaba/arthas/pull/1368)
- [X] ognl
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1327](https://github.com/alibaba/arthas/pull/1327)
- [X] sc
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1370](https://github.com/alibaba/arthas/pull/1370)
- [X] sm
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1371](https://github.com/alibaba/arthas/pull/1371)
- [X] dump
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1372](https://github.com/alibaba/arthas/pull/1372)
- [X] heapdump
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1373](https://github.com/alibaba/arthas/pull/1373)
- [X] jad
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1374](https://github.com/alibaba/arthas/pull/1374)
- [X] classloader
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1375](https://github.com/alibaba/arthas/pull/1375)
- [X] mc-redefine
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1376](https://github.com/alibaba/arthas/pull/1376)
- [X] monitor
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1377](https://github.com/alibaba/arthas/pull/1377)
- [X] watch
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1378](https://github.com/alibaba/arthas/pull/1378)
- [X] trace
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1379](https://github.com/alibaba/arthas/pull/1379)
- [X] stack
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1380](https://github.com/alibaba/arthas/pull/1380)
- [X] tt
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1381](https://github.com/alibaba/arthas/pull/1381)
- [X] options
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1382](https://github.com/alibaba/arthas/pull/1382)
- [X] profiler
 - - [X] Chinese
 - - [X] English
 - - [X] PR [#1421](https://github.com/alibaba/arthas/pull/1421)

#### Web Page Updating

 - [X] Part1 PR [#1364](https://github.com/alibaba/arthas/pull/1364)

 - [X] Part2 PR [#1385](https://github.com/alibaba/arthas/pull/1385)

 - [X] Split `command` menu bar PR [#1414](https://github.com/alibaba/arthas/pull/1414)

#### Add Links

This part is included in the `Adding Tutorial` part's PR.

#### Add Guides

[Add guides for using and contributing (#1455)](https://github.com/alibaba/arthas/pull/1455)

#### Bug Fix

[Fix intro.md Problems (#1367)](https://github.com/alibaba/arthas/pull/1367)

[Delete all the arthas-boot.md '--target-ip 0.0.0.0' boot parameter (#1359)](https://github.com/alibaba/arthas/pull/1359)

[Fix classloaderhash Problems (#1417)](https://github.com/alibaba/arthas/pull/1417)

[Fix typos (#1418)](https://github.com/alibaba/arthas/pull/1418)

[Fix typos (#1419)](https://github.com/alibaba/arthas/pull/1419)

[Fix typos (#1434)](https://github.com/alibaba/arthas/pull/1434)

[Fix Website (#1435)](https://github.com/alibaba/arthas/pull/1435)

[Fix displaying (#1436)](https://github.com/alibaba/arthas/pull/1436)

[Update sc/sm Online Tutorial for classLoaderClass (#1443)](https://github.com/alibaba/arthas/pull/1443)

[Fix ID doesn't exist in T4 (#1451)](https://github.com/alibaba/arthas/pull/1451)

[Fix links, typos, 'intro.md', 'finish.md' for Online Tutorials (#1453)](https://github.com/alibaba/arthas/pull/1453)

[Add Press Q or Ctrl+C to abort for enhanced commands (#1454)](https://github.com/alibaba/arthas/pull/1454)

[Classloader using --classLoaderClass in Advanced tutorial (#1456)](https://github.com/alibaba/arthas/pull/1456)

[Fix typos and accessibility #847 (#1460)](https://github.com/alibaba/arthas/pull/1460)

#### Add --classLoaderClass Param PRs

[Classloader support matching classloader by class name (#1428)](https://github.com/alibaba/arthas/pull/1428)

[Optimize --classLoaderClass #1428 (#1431)](https://github.com/alibaba/arthas/pull/1431)

[Add --classLoaderClass for sc/sm (#1433)](https://github.com/alibaba/arthas/pull/1433)

[Add --classLoaderClass for logger (#1445)](https://github.com/alibaba/arthas/pull/1445)

[Add --classLoaderClass for dump/getstatic/jad/mc/redifine (#1447)](https://github.com/alibaba/arthas/pull/1447)

#### Other Unmerged PRs

[Split arthas-advanced to arthas-command (#2)](https://github.com/hengyunabc/katacoda-scenarios/pull/2)

[Arthas Online course arrangement and compilation supplement (#5)](https://github.com/hengyunabc/katacoda-scenarios/pull/5)

[Arthas Online course arrangement and compilation supplement (#1239)](https://github.com/alibaba/arthas/pull/1239)

[Arthas Online course arrangement and compilation supplement —— Update web pages (#1241)](https://github.com/alibaba/arthas/pull/1241)

[Arthas Basic Command Tutorial (#1303)](https://github.com/alibaba/arthas/pull/1303)

[Fix typos in #1292 (#1446)](https://github.com/alibaba/arthas/pull/1446)

### Project highlights

1. Straightforward and convenient menu design. Commands and user cases are classified to facilitate users to retrieve certain problems or specific usage methods.

2. Introduce the online tutorial in the official documents, which is convenient for users to click the link directly.

3. Online tutorial can use real environment to learn and test new technology in browser, and help developers learn and master best practices.

4. Online tutorial can quickly provide a complete set of temporary environment and recycle it after use. Users can operate the environment through the browser terminal interface according to the designed guidance steps, and learn and practice step by step.

5. Solve the user's trouble of too troublesome to set up own environment, not having supported environment to try Arthas and the poor operability of the documents and the difficulty of hands-on practice.

6. The git repository of the tutorial is placed in Arthas itself so that Arthas contributors can easily find the source code location of the online tutorial and continue to contribute to it.

7. Actively Add --classloaderclas parameter for classloader/sc/sm/logger/dump/getstatic/jad/mc/redifine, through which you can directly specify a classloader which has no duplicate name, and do not need to use c parameter to specify dynamically changing hash value of classloader, which is convenient for online tutorial writing.

### Experience

Alibaba Summer of Code 2020 has greatly trained my team cooperation and communication skills, broadened my vision, and I gained a lot.

The two mentors also gave me a lot of guiding opinions during ASoC 2020, and I would like to thank them for their hard guidance 😀！

Therefore, students, if you have enough enthusiasm for open source, you are recommended to participate in the future Alibaba Summer of Code activities!
