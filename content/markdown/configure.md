# 配置 Apache Maven
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
The configuration for Apache Maven usage itself and projects built with resides 
in a number of places: 

## `MAVEN_OPTS` 环境变量:

这个变量包含用于启动运行Maven的JVM的参数，并可用于为其提供附加选项。
例如，JVM内存设置可以定义为`-Xms256m -Xmx512m`。

## `settings.xml` 文件:

位于 `USER_HOME/.m2` 的设置文件被设计成包含Maven跨项目使用的任何配置。

## `.mvn` 目录:

位于项目的顶级目录中，`maven.config`, `jvm.config`, 和 `extensions.xml` 包含用于运行Maven的项目特定配置。

此目录是项目的一部分，可以签入到版本控制中。

### `.mvn/extensions.xml` 文件:

老方法（在 Maven 3.2.5 之前）是创建一个包含扩展的 jar（如果您有其他依赖项，则必须使用阴影），并手动将其放入 `${MAVEN_HOME}/lib/ext` 目录。
这意味着您必须更改Maven安装。 结果是，每个想要使用此功能的人都需要更改它的安装，这使得开发人员的入职培训更加不方便。
另一种方法是在命令行上通过 `mvn -Dmaven.ext.class.path=extension.jar` 给出 jar 的路径。
这样做的缺点（drawback）是，每次调用 Maven 时，都需要将这些选项提供给 Maven 构建。也不是很方便。

从现在开始，这可以用更简单、更专业的方式来完成。
所以你可以定义一个 `${maven.projectBasedir}/.mvn/extensions.xml` 文件，它看起来如下所示:

```xml
<extensions xmlns="http://maven.apache.org/EXTENSIONS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/EXTENSIONS/1.0.0 http://maven.apache.org/xsd/core-extensions-1.0.0.xsd">
  <extension>
    <groupId/>
    <artifactId/>
    <version/>
  </extension>
</extensions>
```

现在，您可以像定义任何其他工件一样，简单地通过定义通常的maven坐标groupId、artifactId、version来使用扩展。
此外，这些扩展的所有可传递性依赖项都将自动从存储库下载。 所以不需要再创建阴影工件（a shaded artifact）了。

### `.mvn/maven.config` 文件:

很难为调用 maven 命令行定义一组通用的选项。
从 Maven 3.3.1+ 开始，这个问题可以通过把这些选项放到脚本中来解决，
但是现在可以通过定义 `${maven.projectBasedir}/.mvn/maven.config` 文件来简单解决。
这个文件是包含 `mvn` 命令行的配置选项的配置文件。

比如，配置了 `-T3 -U --fail-at-end` 后，
您只需通过使用 `mvn clean package` 来调用 Maven，
而不是使用 `mvn -T3 -U --fail-at-end clean package` 并且在每次调用时都不能丢失 `-T3 -U --fail-at-end` 选项
位于 `${maven.projectBasedir}/.mvn/` 目录下的 `${maven.projectBasedir}/.mvn/maven.config` 文件，
也可以在多模块构建的根目录下工作。

### `.mvn/jvm.config` 文件:

从 Maven 3.3.1+ 开始，您可以通过 `${maven.projectBasedir}/.mvn/jvm.config` 文件定义 JVM 配置。
这意味着您可以在每个项目的基础上定义您的构建的选项。
此文件将成为项目的一部分，并与项目一起签入。所以不再需要 `MAVEN_OPTS`, `.mavenrc` 文件。
例如，如果您将以下JVM选项放入 `${maven.projectBasedir}/.mvn/jvm.config` 文件

        -Xmx2048m -Xms1024m -XX:MaxPermSize=512m -Djava.awt.headless=true

您不需要在 `MAVEN_OPTS` 中使用这些选项，也不需要在不同的配置之间切换。

## 其它指南

以下指南包含有关特定配置方面的更多信息：

* [Recommended Best Practice - Using a Repository Manager](./repository-management.html)
* [Documentation for settings.xml](./settings.html)
* [Configuring the logging](./maven-logging.html)
* [Configuring a HTTP Proxy](./guides/mini/guide-proxies.html)
* [Configuring a repository mirror](./guides/mini/guide-mirror-settings.html)
* [Various Tips for Configuring Maven](./guides/mini/guide-configuring-maven.html)
* [Password Encryption](./guides/mini/guide-encryption.html)
