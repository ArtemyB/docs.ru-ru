---
title: '&lt;securityTokenHandlers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3151ec3511bca598e5aaabc72b821bdd3aed0b7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="ltsecuritytokenhandlersgt"></a>&lt;securityTokenHandlers&gt;
Задает коллекцию обработчиков токенов безопасности, которые зарегистрированы с конечной точкой.  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|имя|Указывает имя коллекции обработчика токенов. Только значения, распознаваемые платформа: «ActAs» и «OnBehalfOf». Если обработчик маркеров коллекций указаны с помощью любого из этих имен, коллекции будет использоваться при обработке ActAs "или" OnBehalfOf маркеров соответственно.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Добавляет обработчик маркеров безопасности в коллекцию обработчиков токенов.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|Удаляет все обработчики маркеров безопасности из коллекции обработчиков маркеров.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|Удаляет обработчик маркеров безопасности из коллекции обработчиков маркеров.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Обеспечивает настройку для коллекцию обработчиков токенов.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Указывает параметры уровня службы удостоверений.|  
  
## <a name="remarks"></a>Примечания  
 Можно указать одну или несколько именованных коллекций обработчиков токенов безопасности в конфигурации службы. Можно указать имя для коллекции с помощью `name` атрибута. Только имена, что маркеры framework являются «ActAs» и «OnBehalfOf». Если в эти коллекции существуют обработчики, они используются службой маркеров безопасности (STS) вместо обработчики по умолчанию при обработке `ActAs` и `OnBehalfOf` маркеров.  
  
 По умолчанию коллекция заполняется следующие типы обработчиков: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, и <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>. Коллекции можно изменить с помощью `<add>`, `<remove>`, и `<clear>` элементы. Необходимо убедиться, что только один обработчик любого конкретного типа существует в коллекции. Например, если вы наследуете обработчик из <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> класса, либо обработчик или <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> может быть настроен в одной коллекции, но не оба.  
  
 Используйте `<securityTokenHandlerConfiguration>` элемента, чтобы указать параметры конфигурации для обработчиков в коллекции. Параметры, заданные с помощью этого элемента переопределить указанные службы с помощью [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) элемента. Обработчики (включая некоторые типы встроенных обработчиков) может поддерживать дополнительные конфигурации с помощью дочерний элемент элемента `<add>` элемент. Параметры, заданные в обработчик переопределить эквивалентные настройки, заданные на коллекции или службы.
