---
title: OMP_DYNAMIC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_DYNAMIC
dev_langs:
- C++
helpviewer_keywords:
- OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b02a2a4d660057ab83da39add7fd32bcff3e6d90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392135"
---
# <a name="ompdynamic"></a>OMP_DYNAMIC

Určuje, zda OpenMP běhu můžete upravit počet vláken v paralelní oblasti.

## <a name="syntax"></a>Syntaxe

```
set OMP_DYNAMIC[=TRUE | =FALSE]
```

## <a name="remarks"></a>Poznámky

`OMP_DYNAMIC` Proměnné prostředí můžete přepsat [omp_set_dynamic –](../../../parallel/openmp/reference/omp-set-dynamic.md) funkce.

Je výchozí hodnotu v implementaci Visual C++ OpenMP standard `OMP_DYNAMIC=FALSE`.

Další informace najdete v tématu [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

## <a name="example"></a>Příklad

Nastaví zadáním následujícího příkazu `OMP_DYNAMIC` proměnné prostředí na hodnotu TRUE:

```
set OMP_DYNAMIC=TRUE
```

Následující příkaz zobrazí aktuální nastavení `OMP_DYNAMIC` proměnné prostředí:

```
set OMP_DYNAMIC
```

## <a name="see-also"></a>Viz také

[Proměnné prostředí](../../../parallel/openmp/reference/openmp-environment-variables.md)