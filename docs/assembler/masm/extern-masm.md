---
title: EXTERN (MASM) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- extern
dev_langs:
- C++
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1688854dd505e03f6302e5651d1903e4cb8d638f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="extern-masm"></a>EXTERN (MASM)
Určuje jeden nebo více externí proměnné, popisky nebo symboly názvem *název* s jiným typem `type`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
   EXTERN [[langtype]] name [[(altid)]] :  
type [[, [[langtype]] name [[(altid)]] :type]]...  
```  
  
## <a name="remarks"></a>Poznámky  
 `type` Může být [ABS](../../assembler/masm/operator-abs.md), který importuje *název* jako konstanta. Stejné jako [extrn –](../../assembler/masm/extrn.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)