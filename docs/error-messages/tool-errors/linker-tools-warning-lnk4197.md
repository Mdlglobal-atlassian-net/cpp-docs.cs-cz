---
title: "Upozornění linkerů Lnk4197 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4197
dev_langs: C++
helpviewer_keywords: LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1fadbf2ba5b18004f0e89142c88a68437842a92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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