---
title: __debugbreak
ms.date: 09/02/2019
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: e4cf2c85818a878417c560ddb5a80f8690e60a93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217932"
---
# <a name="__debugbreak"></a>__debugbreak

**Specifické pro společnost Microsoft**

Umístí do kódu zarážku, kde uživatel bude vyzván ke spuštění ladicího programu.

## <a name="syntax"></a>Syntaxe

```C
void __debugbreak();
```

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|Záhlaví|
|---------------|------------------|------------|
|`__debugbreak`|x86, x64, ARM, ARM64|\<intrin.h>|

## <a name="remarks"></a>Poznámky

Vnitřní kompilátor, podobně jako DebugBreak, je přenosným způsobem Win32, který způsobuje zarážku. [](/windows/win32/api/debugapi/nf-debugapi-debugbreak) `__debugbreak`

> [!NOTE]
> Při kompilaci s možností **/CLR**bude funkce obsahující `__debugbreak` hodnotu zkompilována do jazyka MSIL. Klíčové slovo `asm int 3` zajistí zkompilování funkce jako nativní. Další informace najdete v tématu [__asm](../assembler/inline/asm.md).

Příklad:

```C
main() {
   __debugbreak();
}
```

je podobné kódu:

```C
main() {
   __asm {
      int 3
   }
}
```

na počítači architektury x86.

V ARM64 `__debugbreak` je vnitřní kompilace zkompilována do instrukce `brk #0xF000`.

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Klíčová slova](../cpp/keywords-cpp.md)
