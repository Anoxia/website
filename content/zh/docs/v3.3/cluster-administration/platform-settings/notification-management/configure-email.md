---
title: "配置邮件通知"
keywords: 'KubeSphere, Kubernetes, 自定义, 平台'
description: '配置邮件服务器并添加接收人以接收邮件通知。'
linkTitle: "配置邮件通知"
weight: 8722
---

本教程演示如何配置邮件通知及添加接收人，以便接收告警策略的邮件通知。

## 配置邮件服务器

1. 使用具有 `platform-admin` 角色的用户登录 Web 控制台。

2. 点击左上角的**平台管理**，选择**平台设置**。

3. 导航至**通知管理**下的**通知配置**，选择**邮件**。

4. 在**服务器设置**下，填写以下字段配置邮件服务器。

   - **SMTP 服务器地址**：能够提供邮件服务的 SMTP 服务器地址。端口通常是 `25`。
   - **使用 SSL 安全连接**：SSL 可以用于加密邮件，从而提高通过邮件传输的信息的安全性。通常来说，您必须为邮件服务器配置证书。
   - **SMTP 用户名**：SMTP 用户的名称。
   - **SMTP 密码**：SMTP 帐户的密码。
   - **发件人邮箱**：发件人的邮箱地址。

5. 点击**确定**。

## 接收设置

### 添加接收人

1. 在**接收设置**下，输入接收人的邮箱地址，点击**添加**。

2. 添加完成后，接收人的邮箱地址将在**接收设置**下列出。您最多可以添加 50 位接收人，所有接收人都将能收到通知。

3. 若想移除接收人，请将鼠标悬停在想要移除的邮箱地址上，然后点击右侧的 <img src="/images/docs/v3.3/common-icons/trashcan.png" width='25' height='25' alt="icon" />。

### 设置通知条件

1. 勾选**通知条件**左侧的复选框即可设置通知条件。
   
   - **标签**：告警策略的名称、级别或监控目标。您可以选择一个标签或者自定义标签。
   - **操作符**：标签与值的匹配关系，包括**包含值**，**不包含值**，**存在**和**不存在**。
   - **值**：标签对应的值。
   {{< notice note >}}
   - 操作符**包含值**和**不包含值**需要添加一个或多个标签值。使用回车分隔多个值。
   - 操作符**存在**和**不存在**判断某个标签是否存在，无需设置标签值。
   {{</ notice >}}

2. 您可以点击**添加**来添加多个通知条件。

3. 您可以点击通知条件右侧的 <img src="/images/docs/v3.3/common-icons/trashcan.png" width='25' height='25' alt="icon" /> 来删除通知条件。

4. 配置完成后，您可以点击右下角的**发送测试信息**进行验证。

5. 在右上角，打开**未启用**开关来接收邮件通知，或者关闭**已启用**开关来停用邮件通知。

   {{< notice note >}}
   - 通知条件设置后，接收人只会接受符合条件的通知。
   - 如果您更改了现有配置，则必须点击**确定**以应用更改。

   {{</ notice >}} 

## 接收邮件通知

配置邮件通知并添加接收人后，您需要启用 [KubeSphere 告警](../../../../pluggable-components/alerting/)，并为工作负载或节点创建告警策略。告警触发后，所有接收人都将能收到邮件通知。

{{< notice note >}}

- 如果您更新了邮件服务器配置，KubeSphere 将根据最新配置发送邮件通知。
- 默认情况下，KubeSphere 大约每 12 小时针对同一告警发送通知。告警重复间隔期主要由 `kubesphere-monitoring-system` 项目中 `alertmanager-main` 密钥的 `repeat_interval` 所控制。您可以按需自定义间隔期。
- KubeSphere 拥有内置告警策略，在不设置任何自定义告警策略的情况下，只要内置告警策略被触发，您的接收人仍能收到邮件通知。

{{</ notice >}} 
