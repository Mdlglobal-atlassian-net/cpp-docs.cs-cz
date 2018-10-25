---
title: Ccomautodeletecriticalsection – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 327c5fdcdc2a73cc8ee662ed71736f848ccd2e9d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066341"
---
# <a name="ccomautodeletecriticalsection-class"></a>Ccomautodeletecriticalsection – třída

Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritický oddíl.

## <a name="syntax"></a>Syntaxe

```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```

## <a name="remarks"></a>Poznámky

`CComAutoDeleteCriticalSection` je odvozena od třídy [ccomsafedeletecriticalsection –](../../atl/reference/ccomsafedeletecriticalsection-class.md). Ale `CComAutoDeleteCriticalSection` přepsání [termín](ccomsafedeletecriticalsection-class.md#term) metodu **privátní** přístup, který vynutí interní paměť vyčištění každý pouze pokud dostanou mimo rozsah nebo jsou explicitně odstranit z instance této třídy paměť.

Tato třída představuje žádné další metody v její základní třídě. Zobrazit [ccomsafedeletecriticalsection –](../../atl/reference/ccomsafedeletecriticalsection-class.md) a [ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md) Další informace o kritický oddíl pomocné třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md)

[Ccomsafedeletecriticalsection –](../../atl/reference/ccomsafedeletecriticalsection-class.md)

`CComAutoDeleteCriticalSection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="see-also"></a>Viz také

[CComSafeDeleteCriticalSection – třída](../../atl/reference/ccomsafedeletecriticalsection-class.md)<br/>
[CComAutoCriticalSection – třída](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
