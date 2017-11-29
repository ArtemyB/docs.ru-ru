---
title: "Функция GetCLRIdentityManager"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCLRIdentityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: GetCLRIdentityManager
helpviewer_keywords: GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ddc0395b6fd659ecd6a26a3132fccc65bbb961fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="0bef3-102">Функция GetCLRIdentityManager</span><span class="sxs-lookup"><span data-stu-id="0bef3-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="0bef3-103">Возвращает указатель на интерфейс, который позволяет общеязыковой среды выполнения (CLR) для управления удостоверениями.</span><span class="sxs-lookup"><span data-stu-id="0bef3-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="0bef3-104">Эта функция рекомендуется к использованию в [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0bef3-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bef3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0bef3-105">Syntax</span></span>  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0bef3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0bef3-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="0bef3-107">[in] Объект `REFIID` (идентификатор интерфейса), задающий интерфейс, который нужно получить.</span><span class="sxs-lookup"><span data-stu-id="0bef3-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="0bef3-108">Это значение должно быть IID_ICLRAssemblyIdentityManager или IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="0bef3-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="0bef3-109">[out] Указатель на адрес [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) или [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) объекта.</span><span class="sxs-lookup"><span data-stu-id="0bef3-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bef3-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="0bef3-110">Remarks</span></span>  
 <span data-ttu-id="0bef3-111">Вызовите [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) функции, чтобы получить указатель на `GetCLRIdentityManager` функции.</span><span class="sxs-lookup"><span data-stu-id="0bef3-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bef3-112">Требования</span><span class="sxs-lookup"><span data-stu-id="0bef3-112">Requirements</span></span>  
 <span data-ttu-id="0bef3-113">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bef3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bef3-114">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0bef3-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0bef3-115">**Библиотека:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="0bef3-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="0bef3-116">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bef3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bef3-117">См. также</span><span class="sxs-lookup"><span data-stu-id="0bef3-117">See Also</span></span>  
 [<span data-ttu-id="0bef3-118">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="0bef3-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)