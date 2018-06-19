---
title: Argtraitshelper – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs:
- C++
helpviewer_keywords:
- ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6205d69962d70d9da76c932fdd8b3f66f491ebc9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857698"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper – struktura
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename TDelegateInterface>  
struct ArgTraitsHelper;  
```  
  
#### <a name="parameters"></a>Parametry  
 `TDelegateInterface`  
 Delegát rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Pomáhá definovat běžné vlastnosti delegáta argumenty.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`methodType`|Synonymum pro `decltype(&TDelegateInterface::Invoke)`.|  
|`Traits`|Synonymum pro `ArgTraits<methodType>`.|  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[ArgTraitsHelper::args – konstanta](../windows/argtraitshelper-args-constant.md)|Pomáhá [argtraits::args –](../windows/argtraits-args-constant.md) zachovat počet parametrů na metodu Invoke rozhraní delegáta.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ArgTraitsHelper`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)