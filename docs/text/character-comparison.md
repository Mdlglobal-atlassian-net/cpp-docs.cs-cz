---
title: Porovnávání znaků
ms.date: 11/04/2016
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
ms.openlocfilehash: 206910d4b76f93a92ee5230a227d6f0346a85e61
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615407"
---
# <a name="character-comparison"></a>Porovnávání znaků

Použijte následující tipy:

- Porovnání známé vedoucí bajt s znaku ASCII funguje správně:

    ```cpp
    if( *sz1 == 'A' )
    ```

- Porovnání dvou znaků Neznámý vyžaduje použití některého z makra definovaná v Mbstring.h:

    ```cpp
    if( !_mbccmp( sz1, sz2) )
    ```

   Tím se zajistí, že jsou oba bajtů dvoubajtové znakové porovnána shoda.

## <a name="see-also"></a>Viz také

[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)<br/>
[Přetečení vyrovnávací paměti](../text/buffer-overflow.md)