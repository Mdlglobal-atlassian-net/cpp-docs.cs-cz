---
title: _mm_cvttss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 69016a4e23b020b2c4c79c6b97a5a76f2b2dc028
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217415"
---
# <a name="_mm_cvttss_si64x"></a>_mm_cvttss_si64x

**Specifické pro společnost Microsoft**

Vygeneruje rozšířenou verzi x64 s plovoucí desetinnou čárkou s jednoduchou přesností na 64 () instrukcí typu celé číslo`cvttss2si`().

## <a name="syntax"></a>Syntaxe

```C
__int64 _mm_cvttss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>Parametry

*osa*\
pro `__m128` Struktura obsahující hodnoty s plovoucí desetinnou čárkou s jednoduchou přesností.

## <a name="return-value"></a>Návratová hodnota

Výsledek převodu první hodnoty s plovoucí desetinnou čárkou na 64 celé číslo.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_mm_cvttss_si64x`|x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Vnitřní se liší od `_mm_cvtss_si64x` pouze v tom, že nepřesné převody jsou zkráceny směrem k nule. Vzhledem k tomu, že StrukturapředstavujeregistrXMM,vygenerovanáinstrukcepřesunedatazregistruXMMdosystémovépaměti.`__m128`

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="example"></a>Příklad

```cpp
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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__m128](../cpp/m128.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
