---
title: Makeallocator::allocate – metoda | Microsoft Docs
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
ms.openlocfilehash: d0e8d387dea7687ad61d85f975d58aa47489266d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__forceinline void* Allocate();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného ukazatel na přidělenou paměť; v opačném `nullptr`.  
  
## <a name="remarks"></a>Poznámky  
 Přidělí paměť a přidruží ji s aktuálním objektem MakeAllocator.  
  
 Velikost přidělenou paměť je velikost v typu zadaném pomocí aktuální MakeAllocator parametr šablony.  
  
 Vývojář musí potlačení pouze Allocate() metody k implementaci model přidělení různých paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [MakeAllocator – třída](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)