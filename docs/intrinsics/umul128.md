---
title: _umul128
ms.date: 11/04/2016
f1_keywords:
- __umul128
helpviewer_keywords:
- __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
ms.openlocfilehash: 94f26a6baeb4d3440d7f16af298b9880b91860f2
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220488"
---
# <a name="umul128"></a>_umul128

**Specifické pro Microsoft**

Vynásobí dvě 64-bit celých čísel bez znaménka předaný jako první dva argumenty a umístí vysokou 64bitová verze produktu 64bitové celé číslo bez znaménka na které odkazuje `HighProduct` a vrátí nízké 64bitová verze produktu.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 _umul128(
   unsigned __int64 Multiplier,
   unsigned __int64 Multiplicand,
   unsigned __int64 *HighProduct
);
```

#### <a name="parameters"></a>Parametry

*Násobitel*<br/>
[in] První 64bitové celé číslo pro vynásobení.

*Násobenec*<br/>
[in] Druhé 64bitové celé číslo pro vynásobení.

*HighProduct*<br/>
[out] 64 bitů produktu.

## <a name="return-value"></a>Návratová hodnota

Nízká 64 bitů produktu.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_umul128`|x64|\<intrin.h >|

## <a name="example"></a>Příklad

```
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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)
