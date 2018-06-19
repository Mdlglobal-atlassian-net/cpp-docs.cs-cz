---
title: Nahrazení makra | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4028ee710cf38b6a4ef929de9a7e4ffad95f3e41
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368067"
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