---
title: Bajtové indexy
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
ms.openlocfilehash: 5305a977c23d7a978a89c84809cc6fab8c5731eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410717"
---
# <a name="byte-indices"></a>Bajtové indexy

Použijte následující tipy:

- Práce s byjtově orientovaným index do řetězce přináší problémy, které jsou podobné těm, manipulaci s ukazatelem. Vezměte v úvahu tento příklad, který vyhledá v řetězci zpětné lomítko:

    ```cpp
    while ( rgch[ i ] != '\\' )
        i++;
    ```

   To může být index bajt, není vedoucí bajt, a proto nemusí přejděte `character`.

- Použití [_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) funkce předchozí problém vyřešit:

    ```cpp
    while ( rgch[ i ] != '\\' )
        i += _mbclen ( rgch + i );
    ```

   To správně indexuje vedoucí bajt, proto k `character`. `_mbclen` Funkce určuje velikost znaku (1 nebo 2 bajtů).

## <a name="see-also"></a>Viz také:

[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)<br/>
[Poslední znak v řetězci](../text/last-character-in-a-string.md)
