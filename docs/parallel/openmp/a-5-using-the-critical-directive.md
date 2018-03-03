---
title: "Using – direktiva kritické A.5 | Microsoft Docs"
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
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cf4170fae6792906db29c90f61f067886b00f1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="a5---using-the-critical-directive"></a>A.5   Použití direktivy critical
Následující příklad obsahuje několik `critical` direktivy ([části 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) na stránce 18). Tento příklad znázorňuje model služby Řízení front, ve kterém je úloha vyjmutou a na kterých. Chcete-li chránit proti více vláken vyřazení pro stejnou úlohu, musí být dequeuing operaci v `critical` části. Vzhledem k tomu, že dvě fronty v tomto příkladu jsou nezávislé, jsou chráněné `critical` direktivy s různými názvy *xaxis* a *yaxis*.  
  
```  
#pragma omp parallel shared(x, y) private(x_next, y_next)  
{  
    #pragma omp critical ( xaxis )  
        x_next = dequeue(x);  
    work(x_next);  
    #pragma omp critical ( yaxis )  
        y_next = dequeue(y);  
    work(y_next);  
}  
```