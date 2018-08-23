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
ms.openlocfilehash: 4422dea0b0bfb07904d0c4defad8f33281a51bec
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609859"
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate – metoda

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
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

[MakeAllocator – třída](../windows/makeallocator-class.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)