---
title: "Поддержка нескольких привязок узла IIS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bf2dbccd81b9c2e7b4ec78863d3de0227baedf92
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="supporting-multiple-iis-site-bindings"></a>Поддержка нескольких привязок узла IIS
При размещении службы [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] в каталоге служб IIS 7.0 может понадобиться предоставить несколько базовых адресов, использующих один и тот же протокол на одном и том же узле. Это позволяет одной и той же службе отвечать на несколько разных URI. Это может оказаться полезным в том случае, если необходимо разместить службу, следящую за http://www.contoso.com и http://contoso.com, Также может использоваться при создании службы, имеющей базовый адрес для внутренних пользователей и отдельный базовый адрес для внешних пользователей. Пример: http://internal.contoso.com и http://www.contoso.com.  
  
> [!NOTE]
>  Эта функция доступна только при использовании протокола HTTP.  
  
## <a name="multiple-base-addresses"></a>Несколько базовых адресов  
 Данная функция доступна только в службах [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], размещенных в службах IIS. Эта функция отключена по умолчанию. Чтобы включить, то необходимо добавить `multipleSiteBindingsEnabled` атрибут <`serviceHostingEnvironment`> элемент в файл Web.config файл и присвойте ему значение `true`, как показано в следующем примере.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 При размещении службы [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] в службах IIS создается один базовый адрес на основе URI в виртуальном каталоге, содержащем приложение. Чтобы добавить одну или несколько привязок, можно с помощью диспетчера служб IIS добавить на веб-сайт дополнительные базовые адреса, использующие тот же протокол. Для каждой привязки укажите протокол (HTTP или HTTPS), IP-адрес, порт и имя узла. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]с помощью диспетчера служб IIS, в разделе [диспетчера служб IIS (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Добавление привязки к сайту, в разделе [создать веб-сайт (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Указание нескольких базовых адресов для одного и того же узла влияет на содержимое страницы справки [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], импорт схемы и сведения WSDL/MEX, сформированные службой. Страница справки [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] отображает командную строку для создания клиента [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], способного взаимодействовать со службой. Эта командная строка содержит только первый адрес, указанный в привязке служб IIS для веб-сайта. Аналогичным образом при импорте схемы используется только первый базовый адрес, указанный в привязке служб IIS. Данные WSDL и MEX содержит все базовые адреса, указанные в привязках служб IIS.  
  
> [!WARNING]
>  Это означает, что если служба имеет два базовых адреса (для внутренних и для внешних пользователей), то оба они указываются в данных WSDL/MEX, сформированных службой.
