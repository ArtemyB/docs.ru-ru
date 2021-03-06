---
title: "Практическое руководство. Предоставление доступа к сертификатам X.509 для WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e03a38e2a93dd866bc3da65527d5410b09009e00
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Практическое руководство. Предоставление доступа к сертификатам X.509 для WCF
Чтобы сделать сертификат X.509 доступным для [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], в коде приложения необходимо указать имя хранилища сертификатов и его расположение. В некоторых случаях идентификатор процесса должен иметь доступ к файлу, который содержит закрытый ключ, связанный с сертификатом X.509. Чтобы получить закрытый ключ, связанный с сертификатом X.509 в хранилище сертификатов, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] должен иметь соответствующее разрешение. По умолчанию доступ к закрытому ключу сертификата имеют только владелец и системная учетная запись.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Предоставление доступа к сертификатам X.509 для WCF  
  
1.  Предоставьте учетной записи, от имени которой выполняется [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], доступ для чтения к файлу, содержащему закрытый ключ, который связан с сертификатом X.509.  
  
    1.  Определите, требуется ли для [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] доступ для чтения к закрытому ключу для сертификата X.509.  
  
         В следующей таблице приводятся сведения о том, должен ли закрытый ключ быть доступным при использовании сертификата X.509.  
  
        |Использование сертификата X.509|Закрытый ключ|  
        |---------------------------|-----------------|  
        |Цифровая подпись исходящего сообщения SOAP.|Да|  
        |Проверка подписи входящего сообщения SOAP.|Нет|  
        |Шифрование исходящего сообщения SOAP.|Нет|  
        |Расшифровка входящего сообщения SOAP.|Да|  
  
    2.  Определите расположение и имя хранилища сертификатов, в котором хранится сертификат.  
  
         Хранилище сертификатов, в котором хранится сертификат, задается в коде приложения или конфигурации. Например, в следующем примере задано, что сертификат расположен в хранилище сертификатов `CurrentUser` с именем `My`.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  Определить, где находится закрытый ключ для сертификата на компьютере с помощью [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) средства.  
  
         [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) имя хранилища сертификатов, расположение хранилища сертификатов и что-то, которое однозначно идентифицирует этот сертификат для запуска этого средства. Средство принимает имя субъекта сертификата или его отпечаток в качестве уникального идентификатора. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]как определить отпечаток для сертификата см. в разделе [как: извлечение отпечатка сертификата](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         Следующий пример кода использует [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) , которая позволяет определить расположение файла закрытого ключа для сертификата в `My` хранить в `CurrentUser` с отпечатком `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  Определите учетную запись, в которой выполняется [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
         В следующей таблице описана учетная запись, в которой выполняется [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] для данного сценария.  
  
        |Сценарий|Идентификатор процесса|  
        |--------------|----------------------|  
        |Клиент (консоль или приложение WinForms).|Текущий пользователь.|  
        |Служба, являющаяся резидентной.|Текущий пользователь.|  
        |Служба, размещенная в IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) или IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).|NETWORK SERVICE|  
        |Служба, размещенная в IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).|Управляется с помощью элемента `<processModel>` в файле Machine.config. По умолчанию используется учетная запись ASPNET.|  
  
    5.  С помощью соответствующего средства (например, cacls.exe) предоставьте учетной записи, в которой выполняется [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], доступ для чтения к файлу, содержащему закрытый ключ.  
  
         В следующем примере кода изменяется (/E) список управления доступом (ACL) для заданного файла, чтобы предоставить (/G) учетной записи NETWORK SERVICE доступ для чтения (:R) к файлу.  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>См. также  
 [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [Как: извлечение отпечатка сертификата](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [Работа с сертификатами](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
