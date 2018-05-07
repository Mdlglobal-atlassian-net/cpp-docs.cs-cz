---
title: Chyba linkerů Lnk1181 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1181
dev_langs:
- C++
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 617678e5453acdafaf72875857b0e0f9b84a110a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1181"></a>Chyba linkerů LNK1181
Nelze otevřít vstupní soubor 'název souboru.  
  
 Nelze najít linkeru `filename` protože neexistuje nebo nebyla nalezena cesta.  
  
 Některé běžné příčiny chyby LNK1181 zahrnují:  
  
-   `filename` je odkazováno jako další závislost na řádku linkeru, ale soubor neexistuje.  
  
-   A **/Libpath** příkaz, který určuje adresář obsahující `filename` chybí.  
  
 Chcete-li vyřešit uvedené problémy, zajistěte, aby všechny soubory, které odkazuje na řádek linkeru k dispozici v systému.  Také zajistěte **/Libpath** příkaz pro každý adresář se souborem linkeru závislé.  
  
 Pro LNK1181 další možnou příčinou je, že dlouhé názvy souborů s vložených mezer nebyla uzavřena v uvozovkách.  V takovém případě bude linkeru pouze rozpoznat název souboru po první mezeru a pak předpokládají příponu souboru. objektu vývoz.  Tuto situaci lze vyřešit je uzavřete dlouhý název souboru (název cesty a souboru) v uvozovkách.  
  
 Další informace najdete v tématu [soubory .lib jako vstup Linkeru](../../build/reference/dot-lib-files-as-linker-input.md).  
  
## <a name="see-also"></a>Viz také  
 [/LIBPATH (další proměnná Libpath)](../../build/reference/libpath-additional-libpath.md)