---
title: Operátory přístupu členů:. a -&gt;
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
ms.openlocfilehash: 0f370aa04af2e78efd5edfb7836fb71a4c4516a7
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345987"
---
# <a name="member-access-operators--and--gt"></a>Operátory přístupu členů:. a -&gt;

## <a name="syntax"></a>Syntaxe

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>Poznámky

Operátory přístupu členů **.** a **->** slouží k odkazování na členy struktur, sjednocení a tříd. Výrazy členského přístupu mají hodnotu typu vybraného členu.

Existují dva typy výrazů členského přístupu:

1. V prvním *postfix-expression* představuje hodnotu struktury, třídy nebo typu sjednocení a *název* pojmenovává člen zadané struktury, sjednocení nebo třídy. Hodnotu operace má *název* a je l hodnotou, pokud *postfix-expression* l-hodnotou.

1. Druhý typ *postfix-expression* představuje ukazatel na strukturu, sjednocení nebo třídy, a *název* pojmenovává člen zadané struktury, sjednocení nebo třídy. Hodnota je u *název* a je l hodnotou. **->** Operátor provádí dereferenci ukazatele. Proto výrazy `e->member` a `(*e).member` (kde *e* představuje ukazatel) poskytují shodné výsledky (s výjimkou, kdy operátory **->** nebo <strong>\*</strong> jsou přetížené).

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

## <a name="see-also"></a>Viz také:

[Výrazy přípony](../cpp/postfix-expressions.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Třídy a struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Členy struktury a sjednocení](../c-language/structure-and-union-members.md)