---
title: _disable
ms.date: 11/04/2016
f1_keywords:
- _disable_cpp
- _disable
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
ms.openlocfilehash: 64e7031ab578632322dfd5c73eb81e0750c1e0b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587808"
---
# <a name="disable"></a>_disable

**Specifické pro Microsoft**

Zakáže přerušení.

## <a name="syntax"></a>Syntaxe

```
void _disable(void);
```

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_disable`|x86, ARM, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

`_disable` dává pokyn Vymazat příznak přerušení procesoru. Na x86 systémy, tato funkce generuje Vymazat příznak přerušení (`cli`) instrukce.

Tato funkce je pouze k dispozici v režimu jádra. Pokud použity v uživatelském režimu, je vyvolána výjimka Privilegovaná instrukce v době běhu.

Na platformách ARM se tato rutina je k dispozici pouze jako vnitřní.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)