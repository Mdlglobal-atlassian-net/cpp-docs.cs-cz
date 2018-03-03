---
title: "2.7.1 threadprivate – direktiva | Microsoft Docs"
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
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 22bb7f477be397f01ee4bd82f472ff26a26ce811
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="271-threadprivate-directive"></a>2.7.1 threadprivate – direktiva
`threadprivate` – Direktiva umožňuje pojmenované rozsah souboru, obor názvů nebo statický rozsah bloku proměnné zadané v *seznamu proměnné* privátní na vlákno. *Proměnná seznamu* je textový soubor s oddělovači seznam proměnných, které nemají typ neúplné. Syntaxe `threadprivate` – Direktiva vypadá takto:  
  
```  
#pragma omp threadprivate(variable-list) new-line  
```  
  
 Každá kopie `threadprivate` proměnné je inicializován jednou, neurčené okamžiku v programu před první odkaz na tuto kopii a obvyklým způsobem (tj. jako hlavní kopii by jde inicializovat na sériové provádění programu). Všimněte si, že pokud objekt odkazuje explicitní inicializátor `threadprivate` proměnné a hodnotu objektu je upravena před první odkaz na kopii proměnnou a pak toto chování neurčená.  
  
 Jako s soukromé proměnné, vlákno nesmí odkazovat na jiné vlákno kopii `threadprivate` objektu. Během sériové oblasti a hlavní oblasti programu odkazy bude hlavní vlákno kopii objektu.  
  
 Po provedení první paralelní oblast, data v `threadprivate` objekty záruku, že k zachování jen pokud dynamická vláken mechanismus je zakázané, a pokud počet vláken, zůstane nezměněno pro všechny paralelní oblasti.  
  
 Omezení, které mají `threadprivate` – direktiva jsou následující:  
  
-   A `threadprivate` směrnice pro proměnné rozsah souboru nebo oboru názvů musí být uvedena mimo žádná definice nebo deklarace a musí předcházet lexikálně všechny odkazy na všechny proměnné ve svém seznamu.  
  
-   Každou proměnnou v *seznamu proměnné* z `threadprivate` směrnice v souboru nebo oboru názvů oboru musí odkazovat na deklarace proměnné v oboru souboru nebo oboru názvů, který lexikálně předchází direktivu.  
  
-   A `threadprivate` směrnice pro proměnné statický rozsah bloku musí být v rozsahu proměnné a není ve vnořených oboru. Direktiva lexikálně musí předcházet všechny odkazy na všechny proměnné ve svém seznamu.  
  
-   Každou proměnnou v *seznamu proměnné* z `threadprivate` – direktiva v oboru bloku musí odkazovat na deklarace proměnné ve stejném oboru lexikálně předcházejícího direktivu. Deklarace proměnné, musíte použít statické – specifikátor třídy úložiště.  
  
-   Jestliže se v proměnné `threadprivate` direktivy v jednotce jeden překladu, musí být zadaná v `threadprivate` direktivy v každou překlad jednotku, ve kterém je deklarovaná.  
  
-   A `threadprivate` proměnné nesmí zobrazí všechny klauzulí s výjimkou `copyin`, `copyprivate`, `schedule`, `num_threads`, nebo **Pokud** klauzule.  
  
-   Adresa `threadprivate` proměnné není konstantu adresu.  
  
-   A `threadprivate` proměnná nesmí mít typ neúplné nebo typu odkazu.  
  
-   A `threadprivate` proměnná s typu bez POD třídy, pokud je deklarovaný s inicializátoru explicitní, musí mít k přístupný, jednoznačným kopírovacího konstruktoru.  
  
 Následující příklad ilustruje, jak úprava proměnné, která se zobrazí v inicializátoru může způsobit neurčené chování a také jak se vyhnout tomuto problému s použitím pomocného objektu a konstruktor copy.  
  
```  
int x = 1;  
T a(x);  
const T b_aux(x); /* Capture value of x = 1 */  
T b(b_aux);  
#pragma omp threadprivate(a, b)  
  
void f(int n) {  
   x++;  
   #pragma omp parallel for  
   /* In each thread:  
   * Object a is constructed from x (with value 1 or 2?)  
   * Object b is copy-constructed from b_aux  
   */  
   for (int i=0; i<n; i++) {  
      g(a, b); /* Value of a is unspecified. */  
   }  
}  
```  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   Dynamické vláken, najdete v části [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.  
  
-   `OMP_DYNAMIC`proměnné, naleznete v prostředí [části 4.3](../../parallel/openmp/4-3-omp-dynamic.md) na stránce 49.