---
title: Power BI 权限
description: Power BI 权限
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 09/05/2017
ms.author: maghan
ms.openlocfilehash: 4ba0e62dd8c9ba537f56c97489541591ec0bf2bc
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "34289409"
---
# <a name="power-bi-permissions"></a>Power BI 权限
## <a name="permission-scopes"></a>权限范围
Power BI 权限使应用程序能够代表用户执行某些操作。 所有权限均必须经过用户批准才有效。

| 显示名称 | 说明 | 范围值 |
| --- | --- | --- |
| 查看所有数据集 |该应用可以查看已登录用户的所有数据集以及该用户有权访问的数据集。 |Dataset.Read.All |
| 读写所有数据集 |该应用可以查看和写入已登录用户的所有数据集以及该用户有权访问的数据集。 |Dataset.ReadWrite.All |
| 将数据添加到用户的数据集（预览） |对应用授予添加或删除用户的数据集行的访问权限。 此权限不会对应用授予访问用户数据的权限。 |Data.Alter_Any |
| 创建内容（预览） |应用可以自动为用户创建内容和数据集。 |Content.Create |
| 查看用户组 |该应用可以查看已登录用户所属的所有组。 |Group.Read |
| 查看所有组 |该应用可以查看已登录用户所属的所有组。 |Group.Read.All |
| 查看所有仪表板（预览） |该应用可以查看已登录用户的所有仪表板以及该用户有权访问的仪表板。 |Dashboard.Read.All |
| 查看所有报表（预览） |该应用可以查看已登录用户的所有报表以及该用户有权访问的报表。 该应用还可以查看报表数据及其结构。 |Report.Read.All |
| 读取和写入所有报表 |该应用可以查看和写入已登录用户的所有报表以及该用户有权访问的任何报表。 这不提供创建新报表的权限。 |Report.ReadWrite.All |

首次尝试登录用户的页面时，应用程序可以请求权限，通过在该调用的范围参数中传入所请求的权限实现。 如果授予了该权限，则将向该应用返回一个访问令牌，可在将来的 API 调用上使用该令牌。 该访问权限只能由特定应用程序使用。

> [!NOTE]
> Power BI API 仍将应用工作区视作为组。 对组的任何引用意味着正在使用应用工作区。
> 
> 

## <a name="requesting-permissions"></a>请求权限
虽然你可以调用 API 通过用户名和密码进行验证，以便代表其他用户进行操作，但是他们将需要请求该用户随后批准的权限，然后将生成的访问令牌发送到所有的将来的调用。 对于此过程，我们将遵循标准 [OAuth 2.0](http://oauth.net/2/) 协议。 尽管实际实现可能会有所不同，但 Power BI 的 OAuth 流具有以下元素：

* **登录 UI** - 这是一个开发人员可以调用来请求权限的 UI。 如果用户尚未登录，它将要求该用户登录。 用户还需要批准应用程序请求的权限。 登录窗口将回发访问代码或错误消息，以重定向提供的 URL。
  * 标准重定向 URL 应由 Power BI 提供，以由本机应用程序使用。
* **授权代码** - 通过重定向 URL 中的 URL 参数登录后，授权代码将返回到 Web 应用程序。 由于它们是参数形式，因此存在某些安全风险。 Web 应用程序将必须使用授权代码交换授权令牌
* **授权令牌** - 用于代表其他用户对 API 调用进行验证。 它们将限制用于特定应用程序。 令牌具有已设定的生命周期，过期时，需要将其进行刷新。
* **刷新令牌** - 令牌过期时，将有一个刷新它们的过程。

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)

