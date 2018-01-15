---
title: "A.29 sdílení použití práce vytvoří uvnitř critical – konstrukce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: d5c8a83f-2f51-4f23-8ddf-d267e347507f
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9bd95a689fbb643af5e2291c0a86b248705b5f9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="a29---use-of-work-sharing-constructs-inside-a-critical-construct"></a>A.29   Použití konstrukcí pro sdílení práce uvnitř konstrukce critical
Následující příklad ukazuje, jak pomocí konstrukt sdílení práce uvnitř `critical` vytvořit. V tomto příkladu je kompatibilní, protože sdílení práce vytvořit a `critical` konstrukce vazbu ke stejné paralelní oblasti.  
  
```  
void f()  
{  
  int i = 1;  
  #pragma omp parallel sections  
  {  
    #pragma omp section  
    {  
      #pragma omp critical (name)  
      {  
        #pragma omp parallel  
        {  
          #pragma omp single  
          {  
            i++;  
          }  
        }  
      }  
    }  
  }  
}  
```