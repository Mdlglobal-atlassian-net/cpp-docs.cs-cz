---
title: OMP_SCHEDULE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_SCHEDULE
dev_langs:
- C++
helpviewer_keywords:
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 507067be30db019536ef222a62335244eabfaada
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413858"
---
# <a name="ompschedule"></a>OMP_SCHEDULE

Upravuje chování [plán](../../../parallel/openmp/reference/schedule.md) klauzule při `schedule(runtime)` je zadán v `for` nebo `parallel for` – direktiva.

## <a name="syntax"></a>Syntaxe

```
set OMP_SCHEDULE[=type[,size]]
```

## <a name="arguments"></a>Arguments

*Velikost*<br/>
(Volitelné) Určuje velikost iterací. `size` Musí být kladné celé číslo. Výchozí hodnota je 1, kromě případů, kdy `type` je statická. Není platná v případě `type` je `runtime`.

*Typ*<br/>
Typ plánování:

- `dynamic`

- `guided`

- `runtime`

- `static`

## <a name="remarks"></a>Poznámky

Je výchozí hodnotu v implementaci Visual C++ OpenMP standard `OMP_SCHEDULE=static,0`.

Další informace najdete v tématu [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

## <a name="example"></a>Příklad

Nastaví zadáním následujícího příkazu **OMP_SCHEDULE** proměnné prostředí:

```
set OMP_SCHEDULE="guided,2"
```

Následující příkaz zobrazí aktuální nastavení **OMP_SCHEDULE** proměnné prostředí:

```
set OMP_SCHEDULE
```

## <a name="see-also"></a>Viz také

[Proměnné prostředí](../../../parallel/openmp/reference/openmp-environment-variables.md)