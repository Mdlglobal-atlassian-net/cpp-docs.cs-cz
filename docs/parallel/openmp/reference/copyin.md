---
title: copyin | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- copyin
dev_langs:
- C++
helpviewer_keywords:
- copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 424bb8eaa41e3bbb0cf697df108adcef116e1b04
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379577"
---
# <a name="copyin"></a>copyin

Umožňuje vláken pro přístup k hodnotě hlavní vlákno, [threadprivate](../../../parallel/openmp/reference/threadprivate.md) proměnné.

## <a name="syntax"></a>Syntaxe

```
copyin(var)
```

## <a name="parameters"></a>Parametry

*var*<br/>
`threadprivate` Proměnné, která bude inicializován hodnotou proměnné v hlavním vlákně, protože existuje před paralelní konstrukce.

## <a name="remarks"></a>Poznámky

`copyin` platí pro následující direktivy:

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [Oddíly](../../../parallel/openmp/reference/sections-openmp.md)

Další informace najdete v tématu [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md).

## <a name="example"></a>Příklad

Zobrazit [threadprivate](../../../parallel/openmp/reference/threadprivate.md) pro příklad použití `copyin`.

## <a name="see-also"></a>Viz také

[Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)