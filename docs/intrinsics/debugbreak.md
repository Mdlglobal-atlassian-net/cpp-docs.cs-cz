---
title: __debugbreak | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __debugbreak_cpp
- __debugbreak
dev_langs:
- C++
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2ba9322f4fe94c1c857b0494dc79b417e5d65d8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433886"
---
# <a name="debugbreak"></a>__debugbreak

**Specifické pro Microsoft**

Umístí do kódu zarážku, kde uživatel bude vyzván ke spuštění ladicího programu.

## <a name="syntax"></a>Syntaxe

```
void __debugbreak();
```

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`__debugbreak`|x86, ARM, x64|\<intrin.h >|

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

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)