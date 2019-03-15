---
title: Příkazový řádek BSCMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
ms.openlocfilehash: 7724069a401aadcdb2e3e8487dc85273dac357fc
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818645"
---
# <a name="bscmake-command-line"></a>Příkazový řádek BSCMAKE

Chcete-li spustit nástroje BSCMAKE, použijte následující syntaxi příkazového řádku:

```
BSCMAKE [options] sbrfiles
```

Možnosti může objevit pouze v `options` na příkazovém řádku.

*Sbrfiles* pole určuje jeden nebo více soubory .sbr vytvořené kompilátoru nebo assembleru. Názvy soubory .sbr oddělte mezerami či tabulátory. Je nutné zadat rozšíření; neexistuje žádná výchozí hodnota. Můžete zadat cestu s názvem, a můžete použít zástupné znaky operačního systému (\* a?).

Během přírůstkového sestavení můžete určit nové soubory .sbr, které nejsou součástí původní sestavení. Pokud chcete, aby všechny příspěvky tak si zachováte informačního souboru procházení, je nutné zadat všechny soubory .sbr (včetně souborů zkrácený), které byly původně použili k vytvoření souboru .bsc. Vynecháte-li soubor .sbr, odeberou se tento soubor příspěvek do informačního souboru procházení.

Není zadán soubor .sbr zkrácený pro úplného buildu. Úplné sestavení vyžaduje příspěvků všechny soubory .sbr zadané. Před provedením úplného buildu se znovu zkompilovat projekt a vytvořte nový soubor .sbr pro každý soubor prázdný.

Následující příkaz spustí BSCMAKE k vytvoření souboru s názvem MAIN.bsc z tři soubory .sbr:

```
BSCMAKE main.sbr file1.sbr file2.sbr
```

Související informace naleznete v tématu [soubor příkazů BSCMAKE](bscmake-command-file-response-file.md) a [bscmakee – možnosti](bscmake-options.md).

## <a name="see-also"></a>Viz také:

[BSCMAKE – referenční dokumentace](bscmake-reference.md)
