---
title: "Kompilátoru (úroveň 1) upozornění C4930 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4930
dev_langs: C++
helpviewer_keywords: C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 457124730ea38f1e91f7dab0c709568f23cf6fc2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4930"></a>C4930 kompilátoru upozornění (úroveň 1)
'prototypu': deklaraci není volaná funkce (byl definici proměnné určené?)  
  
 Kompilátor zjištěna prototypu nepoužívané funkce. Prototyp bylo určeno jako deklarace proměnné, odeberte závorkách otevřít nebo zavřít.  
  
 Následující ukázka generuje C4930:  
  
```  
// C4930.cpp  
// compile with: /W1  
class Lock {  
public:  
   int i;  
};  
  
void f() {  
   Lock theLock();   // C4930  
   // try the following line instead  
   // Lock theLock;  
}  
  
int main() {  
}  
```  
  
 C4930 může dojít také při kompilátor nerozlišuje mezi deklaraci funkce prototyp a volání funkce.  
  
 Následující ukázka generuje C4930:  
  
```  
// C4930b.cpp  
// compile with: /EHsc /W1  
  
class BooleanException  
{  
   bool _result;  
  
public:  
   BooleanException(bool result)  
      : _result(result)  
   {  
   }  
  
   bool GetResult() const  
   {  
      return _result;  
   }  
};  
  
template<class T = BooleanException>  
class IfFailedThrow  
{  
public:  
   IfFailedThrow(bool result)  
   {  
      if (!result)  
      {  
         throw T(result);  
      }  
   }  
};  
  
class MyClass  
{  
public:  
   bool MyFunc()  
   {  
      try  
      {  
         IfFailedThrow<>(MyMethod()); // C4930  
  
         // try one of the following lines instead  
         // IfFailedThrow<> ift(MyMethod());  
         // IfFailedThrow<>(this->MyMethod());  
         // IfFailedThrow<>((*this).MyMethod());  
  
         return true;  
      }  
      catch (BooleanException e)  
      {  
         return e.GetResult();  
      }  
   }  
  
private:  
   bool MyMethod()  
   {  
      return true;  
   }  
};  
  
int main()  
{  
   MyClass myClass;  
   myClass.MyFunc();  
}  
```  
  
 V ukázce výše výsledek metody, které nepřijímá žádné argumenty předaného jako argument konstruktoru proměnná nepojmenované místní třídy. Volání může být od sebe jednoznačně rozlišeny pojmenování místní proměnné nebo prefixu volání metody s instanci objektu spolu s příslušnou operátor ukazatele na člena.