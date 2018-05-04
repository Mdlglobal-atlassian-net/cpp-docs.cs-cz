---
title: Return – příkaz (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- return_cpp
dev_langs:
- C++
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1252e6833dae0f04e1cb148c5703d04d42cee353
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="return-statement-c"></a>return – příkaz (C++)
Ukončí provádění funkce a vrátí řízení volající funkci (nebo operačnímu systému, je-li řízení předáváno z funkce `main`). Provádění pokračuje ve volání funkce okamžiku hned po volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
return [expression];  
```  
  
## <a name="remarks"></a>Poznámky  
 Je-li přítomna klauzule `expression`, je převedena na typ zadaný v deklaraci funkce, jako kdyby byla prováděna inicializace. Převedení z typu výrazu na typ `return` funkce může vytvořit dočasné objekty. Další informace o tom, jak a kdy se vytvářejí dočasné proměnné najdete v tématu [dočasné objekty](../cpp/temporary-objects.md).  
  
 Hodnota klauzule `expression` je vrácena volající funkci. Pokud je výraz vynechán, návratová hodnota funkce není definována. Konstruktory a destruktory a funkce typu `void`, nelze zadat výraz v `return` příkaz. Funkce všech ostatních typů musejí zadat výraz v příkazu `return`.  
  
 Pokud tok řízení opustí blok ohraničující definice funkce, výsledek je stejný jako u příkazu `return` bez vykonání výrazu. Toto neplatí u funkcí, které jsou deklarovány jako návratová hodnota.  
  
 Funkce může mít libovolný počet příkazů `return`.  
  
 Následující příklad používá výraz s příkazem `return` pro získání dvou největších celých čísel.  
  
## <a name="example"></a>Příklad  
  
```  
// return_statement2.cpp  
#include <stdio.h>  
  
int max ( int a, int b )  
{  
   return ( a > b ? a : b );  
}  
  
int main()  
{  
    int nOne = 5;  
    int nTwo = 7;  
  
    printf_s("\n%d is bigger\n", max( nOne, nTwo ));  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Jump – příkazy](../cpp/jump-statements-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)