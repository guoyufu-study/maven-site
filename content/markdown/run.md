# 运行 Apache Maven
<!--
Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under the License.
-->
运行Maven的语法如下所示：

    mvn [options] [<goal(s)>] [<phase(s)>]

所有可用的选项都记录在内置帮助中，您可以使用下面的命令访问

    mvn -h

使用Maven生命周期阶段构建Maven项目的典型调用。比如：  

    mvn package

内置的生命周期和它们的阶段依次是:

* clean - pre-clean, clean, post-clean

* default - validate, initialize, generate-sources, process-sources, generate-resources, 
process-resources, compile, process-classes, generate-test-sources, process-test-sources, 
generate-test-resources, process-test-resources, test-compile, process-test-classes, 
test, prepare-package, package, pre-integration-test, integration-test, post-integration-test, 
verify, install, deploy

* site - pre-site, site, post-site, site-deploy

生成所有打包输出和文档站点并将其部署到存储库管理器的项目的新构建可以通过

    mvn clean deploy site-deploy

只创建包并将其安装在本地存储库中，以便从其他项目中重用，就可以使用

    mvn verify

这是Maven项目最常见的构建调用。

当不处理项目时，或者在其他一些用例中，您可能希望调用由Maven的一部分实现的特定任务 — 这称为插件的**目标**。例如：

    mvn archetype:generate

或者，

    mvn checkstyle:check

有许多不同的插件可用，它们都实现不同的目标。


更多资源: 

* [使用 Maven 构建一个项目](./run-maven/index.html)
