---
title: Ccomfakecriticalsection – třída
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
ms.openlocfilehash: 39a9859380eba1b72768234eb8f43d80fca0143f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302140"
---
# <a name="ccomfakecriticalsection-class"></a>Ccomfakecriticalsection – třída

Tato třída poskytuje metody stejný jako [ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md) ale neposkytuje kritický oddíl.

## <a name="syntax"></a>Syntaxe

```
class CComFakeCriticalSection
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComFakeCriticalSection::Init](#init)|Nemá žádný účinek, protože neexistuje žádný kritický oddíl.|
|[CComFakeCriticalSection::Lock](#lock)|Nemá žádný účinek, protože neexistuje žádný kritický oddíl.|
|[CComFakeCriticalSection::Term](#term)|Nemá žádný účinek, protože neexistuje žádný kritický oddíl.|
|[CComFakeCriticalSection::Unlock](#unlock)|Nemá žádný účinek, protože neexistuje žádný kritický oddíl.|

## <a name="remarks"></a>Poznámky

`CComFakeCriticalSection` Zrcadlí metody v [ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md). Ale `CComFakeCriticalSection` neposkytuje kritický oddíl; proto její metody Neprovádět žádnou akci.

Obvykle použijete `CComFakeCriticalSection` prostřednictvím `typedef` název buď `AutoCriticalSection` nebo `CriticalSection`. Při použití [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [ccommultithreadmodelnocs –](../../atl/reference/ccommultithreadmodelnocs-class.md), obě tyto `typedef` názvy odkaz `CComFakeCriticalSection`. Při použití [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), které odkazují [ccomautocriticalsection –](../../atl/reference/ccomautocriticalsection-class.md) a `CComCriticalSection`v uvedeném pořadí.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

##  <a name="init"></a>  CComFakeCriticalSection::Init

Nemá žádný účinek, protože neexistuje žádný kritický oddíl.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

##  <a name="lock"></a>  CComFakeCriticalSection::Lock

Nemá žádný účinek, protože neexistuje žádný kritický oddíl.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

##  <a name="term"></a>  CComFakeCriticalSection::Term

Nemá žádný účinek, protože neexistuje žádný kritický oddíl.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

##  <a name="unlock"></a>  CComFakeCriticalSection::Unlock

Nemá žádný účinek, protože neexistuje žádný kritický oddíl.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
