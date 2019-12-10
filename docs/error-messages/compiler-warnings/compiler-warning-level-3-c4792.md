---
title: Upozornění kompilátoru (úroveň 3) C4792
ms.date: 11/04/2016
f1_keywords:
- C4792
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
ms.openlocfilehash: f0efed41fad2648d7e681fa4e5575e7f36fb6aeb
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991671"
---
# <a name="compiler-warning-level-3-c4792"></a>Upozornění kompilátoru (úroveň 3) C4792

funkce Function deklarovaná pomocí: sysimport a odkazovaná z nativního kódu; Knihovna importu požadovaná pro propojení

Nativní funkce, která byla importována do programu pomocí DllImport, byla volána z nespravované funkce. Proto je nutné propojit knihovnu importů pro knihovnu DLL.

Toto upozornění nelze přeložit v kódu nebo změnou způsobu, jakým kompilujete. Toto upozornění můžete zakázat pomocí direktivy pragma [Upozornění](../../preprocessor/warning.md) .

Následující ukázka generuje C4792:

```cpp
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
