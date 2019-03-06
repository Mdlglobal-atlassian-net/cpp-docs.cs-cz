---
title: Výrazy v předběžném zpracování souboru pravidel
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
ms.openlocfilehash: e55be14b6623232966b1539615c4f7f40139e38f
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421845"
---
# <a name="expressions-in-makefile-preprocessing"></a>Výrazy v předběžném zpracování souboru pravidel

**! Pokud** nebo **! ELSE IF** `constantexpression` se skládá z příkazy, řetězcové konstanty nebo celočíselné konstanty (v desítkové nebo jazyka C zápisu). Závorky lze použijte k skupinové výrazy. Výrazy používají C-style dlouhé celé číslo se znaménkem aritmetické; čísla jsou v podobě 32bitové dvojkového doplňku v rozsahu - 2147483648 do 2147483647.

Výrazy můžete použít operátory, které fungují na konstantní hodnoty, ukončovací kód z příkazů, řetězce, makra a cesty k systému souborů.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

[Operátory předzpracování souboru pravidel](../build/makefile-preprocessing-operators.md)

[Spuštění programu při předběžném zpracování](../build/executing-a-program-in-preprocessing.md)

## <a name="see-also"></a>Viz také:

[Předběžné zpracování souboru pravidel](../build/makefile-preprocessing.md)
