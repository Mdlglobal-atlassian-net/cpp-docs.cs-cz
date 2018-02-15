---
title: "Méně závažná chyba nástroje ML A2008 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A2008
dev_langs:
- C++
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afef8194fea15f9ebfa65201d43ddbdda2b61786
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ml-nonfatal-error-a2008"></a>Méně závažná chyba nástroje ML A2008
**Chyba syntaxe:**  
  
 Token do aktuálního umístění způsobila chybu syntaxe.  
  
 Mohlo dojít jednu z těchto možností:  
  
-   Předpona tečkou byl přidán do nebo vynechaný direktivu.  
  
-   Vyhrazené slovo (například **C** nebo **velikost**) byla použita jako identifikátor.  
  
-   Byl použit instrukce, které nebyly k dispozici s aktuálním výběrem procesoru nebo koprocesor.  
  
-   Operátor porovnání runtime (například `==`) byl použit v příkazu podmíněného sestavení místo relační operátor (například [EQ](../../assembler/masm/operator-eq.md)).  
  
-   Pokyn nebo – direktiva byla zadána příliš málo operandy.  
  
-   Zastaralá direktiva byl použit.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)