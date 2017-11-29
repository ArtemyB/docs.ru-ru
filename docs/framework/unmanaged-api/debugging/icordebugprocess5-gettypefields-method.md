---
title: "Метод ICorDebugProcess5::GetTypeFields"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeFields
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7a64e754a77c7d730d921f8a8c1547dd18b66d77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="23807-102">Метод ICorDebugProcess5::GetTypeFields</span><span class="sxs-lookup"><span data-stu-id="23807-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="23807-103">Сведения о полях, которые принадлежат к типу.</span><span class="sxs-lookup"><span data-stu-id="23807-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23807-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="23807-104">Syntax</span></span>  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23807-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="23807-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="23807-106">[in] Идентификатор типа, сведения о поле которого извлекается.</span><span class="sxs-lookup"><span data-stu-id="23807-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="23807-107">[in] Число [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) объектов, поле сведения о которой требуется получить.</span><span class="sxs-lookup"><span data-stu-id="23807-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="23807-108">[out] Массив [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) объектов, которые предоставляют сведения о полях, которые относятся к типу.</span><span class="sxs-lookup"><span data-stu-id="23807-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="23807-109">[out] Указатель на число [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) объекты, включенные в `fields`.</span><span class="sxs-lookup"><span data-stu-id="23807-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23807-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="23807-110">Remarks</span></span>  
 <span data-ttu-id="23807-111">`celt` Параметр, который задает количество полей, сведения о поле, метод использует для заполнения `fields`, должен соответствовать значению `COR_TYPE_LAYOUT::numFields` поля.</span><span class="sxs-lookup"><span data-stu-id="23807-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23807-112">Требования</span><span class="sxs-lookup"><span data-stu-id="23807-112">Requirements</span></span>  
 <span data-ttu-id="23807-113">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23807-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23807-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23807-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23807-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23807-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23807-116">**Версии платформы .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23807-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23807-117">См. также</span><span class="sxs-lookup"><span data-stu-id="23807-117">See Also</span></span>  
 [<span data-ttu-id="23807-118">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="23807-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="23807-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="23807-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)