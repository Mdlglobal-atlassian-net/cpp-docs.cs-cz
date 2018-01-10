---
title: "Nahrazení makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c2ea7a2509e58cfd4da163cc76c018d06c244fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="macro-substitution"></a>Nahrazení makra
Když *makro* vyvolání každý výskyt *řetězec1* v jeho definice řetězec nahrazuje *řetězec2*.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
$(macroname:string1=string2)  
```  
  
## <a name="remarks"></a>Poznámky  
 Nahrazení makra je velká a malá písmena a je literál; *řetězec1* a *řetězec2* nemohou vyvolat makra. Nahrazení neupravuje původní definici. Můžete nahradit text v žádné předdefinované makro s výjimkou [ $$@ ](../build/filename-macros.md).  
  
 Nesmí být mezery ani karty předcházet dvojtečkou; žádné po dvojtečkou se interpretují jako literál. Pokud *řetězec2* je null, všechny výskyty *řetězec1* jsou odstraněny z jeho definice řetězce.  
  
## <a name="see-also"></a>Viz také  
 [Použití makra NMAKE](../build/using-an-nmake-macro.md)