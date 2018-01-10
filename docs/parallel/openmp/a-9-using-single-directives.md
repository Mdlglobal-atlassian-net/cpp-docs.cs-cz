---
title: Jeden direktivy Using A.9 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 11d41d62448d41d7a11ef747e65cc6ac47e4bd7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="a9---using-single-directives"></a>A.9   Použití direktiv single
Následující příklad ukazuje `single` – direktiva ([části 2.4.3](../../parallel/openmp/2-4-3-single-construct.md) na stránce 15). V příkladu pouze jedno vlákno (obvykle první vlákno, které narazí `single` – direktiva) zobrazí zpráva o průběhu. Uživatel nesmí vytvořit žádný odhad jako na vlákno, které budou spuštěny `single` části. Přeskočí jiná vlákna `single` části a zastavit bariéry na konci `single` vytvořit. Pokud jiná vlákna můžete pokračovat bez čekání na vlákno provádění `single` části `nowait` jde zadat klauzuli `single` – direktiva.  
  
```  
#pragma omp parallel  
{  
    #pragma omp single  
        printf_s("Beginning work1.\n");  
    work1();  
    #pragma omp single  
        printf_s("Finishing work1.\n");  
    #pragma omp single nowait  
        printf_s("Finished work1 and beginning work2.\n");  
    work2();  
}  
```