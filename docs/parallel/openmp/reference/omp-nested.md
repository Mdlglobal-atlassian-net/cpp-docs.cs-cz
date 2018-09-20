---
title: OMP_NESTED | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NESTED
dev_langs:
- C++
helpviewer_keywords:
- OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c90878ce96cf1639c983be899ba13eccf1f040e8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376528"
---
# <a name="ompnested"></a>OMP_NESTED

Určuje, zda je vnořené paralelismu povoleno, není-li povolit nebo zakázat pomocí vnořených paralelismu `omp_set_nested`.

## <a name="syntax"></a>Syntaxe

```
set OMP_NESTED[=TRUE | =FALSE]
```

## <a name="remarks"></a>Poznámky

`OMP_NESTED` Proměnné prostředí můžete přepsat [omp_set_nested –](../../../parallel/openmp/reference/omp-set-nested.md) funkce.

Je výchozí hodnotu v implementaci Visual C++ OpenMP standard `OMP_DYNAMIC=FALSE`.

Další informace najdete v tématu [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

## <a name="example"></a>Příklad

Nastaví zadáním následujícího příkazu `OMP_NESTED` proměnné prostředí na hodnotu TRUE:

```
set OMP_NESTED=TRUE
```

Následující příkaz zobrazí aktuální nastavení `OMP_NESTED` proměnné prostředí:

```
set OMP_NESTED
```

## <a name="see-also"></a>Viz také

[Proměnné prostředí](../../../parallel/openmp/reference/openmp-environment-variables.md)