---
title: 第三方服务：适用于 Power BI Desktop 的 Facebook 连接器
description: 第三方服务：适用于 Power BI Desktop 的 Facebook 连接器
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 48009ea065909c75d4629f9c669d1bfa6d88646d
ms.sourcegitcommit: f01a88e583889bd77b712f11da4a379c88a22b76
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2018
ms.locfileid: "39330434"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>适用于 Power BI Desktop 的 Facebook 连接器
**Power BI Desktop** 中的 Facebook 连接器依赖于 Facebook Graph API。 同样，功能和可用性可能会随着时间推移有所不同。

你可以查看 [Power BI Desktop 的 Facebook 连接器的相关教程](desktop-tutorial-facebook-analytics.md)。

Facebook 的 Graph API v1.0 已在 2015 年 4 月 30 日<sup></sup>过期。 Power BI 在后台对 Facebook 连接器使用 Graph API，从而允许你连接到你的数据并对其进行分析。

2015 年 4 月 30 日<sup></sup>之前生成的查询可能将不再工作或返回更少的数据。 2015 年 4 月 30 日<sup></sup>之后，Power BI 将在所有对 Facebook API 调用中使用 v2.8。 如果你的查询在 2015 年 4 月 30 日之前生成，并且从那以后再也没有使用，你可能需要重新进行验证，以批准我们将要求的新权限集。

尽管我们尝试依照任何更改发布更新，API 可能会以影响我们生成的查询的结果的方式进行更改。 在某些情况下，某些查询可能不再受支持。 由于此依赖关系，使用此连接器时，我们无法保证你的查询的结果。

可在[此处](https://developers.facebook.com/docs/apps/changelog#v2_0)了解有关 Facebook API 中更改的详细信息。

