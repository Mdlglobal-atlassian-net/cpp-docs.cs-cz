---
title: "Using – direktiva kritické A.5 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1ef678b58df9d2c323cdebb61feed52ebbaf607f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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