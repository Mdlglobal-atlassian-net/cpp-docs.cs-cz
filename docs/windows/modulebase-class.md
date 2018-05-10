---
title: ModuleBase – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
dev_langs:
- C++
helpviewer_keywords:
- ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bfee0c0cd7ff7bd7f4525a291184f08f1e2898e5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="modulebase-class"></a>ModuleBase – třída
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ModuleBase;  
```  
  
## <a name="remarks"></a>Poznámky  
 Představuje základní třídu [modulu](../windows/module-class.md) třídy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[ModuleBase::ModuleBase – konstruktor](../windows/modulebase-modulebase-constructor.md)|Inicializuje novou instanci třídy modulu.|  
|[ModuleBase::~ModuleBase – destruktor](../windows/modulebase-tilde-modulebase-destructor.md)|Deinitializes aktuální instance třídy modulu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ModuleBase::DecrementObjectCount – metoda](../windows/modulebase-decrementobjectcount-method.md)|Pokud je implementována, snižuje počet objektů, které sledují modulem.|  
|[ModuleBase::IncrementObjectCount – metoda](../windows/modulebase-incrementobjectcount-method.md)|Pokud je implementována, zvýší počet objektů, které sledují modulem.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ModuleBase`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)