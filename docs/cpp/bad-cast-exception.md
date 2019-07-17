---
title: bad_cast – výjimka
ms.date: 11/04/2016
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: b40f64671e7c259b7dc04b31a11d20d0fc76c5c4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68242393"
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
class bad_cast : public exception
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

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[bad_cast –](#bad_cast)|Konstruktor pro objekty typu `bad_cast`.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[Co](#what)|Bude určeno později|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Operátor přiřazení, který se přiřadí jednu `bad_cast` objektu na jiný.|

## <a name="bad_cast"></a> bad_cast –

Konstruktor pro objekty typu `bad_cast`.

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="op_eq"></a> operátor =

Operátor přiřazení, který se přiřadí jednu `bad_cast` objektu na jiný.

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a> Co

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>Viz také:

[dynamic_cast – operátor](../cpp/dynamic-cast-operator.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)