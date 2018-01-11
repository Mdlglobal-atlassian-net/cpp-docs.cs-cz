---
title: "Interfacelisthelper – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::InterfaceListHelper
dev_langs: C++
helpviewer_keywords: InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 241613f94431903c7d9e3957cece46844dc67ad9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper – struktura
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename T0,  
   typename T1 = Nil,  
   typename T2 = Nil,  
   typename T3 = Nil,  
   typename T4 = Nil,  
   typename T5 = Nil,  
   typename T6 = Nil,  
   typename T7 = Nil,  
   typename T8 = Nil,  
   typename T9 = Nil  
>  
struct InterfaceListHelper;  
  
template <  
   typename T0  
>  
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T0`  
 Parametr šablony 0, který je vyžadován.  
  
 `T1`  
 Parametr šablony 1, který ve výchozím nastavení neurčená.  
  
 `T2`  
 Parametr šablony 2, který ve výchozím nastavení neurčená. Třetí parametr šablony.  
  
 `T3`  
 Parametr šablony 3, který ve výchozím nastavení neurčená.  
  
 `T4`  
 Parametr šablony 4, který ve výchozím nastavení neurčená.  
  
 `T5`  
 Parametr šablony 5, který ve výchozím nastavení neurčená.  
  
 `T6`  
 Parametr šablony 6, který ve výchozím nastavení neurčená.  
  
 `T7`  
 Parametr šablony 7, který ve výchozím nastavení neurčená.  
  
 `T8`  
 Parametr šablony 8, který ve výchozím nastavení neurčená.  
  
 `T9`  
 Parametr šablony 9, který ve výchozím nastavení neurčená.  
  
## <a name="remarks"></a>Poznámky  
 Vytvoří typ interfacelist – rekurzivně použití argumenty parametrů určené šablony.  
  
 Interfacelisthelper – šablona používá parametr šablony `T0` definovat první data člena do interfacelist – struktura a pak rekurzivně platí šabloně interfacelisthelper – pro všechny ostatní parametry šablony. Interfacelisthelper – zastaví, pokud nejsou žádné zbývající parametry šablony.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`TypeT`|Synonymum pro typ interfacelist –.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `InterfaceListHelper`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)