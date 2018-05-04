---
title: Příkazový řádek BSCMAKE | Microsoft Docs
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
ms.openlocfilehash: 7866d2960acdd89c3015470ef3971307ba162cd3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="bscmake-command-line"></a>Příkazový řádek BSCMAKE
Pokud chcete spustit BSCMAKE, použijte následující syntaxi příkazového řádku:  
  
```  
BSCMAKE [options] sbrfiles  
```  
  
 Možnosti může vyskytovat pouze v `options` pole na příkazovém řádku.  
  
 *Sbrfiles* pole určuje jeden nebo více souborů .sbr vytvořené kompilátoru nebo assembleru. Oddělte názvy souborů .sbr mezerami nebo karty. Je nutné zadat rozšíření; neexistuje žádná výchozí hodnota. Můžete zadat cestu s názvem, a můžete použít zástupné znaky operačního systému (* a?).  
  
 Během přírůstkové sestavení můžete určit nové soubory .sbr, které není součástí původní sestavení. Pokud chcete, aby všechny příspěvky zůstat v soubor s informacemi o procházení, je nutné zadat všechny soubory .sbr (včetně zkrácený soubory), které byly původně použity k vytvoření souboru BSC programem. Pokud vynecháte souboru .sbr, odeberou se tento soubor příspěvku soubor s informacemi o procházení.  
  
 Nezadávejte soubor zkrácený .sbr pro úplné sestavení. Úplné sestavení vyžaduje příspěvky ze všech souborů zadaný .sbr. Před provedením úplné sestavení, znovu zkompiluje projekt a vytvořte nový soubor .sbr pro každý soubor prázdný.  
  
 Tento příkaz spustí BSCMAKE k sestavení do souboru s názvem MAIN.bsc z tři soubory .sbr:  
  
```  
BSCMAKE main.sbr file1.sbr file2.sbr  
```  
  
 Související informace najdete v tématu [soubor příkazů BSCMAKE](../../build/reference/bscmake-command-file-response-file.md) a [možnosti BSCMAKE](../../build/reference/bscmake-options.md).  
  
## <a name="see-also"></a>Viz také  
 [BSCMAKE – referenční dokumentace](../../build/reference/bscmake-reference.md)