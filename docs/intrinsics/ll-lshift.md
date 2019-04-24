---
title: __ll_lshift
ms.date: 11/04/2016
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 5a91ce5db46b19be570f8d48a584a2caeabcc163
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263383"
---
# <a name="lllshift"></a>__ll_lshift

**Microsoft Specific**

Přesouvá se zadanou hodnotou 64-bit na levé straně zadaný počet bitů.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

#### <a name="parameters"></a>Parametry

*Maska*<br/>
[in] 64bitové celočíselné hodnoty posun doleva.

*nBit*<br/>
[in] Počet bitů na posunu.

## <a name="return-value"></a>Návratová hodnota

Maska posunuty vlevo o `nBit` bits.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__ll_lshift`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Pokud kompilujete program pomocí 64bitovou architekturu a `nBit` je větší než 63, je počet bitů, chcete-li posunout `nBit` modulo 64. Pokud při kompilaci programu pomocí 32bitové architektury a `nBit` je větší než 31, je počet bitů, chcete-li posunout `nBit` modulo 32.

`ll` v názvu označuje, že se jedná operaci na `long long` (`__int64`).

## <a name="example"></a>Příklad

```
// ll_lshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_lshift)

int main()
{
   unsigned __int64 Mask = 0x100;
   int nBit = 8;
   Mask = __ll_lshift(Mask, nBit);
   cout << hex << Mask << endl;
}
```

## <a name="output"></a>Výstup

```
10000
```

**Poznámka:** není bez znaménka verze operaci posunutí doleva. Důvodem je, že `__ll_lshift` již používá nepodepsané vstupního parametru. Na rozdíl od posunutí doprava není žádný znak závislost pro posunutí doleva, protože nejméně významných bitů ve výsledku je vždycky nastavený na hodnotu nula, bez ohledu na znaménko hodnoty posunutí.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[__ll_rshift](../intrinsics/ll-rshift.md)<br/>
[__ull_rshift](../intrinsics/ull-rshift.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)