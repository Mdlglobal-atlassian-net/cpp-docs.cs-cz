---
title: "Vrátí Statement (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d5ec29b7348d858b502f292efd797020a17bfa0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="return-statement-c"></a>return – příkaz (C)
`return` Příkaz ukončí provádění funkce a vrátí ovládací prvek volání funkce. Provádění pokračuje ve volání funkce okamžiku hned po volání. A `return` příkaz můžete také vrátit hodnotu volání funkce. V tématu [návratového typu](../c-language/return-type.md) Další informace.  
  
## <a name="syntax"></a>Syntaxe  
 *příkaz přechod*:  
 **Vrátí***výraz* opt**;**   
  
 Hodnota *výraz*, pokud existuje, je vrácen do volání funkce. Pokud *výraz* je tento parametr vynechán, návratovou hodnotu funkce není definován. Výraz, pokud existuje, je vyhodnocena a pak převést na typ vrácený funkcí. Pokud funkce byla deklarována s návratovým typem `void`, `return` příkazu, který obsahuje výraz generuje upozornění a výraz, nebude hodnocen.  
  
 Pokud žádné `return` příkazu se zobrazí v definici funkce řízení automaticky vrátí k funkci volání po provedení posledního prohlášení o volaná funkce. V takovém případě návratová hodnota volaná funkce není definován. Pokud návratovou hodnotu není potřeba, deklarovat funkci tak, aby měl `void` návratový typ; jinak, výchozí návratový typ je `int`.  
  
 Závorky lze použít mnoho programátorů na uzavřete *výraz* argument `return` příkaz. C nevyžaduje závorkách.  
  
 Tento příklad ukazuje `return` příkaz:  
  
```  
#include <limits.h>  
#include <stdio.h>  
  
void draw( int i, long long ll );  
long long sq( int s );  
  
int main()  
{  
    long long y;  
    int x = INT_MAX;  
  
    y = sq( x );  
    draw( x, y );  
    return x;  
}  
  
long long sq( int s )  
{  
    // Note that parentheses around the return expression   
    // are allowed but not required here.  
    return( s * (long long)s );  
}  
  
void draw( int i, long long ll )  
{  
    printf( "i = %d, ll = %lld\n", i, ll );  
    return;  
}  
  
```  
  
 V tomto příkladu `main` funkce volá dvě funkce: `sq` a `draw`. `sq` Funkce vrátí hodnotu `x * x` k `main`, kde je přiřazen návratovou hodnotu `y`. Závorky návratový výrazu v `sq` , jsou vyhodnoceny jako součást výrazu a nejsou požadována příkaz return. Vzhledem k tomu, že je návratový výraz vyhodnocen předtím, než je převést na typ návratové `sq` vynutí typ výrazu, který má být návratový typ s přetypování, aby zabránil přetečení možné celé číslo, které může vést k neočekávaným výsledkům. `draw` Funkce je deklarován jako `void` funkce. Vytiskne hodnoty jeho parametrů a poté prázdný příkaz return končí funkce a nevrací hodnotu. Pokus o přiřazení návratová hodnota `draw` by způsobilo diagnostické zprávy, která se vydává. `main` Funkce vrátí hodnotu `x` v operačním systému.  
  
 Výstup tohoto příkladu vypadá takto:  
  
```Output  
i = 2147483647, ll = 4611686014132420609  
```  
  
## <a name="see-also"></a>Viz také  
 [Příkazy](../c-language/statements-c.md)