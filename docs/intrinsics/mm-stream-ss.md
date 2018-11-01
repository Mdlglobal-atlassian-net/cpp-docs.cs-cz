---
title: _mm_stream_ss
ms.date: 11/04/2016
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 089f8d5501c18b679a3d5878bb30762d2dcc1e04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438906"
---
# <a name="mmstreamss"></a>_mm_stream_ss

**Specifické pro Microsoft**

Zapíše data 32-bit do umístění v paměti bez zahlcení mezipamětí.

## <a name="syntax"></a>Syntaxe

```
void _mm_stream_ss(
   float * Dest,
   __m128 Source
);
```

#### <a name="parameters"></a>Parametry

*cíl*<br/>
[out] Ukazatel na umístění, do níž je zapsána zdrojová data.

*Zdroj*<br/>
[in] 128bitové číslo, které obsahuje `float` hodnota má být zapsán v její dolní části 32 bitů...

## <a name="return-value"></a>Návratová hodnota

Žádné

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní vygeneruje `movntss` instrukce. Chcete-li určit hardwarovou podporu pro tento pokyn, zavolejte `__cpuid` vnitřní s `InfoType=0x80000001` a zkontrolujte bit 6 `CPUInfo[2] (ECX)`. Tento bit jinak je 1 podporováno podle pokynů a 0.

Při spuštění kódu, který používá `_mm_stream_ss` vnitřní na hardwaru, který není podporován `movntss` instrukce, výsledky nepředvídatelné.

## <a name="example"></a>Příklad

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128 vals;
    float f[4];

    f[0] = -1.;
    f[1] = -2.;
    f[2] = -3.;
    f[3] = -4.;
    vals.m128_f32[0] = 0.;
    vals.m128_f32[1] = 1.;
    vals.m128_f32[2] = 2.;
    vals.m128_f32[3] = 3.;
    _mm_stream_ss(&f[3], vals);
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;
}
```

```Output
f[0] = -1, f[1] = -2
f[2] = -3, f[3] = 3
```

**Specifické pro END Microsoft**

Copyright 2007 pokročilé zařízení Micro, Inc. Všechna práva vyhrazena. Reprodukovat se svolením rozšířené Micro zařízení, Inc.

## <a name="see-also"></a>Viz také

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)<br/>
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)<br/>
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)<br/>
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)