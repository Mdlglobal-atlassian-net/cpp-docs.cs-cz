---
title: _mm_stream_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 005f4f697d64f6ea68b35dc32daf1217be463a2a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217345"
---
# <a name="_mm_stream_ss"></a>_mm_stream_ss

**Specifické pro společnost Microsoft**

Zapisuje 32 – bitová data do umístění v paměti bez znečišťujících mezipamětí.

## <a name="syntax"></a>Syntaxe

```C
void _mm_stream_ss(
   float * Destination,
   __m128 Source
);
```

### <a name="parameters"></a>Parametry

*Tabulka*\
mimo Ukazatel na umístění, kde jsou napsána zdrojová data.

*Zdrojová*\
pro 128 číslo, které obsahuje `float` hodnotu, která se má zapsat do dolních 32 bitů.

## <a name="return-value"></a>Návratová hodnota

Žádné

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Vnitřní vygeneruje `movntss` instrukci. Chcete-li zjistit hardwarovou podporu pro tuto instrukci, `InfoType=0x80000001` zavolejte `__cpuid` vnitřní s a zkontrolujte `CPUInfo[2] (ECX)`bit 6 z. Tento bit je 1, pokud je instrukce podporována a 0 jinak.

Pokud spustíte kód, který používá `_mm_stream_ss` vnitřní na hardwaru, který `movntss` nepodporuje instrukci, výsledky se nepředvídatelné.

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

**Specifické pro konec Microsoftu**

Copyright 2007 od Advanced Micro Devices, Inc. Všechna práva vyhrazena. Reprodukováno s oprávněním z Advanced Micro Devices, Inc.

## <a name="see-also"></a>Viz také:

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)\
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)\
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
