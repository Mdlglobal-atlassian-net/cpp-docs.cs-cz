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
ms.openlocfilehash: b52c34014402a235e03c45f82dcd1e5c542e4919
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023097"
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
|`__debugbreak`|x86, ARM, x64|\<intrin.h>|

## <a name="remarks"></a>Poznámky

`__debugbreak` Kompilátoru vnitřní, podobně jako [DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297.aspx), přenosná Win32 způsob, jak způsobit, že zarážku.

> [!NOTE]
>  Při kompilaci s **/CLR**, funkce obsahující `__debugbreak` bude zkompilována do jazyka MSIL. `asm int 3` způsobí, že funkce na nativní. Další informace najdete v tématu [__asm](../assembler/inline/asm.md).

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

**END Specifické pro Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[klíčová slova](../cpp/keywords-cpp.md)