## 入门
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

Maven是一个[意第绪语（Yiddish）单词](https://en.wikipedia.org/wiki/Maven)，意思是*知识的积累者*，
最初是为了简化 Jakarta Turbine 项目的构建过程。 有几个项目，每个项目都有自己的 Ant 构建文件，它们都略有不同。 JARs 被检入 CVS。
我们想要一种构建项目的标准方法，一个定义项目由什么组成的明确定义，一种发布项目信息的简单方法，以及一种跨多个项目共享jar的方法。

其结果是现在可以用于构建和管理任何基于java的项目的工具。
我们希望我们已经创建了一些东西，可以使Java开发人员的日常工作变得更容易，并通常有助于理解任何基于Java的项目。

## Maven 的目标

Maven的主要目标是让开发人员在最短的时间内理解开发工作的完整状态。为了实现这一目标，Maven处理了几个值得关注的领域：

- 简化构建过程
- 提供统一的构建系统
- 提供优质项目信息
- 鼓励更好的开发实践

### 简化构建过程

虽然使用Maven并不能消除（eliminate）了解底层机制的需要，但Maven确实可以让开发人员避开（shield）许多细节。

### 提供统一的构建系统

Maven使用其项目对象模型（POM）和一组插件构建一个项目。
一旦您熟悉了（familiarize）一个Maven项目，您就知道了所有Maven项目是如何构建的。这样可以在浏览（navigating）许多项目时节省时间。

### 提供优质项目信息

Maven提供了一些有用的项目信息，这些信息一部分来自POM，一部分来自项目的源代码。例如，Maven可以提供:

-   直接从源代码管理创建的更改日志
-   交叉引用源
-   由项目管理的邮件列表
-   项目使用的依赖项
-   单元测试报告，包括覆盖率

第三方代码分析产品还提供了Maven插件，可以将它们的报告添加到 Maven 提供的标准信息中。

### 提供最佳实践开发指南

Maven的目标是收集（gather）当前最佳实践开发的原则（principles），并使之易于指导项目朝这个方向发展。

例如，单元测试的规范、执行和报告是使用Maven的正常构建周期的一部分。当前的单元测试最佳实践被用作指导方针：

-   将测试源代码保存在独立但并行的源代码树中
-   使用测试用例命名约定来定位和执行测试
-   让测试用例设置他们的环境，而不是为测试准备定制构建

Maven还协助（assists in）项目工作流，如发布和问题管理（issue management）。

Maven还就如何布局项目的目录结构提出了一些建议。一旦您了解了布局，就可以轻松地浏览其他使用Maven的项目。

虽然对项目布局采取了固执己见的做法（an opinionated approach），但由于历史原因，一些项目可能不适合（fit with）这种结构。
虽然Maven的设计可以灵活地（flexible）满足不同项目的需求，但它不能在不损害（compromising）目标的情况下满足（cater）每一种情况。

如果您的项目有一个不寻常的构建结构，无法重新组织，那么您可能不得不放弃（forgo）一些特性或完全（altogether）放弃Maven的使用。

## Maven不是什么？

你可能听说过以下一些关于Maven的事情:

-   Maven 是一个站点和文档工具
-   Maven 扩展了Ant，让您可以下载依赖项
-   Maven 是一组可重用的Ant脚本

就像你可以在上面的 “Maven 是什么？” 部分中看到的一样，Maven 能完成这些事情，但是 
这些不是 Maven 的唯一特性，它的目标也完全不同。

