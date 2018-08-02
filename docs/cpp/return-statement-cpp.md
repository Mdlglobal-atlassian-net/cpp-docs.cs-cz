---
title: Return – příkaz (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: dda9406909f3508472c11524402c37baa17a76b0
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465786"
---
# <a name="return-statement-c"></a>return – příkaz (C++)
Ukončí provádění funkce a vrátí řízení volající funkci (nebo operačnímu systému, je-li řízení předáváno z funkce `main`). Provádění pokračuje ve volání funkce v okamžiku, ihned po volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
return [expression];  
```  
  
## <a name="remarks"></a>Poznámky  
 Je-li přítomna klauzule `expression`, je převedena na typ zadaný v deklaraci funkce, jako kdyby byla prováděna inicializace. Převod z typu výrazu **vrátit** typ funkce může vytvořit dočasné objekty. Další informace o tom, jak a kdy jsou vytvářeny, naleznete v tématu [dočasné objekty](../cpp/temporary-objects.md).  
  
 Hodnota klauzule `expression` je vrácena volající funkci. Pokud je výraz vynechán, návratová hodnota funkce není definována. Konstruktory a destruktory a funkce typu **void**, nelze zadat výraz v **vrátit** příkazu. Funkce všech ostatních typů musejí zadat výraz v **vrátit** příkazu.  
  
 Pokud tok řízení opustí blok ohraničující definice funkce, výsledek je stejný, jako kdyby byl-li **vrátit** měl byl proveden příkaz bez vykonání výrazu. Toto neplatí u funkcí, které jsou deklarovány jako návratová hodnota.  
  
 Funkce může mít libovolný počet **vrátit** příkazy.  
  
 Následující příklad používá výraz s **vrátit** příkazu získat největší dvou celých čísel.  
  
## <a name="example"></a>Příklad  
  
```cpp 
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
  
## <a name="see-also"></a>Viz také:  
 [Jump – příkazy](../cpp/jump-statements-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)