---
title: "Méně závažná chyba nástroje ML A2085 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2085
dev_langs: C++
helpviewer_keywords: A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d93ec58a7f55a2d875cc07dfbddff103b052f98c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ml-nonfatal-error-a2085"></a>Méně závažná chyba nástroje ML A2085
**instrukce nebo zaregistrovat nebylo přijato. v aktuální režim procesoru**  
  
 Došlo pokusu o použít instrukce, registrace nebo klíčové slovo, které nebyla platná pro aktuální režim procesoru.  
  
 Například 32-bit registry vyžadovat [.386](../../assembler/masm/dot-386.md) nebo vyšší. Ovládací prvek zaregistruje, jako je CR0 vyžadují privilegovaném režimu [.386p –](../../assembler/masm/dot-386p.md) nebo vyšší. Tato chyba bude vygenerována také pro **NEAR32**, **FAR32**, a **ploché** klíčová slova, která vyžadují. **386** nebo vyšší.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy nástroje ML](../../assembler/masm/ml-error-messages.md)