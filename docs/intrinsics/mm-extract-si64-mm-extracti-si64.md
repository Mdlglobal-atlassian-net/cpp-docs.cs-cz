---
title: _mm_extract_si64, _mm_extracti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
ms.openlocfilehash: cfd7029966c29f876f0e4f671830e20e2eacc940
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217411"
---
# <a name="_mm_extract_si64-_mm_extracti_si64"></a>_mm_extract_si64, _mm_extracti_si64

**Specifické pro společnost Microsoft**

Vygeneruje `extrq` instrukci pro extrakci zadaných bitů z dolních 64 bitů prvního argumentu.

## <a name="syntax"></a>Syntaxe

```C
__m128i _mm_extract_si64(
   __m128i Source,
   __m128i Descriptor
);
__m128i _mm_extracti_si64(
   __m128i Source,
   int Length,
   int Index
);
```

### <a name="parameters"></a>Parametry

*Zdrojová*\
pro 128-bitové pole se vstupními daty v dolních 64 bitech.

*Popisovač*\
pro 128 pole, které popisuje bitové pole k extrakci.

*Časový*\
pro Celé číslo, které určuje délku pole k extrakci.

*Indexovacím*\
pro Celé číslo, které určuje index pole k extrakci

## <a name="return-value"></a>Návratová hodnota

128 pole s extrahovaným polem v nejméně významných bitech.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_mm_extract_si64`|SSE4a|
|`_mm_extracti_si64`|SSE4a|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tyto vnitřní objekty generují `extrq` instrukci pro extrakci služby BITS ze *zdroje*. Existují dvě verze: `_mm_extracti_si64` okamžitá verze a `_mm_extract_si64` je neokamžitá. Každá verze extrahuje ze *zdroje* bitové pole definované jeho délkou a indexem jeho nejméně významného bitu. Hodnoty délky a indexu jsou pořízeny mod 64, takže obě-1 i 127 jsou interpretovány jako 63. Pokud součet délky pole (redukovaný) index a (zmenšeno) je větší než 64, nejsou výsledky definovány. Hodnota nula pro délku pole je interpretována jako 64. Pokud je délka pole a bitový index nula, jsou extrahovány bity 63:0 *zdroje* . Pokud je délka pole nula, ale bit indexu je nenulový, výsledky nejsou definovány.

V volání `_mm_extract_si64`, *popisovač* obsahuje index v bitech 13:8 a pole dat, která se mají extrahovat v bitech 5:0.

Pokud zavoláte `_mm_extracti_si64` argumenty, které kompilátor nemůže určit jako celočíselné konstanty, kompilátor vygeneruje kód pro zabalení těchto hodnot do registru XMM (*deskriptor*) a volání `_mm_extract_si64`metody.

Chcete-li zjistit hardwarovou `extrq` podporu instrukce, `__cpuid` zavolejte vnitřní s `InfoType=0x80000001` a zkontrolujte bit 6 z `CPUInfo[2] (ECX)`. Tento bit bude 1, pokud je instrukce podporovaná a 0 jinak. Pokud spustíte kód, který používá tento vnitřní hardware, který `extrq` nepodporuje instrukci, výsledky se nepředvídatelné.

## <a name="example"></a>Příklad

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source, descriptor, result1, result2, result3;

int
main()
{
    source.ui64[0] =     0xfedcba9876543210ll;
    descriptor.ui64[0] = 0x0000000000000b1bll;

    result1.m = _mm_extract_si64 (source.m, descriptor.m);
    result2.m = _mm_extracti_si64(source.m, 27, 11);
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;
}
```

```Output
result1 = 0x30eca86
result2 = 0x30eca86
result3 = 0x30eca86
```

**Specifické pro konec Microsoftu**

Copyright 2007 od Advanced Micro Devices, Inc. Všechna práva vyhrazena. Reprodukováno s oprávněním z Advanced Micro Devices, Inc.

## <a name="see-also"></a>Viz také:

[_mm_insert_si64, _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
