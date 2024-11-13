# perf-schema-analyzer-for-mysql

这是一个利用 MySQL Performance Schema 分析慢查询的工具。它可以帮助你识别和优化数据库中的慢查询,提高系统性能。

## 分析TopSQL
```shell
python3 slow-query-digest.py 
    --host localhost 
    --user your_username 
    --password your_password 
    --database mytest  
    --days 3 
    --limit 10
```

## 背景

MySQL Performance Schema 是一个用于监控数据库运行时性能的功能。通过启用 Performance Schema,你可以收集有关数据库服务器操作的详细信息,比如查询执行时间、索引使用情况、表锁定信息等。这些数据对于理解数据库的性能特性和瓶颈非常有帮助。

与传统的慢查询日志和 `SHOW PROFILE` 等工具相比,Performance Schema 提供了更全面、更细粒度的性能数据,同时对系统性能的影响也更小。你可以通过简单的程序处理来统计 SQL 的执行频率和延迟。

## 功能

本工具可以统计出 Top 慢查询 SQL,以及每个查询的详细分析,包括:

- 执行次数
- 总执行时间
- 平均执行时间
- 发送的行数
- 检查的行数

这些指标是优化查询性能的重要参考依据,可以帮助数据库管理员和开发人员识别需要优化的查询,并了解查询的整体性能特征。

## 使用方法

1. 确保你的 MySQL 版本支持 Performance Schema 并已启用。
2. 克隆本仓库到本地。
3. 根据你的需求修改配置文件。
4. 通过sysbench工具生成测试数据库及10张数据表，每个数据表装填100w条测试数据。
5. slow-query-generator.py脚本可以随机生成测试SQL，涵盖不同的查询方式in，or，join等操作组成，模拟不同场景下的SQL，你也可以直接利用项目中提供的sql_queries.sql。
6. slow-query-execute-query.py脚本对MySQL数据库进行随机查询。
7. 运行slow-query-digest.py脚本,查看和统计慢SQL语句，该脚本可以统计出top SQL，以及每个查询的详细分析，包括执行次数、总执行时间、平均执行时间、发送的行数和检查的行数；这些指标是优化查询性能的重要参考依据，可以帮助数据库管理员和开发人员识别需要优化的查询，并了解查询的整体性能特征。

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

=============================Disclaimer========================================
The sample code or script or other assets are provided as Service Content (in the case that you are using Amazon Web Services China regions) or AWS Content (in the case that you are using Amazon Web Services regions outside Mainland China) (“Assets”) under the Customer Agreement or the relevant written agreement between you and the operator of the relevant Amazon Web Services region (whichever applies). You should not use the Assets in your production accounts, or on production or other critical data. You are responsible for testing, securing, and optimizing the Assets, as appropriate for production grade use based on your specific quality control practices and standards.  Deploying the Assets may incur charges for creating or using Amazon Web Services chargeable resources, such as running Amazon EC2 instances or using Amazon S3 storage.
示例代码或脚本或其他资料（“资料”）作为您与相关亚马逊云科技区域运营商之间的客户协议或相关书面协议（以适用者为准）下的“服务内容”（如果您使用亚马逊云科技中国区域）或“AWS 内容”（如果您使用中国大陆以外的亚马逊云科技区域）而提供给您。您不应在您的生产账户中使用“资料”，也不应将“资料”用于您的生产或其他关键数据。您负责根据您的特定质量控制实践和标准对“资料”进行测试、采取安全措施和优化，以适合生产级用途。部署“资料”可能会因创建或使用亚马逊云科技收费资源（例如运行Amazon EC2 实例或使用 Amazon S3 存储）而产生费用。
=============================End of disclaimer ===================================