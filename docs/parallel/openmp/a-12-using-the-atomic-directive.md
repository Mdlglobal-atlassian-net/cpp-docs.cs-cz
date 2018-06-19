---
title: Using – direktiva atomic A.12 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 719d7a9843a0759b5a5bd558e07a2004f9ef1543
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691404"
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