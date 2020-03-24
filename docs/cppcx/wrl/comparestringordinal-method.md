---
title: CompareStringOrdinal – metoda
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
ms.openlocfilehash: 1291084395b02602b7a3de9013df6720d2e237fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214094"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal – metoda

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
inline INT32 CompareStringOrdinal(
   HSTRING lhs,
   HSTRING rhs)
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První HSTRING, který se má porovnat

*zarovnání indirekce RHS*<br/>
Druhý HSTRING, který se má porovnat.

## <a name="return-value"></a>Návratová hodnota

|Hodnota|Podmínka|
|-----------|---------------|
|-1|*LHS* je menší než *Zarovnání indirekce RHS*.|
|0|*LHS* se rovná *Zarovnání indirekce RHS*.|
|1|*LHS* je větší než *Zarovnání indirekce RHS*.|

## <a name="remarks"></a>Poznámky

Porovná dva zadané objekty HSTRING a vrátí celé číslo, které označuje jejich relativní pozici v pořadí řazení.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers. h

**Obor názvů:** Microsoft:: WRL:: Wrappers::D etails

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers::Details – obor názvů](microsoft-wrl-wrappers-details-namespace.md)
