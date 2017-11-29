---
title: "while – příkaz (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: while_cpp
dev_langs: C++
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4b076a1679bec8de9407d253d233e96060aaef4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="while-statement-c"></a>while – příkaz (C++)
Provede *příkaz* opakovaně až *výraz* vyhodnotí na hodnotu nula.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      while ( expression )  
   statement  
```  
  
## <a name="remarks"></a>Poznámky  
 Testovací nástroje *výraz* proběhne před každou provádění smyčky; proto `while` smyčky spustí vícekrát nebo. *výraz* musí mít celočíselný typ, ukazatel typu nebo typu třídy s konverzi jednoznačným na celé číslo nebo ukazatel typu.  
  
 A `while` smyčky můžete také při ukončení [zalomení](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), nebo [vrátit](../cpp/return-statement-cpp.md) v rámci příkaz provede se tělo. Použití [pokračovat](../cpp/continue-statement-cpp.md) ukončit aktuální iterace bez ukončení `while` smyčky. **Pokračovat** předá řízení do další iterace `while` smyčky.  
  
 Následující kód používá smyčku `while` k odstranění koncových podtržítek z řetězce:  
  
```  
// while_statement.cpp  
  
#include <string.h>  
#include <stdio.h>  
char *trim( char *szSource )  
{  
    char *pszEOS = 0;  
  
    //  Set pointer to character before terminating NULL  
    pszEOS = szSource + strlen( szSource ) - 1;  
  
    //  iterate backwards until non '_' is found   
    while( (pszEOS >= szSource) && (*pszEOS == '_') )  
        *pszEOS-- = '\0';  
  
    return szSource;  
}  
int main()  
{  
    char szbuf[] = "12345_____";  
  
    printf_s("\nBefore trim: %s", szbuf);  
    printf_s("\nAfter trim: %s\n", trim(szbuf));  
}  
```  
  
 Ukončovací podmínka je vyhodnocena v horní části smyčky. Pokud nejsou přítomna žádná koncová podtržítka, smyčka se nikdy neprovede.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy iterace](../cpp/iteration-statements-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Proveďte-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)   
 [pro příkaz (C++)](../cpp/for-statement-cpp.md)   
 [Na základě rozsahu pro příkaz (C++)](../cpp/range-based-for-statement-cpp.md)