---
title: "Изменения среды выполнения в .NET Framework 4.6 | Документы Майкрософт"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6
- application compatibility
ms.assetid: 5262bcfa-6e48-416b-8972-69cb4002d386
caps.latest.revision: 34
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 77002c3d1b6553156c225b3efba9a2f29009915a
ms.contentlocale: ru-ru
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-46"></a>Изменения среды выполнения в .NET Framework 4.6
В редких случаях изменения среды выполнения могут повлиять на существующие приложения, предназначенные для предыдущих версий .NET Framework, но выполняющиеся в более поздней версии среды выполнения .NET Framework. Они также включают различия в поведении между приложениями, которые выполняются в разных средах .NET Framework. Они включают изменения в следующих областях.  
  
-   [Ядро](#Core)  
  
-   [Данные](#Data)  
  
-   [Сеть](#Networking)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [Установка и развертывание](#Setup)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [Новый 64-разрядный JIT-компилятор](#RyuJIT)  
  
<a name="Core"></a>   
## <a name="core"></a>Ядро  
  
|Функция|Изменение|Последствия|Область|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|Начиная с [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], класс <xref:System.Globalization.PersianCalendar> использует алгоритм солнечного календаря хиджры.|Этот алгоритм получает результаты, идентичные персидскому календарю, который в настоящее время используется в Иране и Афганистане. Он также выдает результаты, которые совпадают с предыдущим алгоритмом для дат с 1800 по 2023 гг. по григорианскому календарю. Даты вне этого диапазона могут отличаться, если класс <xref:System.Globalization.PersianCalendar> используется для преобразований дат (например, дат по григорианскому календарю в даты по персидскому календарю) или для определения високосного года.<br /><br /> Из-за этого изменения значение свойства <xref:System.Globalization.PersianCalendar.MinSupportedDateTime%2A?displayProperty=fullName> изменено с 21 марта 0622 г. на 22 марта 0622 г. для систем, на которых установлено [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].<br /><br /> Дополнительные сведения см. в разделе <xref:System.Globalization.PersianCalendar>.|Дополнительный номер|  
|<xref:System.Runtime.Versioning.TargetFrameworkAttribute>|Для домена приложения по умолчанию значение свойства <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> определяется по атрибуту <xref:System.Runtime.Versioning.TargetFrameworkAttribute>, если таковой имеется, и если оно не определено явно путем назначения имени свойству <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName>.  В предыдущих версиях платформы .NET Framework значение атрибута <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> равнялось `null`, если не было выполнено несколько путей специального кода или не создан домен приложения, отличный от домена по умолчанию, без явного указания целевой платформы в свойстве <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName>.<br /><br /> Для доменов приложения, отличных от домена по умолчанию, изменений в способе определения значения свойства <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> нет. Если свойству <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> не задается явное значение, домен приложения, отличный от домена по умолчанию, наследует имя целевой платформы из домена приложения по умолчанию.|Для домена приложения по умолчанию метод <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> может вернуть непустое значение, если ранее возвращал `null`. Это желаемое поведение.|Пограничный случай|  
|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|Если платформой .NET Framework не поддерживается ни один из сертификатов, установленных в системе, при передаче значения `True` для аргумента `verbose` возвращается допустимая строка. В предыдущих версиях .NET Framework при попытке доступа к информации об открытом ключе для неподдерживаемых сертификатов иногда возникало исключение.|Этот метод является только информационным; в документации отмечено, что выходные данных могут быть не согласованы между версиями .NET Framework. Это значение влияет только на приложения, которые вызывают метод `ToString(True)` и установили сертификаты, не поддерживаемые .NET Framework. Это изменение обеспечивает надежность метода, возвращая строку, а не вызывая исключение.|Пограничный случай|  
|трассировка событий Windows (ETW)|В [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] и 4.6.1 среда выполнения вызывает исключение <xref:System.ArgumentException> в случае, когда имена двух событий отличаются только суффиксами "Start" или "Stop" (например, одно событие с именем `LogUser`, а другое с именем `LogUserStart`). В этом случае среда выполнения не может определить источник событий и, соответственно, сделать запись в журнале.|Проверьте, нет ли событий, имена которых отличаются друг от друга только суффиксами "Start" или "Stop".<br /><br /> Это требование снимается, начиная с [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]. Среда выполнения может устранить неоднозначность событий, имена которых отличаются только суффиксом "Start".|Пограничный случай|  
|Отражение и распределенная модель COM (DCOM)|Объекты отражения больше невозможно передавать из управляемого кода во внепроцессные клиенты DCOM. Это влияет на следующие типы: <xref:System.Reflection.Assembly>; <xref:System.Reflection.MemberInfo> и его производные типы, включая <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Type> и <xref:System.Reflection.TypeInfo>; <xref:System.Reflection.MethodBody>; <xref:System.Reflection.Module> и <xref:System.Reflection.ParameterInfo>.|Вызовы [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707.aspx) для возврата объекта `E_NOINTERFACE`.|Дополнительный номер|  
  
<a name="Data"></a>   
## <a name="data"></a>Данные  
  
|Функция|Изменение|Последствия|Область|  
|-------------|------------|------------|-----------|  
|Подключение к базе данных SQL Server по протоколу TCP/IP, которому сопоставляется `localhost`|Начиная с [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], происходит сбой попытки подключения с сообщением "Произошла ошибка, связанная с сетью или экземпляром, при установлении соединения с SQL Server". Сервер не найден или недоступен. Проверьте правильность имени экземпляра и настройку сервера SQL Server для удаленных подключений. (поставщик: сетевые интерфейсы SQL, ошибка: 26 — ошибка поиска указанного сервера/экземпляра)"|Эта проблема устранена, и восстановлено прежнее поведение в [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]. Для подключения к базе данных SQL Server, которому сопоставляется `localhost`, выполните обновление до [!INCLUDE[net_v462](../../../includes/net-v462-md.md)].|Дополнительный номер|  
  
<a name="Networking"></a>   
## <a name="networking"></a>Сетевое взаимодействие  
  
|Функция|Изменение|Последствия|Область|  
|-------------|------------|------------|-----------|  
|Значения даты и времени в классе <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>.|Чтобы обеспечить соответствие требованиям [RFC822](http://www.ietf.org/rfc/rfc0822.txt) и [RFC2822](http://www.ietf.org/rfc/rfc2822.txt), форматированное значение даты и времени теперь имеет двузначные часы. Ранее значения часа до 10:00 указывались одной цифрой.|Это изменение влияет на следующие сценарии использования:<br /><br /> – Сравнение длин или хэш-кодов сериализованных объектов <xref:System.Net.Mime.ContentDisposition> в версиях .NET Framework.<br />– Сравнение возвращаемых значений метода <xref:System.Net.Mime.ContentDisposition.ToString%2A> или строковых представлений значений свойства даты и времени <xref:System.Net.Mime.ContentDisposition> у разных версий .NET Framework.|Дополнительный номер|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|Функция|Изменение|Последствия|Область|  
|-------------|------------|------------|-----------|  
|Службы WCF, использующие NETTCP с уровнем безопасности SSL и проверкой подлинности сертификатов|В платформе .NET Framework 4.6 в список протоколов WCF SSL по умолчанию добавляются протоколы TLS 1.1 и TLS 1.2. Если на клиентском компьютере и на сервере установлена платформа .NET Framework 4.6 или более поздняя версия, для согласования используется протокол TLS 1.2.|Протокол TLS 1.2 не поддерживает проверку подлинности MD5. Поэтому, если используется сертификат MD5, клиент WCF не сможет подключиться к службе WCF. Дополнительные сведения см. в разделе [Устранение рисков. Службы WCF и проверка подлинности сертификатов](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).|Дополнительный номер|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|Функция|Изменение|Последствия|Область|  
|-------------|------------|------------|-----------|  
|Отрисовка окон при использовании нескольких мониторов|Все содержимое окна выводится без обрезки, если изображение выходит за пределы одного экрана при использовании нескольких мониторов.|См. раздел [Устранение рисков. Отрисовка окна WPF](../../../docs/framework/migration-guide/mitigation-wpf-window-rendering.md).|Дополнительный номер|  
|Проверка орфографии в элементах управления WPF с поддержкой текста|При работе в Windows 10 функция проверки орфографии может не работать, поскольку возможности проверки орфографии платформы доступны только для языков из списка языков ввода.|В Windows 10 при добавлении языка в список доступных клавиатур Windows автоматически загружает и устанавливает соответствующий пакет компонента по запросу (FOD), который предоставляет возможности проверки орфографии. При добавлении языка в список языков ввода проверка орфографии будет поддерживаться.|Дополнительный номер|  
  
<a name="Setup"></a>   
## <a name="setup-and-deployment"></a>Установка и развертывание  
  
|Функция|Изменение|Последствия|Область|  
|-------------|------------|------------|-----------|  
|Управление версиями продукта|Управление версиями продукта отличается от предыдущих версий платформы .NET Framework (.NET Framework 4, 4.5, 4.5.1 и 4.5.2). Дополнительные сведения см. в разделе [Устранение рисков. Управление версиями продукта](../../../docs/framework/migration-guide/mitigation-product-versioning.md).|См. раздел [Устранение рисков. Управление версиями продукта](../../../docs/framework/migration-guide/mitigation-product-versioning.md).|Средняя|  
  
<a name="ClickOnce"></a>   
## <a name="clickonce"></a>ClickOnce  
  
|Функция|Изменение|Последствия|Область|  
|-------------|------------|------------|-----------|  
|Приложения опубликованы с помощью ClickOnce с использованием сертификата подписи кода SHA-256.|Приложения ClickOnce на платформе [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] или более ранних версий, подписанные с помощью сертификата SHA-256, больше не имеют зависимостей среды выполнения от [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] или более поздней версии.|Ранее для подписки на приложение ClickOnce, предназначенное для [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] или более ранних версий, с помощью сертификата SHA-256 требовалась установка на целевой системе [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] или более поздней версии. Это приводило к ошибкам в случае ее отсутствия. Это изменение удаляет зависимость и позволяет использовать сертификаты SHA-256 для подписи приложений ClickOnce на платформе [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] и более ранних версий.|Дополнительный номер|  
  
<a name="RyuJIT"></a>   
## <a name="the-new-64-bit-jit-compiler"></a>Новый 64-разрядный JIT-компилятор  
  
|Функция|Изменение|Последствия|Область|  
|-------------|------------|------------|-----------|  
|64-разрядная JIT-компиляция|Начиная с .NET Framework 4.6, для JIT-компиляции используется новый 64-разрядный компилятор JIT. Это изменение не влияет на 32-разрядный компилятор JIT.|В некоторых случаях вызывается непредвиденное исключение или наблюдается другое поведение, отличное от такого, какое должно быть при выполнении приложения с использованием 32-разрядного компилятора или старого 64-разрядного компилятора JIT. **Примечание.** Все эти проблемы устранены в новом 64-разрядном компиляторе на платформе .NET Framework 4.6.2. Большинство проблем было также устранено в выпусках обновлений платформы .NET Framework 4.6 и 4.6.1, включенных в состав обновления Windows. <br /><br /> Дополнительные сведения см. в разделе [Устранение рисков. Новый 64-разрядный компилятор JIT](../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md).|Пограничный случай|  
|Обработка исключения (возврат из региона `try`)|В отличие от старого JIT-компилятора JIT64, новый 64-разрядный JIT-компилятор не разрешает инструкцию IL `ret` в области `try`.|Возврат из региона `try` запрещен в спецификации ECMA-335, и ни один известный управляемый компилятор не создает такие IL. Однако компилятор JIT64 выполнит такие IL, если они созданы с помощью порождения отражения.<br /><br /> Если ваше приложение создает IL, включающий в себя код операции `ret` в области `try`, вы можете:<br /><br /> – Использовать платформу .NET Framework 4.5 или добавить элемент [ \<useLegacyJIT>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) в файл конфигурации приложения, чтобы использовать старый JIT-компилятор и не делать изменения.<br />– Изменить созданный IL так, чтобы код располагался после области `try`.<br />-|Пограничный случай|