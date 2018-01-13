---
title: "Méně závažná chyba nástroje ML A2219 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2219
dev_langs: C++
helpviewer_keywords: A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f918e79b47a6a1ea88ac8f01dd43f20fb793f99
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ml-nonfatal-error-a2219"></a>Méně závažná chyba nástroje ML A2219
**Unwind chybné zarovnání posun v kódu**  
  
 Operand pro [. ALLOCSTACK](../../assembler/masm/dot-allocstack.md) a [. SAVEREG](../../assembler/masm/dot-savereg.md) musí být násobkem 8.  Operand pro [. SAVEXMM128](../../assembler/masm/dot-savexmm128.md) a [. SETFRAME](../../assembler/masm/dot-setframe.md) musí být násobkem 16.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)