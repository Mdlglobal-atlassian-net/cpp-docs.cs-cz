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
ms.openlocfilehash: 97932dfe0e187a13b72ae5fe70d761224721c3ff
ms.sourcegitcommit: 1acb6755e11379026a96f63facac4d33f4dc47ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67314258"
---
# <a name="debugbreak"></a>__debugbreak

**Microsoft Specific**

Umístí do kódu zarážku, kde uživatel bude vyzván ke spuštění ladicího programu.

## <a name="syntax"></a>Syntaxe

```
void __debugbreak();
```

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`__debugbreak`|x86, x64, ARM, ARM64|\<intrin.h>|

## <a name="remarks"></a>Poznámky

`__debugbreak` Kompilátoru vnitřní, podobně jako [DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297.aspx), přenosná Win32 způsob, jak způsobit, že zarážku.

> [!NOTE]
>  Při kompilaci s **/CLR**, funkce obsahující `__debugbreak` bude zkompilována do jazyka MSIL. Klíčové slovo `asm int 3` zajistí zkompilování funkce jako nativní. Další informace najdete v tématu [__asm](../assembler/inline/asm.md).

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

Na ARM64 `__debugbreak` vnitřní zkompilován instrukce `brk #0xF000`.

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
