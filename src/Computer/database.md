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
