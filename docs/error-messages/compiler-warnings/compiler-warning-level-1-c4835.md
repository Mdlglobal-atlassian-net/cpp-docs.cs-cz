---
title: Upozornění kompilátoru (úroveň 1) C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: f86fcaea8a742c19ce175a453c06669178ed2145
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174853"
---
# <a name="compiler-warning-level-1-c4835"></a>Upozornění kompilátoru (úroveň 1) C4835

' Variable ': inicializátor pro exportovaná data se nespustí, dokud se spravovaný kód poprvé nespustí v sestavení hostitele.

Při přístupu k datům mezi spravovanými komponentami se doporučuje, abyste nepoužívali nativní C++ mechanismy importu a exportu. Místo toho deklarujte své datové členy uvnitř spravovaného typu a odkazujte na metadata pomocí `#using` v klientovi. Další informace najdete v tématu [direktiva #using](../../preprocessor/hash-using-directive-cpp.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4835.

```cpp
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>Příklad

Následující ukázka používá komponentu sestavenou v předchozím příkladu, která ukazuje, že hodnota proměnných není podle očekávání.

```cpp
// C4835_b.cpp
// compile with: /clr C4835.lib
#include <stdio.h>
__declspec(dllimport) int m;
__declspec(dllimport) int *p;

int main() {
   printf("%d\n", m);
   printf("%d\n", p);
}
```

```Output
0
268456008
```
