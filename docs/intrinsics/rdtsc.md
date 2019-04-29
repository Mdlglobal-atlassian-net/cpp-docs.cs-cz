---
title: __rdtsc
ms.date: 11/04/2016
f1_keywords:
- __rdtsc
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
ms.openlocfilehash: 6f30be3340ae1be237bb2f8a008a8cb60c7351f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396571"
---
# <a name="rdtsc"></a>__rdtsc

**Microsoft Specific**

Generuje `rdtsc` instrukce, která vrátí časové razítko procesoru. Časové razítko procesoru zaznamenává počet hodinových cyklů od posledního resetování.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>Návratová hodnota

64bitové celé číslo bez znaménka představující počet cyklů.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__rdtsc`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní.

Výklad TSC hodnotu této generace hardwaru se liší od v dřívějších verzích x64. Najdete v článku hardware příruček pro další informace.

## <a name="example"></a>Příklad

```
// rdtsc.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__rdtsc)

int main()
{
    unsigned __int64 i;
    i = __rdtsc();
    printf_s("%I64d ticks\n", i);
}
```

```Output
3363423610155519 ticks
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)