---
title: "Méně závažná chyba nástroje ML A2006 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2006
dev_langs: C++
helpviewer_keywords: A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 463a66ae4f1f7d21d108644c3aa47b504d742edb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ml-nonfatal-error-a2006"></a>Méně závažná chyba nástroje ML A2006
**Nedefinovaná symbol: identifikátor**  
  
 Byl proveden pokus o použití symbol, který není definovaný.  
  
 Mohlo dojít jednu z těchto možností:  
  
-   Symbol nebyl definován.  
  
-   Pole se není členem zadané strukturu.  
  
-   Symbol byl definován v souboru zahrnout, které nebyly zahrnuty.  
  
-   Externí symbol byl použit bez [EXTERN](../../assembler/masm/extern-masm.md) nebo [externdef –](../../assembler/masm/externdef.md) – direktiva.  
  
-   Bylo zadáno chybně názvu symbolu.  
  
-   Místní znakové štítek odkazovaný mimo její obor.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy nástroje ML](../../assembler/masm/ml-error-messages.md)