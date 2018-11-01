---
title: while – příkaz (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 63a1b4c5433a42edd798926c1b025ab4494b64b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608978"
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

## <a name="see-also"></a>Viz také:

[Příkazy iterace](../cpp/iteration-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[do-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for – příkaz (C++)](../cpp/for-statement-cpp.md)<br/>
[Příkaz For založený na rozsahu (C++)](../cpp/range-based-for-statement-cpp.md)