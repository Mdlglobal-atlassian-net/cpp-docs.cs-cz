---
title: -LINKERMEMBER | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /linkermember
dev_langs:
- C++
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac961f985de65bb7eea9a4ad0f5d10b75fbe60d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="linkermember"></a>/LINKERMEMBER
```  
/LINKERMEMBER[:{1|2}]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost zobrazuje veřejné symboly definované v knihovně. Zadejte 1 argument pro zobrazení symbolů v objektu pořadí, spolu s jejich posun. Zadejte 2 argument zobrazíte odsazení a čísla indexů objektů a potom zobrazí seznam symbolů v abecedním pořadí, společně s index objekt pro každou. K získání obou výstupy, zadejte /LINKERMEMBER bez číslo argumentu.  
  
 Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití na soubory vytvořené pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.  
  
## <a name="see-also"></a>Viz také  
 [DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)