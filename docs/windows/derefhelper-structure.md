---
title: Derefhelper – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
dev_langs:
- C++
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70031553e6a0585dc9f86df336ec2199cd7660ea
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571337"
---
# <a name="derefhelper-structure"></a>DerefHelper – struktura
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename T  
>  
struct DerefHelper;  
  
template <  
   typename T  
>  
struct DerefHelper<T*>;  
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Parametr šablony.  
  
## <a name="remarks"></a>Poznámky  
 Představuje ukazatel přes ukazatel `T*` parametr šablony.  
  
 Derefhelper – je třeba použít ve výrazu: `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`DerefType`|Identifikátor pro parametr šablony přes ukazatel `T*`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `DerefHelper`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)