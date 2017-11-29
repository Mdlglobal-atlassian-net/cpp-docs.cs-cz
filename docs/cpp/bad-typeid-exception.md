---
title: "bad_typeid – výjimka | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bad_typeid
- bad_typeid_cpp
dev_langs: C++
helpviewer_keywords:
- bad_typeid exception
- exceptions [C++], bad_typeid
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8dbf60058a3aea341e5896ed8036096ce78d5f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="badtypeid-exception"></a>bad_typeid – výjimka
`bad_typeid` Výjimku [typeid – operátor](../cpp/typeid-operator.md) při operand pro `typeid` je NULOVÝ ukazatel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      catch (bad_typeid)  
   statement  
```  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní výjimky `bad_typeid` je následující:  
  
```  
class bad_typeid : public exception  
{  
public:  
   bad_typeid(const char * _Message = "bad typeid");  
   bad_typeid(const bad_typeid &);  
   virtual ~bad_typeid();  
};  
```  
  
 Následující příklad ukazuje `typeid` operátor vyvolání `bad_typeid` výjimka.  
  
```  
// expre_bad_typeid.cpp  
// compile with: /EHsc /GR  
#include <typeinfo.h>  
#include <iostream>  
  
class A{  
public:  
   // object for class needs vtable  
   // for RTTI  
   virtual ~A();  
};  
  
using namespace std;  
int main() {  
A* a = NULL;  
  
try {  
   cout << typeid(*a).name() << endl;  // Error condition  
   }  
catch (bad_typeid){  
   cout << "Object is NULL" << endl;  
   }  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
Object is NULL  
```  
  
## <a name="see-also"></a>Viz také  
 [Informace běhového typu](../cpp/run-time-type-information.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)