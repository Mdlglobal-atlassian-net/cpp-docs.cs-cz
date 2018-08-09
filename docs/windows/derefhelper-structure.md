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
ms.openlocfilehash: 9e5c4965ab8a013fdd52e6dfa51e74bfbf54ed73
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651532"
---
# <a name="derefhelper-structure"></a>DerefHelper – struktura
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <  
   typename T  
>  
struct DerefHelper;  
  
template <  
   typename T  
>  
struct DerefHelper<T*>;  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Parametr šablony.  
  
## <a name="remarks"></a>Poznámky  
 Představuje ukazatel přes ukazatel `T*` parametr šablony.  
  
 **Derefhelper –** , jako je použít ve výrazu: `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`.  
  
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