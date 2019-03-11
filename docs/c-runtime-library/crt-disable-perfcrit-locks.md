---
title: _CRT_DISABLE_PERFCRIT_LOCKS
ms.date: 11/04/2016
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
ms.openlocfilehash: b6f4d8dee5577e88aa59af9bff017aab0c7eef89
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740266"
---
# <a name="crtdisableperfcritlocks"></a>_CRT_DISABLE_PERFCRIT_LOCKS

Zakáže uzamčení kritickém pro výkon v vstupně-výstupních operací.

## <a name="syntax"></a>Syntaxe

```
#define _CRT_DISABLE_PERFCRIT_LOCKS
```

## <a name="remarks"></a>Poznámky

Definování tento symbol může zlepšit výkon vstupně-výstupní aplikace s jedním vláknem vynucením všechny vstupně-výstupních operací předpokládat, že vstupně-výstupních operací modelu s jedním vláknem. Další informace najdete v tématu [výkon vícevláknových knihoven](../c-runtime-library/multithreaded-libraries-performance.md).

## <a name="see-also"></a>Viz také:

[Globální konstanty](../c-runtime-library/global-constants.md)
