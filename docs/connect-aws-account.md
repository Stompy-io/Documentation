# 第一次登录如何连接 AWS 账号？

如果您是第一次连接到 Stompy，请参考此页面上的步骤，此页面的目的是想获取您的 AWS 成本和使用率报告（CUR）以为您提供成本优化建议并执行自动化操作。我们建议您在 ap-southeast-1（新加坡）AWS 区域执行此过程中的所有操作，包括将 CUR 文件生成到 ap-southeast-1 中的 S3 存储桶中，以降低访问 Stompy 的网络延迟。

## 主要步骤：

### 第一步：登录您的 AWS 账号

1. 注册后登录，进入连接页面，点击 **登录**。

![img](/_images/aws-login.png)

2. 登录您的 AWS 根账号。

> 建议您登录 AWS 根账号，因为 AWS 根账号能获取组织中其它账号的花费数据，并且能将成本优化方案应用到其它账号。

![img](/_images/aws-root-login.png)



### 第二步：选择您需要的产品权限

* StompyAnalySaver 产品可为您提供花费分析，成本优化建议并自动化执行。
* StompySpoTainer 可为您自动扩容、缩容以管理实例组，使用机器学习和算法为您实现确保可用性下最低成本的自动扩展。

> 若您有使用多个 AWS 账号，不同 Stompy 产品想要不同的 AWS 账号授权，您可以先跳过此连接步骤，重新登录后仍可使用不同的 AWS 账号分别授权不同的 Stompy 产品权限。

> 若您想查看更全面的成本优化建议并自动化执行，建议您登录 AWS 根账号，并添加 StompyAnalySaver 权限，因为 AWS 根账号能获取组织中其它账号的花费数据，并且能将成本优化方案应用到其它账号。

> 若您有特定的 AWS 生产账号来专门跑实例，建议您在此步骤不要勾选 StompySpoTainer，登录 Stompy 平台后可再登录 AWS 生产账号以另外添加 StompySpoTainer 权限。后续步骤可查看：[如何添加StompySpoTainer权限](https://docs.stompy.io/#/get-stompyspotainer-permission)

![img](/_images/aws-stompy-step2.png)



### 第三步：添加 StompyAnalySaver 权限

1. 进入 AWS 管理控制台后，点击右上角个人账号，选择**我的账号**，激活 IAM 用户和角色访问账单信息的权限。

![img](/_images/aws-my-account.png)

![img](/_images/aws-activate-iam-access.png)

2. 打开成本和使用率报告 Cost and Usage Reports（CUR）。

   i. 若您已有 CUR 满足以下条件，则可直接将存放 CUR 的 S3 桶名称复制粘贴到 Stompy。

- 在附加报告详细信息下包括资源 ID。

- 启用数据刷新设置。

- 时间粒度为每小时。

- 使用 Amazon Athena 集成报告数据。

![img](/_images/aws-cost-usage-report.png)

![img](/_images/aws-cost-usage-report-details.png)

![img](/_images/aws-stompy-step3.png)

   ii. 若没有CUR满足以上条件，则需创建新的CUR：

![img](/_images/aws-cost-usage-report-create.png)

a. 创建您的 CUR 报告，并为之命名，确保您的报告细节和数据刷新的设置均已被勾选上，点击**继续**。

![img](/_images/aws-cost-usage-report-create-step.png)

b. 选择 CUR 存放的 S3桶，若您已有新加坡地区的 S3 桶，选中即可；若没有，则需创建您的 S3 桶，为之命名，并选择区域为**新加坡**，这很重要，若您没有选择新加坡，我们为您获取数据时可能会有一定的延迟，点击**继续**。

![img](/_images/aws-cost-usage-report-create-s3.png)

c. 勾选**我已确认政策无误**，并点击**保存**。

![img](/_images/aws-cost-usage-report-create-save.png)

d. 为您的报告路径命名（S3桶中存储CUR的路径名称），确保时间间隔选每小时，报表数据集成于**Amazon Athena**，Compression type 用 Parquet, 点击**继续**。

![img](/_images/aws-cost-usage-report-do.png)

e. 在交付选项处，复制 S3 桶的名称，点击**检查和完成**。

![img](/_images/aws-cost-usage-report-complete.png)

f. 如果您之前没有设置过 CUR，这里需要等24-48个小时(取决于您的数据量)，等待AWS官方处理完毕后，回到 Stompy 页面，粘贴 S3 桶名称，点击**确认**。

![img](/_images/aws-stompy-step3-run.png)

3. 点击**运行模板**。

![img](/_images/aws-stompy-step3-run.png)

4. 页面跳转到 AWS 的 CloudFormation 页面后，勾选**我已知晓 AWS CloudFormation 可能会创建 IAM 资源**，点击**创建堆栈**。

![img](/_images/aws-cloudformation-create.png)

5. 等待 AWS 运行完成后，过程大概需要几分钟（运行过程可在 **Events** 一栏查看），在**输出**一栏复制**值**，粘贴到 Stompy 页面。

![img](/_images/aws-cloudformation-status.png)

![img](/_images/aws-stompy-step3-arn.png)

### 第四步：添加 StompySpoTainer 权限

1.  点击**运行模板**。

![img](/_images/aws-stompy-step4-run.png)

2. 页面跳转到 AWS 的 CloudFormation 页面后，勾选**我已知晓 AWS CloudFormation 可能会创建 IAM 资源**，点击**创建堆栈**。

![img](/_images/aws-cloudformation-create.png)

3. 等待 AWS 运行完成后，过程大概需要几分钟（运行过程可在 **Events** 一栏查看），在**输出**一栏复制**值**，粘贴到 Stompy 页面。

![img](/_images/aws-cloudformation-step4.png)

![img](/_images/aws-stompy-step4-connect.png)

4. 点击**连接**，完成！
