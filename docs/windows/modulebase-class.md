---
title: "ModuleBase – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::ModuleBase
dev_langs: C++
helpviewer_keywords: ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b02efe3ee61234b2439c1cbbae07827d6a879b2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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