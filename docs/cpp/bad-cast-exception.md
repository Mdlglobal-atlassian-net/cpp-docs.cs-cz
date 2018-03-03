---
title: "bad_cast – výjimka | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d7880a01f247d5dc3cce5a6f247297ef65289367
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
  
```  
class bad_cast : public exception {  
public:  
   bad_cast(const char * _Message = "bad cast");  
   bad_cast(const bad_cast &);  
   virtual ~bad_cast();  
};  
```  
  
 Následující kód obsahuje příklad neúspěšného přetypování `dynamic_cast`, které vyvolá výjimku `bad_cast`.  
  
```  
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
  
```  
Circle circle_instance;  
Circle& ref_circle = circle_instance;  
```  
  
 Poté zaměňte význam přetypování v bloku `try` takto:  
  
```  
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);  
```  
  
## <a name="see-also"></a>Viz také  
 [dynamic_cast – operátor](../cpp/dynamic-cast-operator.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)