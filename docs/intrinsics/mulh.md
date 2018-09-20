---
title: __mulh | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __mulh
dev_langs:
- C++
helpviewer_keywords:
- __mulh intrinsic
ms.assetid: cd2ab093-9ef6-404d-ac34-0bee033882f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9393026814e8f3f7dd90704cd08ea96dfb9a35a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407319"
---
# <a name="mulh"></a>__mulh

**Specifické pro Microsoft**

Vrátí hodnotu 64 bitů součin dvou 64-bit celá čísla se znaménkem.

## <a name="syntax"></a>Syntaxe

```
__int64 __mulh( 
   __int64 a, 
   __int64 b 
);
```

#### <a name="parameters"></a>Parametry

*a*<br/>
[in] První číslo pro vynásobení.

*b*<br/>
[in] Druhé číslo pro vynásobení.

## <a name="return-value"></a>Návratová hodnota

Vysoká 64 bitů 128bitové výsledek násobení.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__mulh`|x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="example"></a>Příklad

```
// mulh.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__mulh)

int main()
{
    __int64 a = 0x0fffffffffffffffI64;
    __int64 b = 0xf0000000I64;

    __int64 result = __mulh(a, b); // the high 64 bits
    __int64 result2 = a * b; // the low 64 bits

    printf_s(" %#I64x * %#I64x = %#I64x%I64x\n",
             a, b, result, result2);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)