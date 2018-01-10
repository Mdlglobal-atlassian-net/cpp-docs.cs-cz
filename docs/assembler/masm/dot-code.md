---
title: ". KÓD | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .CODE
dev_langs: C++
helpviewer_keywords: .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 150b5a0c26be3c3c4d0412157179ebfcbec128e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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