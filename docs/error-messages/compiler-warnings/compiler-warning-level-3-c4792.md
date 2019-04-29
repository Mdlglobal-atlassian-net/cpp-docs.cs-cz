---
title: Kompilátor upozornění (úroveň 3) C4792
ms.date: 11/04/2016
f1_keywords:
- C4792
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
ms.openlocfilehash: adf233673c4b654927aa9488565adf6ceef5d3e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401563"
---
# <a name="compiler-warning-level-3-c4792"></a>Kompilátor upozornění (úroveň 3) C4792

Funkce 'function' deklarovaná pomocí: sysimport a odkazuje z nativního kódu; naimportujte knihovnu požadovanou pro propojení.

Nativní funkce, které byly naimportovány do programu v rámci atributu DllImport byla volána z nespravované funkce. Proto je třeba propojit knihovnu importu pro knihovnu DLL.

Toto upozornění nelze vyřešit v kódu nebo tak, že změníte způsob kompilace. Použití [upozornění](../../preprocessor/warning.md) direktivy pragma zakážete toto upozornění.

Následující ukázka generuje C4792:

```
// C4792.cpp
// compile with: /clr /W3
// C4792 expected
using namespace System::Runtime::InteropServices;
[DllImport("msvcrt")]
extern "C" int __cdecl puts(const char *);
int main() {}

// Uncomment the following line to resolve.
// #pragma warning(disable : 4792)
#pragma unmanaged
void func(void){
   puts("test");
}
```