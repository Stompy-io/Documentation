# 如何添加 StompySpoTainer 权限？

如果您登录到Stompy页面后无法访问StompyAnalySaver产品，请参考此页面上的步骤以开通您所需的产品权限。我们建议您在 ap-southeast-1（新加坡）AWS 区域执行此过程中的所有操作，包括将 CUR 文件生成到 ap-southeast-1 中的S3存储桶中，以降低访问Stompy的网络延迟。

## 主要步骤：

### 第一步：登录您的AWS账号

1. 打开StompyAnalySaver产品页面，点击“增加权限”。

![img](/_images/stompyspotainer-add-permission.png)

2. 进入到连接页面，点击“登录”，登录您的AWS账号。

![img](/_images/stompyspotainer-step1-login.png)

### 第二步：运行模板

1. 点击“运行模板”。

![img](/_images/stompyspotainer-step2-run.png)

2. 页面跳转到AWS的CloudFormation页面后，勾选“我已知晓AWS Cloudformation可能会创建IAM资源”，点击“创建堆栈”。

![img](/_images/stompyspotainer-cloudformation-create.png)

### 第三步：粘贴SpoTainerRoleArn

1. 等待AWS运行完成后，过程大概需要几分钟（运行过程可在“Events”一栏查看），在“输出”一栏复制“值”，粘贴到Stompy页面，点击“连接”，完成！

![img](/_images/stompyspotainer-cloudformation-status.png)

![img](/_images/stompyspotainer-step3-connect.png)
