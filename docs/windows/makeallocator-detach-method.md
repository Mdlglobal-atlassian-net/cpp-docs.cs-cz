---
title: Makeallocator::detach – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: 78012634-2dda-4ea2-9ffe-40f105d2fe47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b629ec70ed29866d0f8e37d9e6ce746fbfe6f117
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018462"
---
# <a name="makeallocatordetach-method"></a>MakeAllocator::Detach – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__forceinline void Detach();  
```  
  
## <a name="remarks"></a>Poznámky  
 Zruší přidružení paměť přidělenou [přidělení](../windows/makeallocator-allocate-method.md) metodu z aktuální **MakeAllocator** objektu.  
  
 Při volání **Detach()**, zodpovídáte za odstranění paměti poskytované `Allocate` metody.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Makeallocator – třída](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)