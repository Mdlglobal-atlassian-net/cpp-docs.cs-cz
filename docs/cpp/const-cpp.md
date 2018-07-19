---
title: Const (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- const_cpp
dev_langs:
- C++
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b6fea501724b24c07ab8b2199410a369d62dc9d
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947640"
---
# <a name="const-c"></a>const (C++)
Při úpravách deklarace dat, **const** – klíčové slovo určuje, že objekt nebo proměnnou není možné upravit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
const declaration ;  
member-function const ;  
```  
  
## <a name="const-values"></a>konstantní hodnoty  
 **Const** – klíčové slovo určuje, že hodnota proměnné je konstantní a instruuje kompilátor, aby zabránil programátorovi v úpravách.  
  
```cpp 
// constant_values1.cpp  
int main() {  
   const int i = 5;  
   i = 10;   // C3892  
   i++;   // C2105  
}  
```  
  
 V jazyce C++, můžete použít **const** – klíčové slovo místo [#define](../preprocessor/hash-define-directive-c-cpp.md) direktivy preprocesoru pro definování hodnot konstanty. Hodnoty definované pomocí **const** jsou předmětem kontroly typu a dá se použít místo konstantních výrazů. V jazyce C++ můžete zadat velikost pole **const** proměnné následujícím způsobem:  
  
```cpp 
// constant_values2.cpp  
// compile with: /c  
const int maxarray = 255;  
char store_char[maxarray];  // allowed in C++; not allowed in C  
```  
  
 V jazyce C směřují výchozí hodnoty konstant na externí propojení tak, aby se mohly zobrazit pouze ve zdrojových souborech. V jazyce C++ směřují výchozí hodnoty konstant na vnitřní propojení tak, aby se mohly zobrazit pouze v rámci souborů hlaviček.  
  
 **Const** – klíčové slovo lze také použít v deklaracích ukazatelů.  
  
```cpp 
// constant_values3.cpp  
int main() {  
   char *mybuf = 0, *yourbuf;  
   char *const aptr = mybuf;  
   *aptr = 'a';   // OK  
   aptr = yourbuf;   // C3892  
}  
```  
  
 Ukazatel na proměnnou definovaný jako **const** lze přiřadit pouze k ukazatel, který je také deklarován jako **const**.  
  
```cpp 
// constant_values4.cpp  
#include <stdio.h>  
int main() {  
   const char *mybuf = "test";  
   char *yourbuf = "test2";  
   printf_s("%s\n", mybuf);  
  
   const char *bptr = mybuf;   // Pointer to constant data  
   printf_s("%s\n", bptr);  
  
   // *bptr = 'a';   // Error  
}  
```  
  
 Ukazatele na data konstanty lze použít jako parametry funkce pro zabránění úpravy parametru předaného prostřednictvím ukazatele.  
  
 Pro objekty, které jsou deklarovány jako **const**, lze volat pouze konstantní členské funkce. Tím je zajištěno, že objekt konstanty nebude nikdy změněn.  
  
```cpp 
birthday.getMonth();    // Okay  
birthday.setMonth( 4 ); // Error  
```  
  
 Pro nekonstantní objekt lze volat konstantní nebo nekonstantní členské funkce. Můžete také přetížit pomocí členské funkce **const** – klíčové slovo; to umožňuje funkce, která se pro konstantním a nekonstantním objektům volat jinou verzi.  
  
 Konstruktory a destruktory nelze deklarovat **const** – klíčové slovo.  
  
## <a name="const-member-functions"></a>konstantní členské funkce  
 Deklarování členské funkce s **const** – klíčové slovo určuje, že je funkce, která neprovádí úpravy objektu, pro kterou je volána funkce "jen pro čtení". Konstantní členské funkce nelze měnit jakékoli nestatické datové členy ani volat jakékoli členské funkce, které nejsou konstantní. Pro deklarování konstantní členské funkce, umístěte **const** – klíčové slovo za pravou závorku seznamu argumentů. **Const** – klíčové slovo je požadováno v deklaraci a definici.  
  
```cpp 
// constant_member_function.cpp  
class Date  
{  
public:  
   Date( int mn, int dy, int yr );  
   int getMonth() const;     // A read-only function  
   void setMonth( int mn );   // A write function; can't be const  
private:  
   int month;  
};  
  
int Date::getMonth() const  
{  
   return month;        // Doesn't modify anything  
}  
void Date::setMonth( int mn )  
{  
   month = mn;          // Modifies data member  
}  
int main()  
{  
   Date MyDate( 7, 4, 1998 );  
   const Date BirthDate( 1, 18, 1953 );  
   MyDate.setMonth( 4 );    // Okay  
   BirthDate.getMonth();    // Okay  
   BirthDate.setMonth( 4 ); // C2662 Error  
}  
```  
  
## <a name="c-and-c-const-differences"></a>Rozdíly u konstant v jazycích C a C++  
 Pokud deklarujete proměnnou pro tu **const** v souboru zdrojového kódu jazyka C, takto:  
  
```cpp 
const int i = 2;  
```  
  
 Následně je možné tuto proměnnou použít v jiném modulu takto:  
  
```cpp 
extern const int i;  
```  
  
 Chcete-li získat stejné chování v jazyce C++, je třeba deklarovat, ale vaše **const** proměnné jako:  
  
```cpp 
extern const int i = 2;  
```  
  
 Pokud chcete deklarovat **extern** proměnné v souboru zdrojového kódu jazyka C++ pro použití v jazyce C soubor zdrojového kódu, použijte:  
  
```cpp 
extern "C" const int x=10;  
```  
  
 pro zabránění v úpravě názvu kompilátorem jazyka C++.  
  
## <a name="remarks"></a>Poznámky  
 Když po seznamu parametrů členské funkce, **const** – klíčové slovo určuje, že funkce neprovádí úpravy objektu, pro kterou je vyvolána.  
  
 Další informace o **const**, naleznete v následujících tématech:  
    
-   [Ukazatelé const a volatile](../cpp/const-and-volatile-pointers.md)  
  
-   [Kvalifikátory typu (referenční dokumentace jazyka C)](../c-language/type-qualifiers.md)  
  
-   [volatile](../cpp/volatile-cpp.md)  
  
-   [#define](../preprocessor/hash-define-directive-c-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)