---
title: bad_cast – výjimka
ms.date: 10/04/2019
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: 11b42c9e6210c2432563bba43c55517abd4265fe
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245957"
---
# <a name="bad_cast-exception"></a>bad_cast – výjimka

Výjimka **bad_cast** je vyvolána operátorem **dynamic_cast** jako výsledek neúspěšného přetypování na odkazový typ.

## <a name="syntax"></a>Syntaxe

```
catch (bad_cast)
   statement
```

## <a name="remarks"></a>Poznámky

Rozhraní pro **bad_cast** :

```cpp
class bad_cast : public exception
```

Následující kód obsahuje příklad neúspěšného **dynamic_cast** , který vyvolá výjimku **bad_cast** .

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo>
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

Výjimka je vyvolána, protože objekt, který je přetypování (tvar), není odvozen od zadaného typu přetypování (Circle). Chcete-li se této výjimce vyhnout, přidejte do funkce `main` následující deklarace:

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

Pak převratte smysl přetypování do bloku **Try** následujícím způsobem:

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[bad_cast](#bad_cast)|Konstruktor pro objekty typu `bad_cast`.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[Co](#what)|Bude určeno později|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Operátor přiřazení, který přiřadí jeden objekt `bad_cast` k druhému.|

## <a name="bad_cast"></a>bad_cast

Konstruktor pro objekty typu `bad_cast`.

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="op_eq"></a>operátor =

Operátor přiřazení, který přiřadí jeden objekt `bad_cast` k druhému.

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a>Co

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>Viz také:

[operátor dynamic_cast](../cpp/dynamic-cast-operator.md)\
\ [klíčových slov](../cpp/keywords-cpp.md)
[Moderní C++ osvědčené postupy pro výjimky a zpracování chyb](../cpp/errors-and-exception-handling-modern-cpp.md)
