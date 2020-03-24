---
title: Řešení přetížení volání šablony funkce
ms.date: 11/04/2016
helpviewer_keywords:
- function templates overload resolution
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
ms.openlocfilehash: d96046c629e812e342ce86b850b6d52a57094997
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188438"
---
# <a name="overload-resolution-of-function-template-calls"></a>Řešení přetížení volání šablony funkce

Šablona funkce může přetížit nešablonové funkce se stejným názvem. V tomto scénáři jsou volání funkcí řešeny nejprve pomocí odvození argumentu šablony pro vytvoření instance šablony funkce s jedinečnou specializací. Pokud je odvození argumentu šablony neúspěšné, další přetížení funkce se považují za řešení tohoto volání. Tato další přetížení, označovaná také jako kandidátská sada, zahrnují nešablonové funkce a jiné instance šablon funkcí. Pokud je vyrovnávání argumentu šablony úspěšné, pak je vygenerovaná funkce porovnána s ostatními funkcemi pro určení nejlepší shody, podle pravidel pro řešení přetížení. Další informace naleznete v tématu [přetížení funkce](function-overloading.md).

## <a name="example"></a>Příklad

Pokud je nešablonová funkce stejně vhodná pro funkci šablony, je zvolena nešablonovaná funkce (pokud nejsou explicitně zadány argumenty šablony), jako v následujícím příkladu volání `f(1, 1)`.

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

Následující příklad ilustruje, že je upřednostňována přesně vyhovující funkce šablony, pokud funkce nevyžadující šablonu vyžaduje převod.

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

## <a name="see-also"></a>Viz také

[Překlad názvů](../cpp/templates-and-name-resolution.md)<br/>
[typename](../cpp/typename.md)
