---
title: CComCriticalSection – třída
ms.date: 11/04/2016
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
ms.openlocfilehash: ee4ce32ed4ae04bc3b390af5cf104b8a0af599f8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497284"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection – třída

Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritického oddílu.

## <a name="syntax"></a>Syntaxe

```
class CComCriticalSection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComCriticalSection:: init](#init)|Vytvoří a inicializuje objekt kritického oddílu.|
|[CComCriticalSection::Lock](#lock)|Získá vlastnictví objektu kritické části.|
|[CComCriticalSection:: Term](#term)|Uvolní systémové prostředky používané objektem kritické části.|
|[CComCriticalSection:: Unlock](#unlock)|Uvolňuje vlastnictví objektu kritické části.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|Objekt CRITICAL_SECTION.|

## <a name="remarks"></a>Poznámky

`CComCriticalSection`je podobná třídě [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), s tím rozdílem, že je nutné explicitně inicializovat a uvolnit kritickou část.

Obvykle se používá `CComCriticalSection` přes název **typedef** [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Tento název odkazuje `CComCriticalSection` na použití [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) .

Pro bezpečnější způsob použití této třídy, než volání `Lock` a `Unlock` přímo, se podívejte na [třídu CComCritSecLock](../../atl/reference/ccomcritseclock-class.md) .

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore. h

##  <a name="ccomcriticalsection"></a>CComCriticalSection::CComCriticalSection

Konstruktor

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Poznámky

Nastaví datový člen [m_sec](#m_sec) na hodnotu null.

##  <a name="init"></a>CComCriticalSection:: init

Zavolá funkci Win32 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), která inicializuje objekt kritické části obsažený v datovém členu [m_sec](#m_sec) .

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu, E_OUTOFMEMORY nebo E_FAIL při selhání.

##  <a name="lock"></a>CComCriticalSection:: Lock

Zavolá funkci Win32 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), která počká, dokud vlákno nemůže převzít vlastnictví objektu kritického oddílu obsaženého v datovém členu [m_sec](#m_sec) .

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu, E_OUTOFMEMORY nebo E_FAIL při selhání.

### <a name="remarks"></a>Poznámky

Objekt kritického oddílu musí být nejdříve inicializován voláním metody [init](#init) . Po dokončení provádění chráněného kódu vlákno musí volat metodu [Unlock](#unlock) , aby bylo možné uvolnit vlastnictví kritické části.

##  <a name="m_sec"></a>CComCriticalSection::m_sec

Obsahuje objekt kritického oddílu, který je používán všemi `CComCriticalSection` metodami.

```
CRITICAL_SECTION m_sec;
```

##  <a name="term"></a>CComCriticalSection:: Term

Zavolá funkci Win32 [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), která uvolní všechny prostředky používané objektem důležité části obsaženým v datovém členu [m_sec](#m_sec) .

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Po `Term` zavolání již není možné použít pro synchronizaci oddíl Critical.

##  <a name="unlock"></a>CComCriticalSection:: Unlock

Volá funkci Win32 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), která uvolňuje vlastnictví objektu kritického oddílu obsaženého v datovém členu [m_sec](#m_sec) .

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Pro první získání vlastnictví vlákno musí volat metodu [Lock](#lock) . Každé volání `Lock` vyžaduje odpovídající `Unlock` volání k uvolnění vlastnictví kritické části.

## <a name="see-also"></a>Viz také:

[CComFakeCriticalSection – třída](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[CComCritSecLock – třída](../../atl/reference/ccomcritseclock-class.md)
