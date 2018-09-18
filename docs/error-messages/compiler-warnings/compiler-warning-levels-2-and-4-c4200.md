---
title: Upozornění kompilátoru (úrovně 2 a 4) C4200 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4200
dev_langs:
- C++
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34e0befb93db742bb2d132b2092414a1a167b87b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100718"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>Upozornění kompilátoru (úrovně 2 a 4) C4200

používá se nestandardní rozšíření: pole nulové velikosti ve struktuře/sjednocení

Označuje, že struktura nebo sjednocení obsahuje pole, které má nulovou velikost.

Deklarace pole s nulovou velikostí je rozšířením společnosti Microsoft. To způsobí, že upozornění úrovně 2 při kompilaci souboru jazyka C++ a upozornění úrovně 4 při kompilaci souboru jazyka C. Kompilace jazyka C++ nabízí také toto upozornění: "Nelze generovat konstruktor Copy nebo přiřazení kopie operátor při UDT obsahuje pole s nulovou velikostí." Tento příklad generuje upozornění C4200:

```cpp
// C4200.cpp
// compile by using: cl /W4 c4200.cpp
struct A {
    int a[0];  // C4200
};
int main() {
}
```

Toto nestandardní rozšíření se často používá ke kódu rozhraní s externích datových struktur, které mají s proměnnou délkou. Pokud se tento scénář se vztahuje na váš kód, můžete zakázat upozornění:

## <a name="example"></a>Příklad

```cpp
// C4200b.cpp
// compile by using: cl /W4 c4200a.cpp
#pragma warning(disable : 4200)
struct A {
    int a[0];
};
int main() {
}
```