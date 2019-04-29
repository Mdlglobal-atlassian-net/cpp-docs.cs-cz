---
title: _mm_insert_si64, _mm_inserti_si64
ms.date: 11/04/2016
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
ms.openlocfilehash: f8c8f2f9b33588513e25b2290772aac464f46808
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396675"
---
# <a name="mminsertsi64-mminsertisi64"></a>_mm_insert_si64, _mm_inserti_si64

**Microsoft Specific**

Generuje `insertq` pokyny, jak vložit bits ze svým druhým operandem do jeho prvním operandem.

## <a name="syntax"></a>Syntaxe

```
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

#### <a name="parameters"></a>Parametry

*Zdroj1*<br/>
[in] 128bitové pole se vstupní data v její dolní 64 bitů, do kterých se vloží pole.

*Zdroj2*<br/>
[in] 128bitové pole s dat vložte bity jsou nízké.  Pro `_mm_insert_si64`, také obsahuje popisovač pole v jeho bitů.

*Délka*<br/>
[in] Celočíselná konstanta, která určuje délku pole pro vložení.

*Index*<br/>
[in] Celočíselná konstanta, která určuje index nejméně významných bitů pole, do kterého budou data vložena.

## <a name="return-value"></a>Návratová hodnota

128bitové pole, jehož dolním 64 bitů obsahovat původní nízké 64 bitů z `Source1` pomocí zadané bitové pole nahrazuje nízké bity `Source2`. Horní 64 bitů vrácené hodnoty nejsou definovány.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní vygeneruje `insertq` pokyny, jak vložit bitů z `Source2` do `Source1`. Existují dvě verze tohoto vnitřní: `_mm_inserti_si64`, okamžité verze a `_mm_insert_si64` je – okamžitě.  Každá verze extrahuje bitového pole dané délky z zdroj2 a vloží jej do zdroj1.  Extrahované bity jsou nejméně významných bitů zdroj2.  Zdroj1 pole, do kterého budou vloženy těchto bitů je definována délku a index jeho nejméně významných bitů.  Index a délka hodnoty pocházejí mod 64, tedy -1 do 127 číslic se interpretují jako 63. Pokud součet (nižší) bit index a délky pole (nižší) je větší než 64, nejsou výsledky definovány. Hodnota 0 pro délku pole je interpretován jako 64.  Pokud je index délku a bitová pole jsou obě nulové, služba bits 63:0 z `Source2` jsou vloženy do `Source1`.  Pokud délka pole je nula, ale bit index je nenulová, nejsou výsledky definovány.

Ve volání _mm_insert_si64 délka pole je součástí bits 77:72 zdroj2 a indexu v bits 69:64.

Při volání `_mm_inserti_si64` argumentů, kompilátor nemůže určit být konstanty typu integer, kompilátor generuje kód se zabalit tyto hodnoty do registru XMM a k volání `_mm_insert_si64`.

K určení hardwarovou podporu `insertq` volání instrukce `__cpuid` vnitřní s `InfoType=0x80000001` a zkontrolujte bit 6 `CPUInfo[2] (ECX)`. Tato verze bude 1, pokud podporované instrukce a 0 jinak. Pokud jste spustili kód, který používá tuto vnitřní hardware, který není podporován `insertq` instrukce, výsledky nepředvídatelné.

## <a name="example"></a>Příklad

```
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

**Specifické pro END Microsoft**

Copyright 2007 by Advanced Micro Devices, Inc. Všechna práva vyhrazena. Reprodukovat se svolením rozšířené Micro zařízení, Inc.

## <a name="see-also"></a>Viz také:

[_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)