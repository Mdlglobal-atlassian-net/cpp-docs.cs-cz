---
title: __debugbreak
ms.date: 11/04/2016
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: ed75b94e8bf0aca9369c56f23e8ff00ea6953642
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509497"
---
# <a name="__debugbreak"></a>__debugbreak

**Specifické pro společnost Microsoft**

Umístí do kódu zarážku, kde uživatel bude vyzván ke spuštění ladicího programu.

## <a name="syntax"></a>Syntaxe

```
void __debugbreak();
```

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|Záhlaví|
|---------------|------------------|------------|
|`__debugbreak`|x86, x64, ARM, ARM64|\<intrin.h>|

## <a name="remarks"></a>Poznámky

Vnitřní kompilátor, podobně jako DebugBreak, je přenosným způsobem Win32, který způsobuje zarážku. [](/windows/win32/api/debugapi/nf-debugapi-debugbreak) `__debugbreak`

> [!NOTE]
>  Při kompilaci s možností **/CLR**bude funkce obsahující `__debugbreak` hodnotu zkompilována do jazyka MSIL. Klíčové slovo `asm int 3` zajistí zkompilování funkce jako nativní. Další informace najdete v tématu [__asm](../assembler/inline/asm.md).

Příklad:

```
main() {
   __debugbreak();
}
```

je podobné kódu:

```
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

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
