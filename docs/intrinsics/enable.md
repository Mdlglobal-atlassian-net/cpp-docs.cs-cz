---
title: _enable
ms.date: 11/04/2016
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: 1d129db17b489972555efb0b5df2de52e01fa649
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631234"
---
# <a name="enable"></a>_enable

**Specifické pro Microsoft**

Umožňuje přerušení.

## <a name="syntax"></a>Syntaxe

```
void _enable(void);
```

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_enable`|x86, ARM, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

`_enable` dává pokyn k nastavení příznaku přerušení procesoru. Na x86 systémy, tato funkce generuje nastavit příznak přerušení (`sti`) instrukce.

Tato funkce je pouze k dispozici v režimu jádra. Pokud se použije v uživatelském režimu, je vyvolána výjimka Privilegovaná instrukce.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)