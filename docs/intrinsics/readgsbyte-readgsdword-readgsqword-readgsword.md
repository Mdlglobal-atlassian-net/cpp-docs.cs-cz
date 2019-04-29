---
title: __readgsbyte, __readgsdword, __readgsqword, __readgsword
ms.date: 11/04/2016
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
ms.openlocfilehash: a677b96975e0d2adcc7e548992a12bd597bea6a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396467"
---
# <a name="readgsbyte-readgsdword-readgsqword-readgsword"></a>__readgsbyte, __readgsdword, __readgsqword, __readgsword

**Microsoft Specific**

Čtení paměti z umístění, které určuje posun vzhledem k začátku segmentu GS.

## <a name="syntax"></a>Syntaxe

```
unsigned char __readgsbyte(
   unsigned long Offset
);
unsigned short __readgsword(
   unsigned long Offset
);
unsigned long __readgsdword(
   unsigned long Offset
);
unsigned __int64 __readgsqword(
   unsigned long Offset
);
```

#### <a name="parameters"></a>Parametry

*Posun*<br/>
[in] Posun od začátku `GS` ke čtení z.

## <a name="return-value"></a>Návratová hodnota

Obsah paměti byte, word, slovo double nebo quadword (jak je uvedeno podle názvu funkce volaná) v umístění `GS:[Offset]`.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__readgsbyte`|x64|
|`__readgsdword`|x64|
|`__readgsqword`|x64|
|`__readgsword`|x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tyto rutiny jsou dostupné jenom jako vnitřní.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)
