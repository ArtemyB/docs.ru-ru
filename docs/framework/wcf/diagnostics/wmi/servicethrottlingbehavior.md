---
title: ServiceThrottlingBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59f85a148d6707876a4df512d5cfbd07ca0e54b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="servicethrottlingbehavior"></a>ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## <a name="syntax"></a>Синтаксис  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a>Методы  
 Класс ServiceThrottlingBehavior не определяет никаких методов.  
  
## <a name="properties"></a>Свойства  
 Класс ServiceThrottlingBehavior имеет следующие свойства.  
  
### <a name="maxconcurrentcalls"></a>MaxConcurrentCalls  
 Тип данных: sint32  
  
 Тип доступа: только для чтения  
  
 Максимальное количество сообщений, которые могут одновременно обрабатываться во всех объектах диспетчера в узле ServiceHost.  
  
### <a name="maxconcurrentinstances"></a>MaxConcurrentInstances  
 Тип данных: sint32  
  
 Тип доступа: только для чтения  
  
 Максимальное число объектов службы, которые могут выполняться одновременно.  
  
### <a name="maxconcurrentsessions"></a>MaxConcurrentSessions  
 Тип данных: sint32  
  
 Тип доступа: только для чтения  
  
 Максимальное число сеансов, одновременно принимаемых узлом.  
  
## <a name="requirements"></a>Требования  
  
|MOF|Объявлено в файле Servicemodel.mof.|  
|---------|-----------------------------------|  
|Пространство имен|Определено в root\ServiceModel.|  
  
## <a name="see-also"></a>См. также  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
