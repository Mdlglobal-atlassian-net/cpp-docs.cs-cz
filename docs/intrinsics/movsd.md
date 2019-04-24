---
title: __movsd
ms.date: 11/04/2016
f1_keywords:
- __movsd
helpviewer_keywords:
- rep movsd instruction
- __movsd intrinsic
- movsd instruction
ms.assetid: eb5cccf3-aa76-47f0-b9fc-eeca38fd943f
ms.openlocfilehash: 950e83f2cd03e92bb5a9f953affe8e7ff479a408
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263176"
---
# <a name="movsd"></a>__movsd

**Microsoft Specific**

Z nich generuje řetězec přesunout (`rep movsd`) instrukce.

## <a name="syntax"></a>Syntaxe

```
void __movsd(
   unsigned long* Dest,
   unsigned long* Source,
   size_t Count
);
```

#### <a name="parameters"></a>Parametry

*cíl*<br/>
[out] Cíl operace.

*Zdroj*<br/>
[in] Zdroj operaci.

*Počet*<br/>
[in] Počet dvojitými slovy ke kopírování.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__movsd`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Výsledkem je, že první `Count` x doubleword odkazované `Source` se zkopírují do `Dest` řetězec.

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="example"></a>Příklad

```
// movsd.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsd)

int main()
{
    unsigned long a1[10];
    unsigned long a2[10] = {950, 850, 750, 650, 550, 450, 350,
                            250, 150, 50};
    __movsd(a1, a2, 10);

    for (int i = 0; i < 10; i++)
        printf_s("%d ", a1[i]);
    printf_s("\n");
}
```

```Output
950 850 750 650 550 450 350 250 150 50
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)