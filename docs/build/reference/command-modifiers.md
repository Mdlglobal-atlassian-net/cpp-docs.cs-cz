---
title: Modifikátory příkazů
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
ms.openlocfilehash: 6131b94a6ee78026b8d5337061a6238df785b64d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822961"
---
# <a name="command-modifiers"></a>Modifikátory příkazů

Můžete určit jeden nebo více modifikátory příkazů před příkaz, volitelně oddělené mezerami či tabulátory. Stejně jako u příkazů, musí být modifikátory odsazena.

|Modifikátor|Účel|
|--------------|-------------|
|\@*Příkaz*|Zakazuje zobrazení příkazu. Zobrazení příkazů není potlačena. Ve výchozím nastavení vypisuje NMAKE všechny provedené příkazy. Pomocí /S potlačit zobrazení pro celý soubor pravidel; použít **. TICHÉ** potlačit zobrazení části souboru pravidel.|
|**-**\[*číslo*] *příkaz*|Chyba při kontrole vypne *příkaz*. Ve výchozím nastavení NMAKE zastaví, když se příkaz vrátí nenulový ukončovací kód. IF –*číslo* se používá, NMAKE zastaví, pokud překročí ukončovací kód *číslo*. Mezery ani tabulátory se nemůže objevit mezi čárka a *číslo.* Nejméně jedna mezera nebo tabulátor musí být uvedena mezi `number` a *příkaz*. Chcete-li vypnout kontrolu chyb pro celý soubor pravidel; použijte /I použít **. Ignorovat** Chcete-li vypnout kontrolu chyb pro části souboru pravidel.|
|**\!** *Příkaz*|Spustí *příkaz* pro každý soubor závislé Pokud *příkaz* používá <strong>$ \* \*</strong> (všechny závislé soubory v závislosti) nebo **$?** (všechny závislé soubory v závislostí s časovým razítkem vyšší než cílová).|

## <a name="see-also"></a>Viz také:

[Příkazy v souboru pravidel](commands-in-a-makefile.md)
