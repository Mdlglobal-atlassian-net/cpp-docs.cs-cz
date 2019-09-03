---
title: _mm_stream_sd
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: 7f0c6457cc0806a0f1764300cffa1c9878b8a600
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217373"
---
# <a name="_mm_stream_sd"></a>_mm_stream_sd

**Specifické pro společnost Microsoft**

Zapisuje 64 – bitová data do umístění v paměti bez znečišťujících mezipamětí.

## <a name="syntax"></a>Syntaxe

```C
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

### <a name="parameters"></a>Parametry

*Propojovací*\
mimo Ukazatel na umístění, kam budou zapsána zdrojová data.

*Zdrojová*\
pro 128 hodnota, která obsahuje `double` hodnotu, která se má zapsat do dolních 64 bitů.

## <a name="return-value"></a>Návratová hodnota

Žádné

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Vnitřní vygeneruje `movntsd` instrukci. Chcete-li zjistit hardwarovou podporu pro tuto instrukci, `InfoType=0x80000001` zavolejte `__cpuid` vnitřní s a zkontrolujte `CPUInfo[2] (ECX)`bit 6 z. Tento bit je 1, pokud hardware podporuje tuto instrukci a 0 jinak.

Pokud spustíte kód, který používá `_mm_stream_sd` vnitřní na hardwaru, který `movntsd` nepodporuje instrukci, výsledky se nepředvídatelné.

## <a name="example"></a>Příklad

```cpp
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

**Specifické pro konec Microsoftu**

Copyright 2007 od Advanced Micro Devices, Inc. Všechna práva vyhrazena. Reprodukováno s oprávněním z Advanced Micro Devices, Inc.

## <a name="see-also"></a>Viz také:

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)\
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
