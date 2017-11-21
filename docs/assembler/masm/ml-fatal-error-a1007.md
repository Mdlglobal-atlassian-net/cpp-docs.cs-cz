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
ms.openlocfilehash: bb4b55ce7a16620cd501fa8e687339f1bc48e3b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Chybové zprávy nástroje ML](../../assembler/masm/ml-error-messages.md)