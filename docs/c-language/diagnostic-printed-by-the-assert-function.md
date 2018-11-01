---
title: Diagnostika vytištěná podle funkce assert
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: 330c694b53957cab2e44da7cb8b52031c33fb5a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549042"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostika vytištěná podle funkce assert

**ANSI 4.2** diagnostické zprávy vytištěné funkcí a její chování **vyhodnocení** – funkce

**Vyhodnocení** funkce vytiskne diagnostickou zprávu a zavolá **přerušit** rutině, pokud je výraz nepravdivý (0). Diagnostická zpráva má tvar

> **Chyba kontrolního výrazu**: <em>výraz</em>**, soubor** <em>filename</em>**, řádek** *číslo řádku*

kde *filename* je název zdrojového souboru a *linenumber* je číslo řádku výrazu, který se ve zdrojovém souboru se nezdařilo. Pokud nebyla provedena žádná akce *výraz* hodnotu true (nenulovou).

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)