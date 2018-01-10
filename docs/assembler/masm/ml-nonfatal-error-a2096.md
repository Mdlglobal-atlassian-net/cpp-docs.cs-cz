---
title: "Méně závažná chyba nástroje ML A2096 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2096
dev_langs: C++
helpviewer_keywords: A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d4466d87e33068b10b3f620bfbe764e4aec76c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ml-nonfatal-error-a2096"></a>Méně závažná chyba nástroje ML A2096
**Segment, skupiny nebo registr segmentu očekávání**  
  
 Segment nebo skupinu očekával, ale nebyl nalezen.  
  
 Jedním z těchto došlo k chybě:  
  
-   Levý operand zadaným segmentu přepsat – operátor (**:**) nebyla segment registrace (CS, DS, SS, ES, FS nebo GS), název skupiny, název segmentu nebo výraz segmentu.  
  
-   [ASSUME](../../assembler/masm/assume.md) – direktiva byl zadán segment zaregistrovat bez adresu platný segment, registrace segmentu, skupiny nebo speciální **ploché** skupiny.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)