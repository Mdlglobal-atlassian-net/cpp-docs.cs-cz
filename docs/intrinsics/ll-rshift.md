---
title: __ll_rshift
ms.date: 11/04/2016
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
ms.openlocfilehash: e39f8fe797467569077dd24baf49670607915107
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263357"
---
# <a name="llrshift"></a>__ll_rshift

**Microsoft Specific**

Posune 64 bitů hodnotu zadanou pomocí prvního parametru vpravo o počet bitů určený druhý parametr.

## <a name="syntax"></a>Syntaxe

```
__int64 __ll_rshift(
   __int64 Mask,
   int nBit
);
```

#### <a name="parameters"></a>Parametry

*Maska*<br/>
[in] 64bitové celočíselné hodnoty posunutí doprava.

*nBit*<br/>
[in] Počet bitů, chcete-li posunout modulo 64 na x64 a modulo 32 na x86.

## <a name="return-value"></a>Návratová hodnota

Maska o `nBit` bits.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__ll_rshift`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Není-li druhý parametr je větší než 64 na x64 (32 na x86), toto číslo provedena modulo 64 (32 na x86) k určení počtu bitů a posunutí. `ll` Předponu označuje, že se jedná operaci na `long long`, další název `__int64`, 64-bit celočíselný typ se znaménkem.

## <a name="example"></a>Příklad

```
// ll_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_rshift)

int main()
{
   __int64 Mask = - 0x100;
   int nBit = 4;
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
   Mask = __ll_rshift(Mask, nBit);
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
}
```

## <a name="output"></a>Výstup

```
ffffffffffffff00
- 100
fffffffffffffff0
- 10
```

**Poznámka:** Pokud `_ull_rshift` byl použit, MSB hodnotu posunuta doprava by byl nula, tak v případě záporné hodnoty by byly získány požadovaný výsledek.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__ll_lshift](../intrinsics/ll-lshift.md)<br/>
[__ull_rshift](../intrinsics/ull-rshift.md)