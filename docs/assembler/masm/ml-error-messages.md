---
title: "Chybové zprávy nástroje ML | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
dev_langs:
- C++
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 09478bd3cff63e890014c6c14b11335feb8dfb3f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ml-error-messages"></a>Chybové zprávy nástroje ML
Chybové zprávy generované komponentami MASM spadají do tří kategorií:  
  
-   **Závažné chyby.** Ty naznačují k závažnému problému, který zabrání dokončení jeho normální proces nástroj.  
  
-   **Méně závažné chyby.** Tento nástroj může dokončit zpracování. Pokud ano, není pravděpodobné, že je ta, kterou chcete její výsledek.  
  
-   **Upozornění.** Tyto zprávy určují podmínky, které mohou zabránit načítání výsledků, které chcete.  
  
 Všechny chybové zprávy mít tento tvar:  
  
```  
  
Utility: Filename (Line) : [Error_type} (Code): Message_text  
```  
  
 kde:  
  
 `Utility`  
 Program, který odeslal zprávu chyby.  
  
 *Filename*  
 Soubor, který obsahuje stav chyby generování.  
  
 *řádek*  
 Přibližná řádku, kde existuje chybový stav.  
  
 *Error_type*  
 Závažná chyba, chyby nebo upozornění.  
  
 *Kód*  
 Kód chyby jedinečný 5 nebo 6číslic.  
  
 `Message_text`  
 Popis krátký a obecné chybový stav.  
  
## <a name="see-also"></a>Viz také  
 [Microsoft Macro Assembler – referenční dokumentace](../../assembler/masm/microsoft-macro-assembler-reference.md)