---
title: 'Operátor převodu explicitního typu: () | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- explicit data type conversion operator
- conversions [C++], explicit
- operators [C++], explicit type conversion
- data type conversion [C++], explicit
- type conversion [C++], explicit conversions
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93cbd58b3259821292254d8395f5d2435ecaa365
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="explicit-type-conversion-operator-"></a>Operátor převodu explicitního typu: ()
Jazyk C++ umožňuje explicitní převod typu pomocí syntaxe podobné syntaxi volání funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
simple-type-name ( expression-list )  
```  
  
## <a name="remarks"></a>Poznámky  
 A *jednoduchý název typu* následuje *seznam výrazů* uzavřený v závorkách konstrukce objekt zadaného typu pomocí zadaných výrazů. Následující příklad ukazuje explicitní převod typu na typ int:  
  
```  
int i = int( d );  
```  
  
 Následující příklad ukazuje `Point` třídy.  
  
## <a name="example"></a>Příklad  
  
```  
// expre_Explicit_Type_Conversion_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Point  
{  
public:  
    // Define default constructor.  
    Point() { _x = _y = 0; }  
    // Define another constructor.  
    Point( int X, int Y ) { _x = X; _y = Y; }  
  
    // Define "accessor" functions as  
    // reference types.  
    unsigned& x() { return _x; }  
    unsigned& y() { return _y; }  
    void Show()   { cout << "x = " << _x << ", "  
                         << "y = " << _y << "\n"; }  
private:  
    unsigned _x;  
    unsigned _y;  
};  
  
int main()  
{  
    Point Point1, Point2;  
  
    // Assign Point1 the explicit conversion  
    //  of ( 10, 10 ).  
    Point1 = Point( 10, 10 );  
  
    // Use x() as an l-value by assigning an explicit  
    //  conversion of 20 to type unsigned.  
    Point1.x() = unsigned( 20 );  
    Point1.Show();  
  
    // Assign Point2 the default Point object.  
    Point2 = Point();  
    Point2.Show();  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
x = 20, y = 10  
x = 0, y = 0  
```  
  
 Ačkoli předchozí příklad ukazuje explicitní převod typu s použitím konstant, stejný postup funguje při provádění těchto převodů s objekty. Následující fragment kódu to demonstruje:  
  
```  
int i = 7;  
float d;  
  
d = float( i );  
```  
  
 Explicitní převody typu lze zadat také pomocí syntaxe „přetypování“. Předchozí příklad přepsaný pomocí syntaxe přetypování je:  
  
```  
d = (float)i;  
```  
  
 Při převodu z jedné hodnoty vrací převody pomocí přetypování a převody stylu funkce stejné výsledky. Avšak u syntaxe stylu funkce lze zadat více než jeden argument převodu. Tento rozdíl je důležitý pro uživatelské typy. Vezměte v úvahu třídu `Point` a její převody:  
  
```  
struct Point  
{  
    Point( short x, short y ) { _x = x; _y = y; }  
    ...  
    short _x, _y;  
};  
...  
Point pt = Point( 3, 10 );  
```  
  
 V předchozím příkladu, který používá funkce stylu převodu, ukazuje, jak převést dvou hodnot (jednu pro *x* a jeden pro *y*) pro uživatelem definovaný typ `Point`.  
  
> [!CAUTION]
>  Explicitní převody typu používejte opatrně, protože přepisují vestavěnou kontrolu typů kompilátoru jazyka C++.  
  
 [Přetypování](../cpp/cast-operator-parens.md) zápis se musí použít pro převody na typy, které nemají *jednoduchý název typu* (ukazatel nebo odkaz typy, například). Převod na typy, které může být vyjádřený s *jednoduchý název typu* může být napsán v jakémkoli tvaru. V tématu [specifikátory typu](http://msdn.microsoft.com/en-us/34b6c737-0ef1-4470-9b77-b26e46c0bbd4) Další informace o co se považuje za *jednoduchý název typu*.  
  
 Definice typu v rámci přetypování je neplatná.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy přípony](../cpp/postfix-expressions.md)   
 [Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)