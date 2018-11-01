---
title: _mm_stream_sd
ms.date: 11/04/2016
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: d85197aca4c277e8a5ebdf5119c0a63d23f479f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648653"
---
# <a name="mmstreamsd"></a>_mm_stream_sd

**Specifické pro Microsoft**

Zapíše data 64-bit do umístění v paměti bez zahlcení mezipamětí.

## <a name="syntax"></a>Syntaxe

```
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

#### <a name="parameters"></a>Parametry

*cíl*<br/>
[out] Ukazatel na umístění, kam se budou zapisovat zdrojová data.

*Zdroj*<br/>
[in] 128bitové hodnotu obsahující `double` hodnota má být zapsán v její dolní 64 bitů...

## <a name="return-value"></a>Návratová hodnota

Žádné

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní vygeneruje `movntsd` instrukce. Chcete-li určit hardwarovou podporu pro tento pokyn, zavolejte `__cpuid` vnitřní s `InfoType=0x80000001` a zkontrolujte bit 6 `CPUInfo[2] (ECX)`. Tato verze je 1, pokud hardware podporuje tento pokyn a 0 jinak.

Při spuštění kódu, který používá `_mm_stream_sd` vnitřní na hardwaru, který není podporován `movntsd` instrukce, výsledky nepředvídatelné.

## <a name="example"></a>Příklad

```
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128d vals;
    double d[2];

    d[0] = -1.;
    d[1] = -2.;
    vals.m128d_f64[0] = 0.;
    vals.m128d_f64[1] = 1.;
    _mm_stream_sd(&d[1], vals);
    cout << "d[0] = " << d[0] << ", d[1] = " << d[1] << endl;
}

```

```Output
d[0] = -1, d[1] = 1
```

**Specifické pro END Microsoft**

Copyright 2007 pokročilé zařízení Micro, Inc. Všechna práva vyhrazena. Reprodukovat se svolením rozšířené Micro zařízení, Inc.

## <a name="see-also"></a>Viz také

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)<br/>
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)<br/>
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)