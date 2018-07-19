---
title: while – příkaz (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- while_cpp
dev_langs:
- C++
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc826b588f133abb93c9942e7907dd8b0fce9574
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947524"
---
# <a name="while-statement-c"></a>while – příkaz (C++)
Spustí *příkaz* opakovaně, dokud není *výraz* vyhodnocen jako nula.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
while ( expression )  
   statement  
```  
  
## <a name="remarks"></a>Poznámky  
 Test *výraz* probíhá před každým provedením smyčky; proto **při** cyklus se opakuje nulakrát nebo vícekrát. *výraz* musí být integrálního typu, typu ukazatele nebo typu třídy s jednoznačným převodem na integrální nebo typ ukazatele.  
  
 A **při** smyčky může také skončit při [přerušení](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), nebo [vrátit](../cpp/return-statement-cpp.md) v rámci příkaz provede se tělo. Použití [pokračovat](../cpp/continue-statement-cpp.md) k ukončení aktuální iterace bez ukončení **při** smyčky. **Pokračovat** předá řízení následující iteraci **při** smyčky.  
  
 Následující kód používá **při** smyčky k odstranění koncových podtržítek z řetězce:  
  
```cpp 
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
 [klíčová slova](../cpp/keywords-cpp.md)   
 [Proveďte-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)   
 [for – příkaz (C++)](../cpp/for-statement-cpp.md)   
 [Příkaz For založený na rozsahu (C++)](../cpp/range-based-for-statement-cpp.md)