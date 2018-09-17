---
title: BscMake – příkazový řádek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bda0457eecdf6ef7c846d7c12e24078faa4d0da5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720041"
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

## <a name="see-also"></a>Viz také

[BSCMAKE – referenční dokumentace](../../build/reference/bscmake-reference.md)