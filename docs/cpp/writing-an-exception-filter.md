---
title: Zápis filtru výjimek
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: 2bc159247604877fb22ff6084e1fda36946561a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209374"
---
# <a name="writing-an-exception-filter"></a>Zápis filtru výjimek

Výjimku lze zpracovat skokem do úrovně obslužné rutiny výjimky nebo pokračováním provádění. Namísto použití kódu obslužné rutiny výjimky pro zpracování výjimky a předání, můžete použít *filtr* problém odstranit, a potom tak, že vrací hodnotu -1, pokračovat v normálním toku bez vymazání zásobníku.

> [!NOTE]
>  Při některých výjimkách nelze pokračovat. Pokud *filtr* vyhodnotí na hodnotu -1 pro takovou výjimku, systém vyvolá novou výjimku. Při volání [RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552), zjistíte, zda výjimka bude pokračovat.

Například následující kód používá volání funkce v *filtr* výraz: Tato funkce zpracuje problém a poté vrátí hodnotu -1 bude pokračovat normální tok řízení:

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

Je vhodné použít ve volání funkce *filtr* výraz pokaždé, když *filtr* je potřeba provést cokoli složitého. Vyhodnocení výrazu způsobí spuštění funkce, v tomto případě `Eval_Exception`.

Všimněte si použití [GetExceptionCode](/windows/desktop/Debug/getexceptioncode) k určení výjimky. Tuto funkci je nutné volat uvnitř samotného filtru. `Eval_Exception` nejde volat metodu `GetExceptionCode`, ale musí jí předat kód výjimky.

Tato obslužná rutina předá řízení jiné obslužné rutině, pokud se jedná o výjimku přetečení celého čísla nebo přetečení čísla s plovoucí desetinnou čárkou. Pokud je tomu tak, obslužná rutina zavolá funkci (funkce `ResetVars` je pouze příklad, nejedná se o funkci rozhraní API) pro obnovení některých globálních proměnných. *Příkaz blok-2*, což je v tomto příkladu je prázdný, může nikdy provést, protože `Eval_Exception` nikdy nevrátí EXCEPTION_EXECUTE_HANDLER (1).

Použití volání funkce je dobrá univerzální metoda pro řešení složitých výrazů filtru. Další dvě užitečné funkce jazyka C jsou:

- Podmíněný operátor

- Operátor čárka

Podmíněný operátor je často užitečný, protože slouží ke kontrole určitého návratového kódu a poté vrátí jednu ze dvou různých hodnot. Například filtr v následujícím kódu rozpozná výjimku pouze v případě, že výjimka je STATUS_INTEGER_OVERFLOW:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

Účelem podmíněného operátoru v tomto případě je především ujasnit, že následující kód vytvoří stejné výsledky:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

Podmíněný operátor je užitečnější v situacích, kdy chcete filtr vyhodnocen na hodnotu -1, EXCEPTION_CONTINUE_EXECUTION.

Operátor čárka umožňuje provádět více nezávislých operací uvnitř jediného výrazu. Efekt je přibližně takový, že se spustí více příkazů a poté se vrátí hodnota posledního výrazu. Například následující kód uloží kód výjimky do proměnné a poté jej ověří:

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>Viz také:

[Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)