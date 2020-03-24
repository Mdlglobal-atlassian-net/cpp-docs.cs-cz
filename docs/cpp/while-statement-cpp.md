---
title: while – příkaz (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 0dfbbb2865c9cf0a23b04ce213a0e739e29c27da
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187320"
---
# <a name="while-statement-c"></a>while – příkaz (C++)

Provede *příkaz* opakovaně, dokud není *výraz* vyhodnocen jako nula.

## <a name="syntax"></a>Syntaxe

```
while ( expression )
   statement
```

## <a name="remarks"></a>Poznámky

Test *výrazu* probíhá před každým spuštěním smyčky; Proto se smyčka **while** spouští nula nebo vícekrát. *výraz* musí být integrálního typu, typu ukazatele nebo typu třídy s jednoznačným převodem na integrální typ nebo typ ukazatele.

Smyčka **while** může také skončit při spuštění příkazu [Break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md)nebo [return](../cpp/return-statement-cpp.md) v rámci těla příkazu. Použijte [pokračovat](../cpp/continue-statement-cpp.md) pro ukončení aktuální iterace bez ukončení smyčky **while** . **pokračování** předá řízení k další iteraci cyklu **while** .

Následující kód používá smyčku **while** k oříznutí koncových podtržítek z řetězce:

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

[Příkazy iterace](../cpp/iteration-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[do-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for – příkaz (C++)](../cpp/for-statement-cpp.md)<br/>
[Příkaz For založený na rozsahu (C++)](../cpp/range-based-for-statement-cpp.md)
