---
title: Diagnostika vytištěná podle funkce assert
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: 666ba22d642b772fe8ad336f57ab1bdd82bd2e18
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150997"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostika vytištěná podle funkce assert

**ANSI 4.2** diagnostické zprávy vytištěné funkcí a její chování **vyhodnocení** – funkce

**Vyhodnocení** funkce vytiskne diagnostickou zprávu a zavolá **přerušit** rutině, pokud je výraz nepravdivý (0). Diagnostická zpráva má tvar

> **Chyba kontrolního výrazu**: <em>výraz</em>**, soubor** <em>filename</em>**, řádek** *číslo řádku*

kde *filename* je název zdrojového souboru a *linenumber* je číslo řádku výrazu, který se ve zdrojovém souboru se nezdařilo. Pokud nebyla provedena žádná akce *výraz* hodnotu true (nenulovou).

## <a name="see-also"></a>Viz také:

[Funkce knihovny](../c-language/library-functions.md)
