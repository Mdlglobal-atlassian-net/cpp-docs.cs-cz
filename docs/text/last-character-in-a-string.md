---
title: Poslední znak v řetězci
ms.date: 11/04/2016
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
ms.openlocfilehash: 4c99628cd12738fabb877a94cfd04a4033ee45aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410668"
---
# <a name="last-character-in-a-string"></a>Poslední znak v řetězci

Použijte následující tipy:

- Znak ASCII v mnoha případech překrývat s rozsahy posledního bajtu. Prohledávání můžete bezpečně použít pro žádné řídicí znaky (menší než 32).

- Vezměte v úvahu následující řádek kódu, který může kontrolovat, jestli poslední znak v řetězci je znak zpětné lomítko:

    ```cpp
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?
        // . . .
    ```

   Protože `strlen` znakové sady MBCS neví, vrátí počet bajtů, ne počet znaků v vícebajtový řetězec. Všimněte si také, že v některých znakové stránky (například 932) "\\" (0x5c) je platný bajt (`sz` je řetězec jazyka C).

   Jedním z možných řešení je pro přepsání kódu tímto způsobem:

    ```cpp
    char *pLast;
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )
        // . . .
    ```

   Tento kód používá funkce znakové sady MBCS `_mbsrchr` a `_mbsinc`. Protože tyto funkce jsou s ohledem na znakové sady MBCS, lze rozlišit mezi "\\"znak a druhý bajt"\\". Kód provede určitou akci, pokud poslední znak v řetězci je s hodnotou null ('\0').

## <a name="see-also"></a>Viz také:

[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)<br/>
[Přiřazení znaků](../text/character-assignment.md)
