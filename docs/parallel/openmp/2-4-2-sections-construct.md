---
title: "2.4.2 sections – konstrukce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 22aa4cc1bde59234d70803c2e878d3fbf83f499e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="242-sections-construct"></a>2.4.2 sections – konstrukce
**Části** – direktiva identifikuje noniterative konstrukci sdílení práce, která určuje sadu konstrukce, které se rozdělí mezi vláken v týmu. Každá část je jednou spustit vlákno v týmu. Syntaxe **části** – Direktiva vypadá takto:  
  
```  
#pragma omp sections [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-linestructured-block ]  
...  
}  
```  
  
 V klauzuli je jedním z následujících akcí:  
  
 **privátní (** *seznamu proměnné* **)**  
  
 **firstprivate (** *seznamu proměnné* **)**  
  
 **lastprivate (** *seznamu proměnné* **)**  
  
 **snížení (** *operátor* **:***seznamu proměnné* **)**   
  
 **nowait**  
  
 Každá část předchází **části** – direktiva, i když **části** – direktiva je volitelný pro první část. **Části** direktivy musí být v rámci lexikální rozsah **části** – direktiva. Na konci je implicitní bariéry **části** vytvořit, pokud **nowait** je zadán.  
  
 Omezení **části** – direktiva jsou následující:  
  
-   A **části** – direktiva nesmí zobrazí mimo lexikální rozsah **části** – direktiva.  
  
-   Jediným **nowait** klauzule lze zobrazit na **části** – direktiva.  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   **privátní**, **firstprivate**, **lastprivate**, a **snížení** klauzule, najdete v části [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.