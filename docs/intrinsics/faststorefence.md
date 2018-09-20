---
title: __faststorefence | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __faststorefence_cpp
- __faststorefence
dev_langs:
- C++
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5047dbb2023272ab03cc7d49f877f0fcc38a7b76
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402184"
---
# <a name="faststorefence"></a>__faststorefence

**Specifické pro Microsoft**

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

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)