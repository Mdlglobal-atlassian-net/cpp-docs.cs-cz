---
title: A.19   Příklady nesprávného vnoření direktiv pro sdílení práce
ms.date: 11/04/2016
ms.assetid: 906e900d-9259-44d6-a095-c1ba9135d269
ms.openlocfilehash: 5be09dd3282260dabc2ef30dafc249539d6a6418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501943"
---
# <a name="a19---examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19   Příklady nesprávného vnoření direktiv pro sdílení práce

Příklady v této části ilustrují direktiv vnoření pravidla. Další informace o vnořování direktiv, naleznete v tématu [části 2.9](../../parallel/openmp/2-9-directive-nesting.md) na stránce 33.

V následujícím příkladu je nekompatibilní protože vnitřní a vnější `for` direktivy jsou vnořené a vytvořit vazbu na stejný `parallel` – direktiva:

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

Následující verze dynamicky vnořené v předchozím příkladu je také nedodržující předpisy:

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

V následujícím příkladu je nekompatibilní vzhledem k tomu, `for` a `single` direktivy jsou vnořené a jejich připojení ke stejné paralelní oblasti:

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

V následujícím příkladu je nekompatibilní protože `barrier` direktivy uvnitř `for` může vést k zablokování:

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

V následujícím příkladu je nekompatibilní vzhledem k tomu, `barrier` výsledkem zablokování skutečnost, že pouze jedno vlákno najednou můžete zadat důležité části:

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

V následujícím příkladu je nekompatibilní vzhledem k tomu, `barrier` výsledkem zablokování skutečnost, že provede pouze jedno vlákno `single` části:

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