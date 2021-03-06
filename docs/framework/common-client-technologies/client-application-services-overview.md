---
title: "Общие сведения о службах клиентских приложений"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client application services, classes
- client application services, about client application services
ms.assetid: f0a2da13-e282-4fd7-88a1-f9102c9aeab1
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5719cf7cfb5ec99f1bfbf952048e98c9465e1fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="client-application-services-overview"></a>Общие сведения о службах клиентских приложений
Службы клиентских приложений предоставляют упрощенный доступ к службам входа, ролей и профилей [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] из приложений Windows Forms и Windows Presentation Foundation (WPF). Службы приложений [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] включены в расширения Microsoft ASP.NET 2.0 AJAX, которые входят в состав [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)] и [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]. Эти службы позволяют нескольким веб-приложениям и приложениям Windows использовать сведения о пользователе и функции управления пользователями с одного сервера.  
  
 В службы клиентских приложений входят поставщики клиентских служб, которые подключаются к модели расширяемости веб-служб, предоставляя следующие функции для приложений Windows.  
  
-   Простая настройка клиента. Можно включить и настроить службы входа, ролей и профилей с помощью конструктора проектов [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] или указав поставщиков клиентских служб в файле App.config проекта. Дополнительные сведения см. в разделе [Практическое руководство. Настройка служб клиентских приложений](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
-   Простое программирование. После включения и настройки служб клиентских приложений вы можете получить доступ к поставщикам служб косвенным образом, через существующие классы членства, ролей и параметров приложения [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)]. Вы можете также получить прямой доступ к классам [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)], реализующим службы клиентских приложений. Однако в большинстве случаев прямой доступ необязателен. Дополнительные сведения о классах служб клиентских приложений см. в разделе "Классы служб клиентских приложений".  
  
-   Поддержка работы в автономном режиме. Приложениям Windows часто приходится работать в средах с непостоянным сетевым подключением. Если приложение подключено, поставщики клиентских служб будут кэшировать значения, полученные с сервера для использования их в автономном режиме.  
  
-   Интеграция с конструктором параметров приложения [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. При добавлении параметров в проект в [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] можно указать, какие параметры должны быть доступны через поставщика службы клиентских параметров.  
  
 В следующих разделах эти возможности описываются более подробно. Дополнительные сведения о службах приложений [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] см. в разделе [Общие сведения о службах приложений ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
## <a name="authentication"></a>Проверка подлинности  
 Вы можете использовать службы клиентских приложений для проверки пользователя в существующей службе проверки подлинности [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)]. Вы можете проверить пользователя, используя проверку подлинности Windows или проверку подлинности с помощью форм. Проверка подлинности Windows означает, что операционная система предоставляет удостоверение пользователя при входе пользователя на компьютер или в домен. В приложении, развернутом в корпоративной интрасети, обычно используется проверка подлинности Windows. Проверка подлинности с помощью форм означает, что вам нужно включить элементы управления входа в приложение и передать полученные учетные данные поставщику проверки подлинности. Обычно проверка подлинности с помощью форм используется, если приложение развернуто в Интернете.  
  
 Для проверки пользователя вызывается метод `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType>. Этот метод осуществляет доступ к поставщику клиентских служб, настроенному для приложения, и возвращает значение <xref:System.Boolean>, указывающее, допустим ли пользователь. Дополнительные сведения см. в разделе [Практическое руководство. Реализация входа пользователя с помощью служб клиентских приложений](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md).  
  
 При использовании проверки подлинности Windows необходимо передать пустые строки или `null` как параметры метода <xref:System.Web.Security.Membership.ValidateUser%2A>. При использовании проверки подлинности Windows этот метод всегда будет возвращать `true`.  
  
 При использовании проверки подлинности с помощью форм метод <xref:System.Web.Security.Membership.ValidateUser%2A> вернет значение, указывающее, прошел ли пользователь проверку подлинности удаленной службой. Если проверка подлинности успешно пройдена, файл cookie проверки подлинности сохраняется на локальном жестком диске. Этот файл cookie используется для подтверждения проверки при доступе к службам ролей и параметров.  
  
 При использовании проверки подлинности с помощью форм в метод <xref:System.Web.Security.Membership.ValidateUser%2A> можно передать имя пользователя и пароль. Можно также передать пустые строки или `null` как параметры для использования поставщика учетных данных. Поставщик учетных данных — это класс, который вы предоставляете и указываете в конфигурации приложения. Класс поставщика учетных данных должен реализовывать интерфейс <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> с одним методом — <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A>. Использование поставщика учетных данных позволяет использовать одно диалоговое окно входа в разных приложениях. Для получения дополнительной информации см. [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
 Если приложение настроено на использование поставщика учетных данных с проверкой подлинности с помощью форм, необходимо передать пустые строки или `null` как параметры метода <xref:System.Web.Security.Membership.ValidateUser%2A>. Затем поставщик служб вызовет реализацию вашего метода <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType>. Обычно этот метод реализуется для отображения диалогового окна и возврата заполненного объекта <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>.  
  
 Дополнительные сведения о проверке подлинности см. в разделе [Проверка подлинности ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1). Сведения о настройке службы проверки подлинности [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] см. в разделе [Использование проверки подлинности с помощью форм в Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).  
  
## <a name="roles"></a>Роли  
 Вы можете использовать службы клиентских приложений для получения сведений о ролях из существующей службы ролей [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)]. Чтобы определить, имеет ли текущий прошедший проверку подлинности пользователь определенную роль, следует вызвать метод <xref:System.Security.Principal.IPrincipal.IsInRole%2A> интерфейса <xref:System.Security.Principal.IPrincipal>, возвращаемого свойством `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType>. Метод <xref:System.Security.Principal.IPrincipal.IsInRole%2A> принимает имя роли как параметр и возвращает значение <xref:System.Boolean>, указывающее, имеет ли текущий пользователь указанную роль. Этот метод вернет `false`, если пользователь не прошел проверку подлинности или не имеет указанной роли.  
  
 Сведения о настройке службы ролей [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] см. в разделе [Использование сведений о ролях в Microsoft Ajax](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d).  
  
## <a name="settings"></a>Параметры  
 Службы клиентских приложений можно использовать, чтобы получать параметры приложения пользователя из существующей службы профилей [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)]. Функциональность веб-параметров в службах клиентских приложений интегрируется с функциональностью параметров приложения, предоставленной в [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)]. Для извлечения веб-параметров сначала создайте класс `Settings` (доступен как `Properties.Settings.Default` в C# и как `My.Settings` в [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) в своем проекте на вкладке **Параметры** конструктора проектов [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. На вкладке **Параметры** нажмите кнопку **Загрузить веб-параметры**, чтобы получить веб-параметры и добавить их в созданный класс `Settings`. Вы можете использовать веб-параметры, настроенные для использования всеми прошедшими проверку подлинности пользователями или всеми анонимными пользователями.  
  
 Дополнительные сведения о параметрах приложения см. в разделе [Общие сведения о параметрах приложения](../../../docs/framework/winforms/advanced/application-settings-overview.md). Дополнительные сведения о реализации собственного класса параметров вместо создания его в [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] см. в разделе [Практическое руководство. Создание параметров приложения](../../../docs/framework/winforms/advanced/how-to-create-application-settings.md). Сведения о настройке службы профилей [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] см. в разделе [Использование сведений о профилях в Microsoft Ajax](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61).  
  
## <a name="client-application-services-classes"></a>Классы служб клиентских приложений  
 В следующей таблице описываются классы, реализующие функциональность служб клиентских приложений.  
  
 Приложения, использующие только основные функции проверки подлинности и получения сведений о ролях и параметрах, не получат доступ к этим классам напрямую. Вместо этого такие приложения получат непрямой доступ к поставщикам служб клиентских приложений с помощью конфигурации приложения и интерфейсов API, описанных в предыдущих разделах. Вы получите прямой доступ к этим классам для реализации дополнительных возможностей, таких как выход пользователя и автономная работа.  
  
> [!NOTE]
>  Все интерфейсы API служб клиентских приложений являются синхронными. Службы клиентских приложений не поддерживают асинхронное поведение напрямую.  
  
 Поставщики служб клиентских приложений реализуют или расширяют стандартные типы [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], но реализуют не все члены и возможности, определенные этими типами. Например, при создании приложения управления пользователями вы не можете использовать поставщиков служб клиентских приложений для создания новых пользователей и управления членствами ролей. Для реализации этих возможностей необходимо использовать веб-приложение и код на стороне сервера. Чтобы определить, какие члены не реализуются, см. справочную документацию по ссылкам в этой таблице.  
  
|Класс|Описание|  
|-----------|-----------------|  
|<xref:System.Web.ClientServices.ClientFormsIdentity>|Этот класс управляет удостоверением пользователя и файлами cookie для проверки подлинности с помощью форм.<br /><br /> Главная причина необходимости прямого доступа к этому классу — вызов метода <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A>, который повторно проверяет пользователя без его участия (например, при переключении из автономного режима в режим "в сети").<br /><br /> После проверки подлинности пользователя с помощью форм можно получить экземпляр этого класса, используя свойство <xref:System.Security.Principal.IPrincipal.Identity%2A> интерфейса <xref:System.Security.Principal.IPrincipal>, возвращаемого свойством `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.ClientServices.ClientRolePrincipal>|Этот класс управляет ролями пользователей.<br /><br /> В этом классе нет членов, которые недоступны косвенно. Но после проверки подлинности пользователя можно получить доступ к экземпляру этого класса через свойство `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.ClientServices.ConnectivityStatus>|Этот класс предоставляет свойство `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A>, которое используется для переключения приложения в автономный режим.|  
|<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>|Этот класс представляет учетные данные пользователя.<br /><br /> Этот класс будет использоваться только в качестве типа возвращаемого значения для метода <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> при реализации интерфейса <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>.|  
|<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>|Этот класс управляет доступом к удаленной службе проверки подлинности c помощью форм.<br /><br /> Главная причина прямого доступа к классу — использование его членов <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> и <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.UserValidated>, не реализованных базовым классом <xref:System.Web.Security.MembershipProvider>. Задать расположение службы можно программно с помощью свойства <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.ServiceUri%2A>.<br /><br /> Вы можете извлечь экземпляр этого класса через свойство `static` <xref:System.Web.Security.Membership.Provider%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>|Этот класс управляет проверкой подлинности Windows.<br /><br /> Основная причина прямого доступа к этому классу — вызов его метода <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider.Logout%2A>. После выхода пользователь будет считаться прошедшим проверку подлинности Windows, но не сможет получить доступ к удаленным службам клиентских приложений.<br /><br /> Вы можете извлечь экземпляр этого класса через свойство `static` <xref:System.Web.Security.Membership.Provider%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.ClientServices.Providers.ClientRoleProvider>|Этот класс управляет доступом к удаленной службе ролей.<br /><br /> Основная причина доступа к этому классу — вызов его метода <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>. Это может быть полезно, если приложение настроено для использования ненулевого времени ожидания кэша службы ролей. Для получения дополнительной информации см. [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). Задать расположение службы можно программно с помощью свойства <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ServiceUri%2A>.<br /><br /> Вы можете извлечь экземпляр этого класса через свойство `static` <xref:System.Web.Security.Roles.Provider%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.ClientServices.Providers.ClientSettingsProvider>|Этот класс управляет доступом к удаленной службе веб-параметров.<br /><br /> Основная причина доступа к этому классу — обработка события <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved>. Задать расположение службы можно программно с помощью свойства <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.ServiceUri%2A>.|  
|<xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>|Этот интерфейс предоставляет косвенный способ получения приложением учетных данных пользователя для проверки, как было описано ранее в подразделе "Проверка подлинности" этого раздела. Для получения дополнительной информации см. [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).|  
|<xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>|Этот класс предоставляет свойство <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs.FailedSettingsList%2A> для использования в обработчике событий <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType>.|  
|<xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>|Этот класс предоставляет свойство <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs.UserName%2A> для использования в обработчике событий <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.UserValidated>.|  
  
## <a name="see-also"></a>См. также  
 [Службы клиентских приложений](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Практическое руководство. Настройка служб клиентских приложений](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Практическое руководство. Реализация входа пользователя с помощью служб клиентских приложений](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 [Пошаговое руководство. Использование служб клиентских приложений](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Общие сведения о параметрах приложений](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Общие сведения о службах приложений ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [Использование проверки подлинности с помощью форм в Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [Использование сведений о ролях с Microsoft Ajax](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [Использование сведений о профиле с Microsoft Ajax](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [Проверка подлинности ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [Управление авторизацией с помощью ролей](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  
 [Создание и настройка базы данных служб приложений для SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)
