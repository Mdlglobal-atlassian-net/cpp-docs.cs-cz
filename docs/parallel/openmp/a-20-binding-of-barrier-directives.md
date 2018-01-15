---
title: "A.20 vazby direktiv bariéry | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5b8cc2799f0aea9e75b3aad44d3cfa9e3f5e7de4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="a20---binding-of-barrier-directives"></a>A.20   Vazby direktiv barrier
Vazby direktiv pravidla pro volání **barrier** – direktiva vytvořit vazbu na nejbližší obklopuje `parallel` – direktiva. Další informace o vazby direktiv najdete v tématu [části 2.8](../../parallel/openmp/2-8-directive-binding.md) na stránce 32.  
  
 V následujícím příkladu volání z *hlavní* k *sub2* kompatibilní protože **barrier** (v *sub3*) váže k oblasti paralelní v *sub2*. Volání z *hlavní* k *sub1* kompatibilní protože **barrier** váže k oblasti paralelní v podprogramu *sub2*.  Volání z *hlavní* k *sub3* kompatibilní protože **bariéry** nemá vazbu na libovolné paralelní oblasti a bude ignorována. Všimněte si také, že **barrier** synchronizuje pouze týmem vláken v oblasti nadřazených paralelní a ne všechny vláken vytvořené v *sub1*.  
  
```  
int main()  
{  
    sub1(2);  
    sub2(2);  
    sub3(2);  
}  
  
void sub1(int n)  
{  
    int i;  
    #pragma omp parallel private(i) shared(n)  
    {  
        #pragma omp for  
        for (i=0; i<n; i++)  
            sub2(i);  
    }  
}  
  
void sub2(int k)  
{  
     #pragma omp parallel shared(k)  
     sub3(k);  
}  
  
void sub3(int n)  
{  
    work(n);  
    #pragma omp barrier  
    work(n);  
}  
```