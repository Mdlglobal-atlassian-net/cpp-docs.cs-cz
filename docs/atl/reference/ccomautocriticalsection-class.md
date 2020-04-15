---
title: Třída CComautocriticalsection
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 8cbf08082fd24ef2cf0e8794e2944a799baec084
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321095"
---
# <a name="ccomautocriticalsection-class"></a>Třída CComautocriticalsection

`CComAutoCriticalSection`poskytuje metody pro získání a uvolnění vlastnictví objektu kritické části.

## <a name="syntax"></a>Syntaxe

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CcomautocriticalSection::ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection:](#ccomautocriticalsection)|Konstruktor|
|[CcomautocriticalSection::~ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection::~ccomautocriticalsection](#dtor)|Destruktor.|

## <a name="remarks"></a>Poznámky

`CComAutoCriticalSection`je podobná třídě [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), s výjimkou `CComAutoCriticalSection` automatické inicializuje objekt kritického řezu v konstruktoru.

Obvykle se používá `CComAutoCriticalSection` prostřednictvím `typedef` názvu [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Tento název `CComAutoCriticalSection` odkazuje při použití [CComMultiThreadModel.](../../atl/reference/ccommultithreadmodel-class.md)

Metody `Init` `Term` a z [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) nejsou k dispozici při použití této třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Ccomcriticalsekce](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="ccomautocriticalsection"></a>CcomautocriticalSection::ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection:

Konstruktor

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Poznámky

Volá funkci Win32 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), která inicializuje objekt kritického oddílu.

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="dtor"></a>CcomautocriticalSection::~ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection ccomautocriticalsection::~ccomautocriticalsection

Destruktor.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor volá [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), který uvolní všechny systémové prostředky používané objektem kritické části.

## <a name="see-also"></a>Viz také

[CcomfakeCriticalSekce třídy](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)
