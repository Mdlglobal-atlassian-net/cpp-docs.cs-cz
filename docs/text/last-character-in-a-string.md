---
title: Poslední znak v řetězci | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e207ec1d5489a629b765d398e26ac7c07771d0da
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384985"
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

## <a name="see-also"></a>Viz také

[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)<br/>
[Přiřazení znaků](../text/character-assignment.md)