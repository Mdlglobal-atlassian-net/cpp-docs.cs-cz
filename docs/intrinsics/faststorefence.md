---
title: __faststorefence
ms.date: 11/04/2016
f1_keywords:
- __faststorefence_cpp
- __faststorefence
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
ms.openlocfilehash: a0c8027f443a475b03521920e2e036e7ed4eaafb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349001"
---
# <a name="faststorefence"></a>__faststorefence

**Microsoft Specific**

Záruky, že každý předchozí odkaz paměti, včetně načítají a ukládají odkazy na paměť, je viditelné globálně před všechny odkazy na další paměti.

## <a name="syntax"></a>Syntaxe

```
void __faststorefence();
```

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__faststorefence`|x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Generuje posloupnost instrukce barrier úplné paměti, že záruky načítají a ukládají operace vydané před vnitřní jsou globálně viditelná před spuštěním bude pokračovat. Efekt je srovnatelná se ale rychlejší než `_mm_mfence` vnitřní na všechny x64 platformy.

Na platformě AMD64 Tato rutina generuje instrukce, který je rychlejší ohrazení úložiště než `sfence` instrukce. Zadání časově kritického kódu, použijte tuto vnitřní místo `_mm_sfence` pouze na platformách AMD64. Na platformách Intel x64 `_mm_sfence` instrukce je rychlejší.

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)