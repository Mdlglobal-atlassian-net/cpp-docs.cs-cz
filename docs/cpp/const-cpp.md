---
title: Const (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: const_cpp
dev_langs: C++
helpviewer_keywords: const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8290b9c73dbab2c3cc3ab63cfbff10f587e46d7b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="const-c"></a>const (C++)
Při úpravě deklaraci data **const** – klíčové slovo určuje, že objekt nebo proměnné není změn.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      const declaration ;  
member-function const ;  
```  
  
## <a name="const-values"></a>Const hodnoty  
 **Const** – klíčové slovo určuje, že je konstantní hodnota proměnné a určuje kompilátor programátorů bránit v provádění úprav.  
  
```  
// constant_values1.cpp  
int main() {  
   const int i = 5;  
   i = 10;   // C3892  
   i++;   // C2105  
}  
```  
  
 V jazyce C++, můžete použít **const** – klíčové slovo místo [#define](../preprocessor/hash-define-directive-c-cpp.md) direktivy preprocesoru definovat konstantní hodnoty. Hodnoty definované s **const** podléhají kontrola typu a jde použít místo konstantní výrazy. V jazyce C++, můžete zadat velikost pole s **const** proměnná následujícím způsobem:  
  
```  
// constant_values2.cpp  
// compile with: /c  
const int maxarray = 255;  
char store_char[maxarray];  // allowed in C++; not allowed in C  
```  
  
 V jazyce C směřují výchozí hodnoty konstant na externí propojení tak, aby se mohly zobrazit pouze ve zdrojových souborech. V jazyce C++ směřují výchozí hodnoty konstant na vnitřní propojení tak, aby se mohly zobrazit pouze v rámci souborů hlaviček.  
  
 **Const** – klíčové slovo lze také v deklarace ukazatelů.  
  
```  
// constant_values3.cpp  
int main() {  
   char *mybuf = 0, *yourbuf;  
   char *const aptr = mybuf;  
   *aptr = 'a';   // OK  
   aptr = yourbuf;   // C3892  
}  
```  
  
 Ukazatel na proměnná definovaná jako **const** lze přiřadit pouze k ukazatele, který je také deklarován jako **const**.  
  
```  
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
  
 Pro objekty, které jsou deklarovány jako **const**, vám může volat pouze konstantní členské funkce. Tím je zajištěno, že objekt konstanty nebude nikdy změněn.  
  
```  
birthday.getMonth();    // Okay  
birthday.setMonth( 4 ); // Error  
```  
  
 Pro nekonstantní objekt lze volat konstantní nebo nekonstantní členské funkce. Můžete také přetížení funkce člen pomocí **const** – klíčové slovo; to umožňuje jinou verzi funkce, která má být volána pro konstantní a nonconstant objekty.  
  
 Nelze deklarovat konstruktory nebo destruktory s **const** – klíčové slovo.  
  
## <a name="const-member-functions"></a>Const členské funkce  
 Deklarování členské funkce s **const** – klíčové slovo určuje, že funkce je "jen pro čtení" funkci, která neprovádí úpravy objektu, pro kterou je volána. Konstantní členské funkce nelze upravit všechny členy nestatické data nebo volat kteréhokoli člena funkce, které nejsou konstantní. Chcete-li deklarace konstantní členské funkce, zaškrtněte **const** – klíčové slovo po uzavírací kulatá závorka seznamu argumentů. **Const** – klíčové slovo je nutné v deklaraci a definice.  
  
```  
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
 Když je deklarovat proměnnou jako **const** v souboru zdrojového kódu C, uděláte jako:  
  
```  
const int i = 2;  
```  
  
 Následně je možné tuto proměnnou použít v jiném modulu takto:  
  
```  
extern const int i;  
```  
  
 Pokud chcete získat stejné chování v jazyce C++, musíte deklarovat, ale vaše **const** proměnné jako:  
  
```  
extern const int i = 2;  
```  
  
 Chcete-li v souboru zdrojového kódu jazyka C++ deklarovat proměnnou `extern` pro použití v souboru zdrojového kódu jazyka C, je třeba použít:  
  
```  
extern "C" const int x=10;  
```  
  
 pro zabránění v úpravě názvu kompilátorem jazyka C++.  
  
## <a name="remarks"></a>Poznámky  
 Když následující členské funkce seznam parametrů, **const** – klíčové slovo určuje funkce nelze změnit objekt, pro kterou je volána.  
  
 Další informace o **const**, najdete v následujících tématech:  
    
-   [Ukazatelé const a volatile](../cpp/const-and-volatile-pointers.md)  
  
-   [Kvalifikátory typu (referenční dokumentace jazyka C)](../c-language/type-qualifiers.md)  
  
-   [volatile](../cpp/volatile-cpp.md)  
  
-   [#define](../preprocessor/hash-define-directive-c-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)