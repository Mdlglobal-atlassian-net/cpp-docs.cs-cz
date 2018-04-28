---
title: . KÓD | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59e376fc9c10ab8891b02e4da334341ae0534b73
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="code"></a>.CODE
Při použití s [. MODEL](../../assembler/masm/dot-model.md), označuje začátek segmentu kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.CODE [[name]]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`name`|Volitelný parametr, který určuje název segment kódu. Výchozí název je _TEXT – pro malý, malý, zkomprimovat a dvojrozměrném [modely](../../assembler/masm/dot-model.md). Výchozí název je *modulename*_TEXT – pro ostatní modely.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)   
 [.DATA](../../assembler/masm/dot-data.md)