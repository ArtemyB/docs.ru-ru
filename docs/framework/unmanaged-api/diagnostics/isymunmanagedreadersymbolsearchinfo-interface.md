---
title: "Интерфейс ISymUnmanagedReaderSymbolSearchInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReaderSymbolSearchInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReaderSymbolSearchInfo
helpviewer_keywords: ISymUnmanagedReaderSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: fde7e21d-1169-4bed-a34d-792e69652bf9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a3873ce6d1cbca67855816409fac0082945593f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a>Интерфейс ISymUnmanagedReaderSymbolSearchInfo
Предоставляет методы, получающие сведения о поиске символов. Получить этот интерфейс, вызвав `QueryInterface` на объект, реализующий интерфейс [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) интерфейса.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод GetSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|Возвращает сведения о поиске символов.|  
|[Метод GetSymbolSearchInfoCount](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|Возвращает количество сведений для поиска символов.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы хранилища символов диагностики](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
