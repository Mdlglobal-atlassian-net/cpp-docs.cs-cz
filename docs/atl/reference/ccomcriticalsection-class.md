---
title: Třída CComCriticalSection
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
ms.openlocfilehash: f3991d217fbc201bd428ed2522a5c4c25e074928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327971"
---
# <a name="ccomcriticalsection-class"></a>Třída CComCriticalSection

Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritické části.

## <a name="syntax"></a>Syntaxe

```
class CComCriticalSection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CcomcriticalSection::CcomcriticalSection](#ccomcriticalsection)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComCriticalSekce::Init](#init)|Vytvoří a inicializuje objekt kritického řezu.|
|[CcomCriticalSection::Zámek](#lock)|Získá vlastnictví objektu kritické části.|
|[CcomcriticalSection::Termín](#term)|Uvolní systémové prostředky používané objektem kritické části.|
|[CcomCriticalSection::Odemknout](#unlock)|Uvolní vlastnictví objektu kritické části.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CComCriticalSekce::m_sec](#m_sec)|Objekt CRITICAL_SECTION.|

## <a name="remarks"></a>Poznámky

`CComCriticalSection`je podobný třídě [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), s tím rozdílem, že je nutné explicitně inicializovat a uvolnit kritický oddíl.

Obvykle se používá `CComCriticalSection` prostřednictvím **typedef** název [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Tento název `CComCriticalSection` odkazuje při použití [CComMultiThreadModel.](../../atl/reference/ccommultithreadmodel-class.md)

Viz [CComCritSecLock Třídy](../../atl/reference/ccomcritseclock-class.md) pro bezpečnější způsob, `Lock` `Unlock` jak používat tuto třídu než volání a přímo.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="ccomcriticalsectionccomcriticalsection"></a><a name="ccomcriticalsection"></a>CcomcriticalSection::CcomcriticalSection

Konstruktor

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Poznámky

Nastaví datový člen [m_sec](#m_sec) na hodnotu NULL.

## <a name="ccomcriticalsectioninit"></a><a name="init"></a>CComCriticalSekce::Init

Volá funkci Win32 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), která inicializuje objekt kritické části obsažený v [datovém](#m_sec) m_sec.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch, E_OUTOFMEMORY nebo E_FAIL na neúspěch.

## <a name="ccomcriticalsectionlock"></a><a name="lock"></a>CcomCriticalSection::Zámek

Volá win32 funkce [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), který čeká, dokud vlákno může převzít vlastnictví objektu kritické části obsažené v [m_sec](#m_sec) datový člen.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch, E_OUTOFMEMORY nebo E_FAIL na neúspěch.

### <a name="remarks"></a>Poznámky

Objekt kritické části musí být nejprve inicializován voláním metody [Init.](#init) Po dokončení provádění chráněného kódu musí vlákno volat [Unlock,](#unlock) aby uvolnilo vlastnictví kritické části.

## <a name="ccomcriticalsectionm_sec"></a><a name="m_sec"></a>CComCriticalSekce::m_sec

Obsahuje objekt kritického oddílu, `CComCriticalSection` který se používá všechny metody.

```
CRITICAL_SECTION m_sec;
```

## <a name="ccomcriticalsectionterm"></a><a name="term"></a>CcomcriticalSection::Termín

Volá funkci [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), která uvolňuje všechny prostředky používané objektem kritické části obsaženým v datovém členu [m_sec.](#m_sec)

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Jakmile `Term` byla volána, kritický oddíl již nelze použít pro synchronizaci.

## <a name="ccomcriticalsectionunlock"></a><a name="unlock"></a>CcomCriticalSection::Odemknout

Volá funkci Win32 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), která uvolňuje vlastnictví objektu kritické části obsaženého v [datovém](#m_sec) m_sec.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li nejprve získat vlastnictví, podproces musí volat [Lock](#lock) metoda. Každé volání `Lock` vyžaduje odpovídající `Unlock` volání k uvolnění vlastnictví kritické části.

## <a name="see-also"></a>Viz také

[CcomfakeCriticalSekce třídy](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)
