---
title: __movsb
ms.date: 11/04/2016
f1_keywords:
- __movsb
helpviewer_keywords:
- movsb instruction
- rep movsb instruction
- __movsb intrinsic
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
ms.openlocfilehash: 42124743c27b297c723780c1bc19038fb54e638d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263812"
---
# <a name="movsb"></a>__movsb

**Microsoft Specific**

Z nich generuje řetězec přesunout (`rep movsb`) instrukce.

## <a name="syntax"></a>Syntaxe

```
void __movsb(
   unsigned char* Destination,
   unsigned const char* Source,
   size_t Count
);
```

#### <a name="parameters"></a>Parametry

*cíl*<br/>
[out] Ukazatel na cíl kopírování.

*Zdroj*<br/>
[in] Ukazatel na zdroj kopie.

*Počet*<br/>
[in] Počet bajtů, které mají kopírovat.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__movsb`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Výsledkem je, že první `Count` bajtů odkazované `Source` se zkopírují do `Destination` řetězec.

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="example"></a>Příklad

```
// movsb.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsb)

int main()
{
    unsigned char s1[100];
    unsigned char s2[100] = "A big black dog.";
    __movsb(s1, s2, 100);

    printf_s("%s %s", s1, s2);
}
```

```Output
A big black dog. A big black dog.
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)