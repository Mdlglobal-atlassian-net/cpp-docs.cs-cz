---
title: "2.9 vnořování direktiv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f1af9f515861863af5906c99d78aa66d08aa09b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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