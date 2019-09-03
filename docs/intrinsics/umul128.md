---
title: _umul128
ms.date: 09/02/2019
f1_keywords:
- __umul128
helpviewer_keywords:
- __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
ms.openlocfilehash: 205f0f7f9046ede624bb09e18d8ede32fadbc3de
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219688"
---
# <a name="_umul128"></a>_umul128

**Specifické pro společnost Microsoft**

Vynásobí 2 64 celých čísel bez znaménka, která byla předána jako první dva argumenty a umístí vysoké 64 bity produktu do 64-bit unsigned integer ukazují na `HighProduct` hodnotu a vrátí nízké 64 bity produktu.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 _umul128(
   unsigned __int64 Multiplier,
   unsigned __int64 Multiplicand,
   unsigned __int64 *HighProduct
);
```

### <a name="parameters"></a>Parametry

*Koeficient*\
pro První 64 celé číslo, které se má vynásobit.

*Multiplicand*\
pro Druhé 64 celé číslo, které se má vynásobit.

*HighProduct*\
mimo Vysoký 64 bitů produktu.

## <a name="return-value"></a>Návratová hodnota

Dolních 64 bitů produktu.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_umul128`|x64|\<intrin.h>|

## <a name="example"></a>Příklad

```C
// umul128.c
// processor: x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_umul128)

int main()
{
    unsigned __int64 a = 0x0fffffffffffffffI64;
    unsigned __int64 b = 0xf0000000I64;
    unsigned __int64 c, d;

    d = _umul128(a, b, &c);

    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
