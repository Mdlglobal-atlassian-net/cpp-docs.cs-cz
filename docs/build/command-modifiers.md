---
title: Příkaz modifikátory | Dokumentace Microsoftu
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
ms.openlocfilehash: c9e1d883e0c7a2b214842b096fdf697ffc7d0192
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221738"
---
# <a name="command-modifiers"></a>Modifikátory příkazů
Můžete určit jeden nebo více modifikátory příkazů před příkaz, volitelně oddělené mezerami či tabulátory. Stejně jako u příkazů, musí být modifikátory odsazena.  
  
|Modifikátor|Účel|  
|--------------|-------------|  
|@*Příkaz*|Zakazuje zobrazení příkazu. Zobrazení příkazů není potlačena. Ve výchozím nastavení vypisuje NMAKE všechny provedené příkazy. Pomocí /S potlačit zobrazení pro celý soubor pravidel; použít **. TICHÉ** potlačit zobrazení části souboru pravidel.|  
|**-**\[*číslo*] *příkaz*|Chyba při kontrole vypne *příkaz*. Ve výchozím nastavení NMAKE zastaví, když se příkaz vrátí nenulový ukončovací kód. IF –*číslo* se používá, NMAKE zastaví, pokud překročí ukončovací kód *číslo*. Mezery ani tabulátory se nemůže objevit mezi čárka a *číslo.* Nejméně jedna mezera nebo tabulátor musí být uvedena mezi `number` a *příkaz*. Chcete-li vypnout kontrolu chyb pro celý soubor pravidel; použijte /I použít **. Ignorovat** Chcete-li vypnout kontrolu chyb pro části souboru pravidel.|  
|**\!** *Příkaz*|Spustí *příkaz* pro každý soubor závislé Pokud *příkaz* používá <strong>$ \* \*</strong> (všechny závislé soubory v závislosti) nebo **$?** (všechny závislé soubory v závislostí s časovým razítkem vyšší než cílová).|  
  
## <a name="see-also"></a>Viz také  
 [Příkazy v souboru pravidel](../build/commands-in-a-makefile.md)