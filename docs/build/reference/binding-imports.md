---
title: Import vazeb | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cd9bee6423c0eea98941331dcff86c002dd4ef9d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="binding-imports"></a>Import vazeb
Výchozí chování linkeru je vytvoření tabulku vazbu importních adres pro knihovny DLL načtené se zpožděním. Pokud je vázána knihovnu DLL, pomocné funkce se pokusí použít vázané informace namísto volání **GetProcAddress** na každém z odkazovaného importy. Pokud časové razítko nebo upřednostňovanou adresu neodpovídají definicím načtené knihovny DLL, pomocné funkce převezme tabulky adres vázané import je zastaralá a bude pokračovat, protože pokud neexistuje.  
  
 Pokud chcete nikdy vazby importy s odloženým načtením knihovnu DLL, zadání [/delay](../../build/reference/delay-delay-load-import-settings.md): nobind na příkazový řádek linkeru zabráníte tabulku vázané importních adres vygenerovaný a využívání místa v souboru bitové kopie.  
  
## <a name="see-also"></a>Viz také  
 [Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)