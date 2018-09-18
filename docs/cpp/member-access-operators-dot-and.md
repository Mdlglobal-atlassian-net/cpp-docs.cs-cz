---
title: Operátory přístupu členů:. a -&gt; | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- .
- ->
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c02183b3dc03c785ef5a6a08da80dd8435288b0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112769"
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