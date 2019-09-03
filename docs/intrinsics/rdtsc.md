---
title: __rdtsc
ms.date: 09/02/2019
f1_keywords:
- __rdtsc
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
ms.openlocfilehash: 837b68ca6ac63587cd43a7e8828777221c677e3c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217145"
---
# <a name="__rdtsc"></a>__rdtsc

**Specifické pro společnost Microsoft**

Vygeneruje `rdtsc` instrukci, která vrací časové razítko procesoru. Časové razítko procesoru zaznamenává počet hodinových cyklů od posledního resetování.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>Návratová hodnota

64 unsigned integer reprezentující počet impulsů.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__rdtsc`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní.

Interpretace hodnoty čítače TSC v pozdějších generacích hardwaru se liší od v dřívějších verzích x64. Další informace najdete v příručkách k hardwaru.

## <a name="example"></a>Příklad

```cpp
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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
