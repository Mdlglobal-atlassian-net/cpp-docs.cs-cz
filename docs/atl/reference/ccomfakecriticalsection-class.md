---
title: CcomfakeCriticalSekce třídy
ms.date: 11/04/2016
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
ms.openlocfilehash: 4a5b9ba3551397a9c3d59a343e9c6b55b1c1207e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327844"
---
# <a name="ccomfakecriticalsection-class"></a>CcomfakeCriticalSekce třídy

Tato třída poskytuje stejné metody jako [CComCriticalSection,](../../atl/reference/ccomcriticalsection-class.md) ale neposkytuje kritický oddíl.

## <a name="syntax"></a>Syntaxe

```
class CComFakeCriticalSection
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComFakeCriticalSekce::Init](#init)|Neprovede žádnou akci, protože neexistuje žádná kritická část.|
|[CcomfakeCriticalSection::Zámek](#lock)|Neprovede žádnou akci, protože neexistuje žádná kritická část.|
|[CcomfakeCriticalSekce::Termín](#term)|Neprovede žádnou akci, protože neexistuje žádná kritická část.|
|[CcomfakeCriticalSection::Odemknout](#unlock)|Neprovede žádnou akci, protože neexistuje žádná kritická část.|

## <a name="remarks"></a>Poznámky

`CComFakeCriticalSection`zrcadlí metody nalezené v [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Nicméně, `CComFakeCriticalSection` neposkytuje kritický oddíl; proto jeho metody nedělají nic.

Obvykle se používá `CComFakeCriticalSection` prostřednictvím `typedef` názvu, `CriticalSection`nebo `AutoCriticalSection` . Při použití [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), oba tyto `typedef` názvy odkaz `CComFakeCriticalSection`. Při použití [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), které odkazují `CComCriticalSection` [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) a , příslušně.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="ccomfakecriticalsectioninit"></a><a name="init"></a>CComFakeCriticalSekce::Init

Neprovede žádnou akci, protože neexistuje žádná kritická část.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

## <a name="ccomfakecriticalsectionlock"></a><a name="lock"></a>CcomfakeCriticalSection::Zámek

Neprovede žádnou akci, protože neexistuje žádná kritická část.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

## <a name="ccomfakecriticalsectionterm"></a><a name="term"></a>CcomfakeCriticalSekce::Termín

Neprovede žádnou akci, protože neexistuje žádná kritická část.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

## <a name="ccomfakecriticalsectionunlock"></a><a name="unlock"></a>CcomfakeCriticalSection::Odemknout

Neprovede žádnou akci, protože neexistuje žádná kritická část.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
