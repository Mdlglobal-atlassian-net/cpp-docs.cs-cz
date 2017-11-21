---
title: "Using – direktiva atomic A.12 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 12c6467ee3233ce5d36d131ec81072bab8b841fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="a12---using-the-atomic-directive"></a>A.12   Použití direktivy atomic
V následujícím příkladu zabraňuje časování (souběžné aktualizace element *x* více podprocesů) pomocí `atomic` – direktiva ([části 2.6.4](../../parallel/openmp/2-6-4-atomic-construct.md) na stránce 19):  
  
```  
#pragma omp parallel for shared(x, y, index, n)  
    for (i=0; i<n; i++)   
    {  
        #pragma omp atomic  
            x[index[i]] += work1(i);  
        y[i] += work2(i);  
    }  
```  
  
 Výhodou použití `atomic` – direktiva v tomto příkladu je, že umožňuje aktualizace dva různé elementy x být provedeny souběžně. Pokud `critical` – direktiva ([části 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) na stránce 18) používaly místo toho, pak všechny aktualizace prvky *x* by byl proveden sériově (i když není v žádném zaručit pořadí).  
  
 Všimněte si, že `atomic` – direktiva platí pouze pro příkaz jazyka C nebo C++ hned za ho.  V důsledku toho prvky *y* neaktualizují atomicky v tomto příkladu.