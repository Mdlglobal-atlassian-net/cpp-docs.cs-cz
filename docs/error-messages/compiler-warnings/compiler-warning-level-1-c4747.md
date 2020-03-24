---
title: Upozornění kompilátoru (úroveň 1) C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: 2fd7f0960966a981d82d19e7b2533b1ffcd3bc00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175191"
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
