---
title: Méně závažná chyba nástroje ML A2050 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2050
dev_langs:
- C++
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 159ed131c13166435114234b3b16a82cd4d41d1f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32056191"
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