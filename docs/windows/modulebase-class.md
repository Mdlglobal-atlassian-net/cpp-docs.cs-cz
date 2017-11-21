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
ms.openlocfilehash: fe24bd4995acb7a36f6aa50378a03b519c8d8e3e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|[Modulebase::modulebase – konstruktor](../windows/modulebase-modulebase-constructor.md)|Inicializuje novou instanci třídy modulu.|  
|[ModuleBase:: ~ modulebase – destruktor](../windows/modulebase-tilde-modulebase-destructor.md)|Deinitializes aktuální instance třídy modulu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Modulebase::decrementobjectcount – metoda](../windows/modulebase-decrementobjectcount-method.md)|Pokud je implementována, snižuje počet objektů, které sledují modulem.|  
|[Modulebase::incrementobjectcount – metoda](../windows/modulebase-incrementobjectcount-method.md)|Pokud je implementována, zvýší počet objektů, které sledují modulem.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ModuleBase`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)