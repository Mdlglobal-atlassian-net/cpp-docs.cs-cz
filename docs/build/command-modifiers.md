---
title: Příkaz modifikátory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3739c053797bdccd08310e17bf669413ead0db48
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="command-modifiers"></a>Modifikátory příkazů
Můžete určit jeden nebo více modifikátory příkazů předcházející příkaz, volitelně oddělené mezerami nebo karty. Stejně jako u příkazů, musí být odsazeny modifikátory.  
  
|Modifikátor|Účel|  
|--------------|-------------|  
|@*příkaz*|Zabraňuje výstupu příkazu. Zobrazení pomocí příkazů není potlačena. Ve výchozím nastavení vrátí NMAKE všechny spuštění příkazů. Pomocí /S potlačit zobrazení pro celý soubor pravidel; použít **. TICHOU** potlačit zobrazení pro součást souboru pravidel.|  
|**-**[`number` ]*příkaz*|Vypne kontrolu *příkaz*. Ve výchozím nastavení NMAKE zastaví, pokud příkaz vrátí nenulový ukončovací kód. Pokud -`number` se používá, NMAKE zastaví, pokud v něm ukončovací kód překračuje `number`. Mezery nebo karty se nemůže vyskytovat mezi čárka a *číslo.* Minimálně jeden místa nebo kartě musí být mezi `number` a *příkaz*. Chcete-li vypnout kontrolu chyb pro celý soubor pravidel; /I použít použít **. Ignorovat** Chcete-li vypnout kontrolu součástí souboru pravidel.|  
|**!** *příkaz*|Provede *příkaz* pro každý závislý soubor Pokud *příkaz* používá **$ \* \*** (všechny závislé soubory v závislost) nebo **$?** (všechny závislé soubory v závislostí s časovým razítkem novější než cíl).|  
  
## <a name="see-also"></a>Viz také  
 [Příkazy v souboru pravidel](../build/commands-in-a-makefile.md)