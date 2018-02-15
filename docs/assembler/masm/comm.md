---
title: "COMM – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6258a584d39f598b32c43affc0ef2569b77b2047
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="comm"></a>COMM
Vytvoří místní proměnné s atributy určené v `definition`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## <a name="remarks"></a>Poznámky  
 Každý `definition` má následující formát:  
  
 [[*langtype*]] [[**NEAR** &#124; **DÁLNÉHO**]] *popisek***:**`type`[[**:***počet*]]  
  
 *Popisek* je název proměnné. `type` Může být jakékoli specifikátor typu ([BAJTŮ](../../assembler/masm/byte-masm.md), [WORD](../../assembler/masm/word.md)a tak dále) nebo celé číslo určující počet bajtů. *Počet* určuje počet datových objektů (je výchozí hodnota).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)