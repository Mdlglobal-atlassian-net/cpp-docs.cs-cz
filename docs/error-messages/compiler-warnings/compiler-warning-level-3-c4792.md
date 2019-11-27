---
title: Upozornění kompilátoru (úroveň 3) C4792
ms.date: 11/04/2016
f1_keywords:
- C4792
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
ms.openlocfilehash: 84a8a8bbb08ac97fe87d63d1ea44587790f87d92
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189331"
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