---
title: Funkce se seznamy argumentů proměnných (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], variable number of
- variable argument lists
- declarators, functions
- argument lists [C++], variable number of
- declaring functions [C++], variables
- function calls, variable number of arguments
ms.assetid: 27c2f83a-21dd-44c6-913c-2834cb944703
ms.openlocfilehash: f456f31dec631f7d9340563a93dfafeea49a72b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178441"
---
# <a name="functions-with-variable-argument-lists--c"></a>Funkce se seznamy argumentů proměnných (C++)

Deklarace funkce, ve kterých poslední člen je tři tečky (...), může mít proměnlivý počet argumentů. V těchto případech poskytuje jazyk C++ kontrolu typu pouze pro explicitně deklarované argumenty. Seznamy argumentů proměnných lze použít, pokud je zapotřebí provést funkci tak obecnou, že i počet a typ argumentů se může lišit. Rodina funkcí je příkladem funkcí, které používají seznamy argumentů proměnných.`printf` *– deklarace – seznam*

## <a name="functions-with-variable-arguments"></a>Funkce s proměnnými argumenty

Chcete-li získat přístup k argumentům po deklaraci, použijte makra obsažená v souboru include Standard \<STDARG. h >, jak je popsáno níže.

**Specifické pro společnost Microsoft**

Microsoft C++ umožňuje zadat tři tečky jako argument, jsou-li tři tečky posledním argumentem a předchází-li jim čárka. Proto je deklarace `int Func( int i, ... );` platná, ale `int Func( int i ... );` platná není.

**Specifické pro konec Microsoftu**

Deklarace funkce, která přijímá proměnný počet argumentů, vyžaduje alespoň jeden zástupný argument, i když není použit. Není-li tento zástupný symbol zadán, neexistuje žádný způsob, jak získat přístup ke zbývajícím argumentům.

V případě, že argumenty typu **char** jsou předány jako argumenty proměnných, jsou převedeny na typ **int**. Podobně, pokud jsou argumenty typu **float** předány jako argumenty proměnných, jsou převedeny na typ **Double**. Argumenty jiných typů představují objekt běžného povýšení integrálních typů a typů s plovoucí desetinnou čárkou. Další informace najdete v tématu [standardní převody](standard-conversions.md) .

Funkce, které vyžadují seznamy proměnných jsou deklarovány pomocí tří teček (...) v seznamu argumentů. Použijte typy a makra, které jsou popsány v \<STDARG. h > vložených souborů pro přístup k argumentům, které jsou předány seznamem proměnných. Další informace o těchto makrech naleznete v tématu [va_arg, va_copy, va_end va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). v dokumentaci knihovny run-time jazyka C.

Následující příklad ukazuje, jak makra fungují společně s typem (deklarovaným v \<STDARG. h >):

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

1. Před přístupem k jakémukoli argumentu proměnné je zapotřebí vytvořit značku seznamu jako proměnnou typu `va_list`. V předchozím příkladu je tato značka nazvána `vl`.

1. Jednotlivé argumenty jsou přístupné pomocí makra `va_arg`. Makru `va_arg` je zapotřebí sdělit typ argumentu, který má být načten, aby mohlo ze zásobníku přenést správný počet bajtů. Zadáte-li nesprávný typ velikosti odlišný od typu v makru `va_arg` dodaného volajícím programem, jsou výsledky nepředvídatelné.

1. Výsledek získaný pomocí makra `va_arg` by měl být explicitně přetypován na požadovaný typ.

Chcete-li ukončit zpracování variabilních argumentů, je nutné zavolat makro.`va_end`
