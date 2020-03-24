---
title: Chyba kompilátoru C2797
ms.date: 11/04/2016
f1_keywords:
- C2797
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
ms.openlocfilehash: 9973ddcccc69e85bdf79e0623fa4bcc1d6689032
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202073"
---
# <a name="compiler-error-c2797"></a>Chyba kompilátoru C2797

Zastaralé Inicializace seznamu uvnitř seznamu inicializátoru členů nebo inicializátor nestatických datových členů není implementována.

Toto upozornění je zastaralé v aplikaci Visual Studio 2015. V Visual Studio 2013 a starších verzích kompilátor společnosti Microsoft C++ neimplementuje inicializaci seznamu uvnitř seznamu inicializátoru členů ani inicializátoru nestatických datových členů. Před Visual Studio 2013 aktualizace 3 se tato činnost v tichém režimu převedla na volání funkce, což by mohlo vést k chybnému generování kódu. Visual Studio 2013 Update 3 hlásí chybu.

Tento příklad generuje C2797:

```
#include <vector>
struct S {
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'

    std::vector<int> v1;
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'
};
```

Tento příklad také generuje C2797:

```
struct S1 {
    int i;
};

struct S2 {
    S2() : s1{0} {} // C2797, VS2013 RTM interprets as S2() : s1(0) {} causing C2664
    S1 s1;
    S1 s2{0}; // C2797, VS2013 RTM interprets as S1 s2 = S1(0); causing C2664
};
```

Chcete-li tento problém vyřešit, můžete použít explicitní konstrukci vnitřních seznamů. Příklad:

```
#include <vector>
typedef std::vector<int> Vector;
struct S {
    S() : v1(Vector{1}) {}

    Vector v1;
    Vector v2 = Vector{1, 2};
};
```

Pokud nepožadujete inicializaci seznamu:

```
struct S {
    S() : s1("") {}

    std::string s1;
    std::string s2 = std::string("");
};
```

(Kompilátor v Visual Studio 2013 implicitně před Visual Studio 2013 aktualizaci 3.)
