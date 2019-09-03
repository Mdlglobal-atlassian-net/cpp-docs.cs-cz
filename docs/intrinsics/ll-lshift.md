---
title: __ll_lshift
ms.date: 09/02/2019
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 158ecbf39320d70b51f1f498a0b689ba58fec363
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221819"
---
# <a name="__ll_lshift"></a>__ll_lshift

**Specifické pro společnost Microsoft**

Posune dodané 64é hodnoty vlevo o zadaný počet bitů.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>Parametry

*Zrušit*\
pro 64 hodnota celého čísla pro posunutí doleva.

*nBit*\
pro Počet bitů, které se mají posunout

## <a name="return-value"></a>Návratová hodnota

Maska se v `nBit` bitech posunula doleva.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__ll_lshift`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Pokud zkompilujete program pro architekturu 64 a `nBit` je větší než 63, počet bitů k posunu je `nBit` modulo 64. Pokud zkompilujete program pro architekturu 32 a `nBit` je větší než 31, počet bitů k posunutí je `nBit` modulo 32.

V názvu označuje, že se jedná o operaci na `long long` (`__int64`). `ll`

## <a name="example"></a>Příklad

```cpp
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

```Output
10000
```

> [!NOTE]
> Neexistuje žádná nepodepsaná verze operace Left posunutí. Je to proto `__ll_lshift` , že již používá vstupní parametr bez znaménka. Na rozdíl od pravého posunu není pro levý posun žádná závislost, protože nejméně významný bit ve výsledku je vždycky nastavený na nulu bez ohledu na znaménko hodnoty posunuté.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__ll_rshift](../intrinsics/ll-rshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
