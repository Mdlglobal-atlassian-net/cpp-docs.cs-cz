---
title: OpenMP – klauzule | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afd0a8f66f9b0d027671629998597955b3aa69e9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378323"
---
# <a name="openmp-clauses"></a>OpenMP – klauzule

Obsahuje odkazy na použité v rozhraní API OpenMP – klauzule.

Jazyk Visual C++ podporuje následující klauzule OpenMP:

|Klauzule|Popis|
|------------|-----------------|
|[copyin](../../../parallel/openmp/reference/copyin.md)|Umožňuje vláken pro přístup k hodnotě hlavní vlákno, [threadprivate](../../../parallel/openmp/reference/threadprivate.md) proměnné.|
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|Určuje, že jeden nebo více proměnných by měl být sdílena mezi všemi vlákny.|
|[default](../../../parallel/openmp/reference/default-openmp.md)|Určuje chování bez ohledu na obor proměnné v paralelní oblasti.|
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|Určuje, že každé vlákno má svoji vlastní instanci proměnné. proto, že proměnné by měl inicializovat pomocí hodnoty proměnné, protože existuje před paralelní konstrukce.|
|[if](../../../parallel/openmp/reference/if-openmp.md)|Určuje, zda smyčku budou spuštěny paralelně nebo postupně.|
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|Určuje, že verze nadřazeného objektu context proměnné je nastavena na soukromou verzi podle toho, která vlákno spustí poslední iterace (konstrukci smyčky for-loop) nebo poslední část (#pragma oddílů).|
|[nowait](../../../parallel/openmp/reference/nowait.md)|Přepíše překážkou implicitní v direktivě.|
|[num_threads](../../../parallel/openmp/reference/num-threads.md)|Nastaví počet vláken v týmu vlákna.|
|[Řazení](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|Vyžaduje na paralelní [pro](../../../parallel/openmp/reference/for-openmp.md) příkaz Pokud [seřazené](../../../parallel/openmp/reference/ordered-openmp-directives.md) – direktiva se má použít ve smyčce.|
|[private](../../../parallel/openmp/reference/private-openmp.md)|Určuje, že každé vlákno má svoji vlastní instanci proměnné.|
|[reduction](../../../parallel/openmp/reference/reduction.md)|Určuje, že jeden nebo více proměnných, které jsou privátní pro každé vlákno je předmětem operaci snížení na konci paralelní oblasti.|
|[schedule](../../../parallel/openmp/reference/schedule.md)|Platí pro [pro](../../../parallel/openmp/reference/for-openmp.md) směrnice.|
|[Sdílet](../../../parallel/openmp/reference/shared-openmp.md)|Určuje, že jeden nebo více proměnných by měl být sdílena mezi všemi vlákny.|

## <a name="see-also"></a>Viz také

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)<br/>
[Direktivy](../../../parallel/openmp/reference/openmp-directives.md)