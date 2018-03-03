---
title: 2.7.2.8 copyprivate | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21d739fb3ead0512776cfd996b59f1ceab5e8250
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="2728-copyprivate"></a>2.7.2.8 copyprivate
**Copyprivate** klauzule poskytuje mechanismus pro privátní proměnnou použijte k vysílání hodnotu z jednoho člena týmu ostatním členům. Jde o alternativu k použití sdílené proměnné pro hodnotu, při poskytování sdílené proměnné může být obtížné (například v rekurze, vyžadování jiné proměnné na každé úrovni). **Copyprivate** klauzule se může vyskytovat pouze na **jeden** – direktiva.  
  
 Syntaxe **copyprivate** klauzule vypadá takto:  
  
```  
  
copyprivate(  
variable-list  
)  
  
```  
  
 Účinek **copyprivate** klauzule na proměnné ve svém seznamu proměnná dojde po spuštění strukturovaných bloku přidružené **jeden** vytvořit a před spuštěním vláken v tým opustili bariéry na konci konstruktu. Potom v všechna vlákna v týmu, pro každou proměnnou v *seznamu proměnné*, tuto proměnnou stane definované (jako přiřazení) s odpovídající hodnotou proměnné v vláken, která provedla konstruktu je strukturovaná. blok.  
  
 Omezení **copyprivate** klauzule jsou následující:  
  
-   Proměnné, která je zadána v **copyprivate** klauzule nesmí objeví v **privátní** nebo **firstprivate** klauzuli pro stejné **jedním**– direktiva.  
  
-   Pokud **jeden** direktivy s **copyprivate** klauzule se vyskytuje v dynamické rozsah paralelní oblast, všechny proměnné zadané v **copyprivate** musí být klauzule privátní v nadřazených kontextu.  
  
-   Proměnné, která je zadána v **copyprivate** klauzule musí mít operátor přiřazení přístupné jednoznačným kopírování.