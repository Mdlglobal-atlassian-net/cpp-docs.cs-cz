---
title: 2.7.1 threadprivate – direktiva | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31c9c70940b558d0b4cc3f77677665235417694d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398141"
---
# <a name="271-threadprivate-directive"></a>2.7.1 threadprivate – direktiva

`threadprivate` – Direktiva vytvoří pojmenovaného rozsahu souboru, rozsahu oboru názvů nebo zadané v proměnné statického oboru bloku *seznamu proměnné* privátní ve vlákně. *seznamu proměnné* je čárkou oddělený seznam proměnných, které nemají neúplný typ. Syntaxe `threadprivate` direktivy je následující:

```
#pragma omp threadprivate(variable-list) new-line
```

Každá kopie `threadprivate` proměnná je inicializována jednou, neurčené okamžiku v programu před první odkaz na tuto kopii a obvyklým způsobem (tj. jako hlavní kopie by být inicializovány v sériové provádění programu). Všimněte si, že pokud je objekt odkazuje na explicitní inicializátoru `threadprivate` proměnné a hodnoty objektu se upraví před první odkaz na kopii proměnné a pak chování není zadána.

Jak se žádné soukromé proměnné vlákno nesmí odkazovat na jiné vlákno kopii `threadprivate` objektu. Během sériových oblastech a hlavní oblasti program bude odkazy na hlavní podproces kopii objektu.

Po provedení první paralelní oblasti, data v `threadprivate` objekty je zaručeno, že zachování pouze pokud dynamický vlákna mechanismus je zakázané, a pokud počet vláken zůstávají beze změn pro všechny paralelní oblasti.

Omezení týkající `threadprivate` směrnice jsou následující:

- A `threadprivate` směrnice pro proměnné s rozsahem souboru nebo rozsahu oboru názvů musí být uvedena mimo všechny definice nebo deklarace a musí předcházet lexikálně všechny odkazy na některé z proměnné ve svém seznamu.

- Každou proměnnou v *seznamu proměnné* z `threadprivate` – direktiva v oboru souboru nebo oboru názvů musí odkazovat na deklaraci proměnné v oboru souboru nebo oboru názvů, který lexikálně předchází směrnice.

- A `threadprivate` směrnice pro proměnné, statické rozsahu bloku musí být uvedena v oboru proměnné a nejsou ve vnořeném oboru. Direktiva lexikálně musí předcházet všechny odkazy na některé z proměnné ve svém seznamu.

- Každou proměnnou v *seznamu proměnné* z `threadprivate` – direktiva v rozsahu bloku musí odkazovat na deklaraci proměnné ve stejném oboru, který předchází lexikálně směrnice. Deklarace proměnné musí používat specifikátor statickou třídu úložiště.

- Je-li proměnná zadána v `threadprivate` direktiv v jednotce překladu. jeden, musí se zadat v `threadprivate` direktiv v každé jednotce překladu, ve kterém je deklarována.

- A `threadprivate` proměnné nesmí objevit všechny klauzule except `copyin`, `copyprivate`, `schedule`, `num_threads`, nebo **Pokud** klauzuli.

- Adresa `threadprivate` proměnná není konstantu adresu.

- A `threadprivate` proměnná nesmí být neúplný typ nebo typ odkazu.

- A `threadprivate` proměnná typu třídy než POD musí být přístupná a jednoznačná kopírovací konstruktor, pokud je deklarovaná s inicializátorem explicitní.

Následující příklad ukazuje, jak úpravy, které se zobrazí v inicializátoru proměnné může způsobit neurčené chování a také jak se vyhnout tomuto problému s použitím pomocného objektu a konstruktor kopírování.

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

- Dynamické vlákna, naleznete v tématu [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.

- `OMP_DYNAMIC` Proměnná, viz prostředí [části 4.3](../../parallel/openmp/4-3-omp-dynamic.md) na stránce 49.