---
title: "Программа конфигурации WS-AtomicTransaction (wsatConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59b56b542a1624f1bae332ab91e1ac835aa47c8b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2017
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Программа конфигурации WS-AtomicTransaction (wsatConfig.exe)
Программа настройки WS-AtomicTransaction используется для настройки основных параметров поддержки WS-AtomicTransaction.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Примечания  
 Эту программу командной строки можно использовать для настройки основных параметров WS-AT только на локальном компьютере. Если для настройки параметров на локальном и удаленном компьютерах, следует использовать оснастку MMC как описано в [Настройка поддержки транзакций WS-AT](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Программу командной строки можно найти в папке установки пакета Windows SDK:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe  
  
 Если используется [!INCLUDE[wxp](../../../includes/wxp-md.md)] или [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], необходимо выполнить загрузку и обновление перед запуском WsatConfig.exe. Дополнительные сведения об этом обновлении см. в разделе [обновления для Commerce Server 2007 (KB912817)](http://go.microsoft.com/fwlink/?LinkId=95340) и [доступности из Windows XP COM + исправление свертки пакета 13](http://go.microsoft.com/fwlink/?LinkId=95341).  
  
 В следующей таблице представлены параметры, которые можно использовать с программой настройки WS-AtomicTransaction (wsatConfig.exe).  
  
> [!NOTE]
>  При задании SSL-сертификата для выбранного порта выполняется перезапись исходного SSL-сертификата (если он существует), связанного с этим портом.  
  
|Параметры|Описание|  
|-------------|-----------------|  
|— учетные записи:\<учетной записи >|Позволяет указать список разделенных запятыми учетных записей, которые могут участвовать в WS-AtomicTransaction. Проверка допустимости этих учетных записей не выполняется.|  
|-accountsCerts:\<thumb > &#124;» Issuer\SubjectName» >|Позволяет указать список разделенных запятыми сертификатов, которые могут участвовать в WS-AtomicTransaction. Сертификаты указываются отпечатком или парой Issuer\SubjectName. В качестве пустого имени субъекта используйте {EMPTY}.|  
|-endpointCert: < machine &#124; \<thumb > &#124;» Issuer\SubjectName» >|Позволяет использовать сертификат компьютера или другой сертификат локальной конечной точки, указанный отпечатком или парой Issuer\SubjectName. В качестве пустого имени субъекта используйте {EMPTY}.|  
|-maxTimeout:\<сек >|Позволяет указать максимальное время ожидания в секундах. Допустимые значения: от 0 до 3600.|  
|-сети:\<включить &#124; отключить >|Позволяет включить или отключить сетевую поддержку WS-AtomicTransaction.|  
|-порта:\<portNum >|Позволяет задать HTTPS-порт для WS-AtomicTransaction.<br /><br /> Если брандмауэр был включен перед запуском данного средства, порт автоматически регистрируется в списке исключений. Если брандмауэр был отключен перед запуском данного средства, никакой дополнительной настройки относительно брандмауэра не выполняется.<br /><br /> В случае включения брандмауэра после настройки WS-AT необходимо повторно запустить данное средство и указать номер порта с помощью этого параметра. В случае отключения брандмауэра после настройки WS-AT продолжает работу без ввода дополнительных данных.|  
|время ожидания-:\<сек >|Позволяет указать время ожидания по умолчанию в секундах. Диапазон допустимых значений: 1–3600.|  
|-traceActivity:\<включить &#124; отключить >|Позволяет включить или отключить трассировку событий, связанных с выполнением действий.|  
|-traceLevel:\<выкл &#124; Ошибка &#124; Критические &#124; Предупреждение &#124; сведения о &#124; Verbose &#124; Все >}|Позволяет задать уровень трассировки.|  
|-tracePII:\<включить &#124; отключить >|Позволяет включить или отключить трассировку персональных данных.|  
|-traceProp:\<включить &#124; отключить >|Позволяет включить или отключить трассировку событий, связанных с распространением.|  
|-restart|Позволяет перезапустить координатор MSDTC для мгновенного вступления изменений в силу. Если этот параметр не указан, изменения вступают в силу только после перезапуска координатора MSDTC.|  
|-show|Отображает текущие параметры протокола WS-AtomicTransaction.|  
|-Виртуальный_сервер:\<Виртуальный_сервер >|Позволяет указать имя кластера ресурсов DTC.|  
  
## <a name="see-also"></a>См. также  
 [С помощью WS-AtomicTransaction](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)  
 [Настройка поддержки транзакций WS-AT](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
