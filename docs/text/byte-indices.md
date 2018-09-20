---
title: Bajtové indexy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11f7f78e87ddd40fd3cf85fc294e8fadac5dbe45
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423790"
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