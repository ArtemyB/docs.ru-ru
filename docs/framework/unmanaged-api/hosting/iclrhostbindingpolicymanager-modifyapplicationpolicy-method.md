---
title: "Метод ICLRHostBindingPolicyManager::ModifyApplicationPolicy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 51775f52e34f35d8ef9f3a8533363be73e9bd7c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>Метод ICLRHostBindingPolicyManager::ModifyApplicationPolicy
Изменяет политику привязки для указанной сборки и создает новую версию политики.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pwzSourceAssemblyIdentity`  
 [in] Удостоверение сборки для изменения.  
  
 `pwzTargetAssemblyIdentity`  
 [in] Новый идентификатор измененной сборке.  
  
 `pbApplicationPolicy`  
 [in] Указатель на буфер, содержащий данные о политике привязки для сборки для изменения.  
  
 `cbAppPolicySize`  
 [in] Размер политику привязки для замены.  
  
 `dwPolicyModifyFlags`  
 [in] Сочетание логического или [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) значений, указывающих на управление перенаправления.  
  
 `pbNewApplicationPolicy`  
 [out] Указатель на буфер, содержащий новые данные о политике привязки.  
  
 `pcbNewAppPolicySize`  
 [in, out] Указатель на размер буфера новой политики привязки.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
|HRESULT|Описание|  
|-------------|-----------------|  
|S_OK|Политика была успешно изменена.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity`или `pwzTargetAssemblyIdentity` был ссылкой со значением null.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` слишком мал.|  
|ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE|Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.|  
|HOST_E_TIMEOUT|Истекло время ожидания вызова.|  
|HOST_E_NOT_OWNER|Вызывающий объект не является владельцем блокировки.|  
|HOST_E_ABANDONED|Событие было отменено заблокированный поток или ожидал волокон.|  
|E_FAIL|Неизвестная Неустранимая ошибка. После метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе. Последующие вызовы размещение методы возвращают значение HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Примечания  
 `ModifyApplicationPolicy` Метод может вызываться дважды. Первый вызов должен указать значение null для `pbNewApplicationPolicy` параметра. Этот вызов вернет значение, необходимые для `pcbNewAppPolicySize`. Второй вызов должен указывать это значение для `pcbNewAppPolicySize`и выберите пункт размера буфера, для `pbNewApplicationPolicy`.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE.h  
  
 **Библиотека:** включена как ресурс в MSCorEE.dll  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Iclrhostbindingpolicymanager-интерфейс](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
