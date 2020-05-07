---
title: Diagnostika vytištěná podle funkce assert
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: 666ba22d642b772fe8ad336f57ab1bdd82bd2e18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234220"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostika vytištěná podle funkce assert

**ANSI 4,2** Diagnostika vytiskla nástrojem a chování při ukončení funkce **Assert**

Funkce **Assert** vytiskne diagnostickou zprávu a zavolá rutinu **Abort** , pokud má výraz hodnotu false (0). Diagnostická zpráva má tvar

> **Chyba kontrolního výrazu**: <em>výraz</em>**,** <em>název</em>souboru **, řádek** *číslo řádku*

kde *filename* je název zdrojového souboru a *číslo řádku* je číslo řádku kontrolního výrazu, který selhal ve zdrojovém souboru. Pokud je *výraz* true (nenulový), není provedena žádná akce.

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)
