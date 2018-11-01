---
title: Bajtové indexy
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
ms.openlocfilehash: 4e19868e5297e1c1615efabde2aee418bc53c51e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448812"
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

## <a name="see-also"></a>Viz také

[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)<br/>
[Poslední znak v řetězci](../text/last-character-in-a-string.md)