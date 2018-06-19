---
title: -IMPORTS (DUMPBIN) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /imports
dev_langs:
- C++
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af3b9a1bbcf1769e87715e46566dee9c53a96747
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373436"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)
```  
/IMPORTS[:file]  
```  
  
 Tato možnost zobrazí seznam knihovny DLL (obě staticky propojené a [zpoždění načíst](../../build/reference/linker-support-for-delay-loaded-dlls.md)), jsou importovány do spustitelného souboru nebo knihovny DLL a všechny jednotlivé importy z každé z těchto knihoven DLL.  
  
 Volitelné `file` specifikace umožňuje určit, aby se zobrazily importy pro jenom tuto knihovnu DLL. Příklad:  
  
```  
dumpbin /IMPORTS:msvcrt.dll  
```  
  
## <a name="remarks"></a>Poznámky  
 Výstup zobrazuje tato možnost je podobná [/EXPORTUJE](../../build/reference/dash-exports.md) výstup.  
  
 Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití na soubory vytvořené pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.  
  
## <a name="see-also"></a>Viz také  
 [DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)