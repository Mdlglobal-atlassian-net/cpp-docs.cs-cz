---
title: Zápis filtru výjimek
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: 05d3aa79d1293001e80a77b3171b7a4607cd81c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369489"
---
# <a name="writing-an-exception-filter"></a>Zápis filtru výjimek

Výjimku lze zpracovat skokem do úrovně obslužné rutiny výjimky nebo pokračováním provádění. Namísto použití kódu obslužné rutiny výjimky ke zpracování výjimky a propadnutí, můžete použít *filtr* k vyčištění problému a potom vrácením -1, pokračovat normální tok bez vymazání zásobníku.

> [!NOTE]
> Při některých výjimkách nelze pokračovat. Pokud *filtr* vyhodnotí -1 pro takovou výjimku, systém vyvolá novou výjimku. Při volání [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception), můžete určit, zda bude výjimka pokračovat.

Například následující kód používá volání funkce ve výrazu *filtru:* tato funkce zpracovává problém a potom vrátí -1 obnovit normální tok řízení:

```cpp
// exceptions_Writing_an_Exception_Filter.cpp
#include <windows.h>
int main() {
   int Eval_Exception( int );

   __try {}

   __except ( Eval_Exception( GetExceptionCode( ))) {
      ;
   }

}
void ResetVars( int ) {}
int Eval_Exception ( int n_except ) {
   if ( n_except != STATUS_INTEGER_OVERFLOW &&
      n_except != STATUS_FLOAT_OVERFLOW )   // Pass on most exceptions
   return EXCEPTION_CONTINUE_SEARCH;

   // Execute some code to clean up problem
   ResetVars( 0 );   // initializes data to 0
   return EXCEPTION_CONTINUE_EXECUTION;
}
```

Je vhodné použít volání funkce ve výrazu *filtru* vždy, když *filtr* potřebuje provést něco složitého. Vyhodnocení výrazu způsobí spuštění funkce, v tomto případě `Eval_Exception`.

Všimněte si použití [GetExceptionCode](/windows/win32/Debug/getexceptioncode) k určení výjimky. Tuto funkci je nutné volat uvnitř samotného filtru. `Eval_Exception`program `GetExceptionCode`nemůže volat , ale musí mít kód výjimky, který mu byl předán.

Tato obslužná rutina předá řízení jiné obslužné rutině, pokud se jedná o výjimku přetečení celého čísla nebo přetečení čísla s plovoucí desetinnou čárkou. Pokud je tomu tak, obslužná rutina zavolá funkci (funkce `ResetVars` je pouze příklad, nejedná se o funkci rozhraní API) pro obnovení některých globálních proměnných. *Statement-block-2*, který je v tomto příkladu `Eval_Exception` prázdný, nemůže být nikdy proveden, protože nikdy nevrátí EXCEPTION_EXECUTE_HANDLER (1).

Použití volání funkce je dobrá univerzální metoda pro řešení složitých výrazů filtru. Další dvě užitečné funkce jazyka C jsou:

- Podmíněný operátor

- Operátor čárka

Podmíněný operátor je často užitečný, protože slouží ke kontrole určitého návratového kódu a poté vrátí jednu ze dvou různých hodnot. Například filtr v následujícím kódu rozpozná výjimku pouze v případě, že je výjimka STATUS_INTEGER_OVERFLOW:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

Účelem podmíněného operátoru v tomto případě je především ujasnit, že následující kód vytvoří stejné výsledky:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

Podmíněný operátor je užitečnější v situacích, kdy můžete chtít filtr vyhodnotit na -1, EXCEPTION_CONTINUE_EXECUTION.

Operátor čárka umožňuje provádět více nezávislých operací uvnitř jediného výrazu. Efekt je přibližně takový, že se spustí více příkazů a poté se vrátí hodnota posledního výrazu. Například následující kód uloží kód výjimky do proměnné a poté jej ověří:

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>Viz také

[Zápis obslužné rutiny výjimky](../cpp/writing-an-exception-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
