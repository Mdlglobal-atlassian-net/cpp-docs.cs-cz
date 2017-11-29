---
title: 2.8 vazby direktiv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a70dbc0306005473d427015e81d8b93e895da9fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="28-directive-binding"></a>2.8 Vazby direktiv
Dynamické vazby direktiv musí splňovat následující pravidla:  
  
-   **Pro**, **části**, **jeden**, **hlavní**, a **bariéry** direktivy vytvořit vazbu dynamicky uzavření **paralelní**, pokud existuje, bez ohledu na hodnotu všech **Pokud** klauzuli, která může být na tomto – direktiva. Pokud se spouští bez paralelní oblast, direktivy provedení týmem tvořený jenom hlavní vlákno.  
  
-   **Seřazené** – Direktiva sváže dynamicky nadřazených **pro**.  
  
-   **Atomic** – direktiva vynucuje výhradní přístup k **atomic** direktivy v všechna vlákna, ne jenom týmem aktuální.  
  
-   **Kritické** – direktiva vynucuje výhradní přístup k **kritické** direktivy v všechna vlákna, ne jenom týmem aktuální.  
  
-   Direktivu můžete nikdy vázat na všechny – direktiva mimo na nejbližší dynamicky obklopuje **paralelní**.