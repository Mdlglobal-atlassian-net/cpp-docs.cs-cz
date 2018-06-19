---
title: Chyba nástroje BSCMAKE BK1503 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1503
dev_langs:
- C++
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06d4a05a8f2d04c3f8a991d4444b35295408a7b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294791"
---
# <a name="bscmake-error-bk1503"></a>Chyba nástroje BSCMAKE BK1503
Nelze zapisovat do souboru, název souboru' [: Důvod]  
  
 BSCMAKE spojuje soubory .sbr generované během kompilace do jedné databáze prohlížeče. Pokud databázi výsledné prohlížeče překračuje 64 MB, nebo pokud počet vstupních (.sbr) souborů překračuje 4092, bude vygenerované této chybě.  
  
 Pokud problém je způsoben více než 4092 soubory .sbr, je třeba zmenšit počet vstupních souborů. Z Visual Studia, můžete to provést pomocí [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) celý projekt, pak se kontroly na základě soubor po souboru.  
  
 Pokud problém je způsoben souboru BSC větší než 64MB, bude snížit počet soubory .sbr jako vstup snížit velikost výsledný soubor .bsc. Kromě toho může snížit množství informací o procházení prostřednictvím /Em (vyloučit makro rozšířit symboly), /El (vyloučit místní proměnné) a /Es (soubory vyloučit).  
  
## <a name="see-also"></a>Viz také  
 [BSCMAKEE – možnosti](../../build/reference/bscmake-options.md)