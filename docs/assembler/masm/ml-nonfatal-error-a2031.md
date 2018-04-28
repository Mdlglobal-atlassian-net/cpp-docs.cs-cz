---
title: Méně závažná chyba nástroje ML A2031 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2031
dev_langs:
- C++
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ab35776944604f3133254532d2631460c755983
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="ml-nonfatal-error-a2031"></a>Méně závažná chyba nástroje ML A2031
**musí být index nebo základní registrace**  
  
 Byl proveden pokus o použití registrace, který nebyl index nebo základní registrace ve výrazu paměti.  
  
 Tuto chybu způsobí například těchto výrazů:  
  
```  
[ax]  
[bl]  
```  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)