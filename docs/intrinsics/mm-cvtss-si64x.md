---
title: _mm_cvtss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: 6079ed7846a35ff16355f0341d63430f9846057f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217431"
---
# <a name="_mm_cvtss_si64x"></a>_mm_cvtss_si64x

**Specifické pro společnost Microsoft**

Vygeneruje rozšířenou verzi x64 a číslo s plovoucí desetinnou čárkou převáděnou na 64 (`cvtss2si`) instrukcí typu Integer s jednoduchou přesností.

## <a name="syntax"></a>Syntaxe

```C
__int64 _mm_cvtss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>Parametry

*osa*\
pro `__m128` Struktura obsahující pohyblivé hodnoty bodu

## <a name="return-value"></a>Návratová hodnota

64 celé číslo, výsledek převodu první hodnoty s plovoucí desetinnou čárkou na celé číslo.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_mm_cvtss_si64x`|x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

První prvek hodnoty struktury je převeden na celé číslo a vráceno. Bity ovládacího prvku zaokrouhlování v MXCSR slouží k určení chování zaokrouhlení. Výchozím režimem zaokrouhlení je zaokrouhlit na nejbližší, zaokrouhlení na sudé číslo, pokud je desetinná část 0,5. Vzhledem k tomu, že StrukturapředstavujeregistrXMM,vnitřnípřebíráhodnotuzregistruXMMazapisujejedosystémovépaměti.`__m128`

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="example"></a>Příklad

```cpp
// _mm_cvtss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] =
                           { 101.25, 200.75, 300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvtss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__m128d](../cpp/m128d.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
