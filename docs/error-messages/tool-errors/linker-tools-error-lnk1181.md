---
title: "Chyba linkerů Lnk1181 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1181
dev_langs: C++
helpviewer_keywords: LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f5092d4f3ce7b4f96ca4dc5c1554483a7fc3a0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1181"></a>Chyba linkerů LNK1181
Nelze otevřít vstupní soubor 'název souboru.  
  
 Nelze najít linkeru `filename` protože neexistuje nebo nebyla nalezena cesta.  
  
 Některé běžné příčiny chyby LNK1181 zahrnují:  
  
-   `filename`je odkazováno jako další závislost na řádku linkeru, ale soubor neexistuje.  
  
-   A **/Libpath** příkaz, který určuje adresář obsahující `filename` chybí.  
  
 Chcete-li vyřešit uvedené problémy, zajistěte, aby všechny soubory, které odkazuje na řádek linkeru k dispozici v systému.  Také zajistěte **/Libpath** příkaz pro každý adresář se souborem linkeru závislé.  
  
 Pro LNK1181 další možnou příčinou je, že dlouhé názvy souborů s vložených mezer nebyla uzavřena v uvozovkách.  V takovém případě bude linkeru pouze rozpoznat název souboru po první mezeru a pak předpokládají příponu souboru. objektu vývoz.  Tuto situaci lze vyřešit je uzavřete dlouhý název souboru (název cesty a souboru) v uvozovkách.  
  
 Další informace najdete v tématu [soubory .lib jako vstup Linkeru](../../build/reference/dot-lib-files-as-linker-input.md).  
  
## <a name="see-also"></a>Viz také  
 [/ LIBPATH (další proměnná Libpath)](../../build/reference/libpath-additional-libpath.md)