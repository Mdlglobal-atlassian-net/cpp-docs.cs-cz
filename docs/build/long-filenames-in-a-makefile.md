---
title: "Dlouhé názvy souborů v souboru pravidel | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, long filenames
- long filenames
ms.assetid: 626d56fc-8879-46ba-9c2d-dd386c78cccc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f808faff82e9fcd29040f8d15e6cbaa9e037733
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="long-filenames-in-a-makefile"></a>Dlouhé názvy souborů v souboru pravidel
Uzavřete dlouhé názvy souborů v uvozovkách, následujícím způsobem:  
  
```  
all : "VeryLongFileName.exe"  
```  
  
## <a name="see-also"></a>Viz také  
 [Obsah souboru pravidel](../build/contents-of-a-makefile.md)