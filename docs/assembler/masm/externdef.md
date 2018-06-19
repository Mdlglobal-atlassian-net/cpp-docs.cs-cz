---
title: EXTERNDEF – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b010f52f91a04388f34052fcc5c374690cff13df
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052697"
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