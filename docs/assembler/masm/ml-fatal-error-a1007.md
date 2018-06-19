---
title: Závažná chyba nástroje ML A1007 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1007
dev_langs:
- C++
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10b883fad01943cd8cff71b3da9dee66407ccc93
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055726"
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