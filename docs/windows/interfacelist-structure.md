---
title: Interfacelist – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
dev_langs:
- C++
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 318738e5f4ac623987b1002e5204739407adcdb9
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017755"
---
# <a name="interfacelist-structure"></a>InterfaceList – struktura
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <  
   typename T,  
   typename U  
>  
struct InterfaceList;  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Název rozhraní; první mapované rozhraní seznamu rekurzivní.  
  
 *U*  
 Název rozhraní; Zbývající rozhraní v seznamu rekurzivní.  
  
## <a name="remarks"></a>Poznámky  
 Umožňuje vytvořit seznam rekurzivní rozhraní.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`FirstT`|Synonymum pro parametr šablony *T*.|  
|`RestT`|Synonymum pro parametr šablony *U*.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `InterfaceList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)