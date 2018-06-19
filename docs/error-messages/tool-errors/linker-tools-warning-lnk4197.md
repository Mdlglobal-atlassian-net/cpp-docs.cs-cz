---
title: Upozornění linkerů Lnk4197 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4197
dev_langs:
- C++
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfef7f0fe2d9cd50fa6a18ad682c3e4d80df99c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300828"
---
# <a name="linker-tools-warning-lnk4197"></a>Upozornění linkerů LNK4197
Export exportname zadán vícekrát; pomocí prvního specifikace  
  
 Exportu je uveden v několika a různé způsoby. Linkeru používá specifikace první a zbytek ignoruje.  
  
 Pokud se znovu sestavit běhové knihovny jazyka C, můžete tuto zprávu ignorovat.  
  
 Pokud export je úplně stejně, jako zadán vícekrát, linkeru nevydá upozornění.  
  
 Například následující obsah souboru .def by způsobilo toto upozornění:  
  
```  
EXPORTS  
   functioname      NONAME  
   functioname      @10  
```  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Je zadaný stejný export i na příkazovém řádku (prostřednictvím exportu:) a v souboru .def  
  
2.  Stejné export je uveden dvakrát v souboru .def s různé atributy.