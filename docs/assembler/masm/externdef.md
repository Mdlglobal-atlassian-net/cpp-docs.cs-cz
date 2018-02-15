---
title: "EXTERNDEF – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a463f4f74f380c6d927419eb498ccd868587ac6d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="externdef"></a>EXTERNDEF
Určuje jeden nebo více externí proměnné, popisky nebo symboly názvem *název* s jiným typem `type`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EXTERNDEF [[langtype]] name:type [[, [[langtype]] name:type]]...  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud *název* je definována v modulu, je považován za [veřejné](../../assembler/masm/public-masm.md). Pokud *název* se odkazuje v modulu, je považován za [EXTERN](../../assembler/masm/extern-masm.md). Pokud *název* se neodkazuje, bude se ignorovat. `type` Může být [ABS](../../assembler/masm/operator-abs.md), který importuje *název* jako konstanta. Obvykle používaná v zahrnout soubory.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)