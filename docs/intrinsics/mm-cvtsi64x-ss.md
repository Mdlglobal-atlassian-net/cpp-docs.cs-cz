---
title: _mm_cvtsi64x_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: 0e9bacc56f212e804467d1c6e0159a1749235976
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217456"
---
# <a name="_mm_cvtsi64x_ss"></a>_mm_cvtsi64x_ss

**Specifické pro společnost Microsoft**

Vygeneruje rozšířenou verzi x64, která převádí 64 celé číslo na skalární instrukci Value (`cvtsi2ss`) s jednoduchou přesností.

## <a name="syntax"></a>Syntaxe

```C
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

### <a name="parameters"></a>Parametry

*určitého*\
pro `__m128` Struktura obsahující čtyři hodnoty s plovoucí desetinnou čárkou s jednoduchou přesností.

*b*\
pro 64 celé číslo, které má být převedeno na hodnotu s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

`__m128` Struktura, jejíž první hodnota s plovoucí desetinnou čárkou je výsledkem převodu. Ostatní tři hodnoty jsou zkopírovány beze změnyz.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Struktura představuje XMM registr, takže vnitřní umožňuje přesunout hodnotu b ze systémové paměti do registru XMM. `__m128`

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="example"></a>Příklad

```cpp
// _mm_cvtsi64x_ss.cpp
// processor: x64

#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtsi64x_ss)

int main()
{
    __m128 a;
    __int64 b = 54;

    a.m128_f32[0] = 0;
    a.m128_f32[1] = 0;
    a.m128_f32[2] = 0;
    a.m128_f32[3] = 0;
    a = _mm_cvtsi64x_ss(a, b);

    printf_s( "%lf %lf %lf %lf\n",
              a.m128_f32[0], a.m128_f32[1],
              a.m128_f32[2], a.m128_f32[3] );
}
```

```Output
54.000000 0.000000 0.000000 0.000000
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__m128](../cpp/m128.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
