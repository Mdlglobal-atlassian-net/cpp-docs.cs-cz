---
title: __ll_rshift
ms.date: 09/02/2019
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
ms.openlocfilehash: ad17991d84acb7e531baf9435610ebd566197a22
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217496"
---
# <a name="__ll_rshift"></a>__ll_rshift

**Specifické pro společnost Microsoft**

Posune 64 hodnotu určenou prvním parametrem vpravo podle počtu bitů určených druhým parametrem.

## <a name="syntax"></a>Syntaxe

```C
__int64 __ll_rshift(
   __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>Parametry

*Zrušit*\
pro Hodnota 64 celé číslo, která se má posunout vpravo.

*nBit*\
pro Počet bitů, které se mají posunout, modulo 64 na x64 a modulo 32 v x86

## <a name="return-value"></a>Návratová hodnota

Maska posunutá pomocí `nBit` bitů.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__ll_rshift`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Pokud je druhý parametr větší než 64 na platformě x64 (32 na platformě x86), toto číslo povede k určení počtu bitů, které se mají posunout, na hodnotu modulo 64 (32 na platformě x86). Předpona označuje, že se jedná o `long long`operaci s jiným názvem pro `__int64`typ integrálu s podpisem 64. `ll`

## <a name="example"></a>Příklad

```cpp
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

```Output
ffffffffffffff00
- 100
fffffffffffffff0
- 10
```

> [!NOTE]
> Pokud `_ull_rshift` byl použit, hodnota MSB pravého posunutí by měla být nulová, takže požadovaný výsledek nebude získán v případě záporné hodnoty.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)
