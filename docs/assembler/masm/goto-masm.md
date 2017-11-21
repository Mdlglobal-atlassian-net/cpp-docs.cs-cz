---
title: "GOTO – PŘÍKAZ (MASM) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: goto
dev_langs: C++
helpviewer_keywords: GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 896d99b2ed4abe2080e646b6a541eb1e489d2b75
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="goto-masm"></a>GOTO (MASM)
Přenosy sestavení na řádek označený **:***macrolabel*.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GOTO   
macrolabel  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **GOTO** je povoleny pouze uvnitř [makro](../../assembler/masm/macro.md), [pro](../../assembler/masm/for-masm.md), [forc –](../../assembler/masm/forc.md), [opakovat](../../assembler/masm/repeat.md), a **při**bloky. Popisek musí být pouze – direktiva na řádku a musí předcházet úvodní dvojtečkou.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)