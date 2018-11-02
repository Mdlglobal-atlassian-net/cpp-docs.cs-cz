---
title: _mm_cvttss_si64x
ms.date: 11/04/2016
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 5c2dd98ad3f74ac56b3656ac5f6f450efc40c088
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522977"
---
# <a name="mmcvttsssi64x"></a>_mm_cvttss_si64x

**Specifické pro Microsoft**

Vysílá x64 rozšířenou verzi Convert s číslem plovoucí desetinné čárky jednoduchou přesnost zkrácení na 64bitové celé číslo (`cvttss2si`) instrukce.

## <a name="syntax"></a>Syntaxe

```
__int64 _mm_cvttss_si64x( 
   __m128 value 
);
```

#### <a name="parameters"></a>Parametry

*value*<br/>
[in] `__m128` Struktury obsahující hodnoty s plovoucí desetinnou čárkou jednoduchou přesností.

## <a name="return-value"></a>Návratová hodnota

Výsledek převodu první hodnota s plovoucí desetinnou čárkou na 64bitové celé číslo.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_mm_cvttss_si64x`|x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Vnitřní typy se liší od `_mm_cvtss_si64x` pouze v tom, že se zkrátí nepřesné převody směrem k nule. Vzhledem k tomu, `__m128` struktura představuje registru XMM, vygeneruje instrukce přesouvá data z registru XMM do systémové paměti.

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="example"></a>Příklad

```
// _mm_cvttss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvttss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] = { 101.5, 200.75,
                                          300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvttss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[__m128](../cpp/m128.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)