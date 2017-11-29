---
title: "Метод IMetaDataImport::GetTypeDefProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeDefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1025ffde2bd066c81c4c562c0dd86e829fc2aef3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="5c9e5-102">Метод IMetaDataImport::GetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="5c9e5-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="5c9e5-103">Возвращает сведения о метаданных для <xref:System.Type> представленного указанным токеном TypeDef.</span><span class="sxs-lookup"><span data-stu-id="5c9e5-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c9e5-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5c9e5-104">Syntax</span></span>  
  
```  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c9e5-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="5c9e5-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="5c9e5-106">[in] Представляющий тип, для возврата метаданных для токен TypeDef.</span><span class="sxs-lookup"><span data-stu-id="5c9e5-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="5c9e5-107">[out] Буфер, содержащий имя типа.</span><span class="sxs-lookup"><span data-stu-id="5c9e5-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="5c9e5-108">[in] Размер в расширенных символах с `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="5c9e5-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="5c9e5-109">[out] Число расширенных символов, возвращаемых в `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="5c9e5-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="5c9e5-110">[out] Указатель на любой флаги, которые изменяют определения типа.</span><span class="sxs-lookup"><span data-stu-id="5c9e5-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="5c9e5-111">Это значение является битовой [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) перечисления.</span><span class="sxs-lookup"><span data-stu-id="5c9e5-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="5c9e5-112">[out] TypeDef или TypeRef токен метаданных, представляющий базовый тип запрошенного типа.</span><span class="sxs-lookup"><span data-stu-id="5c9e5-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c9e5-113">Требования</span><span class="sxs-lookup"><span data-stu-id="5c9e5-113">Requirements</span></span>  
 <span data-ttu-id="5c9e5-114">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c9e5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c9e5-115">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5c9e5-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c9e5-116">**Библиотека:** включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c9e5-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5c9e5-117">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c9e5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9e5-118">См. также</span><span class="sxs-lookup"><span data-stu-id="5c9e5-118">See Also</span></span>  
 [<span data-ttu-id="5c9e5-119">IMetaDataImport-интерфейс</span><span class="sxs-lookup"><span data-stu-id="5c9e5-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="5c9e5-120">IMetaDataImport2-интерфейс</span><span class="sxs-lookup"><span data-stu-id="5c9e5-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)