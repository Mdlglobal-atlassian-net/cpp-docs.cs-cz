---
title: Chyba linkerů LNK1306
ms.date: 11/04/2016
f1_keywords:
- LNK1306
helpviewer_keywords:
- LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
ms.openlocfilehash: ddaa8797e0cf8ff617408aedc770b21cc656cec4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659667"
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
