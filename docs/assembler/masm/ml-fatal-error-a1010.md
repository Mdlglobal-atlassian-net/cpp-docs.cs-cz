---
title: "Závažná chyba nástroje ML A1010 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1010
dev_langs: C++
helpviewer_keywords: A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b495fc2b8bd0e667dd7dae7e23347f6971ec4d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ml-fatal-error-a1010"></a>Závažná chyba nástroje ML A1010
**neodpovídající bloku vnoření:**  
  
 Začátku bloku nemá odpovídající end nebo koncový blok neměl odpovídající začátku. Může být zahrnuta jednu z těchto možností:  
  
-   Direktivu vysoké úrovně, jako [. Pokud](../../assembler/masm/dot-if.md), [. OPAKUJTE](../../assembler/masm/dot-repeat.md), nebo [. Při](../../assembler/masm/dot-while.md).  
  
-   Direktiva podmíněného sestavení jako [Pokud](../../assembler/masm/if-masm.md), [opakovat](../../assembler/masm/repeat.md), nebo **při**.  
  
-   Definice struktury nebo sjednocení.  
  
-   Definice procedury.  
  
-   Definice segmentu.  
  
-   A [popcontext –](../../assembler/masm/popcontext.md) – direktiva.  
  
-   Podmíněné sestavení direktivy, například [ELSE](../../assembler/masm/else-masm.md), [ElseIf –](../../assembler/masm/elseif-masm.md), nebo **ENDIF** bez odpovídající [Pokud](../../assembler/masm/if-masm.md).  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)