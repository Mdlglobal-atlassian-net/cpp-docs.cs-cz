---
title: 2.9 vnořování direktiv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28e690ba531b4b37973bc2555d904317181ff918
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691336"
---
# <a name="29-directive-nesting"></a>2.9 Vnořování direktiv
Dynamické vnořování direktiv musí splňovat následující pravidla:  
  
-   A **paralelní** direktivy dynamicky uvnitř jiné **paralelní** logicky vytvoří nový tým, který se skládá z aktuální vlákno, pokud vnořené paralelismus je povoleno.  
  
-   **pro**, **části**, a **jeden** direktivy, které vytvořit vazbu na stejný **paralelní** není dovoleno vnořit do sebe navzájem.  
  
-   **kritické** direktivy se stejným názvem není dovoleno vnořit do sebe navzájem. Všimněte si, že toto omezení není dostatečná k zabránění vzájemnému zablokování.  
  
-   **pro**, **části**, a **jeden** direktivy nejsou povoleny v dynamické rozsah **kritické**, **seřazené**, a **hlavní** oblasti pokud direktivy vytvořit vazbu na stejný **paralelní** jako ty oblasti.  
  
-   **Barrier** direktivy nejsou povoleny v dynamické rozsah **pro**, **seřazené**, **části**, **jeden**, **hlavní**, a **kritické** oblasti pokud direktivy vytvořit vazbu na stejný **paralelní** jako ty oblasti.  
  
-   **hlavní** direktivy nejsou povoleny v dynamické rozsah **pro**, **části**, a **jeden** direktivy Pokud **hlavní** direktivy vytvořit vazbu na stejný **paralelní** jako direktivy sdílení práce.  
  
-   **seřazené** direktivy nejsou povoleny v dynamické rozsah **kritické** oblasti pokud direktivy vytvořit vazbu na stejný **paralelní** jako ty oblasti.  
  
-   Všechny direktiva, která je povoleno při spuštění dynamicky uvnitř paralelní oblast je také povoleno po provedení mimo paralelní oblast. Po provedení dynamicky mimo oblast paralelní zadán uživatel direktiva provedený tým skládající se z pouze hlavní vlákno.