---
title: _ReadBarrier
ms.date: 09/02/2019
f1_keywords:
- _ReadBarrier
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
ms.openlocfilehash: 8bbcecf95daeef6ea2d40877d37e0eb6b7f3a0e8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217096"
---
# <a name="_readbarrier"></a>_ReadBarrier

**Specifické pro společnost Microsoft**

Omezuje optimalizace kompilátoru, které mohou změnit pořadí operací přístupu k paměti napříč bodem volání.

> [!CAUTION]
> Vnitřní prvky `_WriteBarrier`kompilátoru, a a makrojsouzastaraléanemělybysepoužívat.`MemoryBarrier` `_ReadBarrier` `_ReadWriteBarrier` Pro komunikaci mezi vlákny použijte mechanismy jako [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) a [std:\<: Atomic T >](../standard-library/atomic.md) , které jsou definovány ve [ C++ standardní knihovně](../standard-library/cpp-standard-library-reference.md). V případě hardwarového přístupu použijte možnost kompilátoru [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) spolu s klíčovým slovem [volatile](../cpp/volatile-cpp.md) .

## <a name="syntax"></a>Syntaxe

```C
void _ReadBarrier(void);
```

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_ReadBarrier`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

`_ReadBarrier` Vnitřní omezuje optimalizace kompilátoru, které mohou odebrat nebo změnit pořadí operací přístupu k paměti v bodě volání.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Klíčová slova](../cpp/keywords-cpp.md)
