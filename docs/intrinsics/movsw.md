---
title: __movsw
ms.date: 11/04/2016
f1_keywords:
- __movsw
helpviewer_keywords:
- movsw instruction
- rep movsw instruction
- __movsw intrinsic
ms.assetid: db402ad5-7f0e-449a-b0b0-eea9928d6435
ms.openlocfilehash: 4bb8a6411c3700b3338fb7d5bc76884f84bb2413
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453612"
---
# <a name="movsw"></a>__movsw

**Specifické pro Microsoft**

Z nich generuje řetězec přesunout (`rep movsw`) instrukce.

## <a name="syntax"></a>Syntaxe

```
void __movsw( 
   unsigned short* Dest, 
   unsigned short* Source, 
   size_t Count 
);
```

#### <a name="parameters"></a>Parametry

*cíl*<br/>
[out] Cíl operace.

*Zdroj*<br/>
[in] Zdroj operaci.

*Počet*<br/>
[in] Počet slova, která chcete kopírovat.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__movsw`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Výsledkem je, že první `Count` slova odkazované `Source` se zkopírují do `Dest` řetězec.

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="example"></a>Příklad

```
// movsw.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsw)

int main()
{
    unsigned short s1[10];
    unsigned short s2[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
    __movsw(s1, s2, 10);

    for (int i = 0; i < 10; i++)
        printf_s("%d ", s1[i]);
    printf_s("\n");
}
```

```Output
0 1 2 3 4 5 6 7 8 9
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)