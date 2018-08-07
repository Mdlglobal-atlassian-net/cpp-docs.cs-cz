---
title: Makeallocator::allocate – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs:
- C++
helpviewer_keywords:
- Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 06f8db4c713feb69e0037d10879383411ea07007
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606260"
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__forceinline void* Allocate();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, ukazatel do přidělené paměti. v opačném případě **nullptr**.  
  
## <a name="remarks"></a>Poznámky  
 Přidělí paměť a přidruží ji k aktuální **MakeAllocator** objektu.  
  
 Velikost přidělené paměti je velikost typu určeného aktuálním **MakeAllocator** parametr šablony.  
  
 Vývojář potřebuje pouze přepsat **Allocate()** metody k implementaci modelu přidělování různých paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Makeallocator – třída](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)