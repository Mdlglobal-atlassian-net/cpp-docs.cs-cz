---
title: CompareStringOrdinal – metoda
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
ms.openlocfilehash: c9dbbe8926036ea18210fb30928fafc40093092e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786741"
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

[Microsoft::WRL::Wrappers::Details – obor názvů](microsoft-wrl-wrappers-details-namespace.md)