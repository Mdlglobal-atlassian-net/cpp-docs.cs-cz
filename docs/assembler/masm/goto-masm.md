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
ms.workload: cplusplus
ms.openlocfilehash: ed7e20bb7f81b74a2f670e604e958ca02f132531
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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