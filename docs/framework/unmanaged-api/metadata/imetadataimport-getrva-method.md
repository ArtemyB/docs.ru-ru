---
title: "Метод IMetaDataImport::GetRVA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetRVA
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f64cc5b0aa6043c5408868a5a6bf23e24278ea26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="2e5f8-102">Метод IMetaDataImport::GetRVA</span><span class="sxs-lookup"><span data-stu-id="2e5f8-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="2e5f8-103">Получает относительный виртуальный адрес (RVA) и флаги реализации метода или поля, представленного указанным токеном.</span><span class="sxs-lookup"><span data-stu-id="2e5f8-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e5f8-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2e5f8-104">Syntax</span></span>  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e5f8-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="2e5f8-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2e5f8-106">[in] MethodDef или FieldDef токен метаданных, представляющий RVA для возвращаемого объекта кода.</span><span class="sxs-lookup"><span data-stu-id="2e5f8-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="2e5f8-107">Если токен FieldDef, поле должно быть глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="2e5f8-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="2e5f8-108">[out] Указатель относительного виртуального адреса объекта кода, представленного маркером.</span><span class="sxs-lookup"><span data-stu-id="2e5f8-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="2e5f8-109">[out] Указатель флаги реализации метода.</span><span class="sxs-lookup"><span data-stu-id="2e5f8-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="2e5f8-110">Это значение является битовой [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) перечисления.</span><span class="sxs-lookup"><span data-stu-id="2e5f8-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="2e5f8-111">Значение `pdwImplFlags` действителен только тогда, когда `tk` токен MethodDef.</span><span class="sxs-lookup"><span data-stu-id="2e5f8-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e5f8-112">Требования</span><span class="sxs-lookup"><span data-stu-id="2e5f8-112">Requirements</span></span>  
 <span data-ttu-id="2e5f8-113">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e5f8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e5f8-114">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2e5f8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e5f8-115">**Библиотека:** включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e5f8-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e5f8-116">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e5f8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e5f8-117">См. также</span><span class="sxs-lookup"><span data-stu-id="2e5f8-117">See Also</span></span>  
 [<span data-ttu-id="2e5f8-118">IMetaDataImport-интерфейс</span><span class="sxs-lookup"><span data-stu-id="2e5f8-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="2e5f8-119">IMetaDataImport2-интерфейс</span><span class="sxs-lookup"><span data-stu-id="2e5f8-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)