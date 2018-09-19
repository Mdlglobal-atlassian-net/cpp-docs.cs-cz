---
title: Upozornění (úroveň 3) C4792 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4792
dev_langs:
- C++
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4afb08cbe3203ff462f59fec4c1e712aa024c081
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136059"
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