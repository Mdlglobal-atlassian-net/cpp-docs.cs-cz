---
title: __shiftleft128
ms.date: 11/04/2016
f1_keywords:
- __shiftleft128
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
ms.openlocfilehash: 5fcb797694c7a45dc4f2113f3d2ed4a2f578c894
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390409"
---
# <a name="shiftleft128"></a>__shiftleft128

**Microsoft Specific**

Množství 128-bit, vyjádřené dvě veličiny 64-bit posune `LowPart` a `HighPart`, doleva o počet bitů určený `Shift` a vrátí hodnotu 64 bitů výsledku.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __shiftleft128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

#### <a name="parameters"></a>Parametry

*LowPart*<br/>
[in] Nízká 64 bitů množství 128 bitů a posunutí.

*HighPart*<br/>
[in] Vysoká 64 bitů množství 128 bitů a posunutí.

*SHIFT*<br/>
[in] Počet bitů na posunu.

## <a name="return-value"></a>Návratová hodnota

64 bitů výsledku.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__shiftleft128`|x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

`Shift` Hodnota je vždy modulo 64 tak, že, například při volání `__shiftleft128(1, 0, 64)`, funkce změní dolní část `0` bitů doleva a vrátit vysokou součástí `0` a ne `1` jako jinak lze očekávat.

## <a name="example"></a>Příklad

```
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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[__shiftright128](../intrinsics/shiftright128.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)