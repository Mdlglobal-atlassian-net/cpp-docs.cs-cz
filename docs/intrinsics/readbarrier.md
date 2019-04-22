---
title: _ReadBarrier
ms.date: 11/04/2016
f1_keywords:
- _ReadBarrier
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
ms.openlocfilehash: f31293b2bef0304bcdc58f0a8dbfce0436df9843
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025483"
---
# <a name="readbarrier"></a>_ReadBarrier

**Microsoft Specific**

Limituje optimalizace kompilátoru, které můžete změnit pořadí operací přístupu k paměti přes místa volání.

> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, A `_ReadWriteBarrier` – vnitřní prvky kompilátoru a `MemoryBarrier` makra jsou všechny zastaralé a neměl by se používat. Pro komunikace mezi vlákny, použijte mechanismy pro zaslání [atomic_thread_fence –](../standard-library/atomic-functions.md#atomic_thread_fence) a [std::atomic\<T >](../standard-library/atomic.md) , která jsou definována v [ C++ standardní knihovny](../standard-library/cpp-standard-library-reference.md). Pro přístup k hardwaru použijte [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru spolu s [volatile](../cpp/volatile-cpp.md) – klíčové slovo.

## <a name="syntax"></a>Syntaxe

```
void _ReadBarrier(void);
```

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_ReadBarrier`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

`_ReadBarrier` Vnitřně limituje optimalizace kompilátoru, které mohou odebrat nebo změnit pořadí operací přístupu k paměti přes místa volání.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)