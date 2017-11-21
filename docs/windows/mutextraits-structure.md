---
title: "Mutextraits – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
dev_langs: C++
helpviewer_keywords: MutexTraits structure
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eebe8ffefedbc28be1f16a0d02a195d4af4ac0c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mutextraits-structure"></a>MutexTraits – struktura
Definuje běžné vlastnosti [Mutex](../windows/mutex-class1.md) třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct MutexTraits : HANDLENullTraits;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Mutextraits::Unlock – metoda](../windows/mutextraits-unlock-method.md)|Uvolní výhradní kontrolu nad sdíleného prostředku.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `HANDLENullTraits`  
  
 `MutexTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [Namespace Microsoft::WRL::Wrappers::HandleTraits](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)