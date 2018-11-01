---
title: __outwordstring
ms.date: 11/04/2016
f1_keywords:
- __outwordstring
helpviewer_keywords:
- rep outsw instruction
- __outwordstring intrinsic
- outsw instruction
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
ms.openlocfilehash: 92ec21cdf7fb9d86ee7c8b9fa5090bbace2fe869
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494611"
---
# <a name="outwordstring"></a>__outwordstring

**Specifické pro Microsoft**

Generuje `rep outsw` instrukce, která odesílá `Count` slova začínající na `Buffer` portu vstupně-výstupní operace určené `Port`.

## <a name="syntax"></a>Syntaxe

```
void __outwordstring( 
   unsigned short Port, 
   unsigned short* Buffer, 
   unsigned long Count 
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port pro odesílání dat na.

*Vyrovnávací paměti*<br/>
[in] Ukazatel na data, která mají být odeslány zadaný port.

*Počet*<br/>
[in] Počet slov k odeslání.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__outwordstring`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)