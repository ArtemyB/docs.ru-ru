---
title: "Метод ICorProfilerInfo2::GetClassLayout"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 988e9daf54d9b4edd623e2488b68dff007e4495b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>Метод ICorProfilerInfo2::GetClassLayout
Получает сведения о макете в памяти полей, определенных с помощью указанного класса. То есть этот метод получает смещения полей класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
#### <a name="parameters"></a>Параметры  
 `classID`  
 [in] Идентификатор класса, для которого будет извлекаться макет.  
  
 `rFieldOffset`  
 [in, out] Массив [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) структуры, каждый из которых содержит токены и смещения полей класса.  
  
 `cFieldOffset`  
 [in] Размер массива `rFieldOffset`.  
  
 `pcFieldOffset`  
 [out] Указатель на общее число доступных элементов. Если параметр `cFieldOffset` имеет значение 0, это значение указывает число необходимых элементов.  
  
 `pulClassSize`  
 [out] Указатель на расположение, которое содержит размер класса в байтах.  
  
## <a name="remarks"></a>Примечания  
 Метод `GetClassLayout` возвращает только поля, определенные самим классом. Если в родительском классе этого класса также определены поля, профилировщик должен вызвать `GetClassLayout` в родительском классе, чтобы получить эти поля.  
  
 Если вы используете метод `GetClassLayout` со строковыми классами, метод завершится с ошибкой с кодом ошибки E_INVALIDARG. Используйте [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) для получения сведений о макете строки. Метод `GetClassLayout` также не завершится с ошибкой при его вызове с классом массива.  
  
 После возврата метода `GetClassLayout` необходимо убедиться, что буфер `rFieldOffset` был достаточно велик, чтобы вместить в себя все доступные структуры `COR_FIELD_OFFSET`. Для этого нужно сравнить значение, указанное параметром `pcFieldOffset`, с размером `rFieldOffset`, деленным на размер структуры `COR_FIELD_OFFSET`. Если параметр `rFieldOffset` имеет недостаточно большое значение, выделите буфер `rFieldOffset` большего размера, обновите параметр `cFieldOffset`, задав новый, больший размер, и вызовите метод `GetClassLayout` снова.  
  
 Кроме того, сначала можно вызвать метод `GetClassLayout` с буфером `rFieldOffset` нулевой длины для получения правильного размера буфера. Затем можно задать размер буфера равным значению, возвращенному в параметре `pcFieldOffset`, и вызвать метод `GetClassLayout` снова.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [ICorProfilerInfo-интерфейс](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2-интерфейс](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Интерфейсы профилирования](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Профилирование](../../../../docs/framework/unmanaged-api/profiling/index.md)
