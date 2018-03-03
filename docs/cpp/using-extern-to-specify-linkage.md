---
title: "Používání příkazu extern pro specifikaci propojení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- extern
dev_langs:
- C++
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db93feb8c8fad13cf8de082858e68b89f93b5323
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-extern-to-specify-linkage"></a>Používání příkazu extern pro specifikaci propojení
## <a name="syntax"></a>Syntaxe  
  
```  
  
      extern string-literal { declaration-list }  
extern string-literal declaration  
```  
  
## <a name="remarks"></a>Poznámky  
 Klíčové slovo `extern` deklaruje proměnnou nebo funkci, pro které určuje, že mají vnější propojení (jejich název je viditelný i v jiných souborech než těch, ve kterých jsou definovány). Při úpravě proměnné klíčové slovo `extern` určuje, že má proměnná statický průběh (její paměť je přidělena na začátku a uvolněna na konci programu). Proměnnou nebo funkci lze definovat v jiném zdrojovém souboru nebo později ve stejném souboru. Deklarace proměnných a funkcí v oboru souboru jsou v rámci výchozího nastavení externí.  
  
## <a name="example"></a>Příklad  
  
```  
// specifying_linkage1.cpp  
int i = 1;  
void other();  
  
int main() {  
   // Reference to i, defined above:  
   extern int i;  
}  
  
void other() {  
   // Address of global i assigned to pointer variable:  
   static int *external_i = &i;  
  
   // i will be redefined; global i no longer visible:  
   // int i = 16;  
}  
```  
  
 V jazyce C++ při použití s řetězcem určuje klíčové slovo `extern` skutečnost, že jsou pro deklarátory použity propojovací konvence jiného jazyka. Funkce a data jazyka C mohou být zpřístupněny pouze v případě, že byly dříve deklarovány s propojením jazyka C. Musí však být definovány v odděleně kompilované jednotce překladu.  
  
 Microsoft C++ podporuje řetězce **"C"** a **"C++"** v *řetězcový literál* pole. Všechny standardní vložené soubory používají syntaxi `extern` „C“ a umožňují tak použití funkcí knihoven modulu runtime v programech jazyka C++.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje alternativní způsoby deklarace názvů, které mají propojení jazyka C:  
  
```  
// specifying_linkage2.cpp  
// compile with: /c  
// Declare printf with C linkage.  
extern "C" int printf( const char *fmt, ... );  
  
//  Cause everything in the specified header files  
//   to have C linkage.  
extern "C" {  
   // add your #include statements here  
   #include <stdio.h>  
}  
  
//  Declare the two functions ShowChar and GetChar  
//   with C linkage.  
extern "C" {  
   char ShowChar( char ch );  
   char GetChar( void );  
}  
  
//  Define the two functions ShowChar and GetChar  
//   with C linkage.  
extern "C" char ShowChar( char ch ) {  
   putchar( ch );  
   return ch;  
}  
  
extern "C" char GetChar( void ) {  
   char ch;  
  
   ch = getchar();  
   return ch;  
}  
  
// Declare a global variable, errno, with C linkage.  
extern "C" int errno;  
```  
  
 Pokud funkce obsahuje více specifikací propojení, musejí tato propojení souhlasit. U deklarace funkcí, které mají propojení jazyka C i C++, se jedná o chybu. Pokud se navíc v jednom programu vyskytují dvě deklarace funkce – jedna se specifikací propojení a jedna bez ní – musí být deklarace se specifikací propojení jako první. Jakékoli nadbytečné deklarace funkcí, které již specifikaci propojení obsahují, obdrží propojení zadané v první deklaraci. Příklad:  
  
```  
extern "C" int CFunc1();  
...  
int CFunc1();            // Redeclaration is benign; C linkage is  
                         //  retained.  
  
int CFunc2();  
...  
extern "C" int CFunc2(); // Error: not the first declaration of  
                         //  CFunc2;  cannot contain linkage  
                         //  specifier.  
```  
  
 Funkce a objekty explicitně deklarován jako **statické** v textu specifikátor složené propojení (**{}**) jsou považovány za statické funkce nebo objekty; specifikátor propojení se ignoruje. Ostatní funkce a objekty se chovají, jako kdyby byly deklarovány pomocí klíčového slova `extern`. (Viz [používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md) podrobnosti o `extern` – klíčové slovo.)  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [extern – specifikátor třídy úložiště](../c-language/extern-storage-class-specifier.md)   
 [Chování identifikátorů](../c-language/behavior-of-identifiers.md)   
 [Propojení](../c-language/linkage.md)