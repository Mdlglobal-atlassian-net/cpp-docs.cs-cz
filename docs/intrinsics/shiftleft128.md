---
title: __shiftleft128
ms.date: 09/02/2019
f1_keywords:
- __shiftleft128
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
ms.openlocfilehash: 5da9ac81cedbdd24e10eb438892f88510c32ca24
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218000"
---
# <a name="__shiftleft128"></a>__shiftleft128

**Specifické pro společnost Microsoft**

Posune 128 množství, které je reprezentováno jako 2 64 množství `LowPart` bitů a `HighPart`nalevo podle počtu bitů určených parametrem `Shift` , a vrátí bity s vysokým 64m výsledku.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __shiftleft128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

### <a name="parameters"></a>Parametry

*LowPart*\
pro Dolní 64 bitů 128 množství, které se má posunout

*HighPart*\
pro Horní 64 bitů 128 množství, které se má posunout

*Posouvá*\
pro Počet bitů, které se mají posunout

## <a name="return-value"></a>Návratová hodnota

Vysoký 64 bitů výsledku.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__shiftleft128`|x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Hodnota *SHIFT* je vždy modulo `__shiftleft128(1, 0, 64)`64, takže pokud například voláte, funkce posune dolní část `0` bitů `0` doleva a vrátí vysokou část a ne `1` tak, jak by jinak bylo možné očekávat.

## <a name="example"></a>Příklad

```C
// shiftleft128.c
// processor: IPF, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__shiftleft128, __shiftright128)

int main()
{
    unsigned __int64 i = 0x1I64;
    unsigned __int64 j = 0x10I64;
    unsigned __int64 ResultLowPart;
    unsigned __int64 ResultHighPart;

    ResultLowPart = i << 1;
    ResultHighPart = __shiftleft128(i, j, 1);

    // concatenate the low and high parts padded with 0's
    // to display correct hexadecimal 128 bit values
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);

    ResultHighPart = j >> 1;
    ResultLowPart = __shiftright128(i, j, 1);

    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);
}
```

```Output
0x100000000000000001 << 1 = 0x200000000000000002
0x100000000000000001 >> 1 = 0x080000000000000000
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__shiftright128](../intrinsics/shiftright128.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
