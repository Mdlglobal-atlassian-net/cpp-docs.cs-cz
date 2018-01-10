---
title: "Méně závažná chyba nástroje ML A2050 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2050
dev_langs: C++
helpviewer_keywords: A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a51a90f294afd0347057efb04ab37ce790532ba4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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