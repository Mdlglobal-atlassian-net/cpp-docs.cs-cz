---
title: "Závažná chyba nástroje ML A1017 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f77f6d2905d70614735beb6cbcefeeb7e07b491
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ml-fatal-error-a1017"></a>Závažná chyba nástroje ML A1017
**Chybí název zdrojového souboru**  
  
 ML nelze vyhledat soubor sestavte nebo předat linkeru.  
  
 Tato chyba se vygeneruje, když poskytují možnosti příkazového řádku ML bez zadání filename k provedení akce. Chcete-li uspořádat soubory, které nemají .asm rozšíření, použijte **/Ta** možnost příkazového řádku.  
  
 Tato chyba může být také generována vyvolání ML bez parametrů, pokud ML – proměnná prostředí obsahuje možnosti příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)