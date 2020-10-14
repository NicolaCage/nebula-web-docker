# 创建图数据模式

在 Nebula Graph 中，您必须先有图数据模式，再向其中写入点数据和边数据。本文描述如何使用 Nebula Graph 的 **控制台** 功能创建图数据模式。

> **说明**：您也可以使用 nebula-console 创建图数据模式。详细信息，参考 [使用 Docker Compose 部署 Nebula Graph
](https://github.com/vesoft-inc/nebula-docker-compose/blob/master/README_zh-CN.md) 和 [Nebula Graph 快速开始](https://docs.nebula-graph.com.cn/manual-CN/1.overview/2.quick-start/1.get-started/)。

## 前提条件

在 Nebula Graph Studio 上创建图数据模式之前，您需要确认以下信息：

- Nebula Graph Studio 已经连接到 Nebula Graph 数据库。
- 您的账号拥有 GOD、ADMIN 或 DBA 权限。详细信息，参考 [Nebula Graph 内置角色](https://docs.nebula-graph.com.cn/manual-CN/3.build-develop-and-administration/4.account-management-statements/built-in-roles/)。
- 您已经规划好了图数据模式的要素。
- 已经创建了图空间。
  > **说明**：本示例假设已经创建了图空间。如果您的账号拥有 GOD 权限，也可以在 **控制台** 上创建一个图空间。

## 操作步骤

按以下步骤创建图数据模式：

1. 在工具栏里，点击 **控制台** 页签。
2. 在 **当前Space** 中选择一个图空间。在本示例中，选择 **mooc_actions**。
   ![在 当前Space 中选择一个图空间](../figs/st-ug-007.png "选择图空间")
3. 在命令行中，依次输入以下语句，并点击 ![表示运行的图标](../figs/st-ug-008.png "Run 图标") 图标。一次只能运行一条语句。

   ```nGQL
    CREATE TAG user (userId int); -- 创建标签 user，带有 1 个属性
    CREATE TAG course (courseId int, courseName string); -- 创建标签 course，带有两个属性
    CREATE EDGE action (actionId int, duration double, label bool, feature0 double, feature1 double, feature2 double, feature3 double); -- 创建边类型，带有 7 个属性
    ```

至此，您已经完成了图数据模式创建。您可以运行以下语句查看标签与边类型的定义是否正确、完整。

```nGQL
SHOW TAGS; -- 列出当前图空间中所有标签
SHOW EDGES; -- 列出当前图空间中所有边类型
DESCRIBE TAG user;
DESCRIBE TAG course;
DESCRIBE EDGE action; -- 查看每种标签和边类型的结构是否正确
```

## 后续操作

创建图数据模式后，您可能需要执行以下操作：

- 根据业务需要，您可以为标签和边类型创建索引。详细信息，参考 [Nebula Graph 的 Schema 索引](https://docs.nebula-graph.com.cn/manual-CN/2.query-language/4.statement-syntax/1.data-definition-statements/)。
- [导入数据](st-ug-import-data.md)。