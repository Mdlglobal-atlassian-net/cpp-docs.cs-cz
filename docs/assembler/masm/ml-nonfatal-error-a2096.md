---
title: Méně závažná chyba nástroje ML A2096 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2096
dev_langs:
- C++
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e5d07afa864c9f6f4214de953aa9e03fe0e7e4f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053669"
---
# <a name="ml-nonfatal-error-a2096"></a>Méně závažná chyba nástroje ML A2096
**Segment, skupiny nebo registr segmentu očekávání**  
  
 Segment nebo skupinu očekával, ale nebyl nalezen.  
  
 Jedním z těchto došlo k chybě:  
  
-   Levý operand zadaným segmentu přepsat – operátor (**:**) nebyla segment registrace (CS, DS, SS, ES, FS nebo GS), název skupiny, název segmentu nebo výraz segmentu.  
  
-   [ASSUME](../../assembler/masm/assume.md) – direktiva byl zadán segment zaregistrovat bez adresu platný segment, registrace segmentu, skupiny nebo speciální **ploché** skupiny.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)