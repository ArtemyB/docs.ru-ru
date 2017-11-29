---
title: "Метод IHostTask::SetPriority"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.SetPriority
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 34dabcb35f46d4a2b0536e00fa1fd69637b14cb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="10f89-102">Метод IHostTask::SetPriority</span><span class="sxs-lookup"><span data-stu-id="10f89-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="10f89-103">Уровень запросов, настройки, узле приоритет потока для задачи, представленный текущим [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) экземпляра.</span><span class="sxs-lookup"><span data-stu-id="10f89-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f89-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="10f89-104">Syntax</span></span>  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10f89-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="10f89-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="10f89-106">[in] Целое число, представляющее значение приоритета запрошенный поток для задачи, представленный текущим `IHostTask` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="10f89-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10f89-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="10f89-107">Return Value</span></span>  
  
|<span data-ttu-id="10f89-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10f89-108">HRESULT</span></span>|<span data-ttu-id="10f89-109">Описание</span><span class="sxs-lookup"><span data-stu-id="10f89-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10f89-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="10f89-110">S_OK</span></span>|<span data-ttu-id="10f89-111">`SetPriority`успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="10f89-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="10f89-112">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="10f89-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="10f89-113">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="10f89-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="10f89-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="10f89-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="10f89-115">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="10f89-115">The call timed out.</span></span>|  
|<span data-ttu-id="10f89-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="10f89-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="10f89-117">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="10f89-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="10f89-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="10f89-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="10f89-119">Событие было отменено заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="10f89-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="10f89-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="10f89-120">E_FAIL</span></span>|<span data-ttu-id="10f89-121">Неизвестная Неустранимая ошибка.</span><span class="sxs-lookup"><span data-stu-id="10f89-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="10f89-122">Если метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="10f89-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="10f89-123">Последующие вызовы размещение методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="10f89-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10f89-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="10f89-124">Remarks</span></span>  
 <span data-ttu-id="10f89-125">Потоки время выполнения предоставляется с помощью системы циклический перебор, частично основывается на уровень приоритета потока.</span><span class="sxs-lookup"><span data-stu-id="10f89-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="10f89-126">`SetPriority`позволяет среде CLR задать уровень приоритета потока для текущей задачи.</span><span class="sxs-lookup"><span data-stu-id="10f89-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="10f89-127">Следующие `newPriority` значения поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="10f89-127">The following `newPriority` values are supported.</span></span>  
  
-   <span data-ttu-id="10f89-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="10f89-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
-   <span data-ttu-id="10f89-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="10f89-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
-   <span data-ttu-id="10f89-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="10f89-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
-   <span data-ttu-id="10f89-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="10f89-131">THREAD_PRIORITY_IDLE</span></span>  
  
-   <span data-ttu-id="10f89-132">ВСЕХ</span><span class="sxs-lookup"><span data-stu-id="10f89-132">THREAD_PRIORITY_LOWEST</span></span>  
  
-   <span data-ttu-id="10f89-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="10f89-133">THREAD_PRIORITY_NORMAL</span></span>  
  
-   <span data-ttu-id="10f89-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="10f89-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="10f89-135">Среда CLR вызывает `SetPriority` при значение <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> изменяется с помощью пользовательского кода.</span><span class="sxs-lookup"><span data-stu-id="10f89-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="10f89-136">Узел можно определить собственные алгоритмы назначения приоритетов потокам и игнорировать этот запрос.</span><span class="sxs-lookup"><span data-stu-id="10f89-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10f89-137">`SetPriority`не сообщает, был ли изменен уровень приоритета потока.</span><span class="sxs-lookup"><span data-stu-id="10f89-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="10f89-138">Вызовите [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) для определения значения уровня приоритета потока задачи.</span><span class="sxs-lookup"><span data-stu-id="10f89-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="10f89-139">Значения уровня приоритета потока определяется Win32 `SetThreadPriority` функции.</span><span class="sxs-lookup"><span data-stu-id="10f89-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="10f89-140">Дополнительные сведения о приоритете потока см. в документации по платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="10f89-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10f89-141">Требования</span><span class="sxs-lookup"><span data-stu-id="10f89-141">Requirements</span></span>  
 <span data-ttu-id="10f89-142">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10f89-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10f89-143">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="10f89-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10f89-144">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="10f89-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10f89-145">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10f89-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f89-146">См. также</span><span class="sxs-lookup"><span data-stu-id="10f89-146">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="10f89-147">ICLRTask-интерфейс</span><span class="sxs-lookup"><span data-stu-id="10f89-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="10f89-148">ICLRTaskManager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="10f89-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="10f89-149">IHostTask-интерфейс</span><span class="sxs-lookup"><span data-stu-id="10f89-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="10f89-150">GetPriority-метод</span><span class="sxs-lookup"><span data-stu-id="10f89-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)  
 [<span data-ttu-id="10f89-151">IHostTaskManager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="10f89-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)