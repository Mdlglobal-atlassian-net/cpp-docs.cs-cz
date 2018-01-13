---
title: "COMM – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COMM
dev_langs: C++
helpviewer_keywords: COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad12de948227f98ec73f779030b8e644dfad8b2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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