---
title: -RAWDATA | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /rawdata
dev_langs: C++
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0a0d9517bae5bdd1eed6cfafda496643aee666d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rawdata"></a>/RAWDATA
```  
/RAWDATA[:{1|2|4|8|NONE[,number]]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost zobrazí obsah nezpracované každého oddílu v souboru. Argumenty kontrolu formátu zobrazení, jak je uvedeno níže:  
  
|Argument|Výsledek|  
|--------------|------------|  
|1|Výchozí nastavení Obsah se zobrazí v hexadecimální bajty a také jako znaků ASCII, pokud mají tištěných reprezentace.|  
|2|Obsah se zobrazí jako hexadecimální hodnoty 2bajtová.|  
|4|Obsah se zobrazí jako hexadecimální hodnoty 4 bajtů.|  
|8|Obsah se zobrazí jako hexadecimální hodnoty 8 bajtů.|  
|NONE|Nezpracovaná data potlačeno. Tento argument je vhodné pro řízení výstup/ALL.|  
|*Číslo*|Zobrazených řádků, které jsou nastavené na šířku, která obsahuje `number` hodnoty na každý řádek.|  
  
 Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití na soubory vytvořené pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti DUMPBIN](../../build/reference/dumpbin-options.md)