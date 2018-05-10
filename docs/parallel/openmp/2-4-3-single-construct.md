---
title: 2.4.3 jednotné konstrukce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db3f9ca834fb3f35c95732698fd02e16f31b4225
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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