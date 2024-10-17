# boost

##  Boost.Asio 网络通信库
## `boost::property_tree` 
`boost::property_tree` 是 Boost 库中的一个模块，用于处理树形结构的数据，特别是用于解析和生成配置文件、XML、JSON 等格式的数据。它提供了一种简单的方式来存储和访问层次化的数据结构。

### 主要特点

* **层次结构**：`property_tree` 允许以树形结构存储数据，每个节点可以包含子节点。
* **多种格式支持**：支持多种数据格式，包括 XML、JSON、INI 和 INFO 文件。
* **简单易用**：提供了简单的接口来读取和写入数据。

### 主要类和函数

* `boost::property_tree::ptree`：这是 `property_tree` 的核心类，表示一个属性树。
* `read_xml`、`write_xml`：用于读取和写入 XML 格式的数据。
* `read_json`、`write_json`：用于读取和写入 JSON 格式的数据。
* `read_ini`、`write_ini`：用于读取和写入 INI 格式的数据。