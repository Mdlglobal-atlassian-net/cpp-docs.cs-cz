---
title: Kompilátor upozornění (úroveň 1) C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: ecaabd482049771b1d3915470a2be7a52e36d361
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462384"
---
# <a name="compiler-warning-level-1-c4747"></a>Kompilátor upozornění (úroveň 1) C4747

Volání spravované 'entrypoint': nastavený zámek zavaděče, včetně vstupního bodu DLL a volání dosáhlo ze vstupního bodu DLL se možná nespustí spravovaný kód

Kompilátor najít (o) vstupní bod knihovny DLL zkompilované na MSIL.  Z důvodu možných problémů při načítání knihovny DLL, jehož vstupního bodu byla zkompilována do jazyka MSIL se důrazně nedoporučuje v kompilaci funkci vstupního bodu DLL do jazyka MSIL.

Další informace najdete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md) a [chyba Linkerů LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Modul s parametrem se nekompilují **/CLR**.

1. Označit funkci vstupního bodu pomocí `#pragma unmanaged`.

## <a name="example"></a>Příklad

Následující ukázka generuje C4747.

```
// C4747.cpp
// compile with: /clr /c /W1
// C4747 expected
#include <windows.h>

// Uncomment the following line to resolve.
// #pragma unmanaged

BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {
   return TRUE;
};
```