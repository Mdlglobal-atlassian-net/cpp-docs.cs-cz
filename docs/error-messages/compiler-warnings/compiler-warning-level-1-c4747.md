---
title: Upozornění kompilátoru (úroveň 1) C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: 623b29d345a850cc312f23e4c521aa0be5b47242
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052434"
---
# <a name="compiler-warning-level-1-c4747"></a>Upozornění kompilátoru (úroveň 1) C4747

Volání spravovaného vstupního bodu: spravovaný kód nesmí běžet pod zámkem zavaděče, včetně vstupního bodu knihovny DLL a volání z příchozího vstupního bodu knihovny DLL.

Kompilátor nalezl (pravděpodobný) vstupní bod knihovny DLL kompilovaný do jazyka MSIL.  Z důvodu potenciálních problémů s načtením knihovny DLL, jejíž vstupní bod byl zkompilován do jazyka MSIL, důrazně nedoporučujeme kompilovat funkci vstupního bodu knihovny DLL do jazyka MSIL.

Další informace naleznete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md) a [nástrojů linkeru chyba linkerů LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Nezkompilujte modul s **/CLR**.

1. Označte funkci vstupního bodu pomocí `#pragma unmanaged`.

## <a name="example"></a>Příklad

Následující ukázka generuje C4747.

```cpp
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