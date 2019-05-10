---
title: Chyba kompilátoru C2797
ms.date: 11/04/2016
f1_keywords:
- C2797
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
ms.openlocfilehash: ccd007bf193bd6529748004a96745fafcb9f3226
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447822"
---
# <a name="compiler-error-c2797"></a>Chyba kompilátoru C2797

(Zastaralé) Inicializace seznamu je uvnitř seznamu inicializátoru členů nebo nestatický datový člen inicializátor není implementována.

Toto upozornění je zastaralé v sadě Visual Studio 2015. V sadě Visual Studio 2013 a předchozími verzemi, Microsoft C++ kompilátoru neimplementuje Inicializace seznamu je uvnitř seznamu inicializátoru členů nebo inicializátoru nestatický datový člen. Před Visual Studio 2013 Update 3 Tento byl text tiše převeden na volání funkce, které by mohlo vést k generování chybného kódu. Visual Studio 2013 Update 3 sestavy to za chybu.

Tento příklad vygeneruje C2797:

```
#include <vector>
struct S {
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'

    std::vector<int> v1;
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'
};
```

Tento příklad také vygeneruje C2797:

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

Chcete-li vyřešit tento problém, můžete použít explicitní konstrukce vnitřní seznamy. Příklad:

```
#include <vector>
typedef std::vector<int> Vector;
struct S {
    S() : v1(Vector{1}) {}

    Vector v1;
    Vector v2 = Vector{1, 2};
};
```

Pokud nechcete, aby Inicializace seznamu:

```
struct S {
    S() : s1("") {}

    std::string s1;
    std::string s2 = std::string("");
};
```

(Kompilátor v sadě Visual Studio 2013 to dělá proto implicitně před Visual Studio 2013 Update 3.)