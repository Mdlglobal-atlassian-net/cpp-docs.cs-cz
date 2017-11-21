---
title: "Adresa operátoru: &amp; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&'
dev_langs: C++
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d542c508b84da14d4f628796ae5fd42983db0114
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="address-of-operator-amp"></a>Adresa operátoru:&amp;
## <a name="syntax"></a>Syntaxe  
  
```  
& cast-expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Operátor unární adresy (**&**) přebírá adresu jeho operandu. Operand operátoru adresa může být označení funkce nebo je l hodnota, který určuje objekt, který není pole bit a není deklarovaný s **zaregistrovat** – specifikátor třídy úložiště.  
  
 Operátor adresy lze použít pouze na proměnné s základní, struktura, třídy, nebo union typy, které jsou deklarovány na úrovni oboru souboru, nebo na nich odkazuje na pole. V těchto výrazech můžete přidat do konstantní výraz, který nezahrnuje operátor adresy nebo odečten od výrazu adresy.  
  
 Při použití funkce nebo hodnoty l, výsledkem výrazu je ukazatel typu (r-value) odvozený od typu operandu. Například, pokud je operand typu `char`, výsledkem výrazu je ukazatel typu `char`. Adresa operátor u **const** nebo `volatile` objekty, jehož výsledkem **const** `type`  **\***  nebo `volatile` `type`  **\*** , kde `type` je typ původní objekt.  
  
 Když je použit operátor adresy [kvalifikovaný název](http://msdn.microsoft.com/en-us/3fefb16d-8120-4627-8b3f-3d90fbdcd1df), výsledek bude záviset na tom, zda *kvalifikovaný název* určuje je statický člen. Pokud ano, výsledkem je ukazatel na typ zadaný v deklaraci člena. Pokud není statický člen, výsledkem je ukazatel na člena *název* třídy indikován *kvalifikovaný název třídy*. (Viz [primární výrazy](../cpp/primary-expressions.md) Další informace o *kvalifikovaný název třídy*.) Následující fragment kódu ukazuje, jak výsledek liší v závislosti na tom, zda je statický člen:  
  
```  
// expre_Address_Of_Operator.cpp  
// C2440 expected  
class PTM {  
public:  
           int   iValue;  
    static float fValue;  
};  
  
int main() {  
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static  
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static  
   float *spfValue     = &PTM::fValue;  // OK  
}  
```  
  
 V tomto příkladu výraz `&PTM::fValue` vypočítá typ `float *` místo typu `float PTM::*` protože `fValue` je statický člen.  
  
 Adresa přetížených funkce můžete provést jenom v případě, že je zřejmé, která verze funkce je odkazováno. V tématu [přetížení funkcí](function-overloading.md) informace o tom, jak získat adresu na konkrétní přetížení funkce.  
  
 Použití address-of – operátor typu odkazu dává stejný výsledek v podobě použití operátor na objekt, ke kterému je vázán odkaz. Příklad:  
  
## <a name="example"></a>Příklad  
  
```  
// expre_Address_Of_Operator2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main() {  
   double d;        // Define an object of type double.  
   double& rd = d;  // Define a reference to the object.  
  
   // Obtain and compare their addresses  
   if( &d == &rd )  
      cout << "&d equals &rd" << endl;  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
&d equals &rd  
```  
  
 Následující příklad používá operátor adresy předat argument ukazatel na funkci:  
  
```  
// expre_Address_Of_Operator3.cpp  
// compile with: /EHsc  
// Demonstrate address-of operator &  
  
#include <iostream>  
using namespace std;  
  
// Function argument is pointer to type int  
int square( int *n ) {  
   return (*n) * (*n);  
}  
  
int main() {  
   int mynum = 5;  
   cout << square( &mynum ) << endl;   // pass address of int  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
25  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Deklarátor odkazu lvalue: &](../cpp/lvalue-reference-declarator-amp.md)   
 [Deferenční operátory a operátory adresy](../c-language/indirection-and-address-of-operators.md)
