---
title: __readfsbyte __readfsdword, __readfsqword, __readfsword
ms.date: 11/04/2016
f1_keywords:
- __readfsword
- __readfsdword
- __readfsbyte
- __readfsqword
helpviewer_keywords:
- __readfsword intrinsic
- readfsword intrinsic
- __readfsdword intrinsic
- readfsbyte intrinsic
- __readfsbyte intrinsic
- readfsdword intrinsic
- readfsqword intrinsic
- __readfsqword intrinsic
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
ms.openlocfilehash: bbf963d3a7b927d46485465a61fa08328b8efb52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507993"
---
# <a name="readfsbyte-readfsdword-readfsqword-readfsword"></a>__readfsbyte __readfsdword, __readfsqword, __readfsword

**Specifické pro Microsoft**

Čtení paměti z umístění, které určuje posun vzhledem k začátku segmentu služby FS.

## <a name="syntax"></a>Syntaxe

```
unsigned char __readfsbyte( 
   unsigned long Offset 
);
unsigned short __readfsword( 
   unsigned long Offset 
);
unsigned long __readfsdword( 
   unsigned long Offset
);
unsigned __int64 __readfsqword( 
   unsigned long Offset 
);
```

#### <a name="parameters"></a>Parametry

*Posun*<br/>
[in] Posun od začátku `FS` ke čtení z.

## <a name="return-value"></a>Návratová hodnota

Obsah paměti byte, word, dvojitého slova nebo quadword (jak je uvedeno podle názvu funkce volaná) v umístění `FS:[Offset]`.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__readfsbyte`|x86|
|`__readfsdword`|x86|
|`__readfsqword`|x86|
|`__readfsword`|x86|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tyto rutiny jsou k dispozici pouze jako vnitřní funkce.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)