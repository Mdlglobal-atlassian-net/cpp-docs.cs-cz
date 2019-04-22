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
ms.openlocfilehash: 93db063c6b53f0bec739ba134728b83379a21f53
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024672"
---
# <a name="disable"></a>_disable

**Microsoft Specific**

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

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)