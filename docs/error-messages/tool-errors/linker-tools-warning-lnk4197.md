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
ms.openlocfilehash: 5977095609dc123866afc39ac610bb0ff9d1619c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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