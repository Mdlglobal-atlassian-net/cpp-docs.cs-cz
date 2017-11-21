---
title: "Chyba nástroje BSCMAKE BK1503 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: BK1503
dev_langs: C++
helpviewer_keywords: BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c75e8513ead68befe2ca4ecd22475dc0a9071431
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="bscmake-error-bk1503"></a>Chyba nástroje BSCMAKE BK1503
Nelze zapisovat do souboru, název souboru' [: Důvod]  
  
 BSCMAKE spojuje soubory .sbr generované během kompilace do jedné databáze prohlížeče. Pokud databázi výsledné prohlížeče překračuje 64 MB, nebo pokud počet vstupních (.sbr) souborů překračuje 4092, bude vygenerované této chybě.  
  
 Pokud problém je způsoben více než 4092 soubory .sbr, je třeba zmenšit počet vstupních souborů. Z Visual Studia, můžete to provést pomocí [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) celý projekt, pak se kontroly na základě soubor po souboru.  
  
 Pokud problém je způsoben souboru BSC větší než 64MB, bude snížit počet soubory .sbr jako vstup snížit velikost výsledný soubor .bsc. Kromě toho může snížit množství informací o procházení prostřednictvím /Em (vyloučit makro rozšířit symboly), /El (vyloučit místní proměnné) a /Es (soubory vyloučit).  
  
## <a name="see-also"></a>Viz také  
 [Možnosti BSCMAKE](../../build/reference/bscmake-options.md)