---
title: "Функция CoEEShutDownCOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CoEEShutDownCOM
helpviewer_keywords: CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d6d9e3d650f65ef084c63104980bca0ac77f1bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="bd45e-102">Функция CoEEShutDownCOM</span><span class="sxs-lookup"><span data-stu-id="bd45e-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="bd45e-103">Принудительно общеязыковой среды выполнения (CLR), чтобы освободить все указатели на интерфейс, содержащиеся внутри вызываемых оболочек времени выполнения (RCW).</span><span class="sxs-lookup"><span data-stu-id="bd45e-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="bd45e-104">Это приводит к по освобождению всех кэшей вызываемой оболочки времени Выполнения.</span><span class="sxs-lookup"><span data-stu-id="bd45e-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="bd45e-105">Рекомендуется использовать эту глобальную функцию в [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd45e-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="bd45e-106">Вместо этого используйте точку входа для конкретной среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="bd45e-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd45e-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bd45e-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd45e-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="bd45e-108">Remarks</span></span>  
 <span data-ttu-id="bd45e-109">`CoEEShutDownCOM` Функция сначала освобождает все оболочки RCW во всех контекстах и всех кэшах, а затем удаляет все уведомления завершаемые, существующих в программе установки.</span><span class="sxs-lookup"><span data-stu-id="bd45e-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="bd45e-110">Выгрузка DLL не выполнена.</span><span class="sxs-lookup"><span data-stu-id="bd45e-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="bd45e-111">Эта функция затрагивает все среды выполнения, загруженные в процесс.</span><span class="sxs-lookup"><span data-stu-id="bd45e-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="bd45e-112">Начиная с версии [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], вызовите точку входа для этой функции в конкретной среде выполнения, который требуется изменить.</span><span class="sxs-lookup"><span data-stu-id="bd45e-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="bd45e-113">Чтобы получить точку входа, вызовите [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) метод и укажите «CoEEShutDownCOM».</span><span class="sxs-lookup"><span data-stu-id="bd45e-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd45e-114">Требования</span><span class="sxs-lookup"><span data-stu-id="bd45e-114">Requirements</span></span>  
 <span data-ttu-id="bd45e-115">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd45e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd45e-116">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bd45e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd45e-117">**Библиотека:** включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd45e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd45e-118">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd45e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd45e-119">См. также</span><span class="sxs-lookup"><span data-stu-id="bd45e-119">See Also</span></span>  
 [<span data-ttu-id="bd45e-120">Глобальные статические функции метаданных</span><span class="sxs-lookup"><span data-stu-id="bd45e-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)