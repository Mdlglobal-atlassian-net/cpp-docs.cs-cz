---
title: CompareStringOrdinal – metoda
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
ms.openlocfilehash: 61ca0cb6d8afc07b73e33a2e5bc3dc10daacc210
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593372"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal – metoda

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
inline INT32 CompareStringOrdinal(
   HSTRING lhs,
   HSTRING rhs)
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První HSTRING k porovnání.

*Zarovnání indirekce RHS*<br/>
Druhý HSTRING k porovnání.

## <a name="return-value"></a>Návratová hodnota

|Hodnota|Podmínka|
|-----------|---------------|
|-1|*LHS* je menší než *zarovnání indirekce rhs*.|
|0|*LHS* rovná *zarovnání indirekce rhs*.|
|1|*LHS* je větší než *zarovnání indirekce rhs*.|

## <a name="remarks"></a>Poznámky

Porovná dva objekty zadané HSTRING a vrátí celé číslo určující jejich relativní umístění v pořadí řazení.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers::Details – obor názvů](../windows/microsoft-wrl-wrappers-details-namespace.md)