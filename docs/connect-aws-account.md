# 第一次登录如何连接 AWS 账号？

如果您是第一次连接到Stompy，请参考此页面上的步骤，此页面的目的是想获取您的AWS成本和使用率报告（CUR）以为您提供成本优化建议并执行自动化操作。我们建议您在 ap-southeast-1（新加坡）AWS 区域执行此过程中的所有操作，包括将 CUR 文件生成到 ap-southeast-1 中的S3存储桶中，以降低访问Stompy的网络延迟。

## 主要步骤：

### 第一步：登录您的 AWS 账号

1. 注册后登录，进入连接页面，点击 **登录**

<img src="/_images/aws-login.png" />

2. 登录您的AWS根账号

> 建议您登录AWS根账号，因为AWS根账号能获取组织中其它账号的花费数据，并且能将成本优化方案应用到其它账号。

<img src="/_images/aws-root-login.png" />


### 第二步：选择您需要的产品权限

* StompyAnalySaver产品可为您提供花费分析，成本优化建议并自动化执行。
* StompySpoTainer可为您自动扩容、缩容管理实例组，使用算法最大化利用Spot实例为您节省成本，并为您提供Spot实例中断自动解决方案。

> 若您没有特殊的AWS账号管理习惯和需求，建议您直接用AWS根账号添加两个产品权限。

> 若您有特定的AWS生产账号来专门跑实例，建议您登录AWS生产账号，并添加Stompy SpoTainer权限。

> 若您想查看更全面的成本优化建议并自动化执行，建议您另注册一个Stompy账号，并登录AWS根账号，并添加StompyAnalySaver权限，因为AWS根账号能获取组织中其它账号的花费数据，并且能将成本优化方案应用到其它账号。

 

### 第三步：添加 StompyAnalySaver 权限

1. 进入AWS管理控制台后，点击右上角个人账号，选择**我的账号**，激活IAM用户和角色访问账单信息的权限。

<img src="/_images/aws-root-login.png" />

![wecom-temp-b1f92eed0435665c0af9eb05fa964ed6](/var/folders/hr/3ggfjhcj5nxcpd0wtwfkx_040000gn/T/com.tencent.WeWorkMac/wecom-temp-b1f92eed0435665c0af9eb05fa964ed6.png)

![img](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image004.png)

![图形用户界面, 文本, 应用程序  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image006.png)

2. 打开成本和使用率报告Cost and Usage Reports（CUR）

1). 若您已有CUR满足以下条件，则可直接将存放CUR的S3桶名称复制粘贴到Stompy。

a. 在附加报告详细信息下包括资源 ID。

b. 启用数据刷新设置。

c. 时间粒度为每小时。

d. 使用 Amazon Athena 集成报告数据。

![图形用户界面, 文本, 应用程序, 电子邮件, 网站  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image007.png)

![图形用户界面, 文本, 应用程序  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image008.png)

![图形用户界面, 文本, 应用程序  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image009.png)

2). 若没有CUR满足以上条件，则需创建新的CUR：

![图形用户界面, 文本, 应用程序, 电子邮件  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image010.png)

a. 创建您的CUR报告，并为之命名，确保您的报告细节和数据刷新的设置均已被勾选上，点击“继续”。

![图形用户界面, 文本, 应用程序  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image011.png)

b. 选择CUR存放的S3桶，若您已有新加坡地区的S3桶，选中即可；若没有，则需创建您的S3桶，为之命名，并选择区域为“新加坡”，这很重要，若您没有选择新加坡，我们为您获取数据时可能会有一定的延迟，点击“继续”。

![图形用户界面, 应用程序  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image012.png)

c. 勾选“我已确认政策无误”，并点击“保存”。

![图形用户界面, 文本, 应用程序  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image013.png)

若系统提示您的S3桶名称已存在，返回重新命名即可。

![图形用户界面, 文本, 应用程序, 电子邮件  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image014.png)

d. 为您的报告路径命名（S3桶中存储CUR的路径名称），确保时间间隔选每小时，报表数据集成于“Amazon Athena”，Compression type用Parquet, 点击“继续”。

![图形用户界面, 应用程序  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image015.png)

e. 在交付选项处，复制S3桶的名称，点击“检查和完成”。

![图形用户界面, 文本, 应用程序, 电子邮件  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image016.png)

f. 如果您之前没有设置过CUR，这里需要等24-48个小时(取决于您的数据量)，等待AWS官方处理完毕后，回到Stompy页面，粘贴S3桶名称，点击确认。

![img](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image009.png)

3. 点击“运行模板”。

![img](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image017.png)

4. 页面跳转到AWS的CloudFormation页面后，勾选“我已知晓AWS CloudFormation可能会创建IAM资源”，点击“创建堆栈”。

![img](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image018.png)

5. 等待AWS运行完成后，过程大概需要几分钟（运行过程可在“Events”一栏查看），在“输出”一栏复制“值”，粘贴到Stompy页面。

![img](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image019.png)

![图形用户界面, 文本, 应用程序  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image020.png)

 

### 第四步：添加 StompySpoTainer 权限

1.  点击“运行模板”。

![图形用户界面, 文本, 应用程序  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image021.png)

2. 页面跳转到AWS的CloudFormation页面后，勾选“我已知晓AWS CloudFormation可能会创建IAM资源”，点击“创建堆栈”。

![图形用户界面, 文本, 应用程序, 电子邮件  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image022.png)

3. 等待AWS运行完成后，过程大概需要几分钟（运行过程可在“Events”一栏查看），在“输出”一栏复制“值”，粘贴到Stompy页面。

![图形用户界面, 应用程序, 电子邮件  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image023.png)

![图形用户界面, 应用程序  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image024.png)

4. 点击连接，完成！

![图形用户界面, 文本, 应用程序, 电子邮件  描述已自动生成](file:////Users/kchou/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image025.png)