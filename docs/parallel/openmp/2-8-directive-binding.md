---
title: 2.8 vazby direktiv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02492b228b4bb47a800955f078a59ce680312a87
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="28-directive-binding"></a>2.8 Vazby direktiv
Dynamické vazby direktiv musí splňovat následující pravidla:  
  
-   **Pro**, **části**, **jeden**, **hlavní**, a **bariéry** direktivy vytvořit vazbu dynamicky uzavření **paralelní**, pokud existuje, bez ohledu na hodnotu všech **Pokud** klauzuli, která může být na tomto – direktiva. Pokud se spouští bez paralelní oblast, direktivy provedení týmem tvořený jenom hlavní vlákno.  
  
-   **Seřazené** – Direktiva sváže dynamicky nadřazených **pro**.  
  
-   **Atomic** – direktiva vynucuje výhradní přístup k **atomic** direktivy v všechna vlákna, ne jenom týmem aktuální.  
  
-   **Kritické** – direktiva vynucuje výhradní přístup k **kritické** direktivy v všechna vlákna, ne jenom týmem aktuální.  
  
-   Direktivu můžete nikdy vázat na všechny – direktiva mimo na nejbližší dynamicky obklopuje **paralelní**.