---
title: A.9 Použití direktiv single | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a3a201450d54355aa96f0ea712ad9fa0f70f63f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448087"
---
# <a name="a9---using-single-directives"></a>A.9   Použití direktiv single

Následující příklad ukazuje, `single` – direktiva ([části 2.4.3](../../parallel/openmp/2-4-3-single-construct.md) na stránce 15). V tomto příkladu pouze jedno vlákno (obvykle první vlákno, které nalezne `single` – direktiva) zobrazí zpráva o průběhu. Uživatel nesmí jakkoli jak pro vlákno, které se spustí `single` oddílu. Přeskočí všechny ostatní vlákna `single` části a zastavit bariéře na konci `single` vytvořit. Pokud se ostatní vlákna bez čekání na vlákno prováděno Přejít `single` části `nowait` klauzule můžete nastavit na `single` – direktiva.

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