---
title: "Практическое руководство. Указание цепочки сертификатов центра сертификации, используемой для проверки сигнатур (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6cba37a82174ab255cb6814e296154485fbdd54c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Практическое руководство. Указание цепочки сертификатов центра сертификации, используемой для проверки сигнатур (WCF)
Когда [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] получает сообщение SOAP, подписанное с помощью сертификата X.509, по умолчанию проверяется, что сертификат X.509 выдан надежным центром сертификации. Для этого выполняется поиск в хранилище сертификатов и проверяется, отмечен ли соответствующий центр сертификации как надежный. Для выполнения этой проверки, осуществляемой [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], цепь сертификатов центра сертификации должна быть установлена в надлежащем хранилище сертификатов.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Установка цепи сертификатов центра сертификации  
  
-   Для каждого центра сертификации, чьи сертификаты X.509 получатель сообщения SOAP должен считать надежными, установите цепь сертификатов центра сертификации в хранилище сертификатов, из которого [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] извлекает сертификаты X.509 (согласно заданным настройкам).  
  
     Например, чтобы получатель сообщений SOAP считал надежными сертификаты X.509, выданные Microsoft, необходимо, чтобы цепь сертификатов центра сертификации Microsoft была установлена в хранилище сертификатов, в котором [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] выполняет поиск сертификатов X.509 (согласно заданным настройкам). Хранилище сертификатов, в котором [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] выполняет поиск сертификатов X.509, можно указать в коде или конфигурации. Например, здесь можно задать в коде с помощью <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> метода или в конфигурации с несколькими способами, включая [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Поскольку Windows поставляется с комплектом цепочек сертификатов по умолчанию для надежных центров сертификации, в некоторых случаях не требуется устанавливать цепочки сертификатов для всех центров сертификации.  
  
    1.  Экспорт цепи сертификатов центра сертификации.  
  
         Конкретный способ экспорта зависит от центра сертификации. Если центр сертификации использует службы сертификации Microsoft, выберите **Загрузка сертификата ЦС, цепочки сертификатов или CRL**, а затем выберите **Загрузка сертификата ЦС**.  
  
    2.  Импорт цепи сертификатов центра сертификации.  
  
         В консоли управления (MMC), откройте оснастку диспетчера сертификатов. Для сертификата хранилища, на который [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] настроен для получения сертификатов X.509 из выберите **доверенных корневых** **центры сертификации**папки. В разделе **доверенные корневые центры сертификации** папку, щелкните правой кнопкой мыши **сертификаты**папку, выберите пункт **все задачи**и нажмите кнопку **импорта** . Укажите файл, экспортированный на предыдущем этапе.  
  
         [!INCLUDE[crabout](../../../../includes/crabout-md.md)]используя оснастку «Сертификаты» с помощью консоли MMC в разделе [как: Просмотр сертификатов с помощью оснастки MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>См. также  
 [Работа с сертификатами](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
