---
title: __stosw | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __stosw
dev_langs:
- C++
helpviewer_keywords:
- stosw instruction
- __stosw intrinsic
- rep stosw instruction
ms.assetid: 7620fd1d-dba5-40e3-8e07-01aa68895133
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41f086c2427d8147014bb6df25f3923d3ab4b84c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401326"
---
# <a name="stosw"></a>__stosw

**Specifické pro Microsoft**

Generuje instrukce řetězec úložiště (`rep stosw`).

## <a name="syntax"></a>Syntaxe

```
void __stosw( 
   unsigned short* Dest, 
   unsigned short Data, 
   size_t Count 
);
```

#### <a name="parameters"></a>Parametry

*cíl*<br/>
[out] Cíl operace.

*Data*<br/>
[in] Data k uložení.

*Počet*<br/>
[in] Délka bloku slova, která chcete zapsat.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__stosw`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Výsledkem je, že slovo `Data` je zapsán do bloku `Count` slova v `Dest` řetězec.

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="example"></a>Příklad

```
// stosw.c
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosw)

int main()
{
    unsigned short val = 128;
    unsigned short a[100];
    memset(a, 0, sizeof(a));
    __stosw(a+10, val, 2);
    printf_s("%u %u %u %u", a[9], a[10], a[11], a[12]);
}
```

```Output
0 128 128 0
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)