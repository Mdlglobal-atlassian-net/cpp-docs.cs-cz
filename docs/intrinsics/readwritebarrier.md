---
title: _ReadWriteBarrier
ms.date: 11/04/2016
f1_keywords:
- _ReadWriteBarrier
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
ms.openlocfilehash: a279017e57c8bf828b302940463bd0b3504f085d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626158"
---
# <a name="readwritebarrier"></a>_ReadWriteBarrier

**Specifické pro Microsoft**

Limituje optimalizace kompilátoru, které mohou změnit pořadí operací přístupu k paměti přes místa volání.

> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, A `_ReadWriteBarrier` – vnitřní prvky kompilátoru a `MemoryBarrier` makra jsou všechny zastaralé a neměl by se používat. Pro komunikace mezi vlákny, použijte mechanismy pro zaslání [atomic_thread_fence –](../standard-library/atomic-functions.md#atomic_thread_fence) a [std::atomic\<T >](../standard-library/atomic.md), které jsou definovány v [standardní knihovny C++](../standard-library/cpp-standard-library-reference.md). Pro přístup k hardwaru použijte [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru spolu s [volatile](../cpp/volatile-cpp.md) – klíčové slovo.

## <a name="syntax"></a>Syntaxe

```
void _ReadWriteBarrier(void);
```

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_ReadWriteBarrier`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

`_ReadWriteBarrier` Vnitřně limituje optimalizace kompilátoru, které mohou odebrat nebo změnit pořadí přístupu k paměti přes místa volání.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[_ReadBarrier](../intrinsics/readbarrier.md)<br/>
[_WriteBarrier](../intrinsics/writebarrier.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)