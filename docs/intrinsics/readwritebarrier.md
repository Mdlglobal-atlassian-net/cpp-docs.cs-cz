---
title: _ReadWriteBarrier
ms.date: 11/04/2016
f1_keywords:
- _ReadWriteBarrier
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
ms.openlocfilehash: 9da26b685be90bd349d6bfe56c4ad980541d09c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263253"
---
# <a name="readwritebarrier"></a>_ReadWriteBarrier

**Microsoft Specific**

Limituje optimalizace kompilátoru, které mohou změnit pořadí operací přístupu k paměti přes místa volání.

> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, A `_ReadWriteBarrier` – vnitřní prvky kompilátoru a `MemoryBarrier` makra jsou všechny zastaralé a neměl by se používat. Pro komunikace mezi vlákny, použijte mechanismy pro zaslání [atomic_thread_fence –](../standard-library/atomic-functions.md#atomic_thread_fence) a [std::atomic\<T >](../standard-library/atomic.md), které jsou definovány v [ C++ standardní knihovny](../standard-library/cpp-standard-library-reference.md). Pro přístup k hardwaru použijte [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru spolu s [volatile](../cpp/volatile-cpp.md) – klíčové slovo.

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

## <a name="see-also"></a>Viz také:

[_ReadBarrier](../intrinsics/readbarrier.md)<br/>
[_WriteBarrier](../intrinsics/writebarrier.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)