---
title: "Практическое руководство. Выполнение запросов к службе данных (службы данных WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 333c11150994ccdbe3dd6e8fd7349610d924806d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Практическое руководство. Выполнение запросов к службе данных (службы данных WCF)
Службы [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] позволяют выполнять запросы к службе данных из клиентского приложения на основе .NET Framework с использованием сформированных клиентских классов службы данных. Выполнять запросы можно одним из следующих способов.  
  
-   Выполнение запроса LINQ к именованному объекту <xref:System.Data.Services.Client.DataServiceQuery%601>, который получен из контекста <xref:System.Data.Services.Client.DataServiceContext>, сформированного программой `Add Data Service Reference`.  
  
-   Неявное перечисление именованного объекта <xref:System.Data.Services.Client.DataServiceQuery%601>, который получен из контекста <xref:System.Data.Services.Client.DataServiceContext>, сформированного программой `Add Data Service Reference`.  
  
-   Явный вызов метода <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> с объектом <xref:System.Data.Services.Client.DataServiceQuery%601> или метода <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> для асинхронного выполнения.  
  
 Дополнительные сведения см. в разделе [запросы к службе данных](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Пример в этом разделе использует образец службы данных Northwind и автоматически сформированные клиентские классы службы данных. Эта служба и клиентские классы данных создаются после выполнения [краткое руководство по службам WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Пример  
 Следующий пример показывает, как определить и выполнить запрос LINQ, возвращающий все сущности `Customers` в службе данных Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Пример  
 Следующий пример показывает, как использовать контекст, сформированный программой `Add Data Service Reference`, для неявного выполнения запроса, возвращающего все сущности `Customers` в службе данных Northwind. URI запрашиваемого набора сущностей `Customers` автоматически определяется контекстом. Запрос выполняется неявно при запуске перечисления.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Пример  
 Следующий пример показывает, как использовать контекст <xref:System.Data.Services.Client.DataServiceContext> для явного выполнения запроса, который возвращает все сущности `Customers` в службе данных Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>См. также  
 [Как: Добавление параметров запроса к запросу службы данных](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
