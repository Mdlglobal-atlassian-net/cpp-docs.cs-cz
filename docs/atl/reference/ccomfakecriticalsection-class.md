---
title: Ccomfakecriticalsection – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48b120b7be3e605b6ed2619cbd71011b0a693bdc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757273"
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

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
