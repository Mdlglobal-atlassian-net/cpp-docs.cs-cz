---
title: Výrazy v předběžném zpracování souboru pravidel | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1070eb01802bd4b39f62ae24519ad6dabca7eb90
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719002"
---
# <a name="expressions-in-makefile-preprocessing"></a>Výrazy v předběžném zpracování souboru pravidel

**! Pokud** nebo **! ELSE IF** `constantexpression` se skládá z příkazy, řetězcové konstanty nebo celočíselné konstanty (v desítkové nebo jazyka C zápisu). Závorky lze použijte k skupinové výrazy. Výrazy používají C-style dlouhé celé číslo se znaménkem aritmetické; čísla jsou v podobě 32bitové dvojkového doplňku v rozsahu - 2147483648 do 2147483647.

Výrazy můžete použít operátory, které fungují na konstantní hodnoty, ukončovací kód z příkazů, řetězce, makra a cesty k systému souborů.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

[Operátory předzpracování souboru pravidel](../build/makefile-preprocessing-operators.md)

[Spuštění programu při předběžném zpracování](../build/executing-a-program-in-preprocessing.md)

## <a name="see-also"></a>Viz také

[Předběžné zpracování souboru pravidel](../build/makefile-preprocessing.md)