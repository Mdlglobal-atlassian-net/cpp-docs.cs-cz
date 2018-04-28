---
title: GOTO – PŘÍKAZ (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9eecdab2fe91de0aae656b37c6fddafe658e60c0
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
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