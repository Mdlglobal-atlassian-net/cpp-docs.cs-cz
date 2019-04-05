---
title: _WriteBarrier
ms.date: 11/04/2016
f1_keywords:
- _WriteBarrier
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
ms.openlocfilehash: d2db648c9f41bd4f773f5bf152f31cf990a75c8e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025762"
---
# <a name="writebarrier"></a>_WriteBarrier

**Specifické pro Microsoft**

Limituje optimalizace kompilátoru, které můžete změnit pořadí operací přístupu k paměti přes místa volání.

> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, A `_ReadWriteBarrier` – vnitřní prvky kompilátoru a `MemoryBarrier` makra jsou všechny zastaralé a neměl by se používat. Pro komunikace mezi vlákny, použijte mechanismy pro zaslání [atomic_thread_fence –](../standard-library/atomic-functions.md#atomic_thread_fence) a [std::atomic\<T >](../standard-library/atomic.md), které jsou definovány v [standardní knihovny C++](../standard-library/cpp-standard-library-reference.md). Pro přístup k hardwaru použijte [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru spolu s [volatile](../cpp/volatile-cpp.md) – klíčové slovo.

## <a name="syntax"></a>Syntaxe

```
void _WriteBarrier(void);
```

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_WriteBarrier`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

`_WriteBarrier` Vnitřně limituje optimalizace kompilátoru, které mohou odebrat nebo změnit pořadí operací přístupu k paměti přes místa volání.

**END Specifické pro Microsoft**

## <a name="see-also"></a>Viz také:

[_ReadBarrier](../intrinsics/readbarrier.md)<br/>
[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[klíčová slova](../cpp/keywords-cpp.md)