---
title: _ReadWriteBarrier | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ReadWriteBarrier
dev_langs:
- C++
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86d9b970453e33aa12590f935689361d239025af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440365"
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