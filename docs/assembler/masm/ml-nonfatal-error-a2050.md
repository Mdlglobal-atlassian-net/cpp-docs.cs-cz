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
ms.openlocfilehash: b06c7374303b606ddf7929f2b7c6d774c55c829c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ml-nonfatal-error-a2050"></a>Méně závažná chyba nástroje ML A2050
**Real nebo není povolený počet BCD**  
  
 Číslo s plovoucí desetinnou čárkou (skutečné) nebo binární programový decimal (BCD) Konstanta používala jiné než jako inicializátoru data.  
  
 Jedním z těchto došlo k chybě:  
  
-   Reálné číslo nebo BCD byla použita ve výrazu.  
  
-   Reálné číslo byla použita k inicializaci direktivu jiné než [DWORD](../../assembler/masm/dword.md), [QWORD](../../assembler/masm/qword.md), nebo [tbyte –](../../assembler/masm/tbyte.md).  
  
-   BCD byla použita k inicializaci direktivu jiné než `TBYTE`.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy nástroje ML](../../assembler/masm/ml-error-messages.md)