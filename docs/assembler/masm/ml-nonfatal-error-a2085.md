---
title: Méně závažná chyba nástroje ML A2085 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f0a014810679f0b48f79198b1335240f5cd6a8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="ml-nonfatal-error-a2085"></a>Méně závažná chyba nástroje ML A2085
**instrukce nebo zaregistrovat nebylo přijato. v aktuální režim procesoru**  
  
 Došlo pokusu o použít instrukce, registrace nebo klíčové slovo, které nebyla platná pro aktuální režim procesoru.  
  
 Například 32-bit registry vyžadovat [.386](../../assembler/masm/dot-386.md) nebo vyšší. Ovládací prvek zaregistruje, jako je CR0 vyžadují privilegovaném režimu [.386p –](../../assembler/masm/dot-386p.md) nebo vyšší. Tato chyba bude vygenerována také pro **NEAR32**, **FAR32**, a **ploché** klíčová slova, která vyžadují. **386** nebo vyšší.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)