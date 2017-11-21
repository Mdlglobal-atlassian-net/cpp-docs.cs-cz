---
title: "Přetížení operátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- operator_cpp
- operator
dev_langs: C++
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3844dc5b53defcb02f1dab1a97f05760d05d531f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="operator-overloading"></a>Přetížení operátoru
`operator` – Klíčové slovo deklaruje funkci zadání co `operator-symbol` znamená při použití instance třídy. To dává operátor více než jeden význam, nebo "přetížení" jej. Kompilátor rozlišuje mezi různé významy operátoru prověřením typy operandů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
type operator operator-symbol ( parameter-list )  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete změnit definici funkce nejvíce integrovaných operátory globálně nebo na základě třídy třídy. Přetížené operátory jsou implementovány jako funkce.  
  
 Název přetížené operátor je `operator x`, kde `x` je operátor, jak se objevuje v následující tabulce. Například k přetížení operátor sčítání, definujete funkci s názvem `operator+`. Stejně tak, aby přetížení operátoru přidání/přiřazení `+=`, definovat funkci s názvem `operator+=`.  
  
### <a name="redefinable-operators"></a>Které lze znovu definovat operátory  
  
|Operátor|Název|Typ|  
|--------------|----------|----------|  
|`,`|Čárka|binární|  
|`!`|Logická NEGACE|Unární|  
|`!=`|Nerovnost|binární|  
|`%`|Modulus|binární|  
|`%=`|Přiřazení modulus|binární|  
|`&`|Bitový operátor AND|binární|  
|`&`|Adresa|Unární|  
|`&&`|Logický operátor AND|binární|  
|`&=`|Přiřazení bitového operátoru AND|binární|  
|`( )`|Volání funkce|—|  
|`( )`|Operátor přetypování|Unární|  
|`*`|Násobení|binární|  
|`*`|Zrušení ukazatele|Unární|  
|`*=`|Přiřazení násobení|binární|  
|`+`|Sčítání|binární|  
|`+`|Unární Plus|Unární|  
|`++`|Přírůstek <sup>1</sup>|Unární|  
|`+=`|Přiřazení sčítání|binární|  
|`-`|Odčítání|binární|  
|`-`|Unární negace|Unární|  
|`--`|Snížení <sup>1</sup>|Unární|  
|`-=`|Přiřazení odčítání|binární|  
|`->`|Výběr členů|binární|  
|`->*`|Výběr ukazatele na člena|binární|  
|`/`|Dělení|binární|  
|`/=`|Přiřazení dělení|binární|  
|`<`|Menší než|binární|  
|`<<`|Posun doleva|binární|  
|`<<=`|Přiřazení posunutí doleva|binární|  
|`<=`|Menší nebo rovno|binární|  
|`=`|Přiřazení|binární|  
|`==`|Rovnost|binární|  
|`>`|Větší než|binární|  
|`>=`|Větší nebo rovno|binární|  
|`>>`|Posun doprava|binární|  
|`>>=`|Přiřazení posunutí doprava|binární|  
|`[ ]`|Dolní index pole|—|  
|`^`|Exkluzivní OR|binární|  
|`^=`|Exkluzivní OR přiřazení|binární|  
|`&#124;`|Bitový inkluzivní operátor OR|binární|  
|`&#124;=`|Přiřazení s bitovým operátorem OR|binární|  
|`&#124;&#124;`|Logický operátor OR|binární|  
|`~`|Doplněk|Unární|  
|`delete`|`Delete`|—|  
|`new`|`New`|—|  
|`conversion operators`|operátory převodu|Unární|  
  
 1 dvě verze unární zvýšit a snížení existovat: preincrement a postincrement.  
  
 V tématu [obecná pravidla přetížení operátoru](../cpp/general-rules-for-operator-overloading.md) Další informace. Omezení u různých kategorií přetížené operátory jsou popsány v následujících tématech:  
  
-   [Unární operátory](../cpp/overloading-unary-operators.md)  
  
-   [Binární operátory](../cpp/binary-operators.md)  
  
-   [Přiřazení](../cpp/assignment.md)  
  
-   [Volání funkce](../cpp/function-call-cpp.md)  
  
-   [Subscripting](../cpp/subscripting.md)  
  
-   [Přístup ke členu – třída](../cpp/member-access.md)  
  
-   [Přírůstek a snížení](../cpp/increment-and-decrement-operator-overloading-cpp.md).  
  
-   [Převody uživatelsky definovaný typ.](../cpp/user-defined-type-conversions-cpp.md)  
  
 Operátory uvedené v následující tabulce nemohou být přetíženy. V tabulce jsou zahrnuty preprocesoru symboly `#` a `##`.  
  
### <a name="nonredefinable-operators"></a>Nonredefinable operátory  
  
|||  
|-|-|  
|`Operator`|`Name`|  
|`.`|Výběr členů|  
|`.*`|Výběr ukazatele na člena|  
|`::`|Rozlišení rozsahu|  
|`? :`|Podmiňovací operátor|  
|`#`|Preprocesor – převést na řetězec|  
|`##`|Preprocesor řetězení|  
  
 I když přetížené operátory se obvykle implicitně nazývají kompilátorem vyskytne v kódu, se může vyvolat explicitně stejným způsobem jako člen nebo je volána funkce nečlenský:  
  
```  
Point pt;  
pt.operator+( 3 );  // Call addition operator to add 3 to pt.  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad přetížení `+` operátor přidat dva komplexní čísla a vrátí výsledek.  
  
```  
// operator_overloading.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct Complex {  
   Complex( double r, double i ) : re(r), im(i) {}  
   Complex operator+( Complex &other );  
   void Display( ) {   cout << re << ", " << im << endl; }  
private:  
   double re, im;  
};  
  
// Operator overloaded using a member function  
Complex Complex::operator+( Complex &other ) {  
   return Complex( re + other.re, im + other.im );  
}  
  
int main() {  
   Complex a = Complex( 1.2, 3.4 );  
   Complex b = Complex( 5.6, 7.8 );  
   Complex c = Complex( 0.0, 0.0 );  
  
   c = a + b;  
   c.Display();  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
6.8, 11.2  
```  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
1.  [Obecná pravidla přetížení operátoru](../cpp/general-rules-for-operator-overloading.md)  
  
2.  [Přetížení unárních operátorů](../cpp/overloading-unary-operators.md)  
  
3.  [Binární operátory](../cpp/binary-operators.md)  
  
4.  [Přiřazení](../cpp/assignment.md)  
  
5.  [Volání funkce](../cpp/function-call-cpp.md)  
  
6.  [Subscripting](../cpp/subscripting.md)  
  
7.  [Přístup ke členu](../cpp/member-access.md)  
  
## <a name="see-also"></a>Viz také  
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)