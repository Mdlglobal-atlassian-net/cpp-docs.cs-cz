---
title: Operátory přístupu členů:. a-&gt;
ms.date: 11/04/2016
f1_keywords:
- .
- ->
helpviewer_keywords:
- member access, expressions
- operators [C++], member access
- dot operator (.)
- -> operator
- member access, operators
- postfix operators [C++]
- . operator
- member access
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
ms.openlocfilehash: 05bab55e1646783e0f8ab9b414d608c912f60a0f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178012"
---
# <a name="member-access-operators--and--gt"></a>Operátory přístupu členů:. a-&gt;

## <a name="syntax"></a>Syntaxe

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>Poznámky

Operátory přístupu členů **.** a **->** slouží k odkazování na členy struktur, sjednocení a tříd. Výrazy členského přístupu mají hodnotu typu vybraného členu.

Existují dva typy výrazů členského přístupu:

1. V prvním formuláři představuje *příponový výraz* hodnotu struktury, třídy nebo typu sjednocení a *název* pojmenovává člena zadané struktury, sjednocení nebo třídy. Hodnotou operace je *název* a je l-hodnotou, pokud je *příponový výraz* l-hodnotou.

1. Ve druhém formuláři představuje *příponový výraz* ukazatel na strukturu, sjednocení nebo třídu *a názvy pojmenují* člena zadané struktury, sjednocení nebo třídy. Hodnota je *název* a je l-hodnotou. Operátor **->** odkazuje na ukazatel. Proto výrazy `e->member` a `(*e).member` (kde *e* představuje ukazatel) poskytují stejné výsledky (s výjimkou případů, kdy jsou přetíženy operátory **->** nebo <strong>\*</strong> ).

## <a name="example"></a>Příklad

Následující příklad ukazuje obě formy operátoru pro přístup k členu.

```cpp
// expre_Selection_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Date {
   Date(int i, int j, int k) : day(i), month(j), year(k){}
   int month;
   int day;
   int year;
};

int main() {
   Date mydate(1,1,1900);
   mydate.month = 2;
   cout  << mydate.month << "/" << mydate.day
         << "/" << mydate.year << endl;

   Date *mydate2 = new Date(1,1,2000);
   mydate2->month = 2;
   cout  << mydate2->month << "/" << mydate2->day
         << "/" << mydate2->year << endl;
   delete mydate2;
}
```

```Output
2/1/1900
2/1/2000
```

## <a name="see-also"></a>Viz také

[Výrazy přípony](../cpp/postfix-expressions.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Třídy a struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Členy struktury a sjednocení](../c-language/structure-and-union-members.md)
