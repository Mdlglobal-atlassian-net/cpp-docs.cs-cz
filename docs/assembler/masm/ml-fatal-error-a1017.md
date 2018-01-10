---
title: "Závažná chyba nástroje ML A1017 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1017
dev_langs: C++
helpviewer_keywords: A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0603ccb1de5767294afcfc012c1b9c8b18ac776d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ml-fatal-error-a1017"></a>Závažná chyba nástroje ML A1017
**Chybí název zdrojového souboru**  
  
 ML nelze vyhledat soubor sestavte nebo předat linkeru.  
  
 Tato chyba se vygeneruje, když poskytují možnosti příkazového řádku ML bez zadání filename k provedení akce. Chcete-li uspořádat soubory, které nemají .asm rozšíření, použijte **/Ta** možnost příkazového řádku.  
  
 Tato chyba může být také generována vyvolání ML bez parametrů, pokud ML – proměnná prostředí obsahuje možnosti příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)