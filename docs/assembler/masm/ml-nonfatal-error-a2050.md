---
title: "Méně závažná chyba nástroje ML A2050 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A2050
dev_langs:
- C++
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 887a18ee274b3e09624a07e214f235333e2a9665
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ml-nonfatal-error-a2050"></a>Méně závažná chyba nástroje ML A2050
**Real nebo není povolený počet BCD**  
  
 Číslo s plovoucí desetinnou čárkou (skutečné) nebo binární programový decimal (BCD) Konstanta používala jiné než jako inicializátoru data.  
  
 Jedním z těchto došlo k chybě:  
  
-   Reálné číslo nebo BCD byla použita ve výrazu.  
  
-   Reálné číslo byla použita k inicializaci direktivu jiné než [DWORD](../../assembler/masm/dword.md), [QWORD](../../assembler/masm/qword.md), nebo [tbyte –](../../assembler/masm/tbyte.md).  
  
-   BCD byla použita k inicializaci direktivu jiné než `TBYTE`.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)