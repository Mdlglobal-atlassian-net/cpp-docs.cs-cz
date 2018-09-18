---
title: Chyba Linkerů LNK1306 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1306
dev_langs:
- C++
helpviewer_keywords:
- LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cc007a4a594c8593d7820365377f1c811b1e23c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050564"
---
# <a name="linker-tools-error-lnk1306"></a>Chyba linkerů LNK1306

> Není možné spravovat funkci vstupního bodu DLL; nativní kompilace

`DllMain` nemohou být zkompilovány do jazyka MSIL; musí být zkompilována pro nativní.

Chcete-li vyřešit tento problém

- Zkompilujte soubor, který obsahuje vstupní bod bez **/CLR**.

- Do vstupního bodu `#pragma unmanaged` oddílu.

Další informace naleznete v tématu:

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [managed, unmanaged](../../preprocessor/managed-unmanaged.md)

- [Inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md)

- [Knihovny DLL a chování běhové knihovny v jazyce Visual C++](../../build/run-time-library-behavior.md)

## <a name="example"></a>Příklad

Následující ukázka generuje LNK1306.

```cpp
// LNK1306.cpp
// compile with: /clr /link /dll /entry:NewDllMain
// LNK1306 error expected
#include <windows.h>
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
```

Chcete-li vyřešit tento problém, nepoužívejte možnost/CLR a zkompilujte tento soubor, nebo použít `#pragma` směrnice vložit definici vstupní bod do nespravované části, jak je znázorněno v tomto příkladu:

```cpp
// LNK1306fix.cpp
// compile with: /clr /link /dll /entry:NewDllMain
#include <windows.h>
#pragma managed(push, off)
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
#pragma managed(pop)
```
