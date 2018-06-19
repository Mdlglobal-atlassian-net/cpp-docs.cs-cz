---
title: Chybové zprávy nástroje ML | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
dev_langs:
- C++
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fbc2ae6388ad11a411850d03de421d2f6820fc03
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057094"
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
  
 *Název souboru*  
 Soubor, který obsahuje stav chyby generování.  
  
 *řádek*  
 Přibližná řádku, kde existuje chybový stav.  
  
 *Error_type –*  
 Závažná chyba, chyby nebo upozornění.  
  
 *Kód*  
 Kód chyby jedinečný 5 nebo 6číslic.  
  
 `Message_text`  
 Popis krátký a obecné chybový stav.  
  
## <a name="see-also"></a>Viz také  
 [Microsoft Macro Assembler – referenční dokumentace](../../assembler/masm/microsoft-macro-assembler-reference.md)