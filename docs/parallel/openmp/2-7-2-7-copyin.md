---
title: 2.7.2.7 copyin | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd296192146e76085e1b987e29a377eb621917ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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