---
title: "Závažná chyba nástroje ML A1007 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1007
dev_langs: C++
helpviewer_keywords: A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 619f1eae458b52eb7851118d6702dccec769a1ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ml-fatal-error-a1007"></a>Závažná chyba nástroje ML A1007
**úroveň vnoření příliš hluboké**  
  
 Assembleru dosáhla svého limitu vnoření. Limit je 20 úrovně, pokud není uvedeno jinak jinak.  
  
 Jedním z těchto byl vnořeny příliš hluboko:  
  
-   Direktivu vysoké úrovně, jako [. Pokud](../../assembler/masm/dot-if.md), [. OPAKUJTE](../../assembler/masm/dot-repeat.md), nebo [. Při](../../assembler/masm/dot-while.md).  
  
-   Struktura definice.  
  
-   Direktivu podmíněného sestavení.  
  
-   Definice procedury.  
  
-   A [pushcontext –](../../assembler/masm/pushcontext.md) – direktiva (limit je 10).  
  
-   Definice segmentu.  
  
-   Vložené soubory.  
  
-   Makro.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)