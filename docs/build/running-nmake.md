---
title: Spuštění příkazu NMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29516dcbcf650225ec3b86eee9e135a35bff82f4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379702"
---
# <a name="running-nmake"></a>Spuštění příkazu NMAKE
## <a name="syntax"></a>Syntaxe  
  
```  
NMAKE [option...] [macros...] [targets...] [@commandfile...]  
```  
  
## <a name="remarks"></a>Poznámky  
 Sestavení NMAKE zadat pouze *cíle* nebo, pokud není zadaný žádný první target v soubor pravidel. Může být první cílového souboru pravidel [pseudotarget](../build/pseudotargets.md) vytvoří jiné cíle. Soubory pravidel zadaným /F; používá NMAKE Pokud není zadán /F, používá soubor souboru pravidel v aktuálním adresáři. Pokud není zadaný žádný soubor pravidel, používá odvozená pravidla k sestavení příkazového řádku *cíle*.  
  
 `commandfile` Textového souboru (nebo soubor odpovědí) obsahuje příkazového řádku vstup. Další vstup lze předcházet nebo postupujte podle`commandfile`. Cestu je povolená. V `commandfile`, konce řádků jsou považovány za mezery. Pokud budou obsahovat mezery, uzavřete definice maker v uvozovkách.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
 [NMAKE – možnosti](../build/nmake-options.md)  
  
 [Tools.ini a příkaz NMAKE](../build/tools-ini-and-nmake.md)  
  
 [Kódy ukončení příkazu NMAKE](../build/exit-codes-from-nmake.md)  
  
## <a name="see-also"></a>Viz také  
 [NMAKE – referenční zdroje](../build/nmake-reference.md)