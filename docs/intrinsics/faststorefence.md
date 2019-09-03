---
title: __faststorefence
ms.date: 09/02/2019
f1_keywords:
- __faststorefence_cpp
- __faststorefence
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
ms.openlocfilehash: d11a20666612fe1bca22f5d46b93e898dae375f6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222175"
---
# <a name="__faststorefence"></a>__faststorefence

**Specifické pro společnost Microsoft**

Garantuje, že všechny předchozí odkazy na paměť, včetně odkazů na paměť Load i Store, jsou globálně viditelné před každým dalším odkazem na paměť.

## <a name="syntax"></a>Syntaxe

```C
void __faststorefence();
```

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__faststorefence`|x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Vygeneruje úplnou sekvenci instrukcí pro zajištění bariéry paměti, která garantuje operace načtení a uložení, které jsou vydány před tím, než bude provádění pokračovat. Efekt je srovnatelný, ale rychlejší než `_mm_mfence` vnitřní na všech platformách x64.

Na platformě amd64 Tato rutina generuje instrukci, která je rychlejší ochranou úložiště než `sfence` instrukce. Pro kód kritický pro čas použijte tento vnitřní místo `_mm_sfence` jenom na platformách amd64. Na platformách `_mm_sfence` Intel x64 je instrukce rychlejší.

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
