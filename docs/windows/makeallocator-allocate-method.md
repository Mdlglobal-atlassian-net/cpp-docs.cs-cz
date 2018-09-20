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
ms.openlocfilehash: c4dd68a3c678b7877db63167fd2c0d48a1daa7ad
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411830"
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

[MakeAllocator – třída](../windows/makeallocator-class.md)<br/>
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)