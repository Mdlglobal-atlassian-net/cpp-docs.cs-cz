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
ms.openlocfilehash: d609b685bb5e3d24d561e66050769b6b7728e691
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607159"
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

[MakeAllocator – třída](../windows/makeallocator-class.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)