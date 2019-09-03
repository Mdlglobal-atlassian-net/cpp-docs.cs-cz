---
title: _mm_insert_si64, _mm_inserti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
ms.openlocfilehash: 08469ad8049df2a07f0e66d650c1ca3118f8b980
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221771"
---
# <a name="_mm_insert_si64-_mm_inserti_si64"></a>_mm_insert_si64, _mm_inserti_si64

**Specifické pro společnost Microsoft**

`insertq` Generuje instrukci pro vložení bitů z jeho druhého operandu do prvního operandu.

## <a name="syntax"></a>Syntaxe

```C
__m128i _mm_insert_si64(
   __m128i Source1,
   __m128i Source2
);
__m128i _mm_inserti_si64(
   __m128i Source1,
   __m128i Source2
   int Length,
   int Index
);
```

### <a name="parameters"></a>Parametry

*Source1*\
pro 128 pole, které má vstupní data v dolních 64 bitech, do kterých bude vloženo pole.

*Source2*\
pro 128 pole obsahující data, která mají být vložena do dolních bitů.  `_mm_insert_si64`Obsahuje také popisovač pole v jeho horních bitech.

*Časový*\
pro Celočíselná konstanta, která určuje délku pole, které má být vloženo.

*Indexovacím*\
pro Celočíselná konstanta, která určuje index nejméně významného bitu pole, do kterého budou vložena data.

## <a name="return-value"></a>Návratová hodnota

128 pole, jehož dolní 64 bitů obsahuje původní nízké 64 bitů *source1*, se zadaným bitovým polem nahrazeným dolními bity *SOURCE2*. Horní 64é bity návratové hodnoty nejsou definovány.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tyto vnitřní objekty generují `insertq` instrukci pro vložení bitů z *SOURCE2* do *source1*. Existují dvě verze: `_mm_inserti_si64`, je okamžitá verze a `_mm_insert_si64` je neokamžitá. Každá verze extrahuje bitové pole dané délky z SOURCE2 a vloží je do source1.  Extrahované bity mají nejméně významné bity z SOURCE2.  Pole source1, do kterého budou vloženy tyto bity, jsou definovány délkou a indexem jeho nejméně významného bitu.  Hodnoty délky a indexu jsou pořízeny mod 64, takže obě-1 i 127 jsou interpretovány jako 63. Je-li součet velikosti (redukovaného) bitového indexu a (zmenšeného) délky pole větší než 64, nejsou výsledky definovány. Hodnota nula pro délku pole je interpretována jako 64. Pokud je délka pole a bitový index nula, do *source1*se vloží bity 63:0 *SOURCE2* . Pokud je délka pole nula, ale bit indexu je nenulový, výsledky nejsou definovány.

V volání _mm_insert_si64 je délka pole obsažena v bitech 77:72 z SOURCE2 a v indexu v bitech 69:64.

Pokud zavoláte `_mm_inserti_si64` argumenty, které kompilátor nemůže určit jako celočíselné konstanty, kompilátor vygeneruje kód pro zabalení těchto hodnot do XMM registru a volání `_mm_insert_si64`.

Chcete-li zjistit hardwarovou `insertq` podporu instrukce, `__cpuid` zavolejte vnitřní s `InfoType=0x80000001` a zkontrolujte bit 6 z `CPUInfo[2] (ECX)`. Tento bit je 1, pokud je instrukce podporována a 0 jinak. Pokud spustíte kód, který používá vnitřní na hardwaru, který nepodporuje `insertq` instrukci, výsledky se nepředvídatelné.

## <a name="example"></a>Příklad

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source1, source2, source3, result1, result2, result3;

int
main()
{

    __int64 mask;

    source1.ui64[0] = 0xffffffffffffffffll;
    source2.ui64[0] = 0xfedcba9876543210ll;
    source2.ui64[1] = 0xc10;
    source3.ui64[0] = source2.ui64[0];

    result1.m = _mm_insert_si64 (source1.m, source2.m);
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);
    mask = 0xffff << 12;
    mask = ~mask;
    result3.ui64[0] = (source1.ui64[0] & mask) |
                      ((source2.ui64[0] & 0xffff) << 12);

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;

}
```

```Output
result1 = 0xfffffffff3210fff
result2 = 0xfffffffff3210fff
result3 = 0xfffffffff3210fff
```

**Specifické pro konec Microsoftu**

Copyright 2007 od Advanced Micro Devices, Inc. Všechna práva vyhrazena. Reprodukováno s oprávněním z Advanced Micro Devices, Inc.

## <a name="see-also"></a>Viz také:

[_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
