---
title: "Přírůstek a snížení přetížení operátoru (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 10987b351ebc34b7b17963e17047e32ee0d9bc5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="increment-and-decrement-operator-overloading-c"></a>Přetížení operátoru inkrementace a dekrementace (C++)
Operátory zvýšení a snížení spadají do zvláštní kategorie, protože existují dvě varianty každého z nich:  
  
-   Preinkrement a postinkrement  
  
-   Predekrement a postdekrement  
  
 Při zápisu funkcí přetížených operátorů může být užitečné implementovat samostatné verze pro předponovou a příponovou verzi těchto operátorů. Chcete-li rozlišit mezi těmito dvěma, dodržujte následující pravidlo: Předponový tvar operátoru je deklarován stejným způsobem jako ostatní unární operátory, příponový tvar přijímá další argument typu `int`.  
  
> [!NOTE]
>  Při zadání přetíženého operátoru pro příponový tvar operátoru zvýšení nebo snížení musí být další argument typu `int`. Zadání jiného typu vygeneruje chybu.  
  
 Následující příklad ukazuje, jak definovat předponové a příponové operátory zvýšení a snížení třídy `Point`:  
  
```  
// increment_and_decrement1.cpp  
class Point  
{  
public:  
   // Declare prefix and postfix increment operators.  
   Point& operator++();       // Prefix increment operator.  
   Point operator++(int);     // Postfix increment operator.  
  
   // Declare prefix and postfix decrement operators.  
   Point& operator--();       // Prefix decrement operator.  
   Point operator--(int);     // Postfix decrement operator.  
  
   // Define default constructor.  
   Point() { _x = _y = 0; }  
  
   // Define accessor functions.  
   int x() { return _x; }  
   int y() { return _y; }  
private:  
   int _x, _y;  
};  
  
// Define prefix increment operator.  
Point& Point::operator++()  
{  
   _x++;  
   _y++;  
   return *this;  
}  
  
// Define postfix increment operator.  
Point Point::operator++(int)  
{  
   Point temp = *this;  
   ++*this;  
   return temp;  
}  
  
// Define prefix decrement operator.  
Point& Point::operator--()  
{  
   _x--;  
   _y--;  
   return *this;  
}  
  
// Define postfix decrement operator.  
Point Point::operator--(int)  
{  
   Point temp = *this;  
   --*this;  
   return temp;  
}  
int main()  
{  
}  
```  
  
 Stejné operátory lze definovat v rozsahu souboru (globálně) pomocí následujících záhlaví funkce:  
  
```  
friend Point& operator++( Point& )      // Prefix increment  
friend Point& operator++( Point&, int ) // Postfix increment  
friend Point& operator--( Point& )      // Prefix decrement  
friend Point& operator--( Point&, int ) // Postfix decrement  
```  
  
 Argument typu `int`, který označuje příponový tvar operátoru zvýšení nebo snížení, není pro předávání argumentů běžně používán. Obvykle obsahuje hodnotu 0. Lze jej však použít následujícím způsobem:  
  
```  
// increment_and_decrement2.cpp  
class Int  
{  
public:  
    Int &operator++( int n );  
private:  
    int _i;  
};  
  
Int& Int::operator++( int n )  
{  
    if( n != 0 )    // Handle case where an argument is passed.  
        _i += n;  
    else  
        _i++;       // Handle case where no argument is passed.  
    return *this;  
}  
int main()  
{  
   Int i;  
   i.operator++( 25 ); // Increment by 25.  
}  
```  
  
 Neexistuje žádná syntaxe pro použití operátorů zvýšení nebo snížení pro předání těchto hodnot jinak než explicitním voláním, jak je uvedeno v předchozím kódu. Jednodušším způsobem implementace této funkce je přetížení operátoru sčítání/přiřazení (`+=`).  
  
## <a name="see-also"></a>Viz také  
 [Přetížení operátoru](../cpp/operator-overloading.md)