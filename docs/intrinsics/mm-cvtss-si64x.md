---
title: _mm_cvtss_si64x | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvtss_si64x
dev_langs:
- C++
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 928cd812df87fef20a6ba551bd596c4214bfdd9f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417006"
---
# <a name="mmcvtsssi64x"></a>_mm_cvtss_si64x

**Specifické pro Microsoft**

Generuje x64 rozšířenou verzi převést skalární jedné přesnosti s plovoucí desetinnou čárkou bodu čísla na 64bitové celé číslo (`cvtss2si`) instrukce.

## <a name="syntax"></a>Syntaxe

```
__int64 _mm_cvtss_si64x( 
   __m128 value 
);
```

#### <a name="parameters"></a>Parametry

*value*<br/>
[in] `__m128` Struktury obsahující hodnot s plovoucí čárkou.

## <a name="return-value"></a>Návratová hodnota

64bitové celé číslo, výsledek převodu první hodnota s plovoucí desetinnou čárkou na celé číslo.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_mm_cvtss_si64x`|x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

První prvek hodnotu struktury je převést na celé číslo a vrátil. Zaokrouhlení řídicí bity v registru MXCSR slouží k určení chování se zaokrouhlováním. Výchozí režim zaokrouhlování je zaokrouhlí na nejbližší zaokrouhlení na číslo sudé, pokud je 0,5 v desetinnou část. Vzhledem k tomu, `__m128` struktura reprezentuje XMM registru, to zabere vnitřní hodnotu z registru XMM a zapisuje je do systémové paměti.

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="example"></a>Příklad

```
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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[__m128d](../cpp/m128d.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)