---
title: "Operátory přístup členy:. a -&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4dc08bce80d27493a8a13ac24bce7011282d7cd3
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="member-access-operators--and--gt"></a>Operátory přístup členy:. a -&gt;
## <a name="syntax"></a>Syntaxe  
  
```  
postfix-expression . name  
postfix-expression -> name  
```  
  
## <a name="remarks"></a>Poznámky  
 Operátory pro přístup ke člen **.** a  **->**  slouží k odkazování na členů struktury, sjednocení a tříd. Výrazy členského přístupu mají hodnotu typu vybraného členu.  
  
 Existují dva typy výrazů členského přístupu:  
  
1.  Ve formuláři první *operátory výraz* reprezentuje hodnotu struktura, třídy nebo typu union a *název* názvy členem zadané struktury, sjednocení nebo třídy. Hodnota operace je u *název* a pokud je hodnotou l *operátory výraz* je l hodnota.  
  
2.  Ve formuláři druhý *operátory výraz* představuje ukazatel struktury, sjednocení nebo třída, a *název* názvy členem zadané struktury, sjednocení nebo třídy. Hodnota je u *název* a je l hodnota.  **->**  Operátor dereferences ukazatele. Proto výrazy * e * **->**  `member` a **(\****e***)**.`member` (kde *e* představuje ukazatel) poskytují stejné výsledky (s výjimkou při operátory  **->**  nebo  **\***  jsou přetížené).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje obě formy operátoru pro přístup k členu.  
  
```  
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
 [Výrazy přípony](../cpp/postfix-expressions.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Třídy a struktury](../cpp/classes-and-structs-cpp.md)   
 [Členy struktury a sjednocení](../c-language/structure-and-union-members.md)