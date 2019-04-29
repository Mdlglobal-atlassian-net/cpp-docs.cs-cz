---
title: __outdwordstring
ms.date: 11/04/2016
f1_keywords:
- __outdwordstring
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
ms.openlocfilehash: 51cb4a97d271d6d41d39d1025e3a5d34b273cdc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396584"
---
# <a name="outdwordstring"></a>__outdwordstring

**Microsoft Specific**

Generuje `rep outsd` instrukce, která odesílá `Count` začínající na x doubleword `Buffer` portu vstupně-výstupní operace určené `Port`.

## <a name="syntax"></a>Syntaxe

```
void __outdwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port pro odesílání dat na.

*Vyrovnávací paměti*<br/>
[in] Ukazatel na data, která mají být odeslány zadaný port.

*Počet*<br/>
[in] Počet x doubleword k odeslání.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__outdwordstring`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)