---
title: "GOTO – PŘÍKAZ (MASM) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c86a9b5bc83110f20dccf73f51b1e1aabc693db2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="goto-masm"></a>GOTO (MASM)
Přenosy sestavení na řádek označený **: *** macrolabel*.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GOTO   
macrolabel  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **GOTO** je povoleny pouze uvnitř [makro](../../assembler/masm/macro.md), [pro](../../assembler/masm/for-masm.md), [forc –](../../assembler/masm/forc.md), [opakovat](../../assembler/masm/repeat.md), a **při**bloky. Popisek musí být pouze – direktiva na řádku a musí předcházet úvodní dvojtečkou.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)