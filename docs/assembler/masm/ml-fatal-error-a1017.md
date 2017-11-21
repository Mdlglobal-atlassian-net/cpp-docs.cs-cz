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
ms.openlocfilehash: ec10e14920572bd8001cf07676c4659bc08a4acc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ml-fatal-error-a1017"></a>Závažná chyba nástroje ML A1017
**Chybí název zdrojového souboru**  
  
 ML nelze vyhledat soubor sestavte nebo předat linkeru.  
  
 Tato chyba se vygeneruje, když poskytují možnosti příkazového řádku ML bez zadání filename k provedení akce. Chcete-li uspořádat soubory, které nemají .asm rozšíření, použijte **/Ta** možnost příkazového řádku.  
  
 Tato chyba může být také generována vyvolání ML bez parametrů, pokud ML – proměnná prostředí obsahuje možnosti příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy nástroje ML](../../assembler/masm/ml-error-messages.md)