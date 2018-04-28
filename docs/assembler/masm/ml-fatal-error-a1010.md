---
title: Závažná chyba nástroje ML A1010 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1010
dev_langs:
- C++
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b622595b6994c4c4eaa74ed8f824f28dffe89b1a
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
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