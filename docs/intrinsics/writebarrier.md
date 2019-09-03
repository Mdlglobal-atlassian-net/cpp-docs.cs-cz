---
title: _WriteBarrier
ms.date: 09/02/2019
f1_keywords:
- _WriteBarrier
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
ms.openlocfilehash: a41f4c6c5cdd6b72e76a596622912e88fbd03f34
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219323"
---
# <a name="_writebarrier"></a>_WriteBarrier

**Specifické pro společnost Microsoft**

Omezuje optimalizace kompilátoru, které mohou změnit pořadí operací přístupu k paměti napříč bodem volání.

> [!CAUTION]
> Vnitřní prvky `_WriteBarrier`kompilátoru, a a makrojsouzastaraléanemělybysepoužívat.`MemoryBarrier` `_ReadBarrier` `_ReadWriteBarrier` Pro komunikaci mezi vlákny použijte mechanismy jako [atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence) a [std:\<: Atomic T >](../standard-library/atomic.md), které jsou definovány ve [ C++ standardní knihovně](../standard-library/cpp-standard-library-reference.md). V případě hardwarového přístupu použijte možnost kompilátoru [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) spolu s klíčovým slovem [volatile](../cpp/volatile-cpp.md) .

## <a name="syntax"></a>Syntaxe

```C
void _WriteBarrier(void);
```

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_WriteBarrier`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

`_WriteBarrier` Vnitřní omezuje optimalizace kompilátoru, které mohou odebrat nebo změnit pořadí operací přístupu k paměti v bodě volání.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[_ReadBarrier](../intrinsics/readbarrier.md)\
[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Klíčová slova](../cpp/keywords-cpp.md)
