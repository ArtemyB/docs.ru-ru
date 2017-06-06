---
title: "Основные сведения о проверке подлинности HTTP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Основные сведения о проверке подлинности HTTP
Проверка подлинности — это процесс проверки наличия у клиента права доступа к ресурсу.Протокол HTTP поддерживает проверку подлинности как средство согласования доступа к защищенному ресурсу.  
  
 Исходный запрос от клиента как правило является анонимными и не содержит информацию для проверки подлинности.Приложения сервера HTTP могут отклонить анонимный запрос, если требуется проверка подлинности.Серверное приложение посылает заголовки WWW\-Authentication для обозначения поддерживаемых схем проверки подлинности.Этот документ описывает несколько схем проверки подлинности для протокола HTTP и описывает их реализацию в [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## Схемы проверки подлинности HTTP  
 Сервер может задать несколько доступных схем проверки подлинности для клиента. В следующей таблице описывается несколько схем проверки подлинности, обычно используемых в приложениях Windows.  
  
|Схема проверки подлинности|Описание|  
|--------------------------------|--------------|  
|Anonymous|Анонимный запрос не содержит информацию для проверки подлинности.Это эквивалентно предоставлению доступа к ресурсу без ограничений.|  
|Basic|Обычная проверка подлинности заключается в передаче строки в кодировке Base64, которая содержит имя пользователя и пароль для клиента.Base64 не является формой шифрования, ее следует рассматривать как передачу пароля и имени пользователя открытым текстом.Если требуется защита ресурса, настоятельно рекомендуется использовать схему проверку подлинности, отличную от обычной.|  
|Digest|Дайджест\-проверка подлинности — это схема запроса\-ответа, предназначенная для замены обычной проверки подлинности.Сервер посылает строку случайных данных клиенту, называемую *специальным словом*, в качестве запроса.Клиент отвечает с хэшем, который содержит помимо дополнительной информации имя пользователя, пароль и специальное слово.Хэширование данных и сложность этого обмена усложняют кражу и повторное использование учетных данных пользователя при использовании этой схемы проверки подлинности.<br /><br /> Дайджест\-проверка подлинности требует использования учетных записей домена Windows.*Область* дайджест\-проверки — это имя домена Windows.Поэтому нельзя использовать дайджест\-проверку подлинности на сервере под управлением операционной системы, которая не поддерживает домены Windows \(например Windows XP Home Edition\).И наоборот, если клиент запущен под управлением операционной системы, которая не поддерживает домены Windows, учетная запись домена должна быть явно задана при проверке подлинности.|  
|NTLM|Проверка подлинности NTLM \(NT LAN Manager\) — это схема запроса\-ответа, которая является более безопасным вариантом дайджест\-проверки подлинности.NTLM использует учетные данные Windows для преобразования данных вызова вместо передачи незашифрованных имени пользователя и пароля.Проверка подлинности NTLM требует множественного обмена между клиентом и сервером.Сервер и любой промежуточный прокси\-сервер должны поддерживать постоянные соединения для успешного завершения проверки подлинности.|  
|Negotiate|Проверка подлинности Negotiate, в зависимости от доступности, автоматически выбирает протокол Kerberos или проверку подлинности NTLM.Если доступен, используется протокол Kerberos, в противном случае предпринимается попытка использования протокола NTLM.Проверка подлинности Kerberos обладает существенными преимуществами перед NTLM.Проверка подлинности Kerberos быстрее NTLM и позволяет использовать взаимную проверку подлинности и делегирование учетных данных удаленным компьютерам.|  
|Windows Live ID|Базовая служба HTTP Windows включает проверку подлинности с использованием федеративных протоколов.Тем не менее, стандартный транспорт HTTP в [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] не поддерживает схемы федеративной проверки подлинности, например идентификатор Microsoft Windows Live ID.Поддержка этой функции в данный момент доступна посредством безопасности сообщения.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Федерация и выданные маркеры](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
## Выбор схемы проверки подлинности  
 При выборе потенциальной схемы проверки подлинности для HTTP\-сервера необходимо учитывать несколько моментов.  
  
-   Рассмотрите, требуется ли защита ресурса.Использование проверки подлинности HTTP требует передачи большего объема данных и может ограничить взаимодействие с клиентами.Можно разрешить анонимный доступ к ресурсу, не требующему защиты.  
  
-   Если требуется защита ресурса, проанализируйте, какая схема проверки подлинности обеспечит требуемый уровень безопасности.Самая слабая стандартная схема проверки подлинности — обычная проверка подлинности.Обычная проверка подлинности не защищает учетные данные пользователя.Самая стойкая стандартная схема проверка подлинности — проверка подлинности Negotiate, реализованная в протоколе Kerberos.  
  
-   Сервер не должен \(в заголовках WWW\-Authentication\) предоставлять любую схему, которая не готова принять или обеспечить достаточную защиту безопасного ресурса.Клиент свободен в выборе любой схемы проверки подлинности, предоставляемой сервером.Некоторые клиенты выбирают по умолчанию слабую схему проверки подлинности или первую схему проверки подлинности в списке сервера.  
  
## См. также  
 [Общие сведения о безопасности транспорта](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)   
 [Использование олицетворения при обеспечении безопасности транспорта](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)   
 [Делегирование и олицетворение](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)