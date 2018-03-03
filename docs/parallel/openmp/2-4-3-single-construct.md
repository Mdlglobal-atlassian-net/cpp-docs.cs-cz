---
title: "2.4.3 jednotné konstrukce | Microsoft Docs"
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
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 72dc551986f149bda668c438ac5f51d01d530c51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="243-single-construct"></a>2.4.3 single – konstrukce
**Jeden** – direktiva identifikuje konstrukce, která určuje, že přidružené strukturovaných bloku provedený pouze jedno vlákno v týmu (nikoli nutně hlavní vlákno). Syntaxe **jeden** – Direktiva vypadá takto:  
  
```  
#pragma omp single [clause[[,] clause] ...] new-linestructured-block  
```  
  
 V klauzuli je jedním z následujících akcí:  
  
 **privátní (** *seznamu proměnné* **)**  
  
 **firstprivate (** *seznamu proměnné* **)**  
  
 **copyprivate (** *seznamu proměnné* **)**  
  
 **nowait**  
  
 Je implicitní bariéry po **jeden** vytvořit, pokud **nowait** je zadána klauzule.  
  
 Omezení **jeden** – direktiva jsou následující:  
  
-   Jediným **nowait** klauzule lze zobrazit na **jeden** – direktiva.  
  
-   **Copyprivate** klauzule nesmějí se používat se **nowait** klauzule.  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   **privátní**, **firstprivate**, a **copyprivate** klauzule, najdete v části [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.