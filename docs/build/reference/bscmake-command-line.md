---
title: Příkazový řádek BSCMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
ms.openlocfilehash: b6268eb6d0ea39e72a1d8fd40ab563347c05f0c6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416836"
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

Související informace naleznete v tématu [soubor příkazů BSCMAKE](../../build/reference/bscmake-command-file-response-file.md) a [bscmakee – možnosti](../../build/reference/bscmake-options.md).

## <a name="see-also"></a>Viz také:

[BSCMAKE – referenční dokumentace](../../build/reference/bscmake-reference.md)
