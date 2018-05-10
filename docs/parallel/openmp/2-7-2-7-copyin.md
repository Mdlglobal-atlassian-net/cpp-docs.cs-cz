---
title: 2.7.2.7 copyin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ee711bfb24e7a2a1cbada1a7e01a243e204f4a8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="2727-copyin"></a>2.7.2.7 copyin
**Copyin** klauzule poskytuje mechanismus pro přiřadit stejnou hodnotu do **threadprivate** proměnných pro každé vlákno v týmu provádění paralelní oblast. Pro každou proměnnou, zadaný v **copyin** zkopírovali klauzule, hodnota proměnné v hlavní vlákno týmu, jako kdyby podle přiřazení, zkopíruje privátní přístup z více vláken na začátku paralelní oblast. Syntaxe **copyin** klauzule vypadá takto:  
  
```  
  
copyin(  
variable-list  
)  
  
```  
  
 Omezení, které mají **copyin** klauzule jsou následující:  
  
-   Proměnné, která je zadána v **copyin** klauzule musí mít operátor přiřazení přístupný, jednoznačným kopírování.  
  
-   Proměnné, která je zadána v **copyin** musí být klauzule **threadprivate** proměnné.