---
title: Funkce se seznamy argumentů proměnných (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], variable number of
- variable argument lists
- declarators, functions
- argument lists [C++], variable number of
- declaring functions [C++], variables
- function calls, variable number of arguments
ms.assetid: 27c2f83a-21dd-44c6-913c-2834cb944703
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e66ee17f8aa82e46011a78e34baa79b3dea3cdb1
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947496"
---
# <a name="functions-with-variable-argument-lists--c"></a>Funkce se proměnné seznamem argumentů (C++)
Deklarace funkcí, ve kterých posledního člena je tlačítko se třemi tečkami (...) může trvat proměnný počet argumentů. V těchto případech poskytuje jazyk C++ kontrolu typu pouze pro explicitně deklarované argumenty. Seznamy argumentů proměnných lze použít, pokud je zapotřebí provést funkci tak obecnou, že i počet a typ argumentů se může lišit. Řada funkcí je příkladem funkcí, které používají seznamy argumentů proměnných. `printf` *argument-declaration-list*  
  
## <a name="functions-with-variable-arguments"></a>Funkce s proměnnými argumenty  
 Chcete-li přístup k argumentům po těch deklarován, použít makra obsažená ve standardním vloženém souboru \<stdarg.h > jak je popsáno níže.  
  
 **Specifické pro Microsoft**  
  
 Microsoft C++ umožňuje zadat tři tečky jako argument, jsou-li tři tečky posledním argumentem a předchází-li jim čárka. Proto je deklarace `int Func( int i, ... );` platná, ale `int Func( int i ... );` platná není.  
  
 **Specifické pro END Microsoft**  
  
 Deklarace funkce, která přijímá proměnný počet argumentů, vyžaduje alespoň jeden zástupný argument, i když není použit. Není-li tento zástupný symbol zadán, neexistuje žádný způsob, jak získat přístup ke zbývajícím argumentům.  
  
 Pokud argumenty typu **char** jsou předány jako argumenty proměnných, jsou převedeny na typ **int**. Podobně když argumenty typu **float** jsou předány jako argumenty proměnných, jsou převedeny na typ **double**. Argumenty jiných typů představují objekt běžného povýšení integrálních typů a typů s plovoucí desetinnou čárkou. Zobrazit [standardní převody](standard-conversions.md) Další informace.  
  
 Funkce vyžadující seznamy proměnných jsou deklarovány pomocí tří teček (...) v seznamu argumentů. Použijte typy a makra, které jsou popsány v \<stdarg.h > soubor pro přístup k argumentům předaným seznamem proměnných. Další informace o těchto makrech naleznete v tématu [va_arg va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). v dokumentaci pro knihovny C Run-Time.  
  
 Následující příklad ukazuje, jak makra fungují společně s typem (deklarované v \<stdarg.h >): 
  
```cpp 
// variable_argument_lists.cpp  
#include <stdio.h>  
#include <stdarg.h>  
  
//  Declaration, but not definition, of ShowVar.  
void ShowVar( char *szTypes, ... );  
int main() {  
   ShowVar( "fcsi", 32.4f, 'a', "Test string", 4 );  
}  
  
//  ShowVar takes a format string of the form  
//   "ifcs", where each character specifies the  
//   type of the argument in that position.  
//  
//  i = int  
//  f = float  
//  c = char  
//  s = string (char *)  
//  
//  Following the format specification is a variable   
//  list of arguments. Each argument corresponds to   
//  a format character in the format string to which   
// the szTypes parameter points   
void ShowVar( char *szTypes, ... ) {  
   va_list vl;  
   int i;  
  
   //  szTypes is the last argument specified; you must access   
   //  all others using the variable-argument macros.  
   va_start( vl, szTypes );  
  
   // Step through the list.  
   for( i = 0; szTypes[i] != '\0'; ++i ) {  
      union Printable_t {  
         int     i;  
         float   f;  
         char    c;  
         char   *s;  
      } Printable;  
  
      switch( szTypes[i] ) {   // Type to expect.  
         case 'i':  
            Printable.i = va_arg( vl, int );  
            printf_s( "%i\n", Printable.i );  
         break;  
  
         case 'f':  
             Printable.f = va_arg( vl, double );  
             printf_s( "%f\n", Printable.f );  
         break;  
  
         case 'c':  
             Printable.c = va_arg( vl, char );  
             printf_s( "%c\n", Printable.c );  
         break;  
  
         case 's':  
             Printable.s = va_arg( vl, char * );  
             printf_s( "%s\n", Printable.s );  
         break;  
  
         default:  
         break;  
      }  
   }  
   va_end( vl );  
}  
//Output:   
// 32.400002  
// a  
// Test string  
```  
  
 Předchozí příklad znázorňuje tyto důležité koncepty:  
  
1.  Před přístupem k jakémukoli argumentu proměnné je zapotřebí vytvořit značku seznamu jako proměnnou typu `va_list`. V předchozím příkladu je tato značka nazvána `vl`.  
  
2.  Jednotlivé argumenty jsou přístupné pomocí makra `va_arg`. Makru `va_arg` je zapotřebí sdělit typ argumentu, který má být načten, aby mohlo ze zásobníku přenést správný počet bajtů. Zadáte-li nesprávný typ velikosti odlišný od typu v makru `va_arg` dodaného volajícím programem, jsou výsledky nepředvídatelné.  
  
3.  Výsledek získaný pomocí makra `va_arg` by měl být explicitně přetypován na požadovaný typ.  
  
 Je nutné volat – makro k ukončení zpracování argumentů proměnných.`va_end`