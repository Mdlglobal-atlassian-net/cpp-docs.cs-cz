---
title: Chyba kompilátoru C2552
ms.date: 11/04/2016
f1_keywords:
- C2552
helpviewer_keywords:
- C2552
ms.assetid: 0e0ab759-788a-4faf-9337-80d4b9e2e8c9
ms.openlocfilehash: b15ee67e39631926b7061826369e855bc3714a96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374196"
---
# <a name="compiler-error-c2552"></a>Chyba kompilátoru C2552

identifikátor: jiné položky než agregace nelze inicializovat pomocí seznamu inicializátorů.

Identifikátor agregace byl nesprávně inicializován.

[Agregáty](../../c-language/initializing-aggregate-types.md) jsou definovány jako:

- Pole

- Třídy, struktury a sjednocení, které nemají:

  - Konstruktory

  - Soukromé nebo chráněné členy

  - Základní třídy

  - Virtuální funkce

Jazyk Visual C++ navíc neumožňuje používat v agregaci datové typy, které obsahují konstruktory.

Následují důvody, proč se při pokusu o inicializaci agregace u určitého typu může zobrazit upozornění C2552:

- Typ má jeden nebo více uživatelem definovaných konstruktorů.

- Typ má jeden nebo více nestatických soukromých datových členů.

- Typ má jednu nebo více virtuálních funkcí.

- Typ má základní třídu.

- Typ je třída ref nebo rozhraní CLR.

- Typ má pole nefixního rozměru (nulové pole), jehož prvky mají destruktory.

Následující ukázka generuje upozornění C2552:

```cpp
// C2552.cpp
// compile with: /clr
#include <string>
using namespace std;

struct Pair_Incorrect {
private:
   string m_name;
   double m_val;
};

struct Pair_Correct1 {
public:
   Pair_Correct1(string name, double val)
      : m_name(name), m_val(val) {}

private:
   string m_name;
   double m_val;
};

struct Pair_Correct2 {
public:
   string m_name;
   double m_val;
};

int main() {
   // To fix, add a constructor to this class and use it for
   // initializing the data members, see Pair_Correct1 (below)
   // or
   // Do not have any private or protected non-static data members,
   // see Pair_Correct2 (below).  Pair_Correct2 is not recommended in
   // case your object model requires some non-static data members to
   // be private or protected

   string name("John");
   Pair_Incorrect pair1 = { name, 0.0 };   // C2552

   // initialize a CLR immutable value type that has a constructor
   System::DateTime dt = {2001, 4, 12, 22, 16, 49, 844};   // C2552

   Pair_Correct1 pair2( name, 0.0 );
   Pair_Correct1 pair3 = Pair_Correct1( name, 0.0 );
   Pair_Correct2 pair4 = { name, 0.0 };
   System::DateTime dt2(2001, 4, 12, 22, 16, 49, 844);
}
```
