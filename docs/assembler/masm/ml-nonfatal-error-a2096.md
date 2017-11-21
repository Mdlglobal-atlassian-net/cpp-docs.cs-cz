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
ms.openlocfilehash: ae268175c1f104f6f39f5ecbfd1f917ef415000e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ml-nonfatal-error-a2096"></a>Méně závažná chyba nástroje ML A2096
**Segment, skupiny nebo registr segmentu očekávání**  
  
 Segment nebo skupinu očekával, ale nebyl nalezen.  
  
 Jedním z těchto došlo k chybě:  
  
-   Levý operand zadaným segmentu přepsat – operátor (**:**) nebyla segment registrace (CS, DS, SS, ES, FS nebo GS), název skupiny, název segmentu nebo výraz segmentu.  
  
-   [ASSUME](../../assembler/masm/assume.md) – direktiva byl zadán segment zaregistrovat bez adresu platný segment, registrace segmentu, skupiny nebo speciální **ploché** skupiny.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy nástroje ML](../../assembler/masm/ml-error-messages.md)