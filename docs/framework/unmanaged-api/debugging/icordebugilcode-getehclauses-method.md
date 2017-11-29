---
title: "Метод ICorDebugILCode::GetEHClauses"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILCode.GetEHClauses
api_location: mscordbi.dll
api_type: COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39d30ef572423d8cb988c074971de095f1709e8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="fb61c-102">Метод ICorDebugILCode::GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="fb61c-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="fb61c-103">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="fb61c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="fb61c-104">Возвращает указатель на список предложений обработки исключений, определенных для этого промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="fb61c-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb61c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fb61c-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb61c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fb61c-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="fb61c-107">[в] Емкость хранилища массива `clauses`.</span><span class="sxs-lookup"><span data-stu-id="fb61c-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="fb61c-108">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="fb61c-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="fb61c-109">[из] Количество предложений, информация о которых записывается в массив `clauses`.</span><span class="sxs-lookup"><span data-stu-id="fb61c-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="fb61c-110">предложения</span><span class="sxs-lookup"><span data-stu-id="fb61c-110">clauses</span></span>  
 <span data-ttu-id="fb61c-111">[out] Массив [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) объекты, содержащие сведения о предложениях, определенных для этого Промежуточного обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="fb61c-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb61c-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="fb61c-112">Remarks</span></span>  
 <span data-ttu-id="fb61c-113">Если `cClauses` равно 0 и `pcClauses` не является**null**, `pcClauses` присваивается количество доступных предложений обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="fb61c-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="fb61c-114">Если значение `cClauses` не равно 0, оно обозначает емкость хранилища массива `clauses`.</span><span class="sxs-lookup"><span data-stu-id="fb61c-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="fb61c-115">Когда метод возвращает не пустое значение, `clauses` содержит максимум элементов `cClauses`, а значению `pcClauses` присваивается количество предложений, записанных в массив `clauses` на данный момент.</span><span class="sxs-lookup"><span data-stu-id="fb61c-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb61c-116">Требования</span><span class="sxs-lookup"><span data-stu-id="fb61c-116">Requirements</span></span>  
 <span data-ttu-id="fb61c-117">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb61c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb61c-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb61c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb61c-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb61c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb61c-120">**Версии платформы .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb61c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb61c-121">См. также</span><span class="sxs-lookup"><span data-stu-id="fb61c-121">See Also</span></span>  
 [<span data-ttu-id="fb61c-122">Интерфейс ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="fb61c-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="fb61c-123">Структура CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="fb61c-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 [<span data-ttu-id="fb61c-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="fb61c-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)