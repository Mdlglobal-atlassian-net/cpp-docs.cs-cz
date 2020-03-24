---
title: Upozornění kompilátoru (úrovně 2 a 4) C4200
ms.date: 11/04/2016
f1_keywords:
- C4200
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
ms.openlocfilehash: 4b0750fe50e18214e0841eff6b3459438e9a6aec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197948"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>Upozornění kompilátoru (úrovně 2 a 4) C4200

používá se nestandardní rozšíření: pole nulové velikosti ve struktuře/sjednocení

Označuje, že struktura nebo sjednocení obsahuje pole, které má nulovou velikost.

Deklarace pole s nulovou velikostí je rozšířením společnosti Microsoft. To způsobí upozornění úrovně 2, když je C++ soubor kompilován, a při kompilaci souboru jazyka C se zobrazí upozornění úrovně 4. C++kompilace také poskytuje toto upozornění: "nelze generovat operátor Copy-ctor nebo Copy-Assignment, když typ UDT obsahuje pole s nulovou velikostí." Tento příklad generuje upozornění C4200:

```cpp
// C4200.cpp
// compile by using: cl /W4 c4200.cpp
struct A {
    int a[0];  // C4200
};
int main() {
}
```

Toto nestandardní rozšíření se často používá k rozhraní kódu s externími datovými strukturami, které mají proměnlivou délku. Pokud se tento scénář vztahuje na váš kód, můžete zakázat upozornění:

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
