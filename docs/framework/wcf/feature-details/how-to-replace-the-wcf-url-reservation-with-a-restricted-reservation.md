---
title: "Как заменить WCF URL резервирование на ограниченное резервирование | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Как заменить WCF URL резервирование на ограниченное резервирование
Резервирование URL\-адреса позволяет ограничить список тех, кто может получать сообщения с URL\-адреса или набора URL\-адресов.Резервирование включает шаблон URL\-адреса, список управления доступом \(ACL\) и набор флагов.Шаблон URL\-адреса определяет, какие URL\-адреса будут затронуты резервированием.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] обработке шаблонов URL\-адресов см. в разделе [Маршрутизация входящих запросов](http://go.microsoft.com/fwlink/?LinkId=136764).Список управления доступом \(ACL\) управляет тем, какой пользователь или группа пользователей может получать сообщения с указанных URL\-адресов.Флаги указывают, разрешает ли резервирование пользователю или группе отслеживать URL\-адрес напрямую или делегирует это разрешение какому\-либо другому процессу.  
  
 Как часть конфигурации операционной системы по умолчанию, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] создает глобально допустимое резервирование для порта 80, чтобы все пользователи могли запускать приложения, использующие двустороннее HTTP\-соединение для дуплексной связи.Поскольку список управления доступом \(ACL\) для данного резервирования предназначен для каждого пользователя, администраторы не могут явным образом позволить или запретить отслеживать URL\-адрес или набор URL\-адресов.В данном разделе объясняется, как удалить это резервирование и создать его повторно с ограниченным списком управления доступом \(ACL\).  
  
 В [!INCLUDE[wv](../../../../includes/wv-md.md)] или [!INCLUDE[lserver](../../../../includes/lserver-md.md)] можно просмотреть все резервирования HTTP URL\-адресов, выполнив в командной строке с правами администратора команду `netsh http show urlacl`.В следующем примере показано, на что должно быть похоже резервирование URL\-адреса [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 Резервирование включает шаблон URL\-адреса, используемый в том случае, если приложение [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] использует двустороннее HTTP\-соединение для дуплексной связи.URL\-адреса этого вида используются службой [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] для отправки сообщений обратно клиенту [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] при двустороннем HTTP\-соединении.Каждый пользователь получает разрешение отслеживать URL\-адрес, но не может делегировать отслеживание другому процессу.Наконец, список управления доступом \(ACL\) описывается на языке Security Descriptor Definition Language \(SSDL\).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] SSDL см. в разделе [SSDL](http://go.microsoft.com/fwlink/?LinkId=136789)  
  
### Удаление резервирования URL\-адреса WCF  
  
1.  Нажмите кнопку **Пуск**, укажите **Все программы**, выберите **Стандартные**, правой кнопкой мыши щелкните **Командная строка** и выберите **Запуск от имени администратора** в появившемся контекстном меню.Нажмите кнопку **Продолжить** в окне «Контроль учетных записей», которое может запросить разрешение на продолжение.  
  
2.  Введите **netsh http delete urlacl url\=http:\/\/\+:80\/Temporary\_Listen\_Addresses\/** в окне командной строки.  
  
3.  Если резервирование удалено успешно, появится следующее сообщение.**URL reservation successfully deleted**  
  
## Создание новой группы безопасности и нового ограниченного резервирования URL\-адреса  
 Чтобы заменить резервирование URL\-адреса [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ограниченным резервированием, сначала следует создать новую группу безопасности.Это можно сделать двумя способами: из командной строки или из консоли управления компьютером.Требуется выполнить только одно действие.  
  
#### Создание новой группы безопасности из командной строки  
  
1.  Нажмите кнопку **Пуск**, укажите **Все программы**, выберите **Стандартные**, правой кнопкой мыши щелкните **Командная строка** и выберите **Запуск от имени администратора** в появившемся контекстном меню.Нажмите кнопку **Продолжить** в окне «Контроль учетных записей», которое может запросить разрешение на продолжение.  
  
2.  Введите **net localgroup "\<security group name\>" \/comment:"\<security group description\>" \/add** окне командной строки.Замените **\<security group name\>** на имя группы безопасности, которую вы хотите создать, и **\<security group description\>** на подходящее описание для данной группы безопасности.  
  
3.  Если группа безопасности создана успешно, появится следующее сообщение.**The command completed successfully.**  
  
#### Создание новой группы безопасности из консоли управления компьютером  
  
1.  Нажмите кнопку **Пуск**, выберите **Панель управления**, **Администрирование** и щелкните **Управление компьютером**, чтобы открыть консоль управления компьютером.Нажмите кнопку **Продолжить** в окне «Контроль учетных записей», которое может запросить разрешение на продолжение.  
  
2.  Нажмите **Служебные программы**, выберите **Локальные пользователи и группы**, щелкните правой кнопкой мыши папку **Группы** и выберите пункт **Новая группа** в появившемся контекстном меню.Введите желаемое **Имя группы**, **Описание** и другие сведения новой группы безопасности и нажмите кнопку **Создать**, чтобы создать группу безопасности.  
  
#### Создание ограниченного резервирования URL\-адреса  
  
1.  Нажмите кнопку **Пуск**, укажите **Все программы**, выберите **Стандартные**, правой кнопкой мыши щелкните **Командная строка** и выберите **Запуск от имени администратора** в появившемся контекстном меню.Нажмите кнопку **Продолжить** в окне «Контроль учетных записей», которое может запросить разрешение на продолжение.  
  
2.  Введите **netsh http add urlacl url\=http:\/\/\+:80\/Temporary\_Listen\_Addresses\/ user\="\<machine name\>\\\<security group name\>** командной строке.Замените **\<machine name\>** на имя компьютера, на котором необходимо создать группу, и **\<security group name\>** на имя созданной ранее вами группы безопасности.  
  
3.  Если резервирование создано успешно, появится следующее сообщение.**URL reservation successfully added**.