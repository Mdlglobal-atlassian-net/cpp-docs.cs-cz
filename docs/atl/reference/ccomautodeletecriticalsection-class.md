---
title: CComAutoDeleteCriticalSection Class
ms.date: 11/04/2016
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
ms.openlocfilehash: d479adce489e0329be3a93b55a70aa3e58a0e038
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265129"
---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection Class

Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritický oddíl.

## <a name="syntax"></a>Syntaxe

```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```

## <a name="remarks"></a>Poznámky

`CComAutoDeleteCriticalSection` je odvozena od třídy [ccomsafedeletecriticalsection –](../../atl/reference/ccomsafedeletecriticalsection-class.md). Ale `CComAutoDeleteCriticalSection` přepsání [termín](ccomsafedeletecriticalsection-class.md#term) metodu **privátní** přístup, který vynutí interní paměť vyčištění každý pouze pokud dostanou mimo rozsah nebo jsou explicitně odstranit z instance této třídy paměť.

Tato třída představuje žádné další metody v její základní třídě. Zobrazit [ccomsafedeletecriticalsection –](../../atl/reference/ccomsafedeletecriticalsection-class.md) a [ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md) Další informace o kritický oddíl pomocné třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)

`CComAutoDeleteCriticalSection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="see-also"></a>Viz také:

[CComSafeDeleteCriticalSection – třída](../../atl/reference/ccomsafedeletecriticalsection-class.md)<br/>
[CComAutoCriticalSection – třída](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
