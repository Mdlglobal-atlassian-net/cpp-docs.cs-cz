---
title: Rozlišení přetížení volání šablony funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function templates overload resolution
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0eae1d77b3d0c9fa34cb2bbd5f39548aea83f6a2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067152"
---
# <a name="overload-resolution-of-function-template-calls"></a>Rozlišení přetížení volání šablony funkce

Šablony funkce lze přetížení funkce nešablonových se stejným názvem. V tomto scénáři jsou vyřešeny volání funkce tak, že nejprve pomocí odvození argumentu šablony pro vytvoření instance šablony funkce s specializaci jedinečný. Pokud selže odvození argumentu šablony další přetížení funkce jsou považovány za vyřešit volání. Tyto další přetížení, označované také jako sada Release candidate, zahrnují funkce nešablonových a další instance funkce šablony. Pokud bude úspěšné odvození argumentu šablony, pak generované funkce je ve srovnání s dalších funkcí, které mají určit nejlepší shodu dle pravidel pro řešení přetížení. Další informace najdete v tématu [přetížení funkce](function-overloading.md).

## <a name="example"></a>Příklad

Pokud je funkce nešablonových stejně dobrým shoda pro šablony funkce, funkce nešablonových zvolená (pokud byly argumenty šablony explicitně zadán), protože při volání metody `f(1, 1)` v následujícím příkladu.

```cpp
// template_name_resolution9.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void f(int, int) { cout << "f(int, int)" << endl; }
void f(char, char) { cout << "f(char, char)" << endl; }

template <class T1, class T2>
void f(T1, T2)
{
   cout << "void f(T1, T2)" << endl;
};

int main()
{
   f(1, 1);   // Equally good match; choose the nontemplate function.
   f('a', 1); // Chooses the template function.
   f<int, int>(2, 2);  // Template arguments explicitly specified.
}
```

```Output
f(int, int)
void f(T1, T2)
void f(T1, T2)
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, že přesně odpovídající funkce šablony je upřednostňované, pokud funkce nešablonových vyžaduje převod.

```cpp
// template_name_resolution10.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void f(int, int) { cout << "f(int, int)" << endl; }

template <class T1, class T2>
void f(T1, T2)
{
   cout << "void f(T1, T2)" << endl;
};

int main()
{
   long l = 0;
   int i = 0;
   // Call the template function f(long, int) because f(int, int)
   // would require a conversion from long to int.
   f(l, i);
}
```

```Output
void f(T1, T2)
```

## <a name="see-also"></a>Viz také:

[Překlad názvů](../cpp/templates-and-name-resolution.md)<br/>
[typename](../cpp/typename.md)