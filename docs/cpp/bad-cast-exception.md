---
title: bad_cast – výjimka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bad_cast
- bad_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bd5bb63e075303856d444cb08c2c1f3abe990b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083935"
---
# <a name="badcast-exception"></a>bad_cast – výjimka

**Bad_cast –** výjimku **dynamic_cast** operátor jako výsledek neúspěšného přetypování na typ odkazu.

## <a name="syntax"></a>Syntaxe

```
catch (bad_cast)
   statement
```

## <a name="remarks"></a>Poznámky

Rozhraní pro **bad_cast –** je:

```cpp
class bad_cast : public exception {
public:
   bad_cast(const char * _Message = "bad cast");
   bad_cast(const bad_cast &);
   virtual ~bad_cast();
};
```

Následující kód obsahuje příklad neúspěšného **dynamic_cast** , které vyvolá **bad_cast –** výjimky.

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo.h>
#include <iostream>

class Shape {
public:
   virtual void virtualfunc() const {}
};

class Circle: public Shape {
public:
   virtual void virtualfunc() const {}
};

using namespace std;
int main() {
   Shape shape_instance;
   Shape& ref_shape = shape_instance;
   try {
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);
   }
   catch (bad_cast b) {
      cout << "Caught: " << b.what();
   }
}
```

Výjimka je vyvolána, protože přetypovaný objekt (Shape) není odvozen ze zadaného typu přetypování (Circle). Chcete-li se této výjimce vyhnout, přidejte do funkce `main` následující deklarace:

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

Poté zaměňte význam přetypování v **zkuste** blokovat následujícím způsobem:

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="see-also"></a>Viz také:

[dynamic_cast – operátor](../cpp/dynamic-cast-operator.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)