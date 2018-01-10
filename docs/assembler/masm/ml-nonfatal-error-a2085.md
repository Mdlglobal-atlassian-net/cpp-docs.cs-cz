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
ms.workload: cplusplus
ms.openlocfilehash: f987b775c13b0e477fd5c1d215d556069535a0fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ml-nonfatal-error-a2085"></a>Méně závažná chyba nástroje ML A2085
**instrukce nebo zaregistrovat nebylo přijato. v aktuální režim procesoru**  
  
 Došlo pokusu o použít instrukce, registrace nebo klíčové slovo, které nebyla platná pro aktuální režim procesoru.  
  
 Například 32-bit registry vyžadovat [.386](../../assembler/masm/dot-386.md) nebo vyšší. Ovládací prvek zaregistruje, jako je CR0 vyžadují privilegovaném režimu [.386p –](../../assembler/masm/dot-386p.md) nebo vyšší. Tato chyba bude vygenerována také pro **NEAR32**, **FAR32**, a **ploché** klíčová slova, která vyžadují. **386** nebo vyšší.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)