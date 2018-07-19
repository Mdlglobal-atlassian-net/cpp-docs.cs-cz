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
ms.openlocfilehash: b50995ff1d5eb730bf6593679194d32d5300b9d7
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947486"
---
# <a name="badcast-exception"></a>bad_cast – výjimka
Výjimka `bad_cast` je vyvolána operátorem `dynamic_cast` jako výsledek neúspěšného přetypování na typ odkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
catch (bad_cast)  
   statement  
```  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní výjimky `bad_cast` je následující:  
  
```cpp 
class bad_cast : public exception {  
public:  
   bad_cast(const char * _Message = "bad cast");  
   bad_cast(const bad_cast &);  
   virtual ~bad_cast();  
};  
```  
  
 Následující kód obsahuje příklad neúspěšného přetypování `dynamic_cast`, které vyvolá výjimku `bad_cast`.  
  
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
  
 Výjimka je vyvolána, protože přetypovaný objekt (Shape) není odvozen ze zadaného typu přetypování (Circle). Aby se zabránilo výjimky, přidejte tyto deklarace k **hlavní**:  
  
```cpp 
Circle circle_instance;  
Circle& ref_circle = circle_instance;  
```  
  
 Poté zaměňte význam přetypování v **zkuste** blokovat následujícím způsobem:  
  
```cpp 
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);  
```  
  
## <a name="see-also"></a>Viz také  
 [dynamic_cast – operátor](../cpp/dynamic-cast-operator.md)   
 [klíčová slova](../cpp/keywords-cpp.md)   
 [Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)