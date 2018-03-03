---
title: "Příklady A.19 zobrazuje nesprávné vnořování direktiv sdílení práce | Microsoft Docs"
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
ms.assetid: 906e900d-9259-44d6-a095-c1ba9135d269
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8a3f8a4e1ca62a77c16dafedd0921ca842d7a048
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="a19---examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19   Příklady nesprávného vnoření direktiv pro sdílení práce
Příklady v této části ilustrují direktivy vnoření pravidla. Další informace o vnořování direktiv najdete v tématu [části 2.9](../../parallel/openmp/2-9-directive-nesting.md) na stránce 33.  
  
 Následující příklad je nekompatibilní protože vnitřní a vnější `for` direktivy jsou vnořeny a vytvořit vazbu na stejný `parallel` – direktiva:  
  
```  
void wrong1(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
      int i, j;  
      #pragma omp for  
      for (i=0; i<n; i++) {  
          #pragma omp for  
              for (j=0; j<n; j++)  
                 work(i, j);  
     }  
   }  
}  
```  
  
 Následující dynamicky vnořené verze v předchozím příkladu je taky nesplňujících požadavky:  
  
```  
void wrong2(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++)  
        work1(i, n);  
  }  
}  
  
void work1(int i, int n)  
{  
  int j;  
  #pragma omp for  
    for (j=0; j<n; j++)  
      work2(i, j);  
}  
```  
  
 Následující příklad je nekompatibilní protože `for` a `single` jsou vnořené direktivy a jejich vazby do stejné oblasti paralelní:  
  
```  
void wrong3(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++) {  
        #pragma omp single  
          work(i);  
      }  
  }  
}  
```  
  
 Následující příklad je nekompatibilní protože `barrier` direktivy uvnitř `for` může mít za následek zablokování:  
  
```  
void wrong4(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++) {  
        work1(i);  
        #pragma omp barrier  
        work2(i);  
      }  
  }  
}  
```  
  
 Následující příklad je nekompatibilní protože `barrier` výsledkem zablokování vzhledem k tomu, že pouze jedno vlákno najednou můžete zadat v kritické části:  
  
```  
void wrong5()  
{  
  #pragma omp parallel  
  {  
    #pragma omp critical  
    {  
       work1();  
       #pragma omp barrier  
       work2();  
    }  
  }  
}  
```  
  
 Následující příklad je nekompatibilní protože `barrier` výsledkem zablokování vzhledem k tomu, že provádí pouze jedno vlákno `single` části:  
  
```  
void wrong6()  
{  
  #pragma omp parallel  
  {  
    setup();  
    #pragma omp single  
    {  
      work1();  
      #pragma omp barrier  
      work2();  
    }  
    finish();  
  }  
}  
```