---
title: _CRT_DISABLE_PERFCRIT_LOCKS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
dev_langs:
- C++
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd01cbddac128e2369971d07320ff95986d822f9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053892"
---
# <a name="crtdisableperfcritlocks"></a>_CRT_DISABLE_PERFCRIT_LOCKS

Zakáže uzamčení kritickém pro výkon v vstupně-výstupních operací.

## <a name="syntax"></a>Syntaxe

```
#define _CRT_DISABLE_PERFCRIT_LOCKS
```

## <a name="remarks"></a>Poznámky

Definování tento symbol může zlepšit výkon vstupně-výstupní aplikace s jedním vláknem vynucením všechny vstupně-výstupních operací předpokládat, že vstupně-výstupních operací modelu s jedním vláknem. Další informace najdete v tématu [výkon vícevláknových knihoven](../c-runtime-library/multithreaded-libraries-performance.md).

## <a name="see-also"></a>Viz také

[Globální konstanty](../c-runtime-library/global-constants.md)