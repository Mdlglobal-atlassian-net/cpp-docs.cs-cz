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
ms.workload: cplusplus
ms.openlocfilehash: 86f2b6d282857409cdb1e1d49e04775e9886cde4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-error-bk1503"></a>Chyba nástroje BSCMAKE BK1503
Nelze zapisovat do souboru, název souboru' [: Důvod]  
  
 BSCMAKE spojuje soubory .sbr generované během kompilace do jedné databáze prohlížeče. Pokud databázi výsledné prohlížeče překračuje 64 MB, nebo pokud počet vstupních (.sbr) souborů překračuje 4092, bude vygenerované této chybě.  
  
 Pokud problém je způsoben více než 4092 soubory .sbr, je třeba zmenšit počet vstupních souborů. Z Visual Studia, můžete to provést pomocí [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) celý projekt, pak se kontroly na základě soubor po souboru.  
  
 Pokud problém je způsoben souboru BSC větší než 64MB, bude snížit počet soubory .sbr jako vstup snížit velikost výsledný soubor .bsc. Kromě toho může snížit množství informací o procházení prostřednictvím /Em (vyloučit makro rozšířit symboly), /El (vyloučit místní proměnné) a /Es (soubory vyloučit).  
  
## <a name="see-also"></a>Viz také  
 [BSCMAKEE – možnosti](../../build/reference/bscmake-options.md)