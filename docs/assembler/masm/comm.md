---
title: COMM – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 111dac47089fea13febe787e5b73557b287beea8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="comm"></a>COMM
Vytvoří místní proměnné s atributy určené v `definition`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## <a name="remarks"></a>Poznámky  
 Každý `definition` má následující formát:  
  
 [[*langtype*]] [[**NEAR** &#124; **DÁLNÉHO**]] *popisek ***:**`type`[[**:*** počet*]]  
  
 *Popisek* je název proměnné. `type` Může být jakékoli specifikátor typu ([BAJTŮ](../../assembler/masm/byte-masm.md), [WORD](../../assembler/masm/word.md)a tak dále) nebo celé číslo určující počet bajtů. *Počet* určuje počet datových objektů (je výchozí hodnota).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)