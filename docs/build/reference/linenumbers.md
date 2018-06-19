---
title: -LINENUMBERS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /linenumbers
dev_langs:
- C++
helpviewer_keywords:
- LINENUMBERS dumpbin option
- line numbers
- -LINENUMBERS dumpbin option
- /LINENUMBERS dumpbin option
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9202d7f46dbd3a619e379d076db217544bd4291
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371756"
---
# <a name="linenumbers"></a>/LINENUMBERS
```  
/LINENUMBERS  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost zobrazuje COFF čísla řádků. Čísla řádků existují v souboru objektu, pokud bylo kompilováno s databázi programu (/Zi) kompatibilní s C7 (/ Z7), nebo čísla pouze řádek (/Zd). Spustitelného souboru nebo knihovny DLL obsahuje COFF čísla řádků, pokud bylo propojeno s Generovat ladicí informace (/ DEBUG).  
  
 Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití na soubory vytvořené pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.  
  
## <a name="see-also"></a>Viz také  
 [DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)