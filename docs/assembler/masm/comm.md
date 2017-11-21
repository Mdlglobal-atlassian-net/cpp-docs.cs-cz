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
ms.openlocfilehash: b8feb74f1da11fb6c4205ec1d8381f78789f684f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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