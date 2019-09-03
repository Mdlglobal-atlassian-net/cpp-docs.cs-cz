---
title: _ReadWriteBarrier
ms.date: 09/02/2019
f1_keywords:
- _ReadWriteBarrier
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
ms.openlocfilehash: d755d045970da01d2eee33377c1452191eac4fe2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217983"
---
# <a name="_readwritebarrier"></a>_ReadWriteBarrier

**Specifické pro společnost Microsoft**

Omezuje optimalizace kompilátoru, které mohou změnit pořadí přístupů k paměti přes bod volání.

> [!CAUTION]
> Vnitřní prvky `_WriteBarrier`kompilátoru, a a makrojsouzastaraléanemělybysepoužívat.`MemoryBarrier` `_ReadBarrier` `_ReadWriteBarrier` Pro komunikaci mezi vlákny použijte mechanismy jako [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) a [std:\<: Atomic T >](../standard-library/atomic.md), které jsou definovány ve [ C++ standardní knihovně](../standard-library/cpp-standard-library-reference.md). V případě hardwarového přístupu použijte možnost kompilátoru [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) spolu s klíčovým slovem [volatile](../cpp/volatile-cpp.md) .

## <a name="syntax"></a>Syntaxe

```C
void _ReadWriteBarrier(void);
```

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_ReadWriteBarrier`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

`_ReadWriteBarrier` Vnitřní omezuje optimalizace kompilátoru, které mohou odebrat nebo změnit pořadí přístupů k paměti přes bod volání.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[_ReadBarrier](../intrinsics/readbarrier.md)\
[_WriteBarrier](../intrinsics/writebarrier.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Klíčová slova](../cpp/keywords-cpp.md)
