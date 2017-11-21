---
title: "Zápis filtru výjimek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e33492c0cdab2429f1d8ccfc0ad50247cd457a9a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="writing-an-exception-filter"></a>Zápis filtru výjimek
Výjimku lze zpracovat skokem do úrovně obslužné rutiny výjimky nebo pokračováním provádění. Místo použití kód obslužné rutiny výjimek pro zpracování výjimky a návratem, můžete použít *filtru* vyčištění problém a pak vrácením -1 obnovení normálního toku bez vymazání zásobníku.  
  
> [!NOTE]
>  Při některých výjimkách nelze pokračovat. Pokud *filtru* vyhodnotí na hodnotu -1 takové výjimky, systém vyvolá novou výjimku. Při volání [raiseexception –](http://msdn.microsoft.com/library/windows/desktop/ms680552), zjistíte, zda bude pokračovat v výjimky.  
  
 Například následující kód používá volání funkce v *filtru* výraz: Tato funkce zpracovává problém a pak vrátí hodnotu -1, chcete-li pokračovat v normálním toku řízení:  
  
```  
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
  
 Je vhodné použít ve volání funkce *filtru* výraz vždy, když *filtru* je potřeba udělat nic komplexní. Vyhodnocení výrazu způsobí spuštění funkce, v tomto případě `Eval_Exception`.  
  
 Všimněte si použití [GetExceptionCode –](http://msdn.microsoft.com/library/windows/desktop/ms679356) lze zjistit výjimka. Tuto funkci je nutné volat uvnitř samotného filtru. `Eval_Exception`nelze volat **GetExceptionCode –**, ale musí mít kód výjimky do ní předán.  
  
 Tato obslužná rutina předá řízení jiné obslužné rutině, pokud se jedná o výjimku přetečení celého čísla nebo přetečení čísla s plovoucí desetinnou čárkou. Pokud je tomu tak, obslužná rutina zavolá funkci (funkce `ResetVars` je pouze příklad, nejedná se o funkci rozhraní API) pro obnovení některých globálních proměnných. *Příkaz bloku-2*, v tomto příkladu je prázdný, můžete nikdy nelze provést, protože `Eval_Exception` nikdy vrátí exception_execute_handler – (1).  
  
 Použití volání funkce je dobrá univerzální metoda pro řešení složitých výrazů filtru. Další dvě užitečné funkce jazyka C jsou:  
  
-   Podmíněný operátor  
  
-   Operátor čárka  
  
 Podmíněný operátor je často užitečný, protože slouží ke kontrole určitého návratového kódu a poté vrátí jednu ze dvou různých hodnot. Například filtr v následujícím kódu rozpozná výjimku pouze v případě, že se jedná o výjimku `STATUS_INTEGER_OVERFLOW`:  
  
```  
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {  
```  
  
 Účelem podmíněného operátoru v tomto případě je především ujasnit, že následující kód vytvoří stejné výsledky:  
  
```  
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {  
```  
  
 Podmíněný operátor je více užitečné v situacích, kde můžete vyhodnotit na hodnotu -1, exception_continue_execution – filtru.  
  
 Operátor čárka umožňuje provádět více nezávislých operací uvnitř jediného výrazu. Efekt je přibližně takový, že se spustí více příkazů a poté se vrátí hodnota posledního výrazu. Například následující kód uloží kód výjimky do proměnné a poté jej ověří:  
  
```  
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )  
```  
  
## <a name="see-also"></a>Viz také  
 [Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)   
 [Strukturované zpracování (C/C++) výjimek](../cpp/structured-exception-handling-c-cpp.md)