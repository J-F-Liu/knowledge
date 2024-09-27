# 数据分析

字不如表，表不如图。数据可视化是数据分析的主要方向之一。

Excel 表格按照原始数据（sheet1）、加工数据（sheet2），图表（sheet3）的类型管理。

BI（商业智能）和图表的区别在于 BI 擅长交互和报表，更擅长解释已经发生和正在发生的数据。将要发生的数据是数据挖掘的方向。

数据可视化的三个过程：了解数据（图表），整合数据（BI），展示数据（信息化）。

Excel 对十万条以内的数据处理起来没有问题，但是互联网行业就是不缺数据。但凡产品有一点规模，数据都是百万起。这时候就需要学习数据库。

SQL 是数据分析的核心技能之一，从 Excel 到 SQL 绝对是数据处理效率的一大进步。

是否具备编程能力，是初级数据分析和高级数据分析的风水岭。数据挖掘，爬虫，可视化报表都需要用到编程能力。掌握一门优秀的编程语言，可以让数据分析师事半功倍。

R 的优点是统计学家编写的，缺点也是统计学家编写。Python 则是万能的胶水语言，适用性强，可以将各类分析的过程脚本化。Pandas，SKLearn 等各包也已经追平 R。

## 数据处理流程

```mermaid
graph LR;
    收集-->处理;
    处理-->存储;
    存储-->查询;
    查询-->分析;
    分析-->展示;
    展示-->监控;
```

- There is a wealth of information hiding in the data in your database just waiting to be discovered.
- See your most important KPIs on interactive, real-time dashboards anywhere, anytime.
- Receive alerts for conditions that you define—a sudden drop in number of orders, increased error rates, or achieved revenue goals.
- Defining and exposing reality based on actual data makes everyone in your company more curious and engaged in your company’s success.

OLTP (Online Transaction Processing): using a database to run your business
OLAP (Online Analytical Processing): using a database to understand your business

A typical relational database stores its data in row form. A single row for a transaction.

Data cube (or datacube) is a multi-dimensional ("n-D") array of values.
An OLAP cube is a multi-dimensional array of data. They are aggregated and then cached subsets of data within the nested array — and occasionally persisted parts of the nested array to disk. New cubes often had to be created whenever a new report or a new analysis was required.

For small business you might be able to get a way with running both OLTP and OLAP query-types on a normal relational database.
For huge database it becomes important to structure your data for analysis separately from the business application.

Massively parallel processing (MPP) database: instead of being limited by the computational power and memory of a single computer, you can radically boost the performance of your query if you spread that query across hundreds if not thousands of machines.

Columnar data warehouse: stores each data field in separate columns.

- Columnar databases have higher read efficiency
- columnar databases have higher sorting and indexing efficiency
- Columnar databases also compress better than row-based relational databases
- update performance in a columnar database is abysmal

The net result of all these properties is that columnar databases give you OLAP cube-like performance without the pain of explicitly designing and building cubes.

## Articles
- [An exploration of vector search](https://blog.shalvah.me/posts/an-exploration-of-vector-search)