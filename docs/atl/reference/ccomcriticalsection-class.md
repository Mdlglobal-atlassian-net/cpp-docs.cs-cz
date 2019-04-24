---
title: Ccomautocriticalsection – třída
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
ms.openlocfilehash: f3a4b50f8dd9bc460a209c47497e720529c40e58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246641"
---
# <a name="ccomcriticalsection-class"></a>Ccomautocriticalsection – třída

Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritický oddíl.

## <a name="syntax"></a>Syntaxe

```
class CComCriticalSection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComCriticalSection::Init](#init)|Vytvoří a inicializuje objekt kritický oddíl.|
|[CComCriticalSection::Lock](#lock)|Získá vlastnictví objektu kritický oddíl.|
|[CComCriticalSection::Term](#term)|Uvolní prostředky systému použité objektem kritický oddíl.|
|[CComCriticalSection::Unlock](#unlock)|Uvolní vlastnictví objektu kritický oddíl.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|Critical_section – objekt.|

## <a name="remarks"></a>Poznámky

`CComCriticalSection` je podobný třídě [ccomautocriticalsection –](../../atl/reference/ccomautocriticalsection-class.md), s tím rozdílem, že je nutné explicitně inicializovat a release kritický oddíl.

Obvykle použijete `CComCriticalSection` prostřednictvím **typedef** název [criticalsection –](ccommultithreadmodel-class.md#criticalsection). Tento název se odkazuje `CComCriticalSection` při [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) je používán.

Zobrazit [ccomcritseclock – třída](../../atl/reference/ccomcritseclock-class.md) pro bezpečnější způsob, jak použít tuto třídu než volání `Lock` a `Unlock` přímo.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

##  <a name="ccomcriticalsection"></a>  CComCriticalSection::CComCriticalSection

Konstruktor

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Poznámky

Nastaví [m_sec](#m_sec) datový člen na hodnotu NULL.

##  <a name="init"></a>  CComCriticalSection::Init

Volá funkci Win32 [InitializeCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsection), který inicializuje objekt kritický oddíl součástí [m_sec](#m_sec) datový člen.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu, E_OUTOFMEMORY nebo E_FAIL při selhání.

##  <a name="lock"></a>  CComCriticalSection::Lock

Volá funkci Win32 [EnterCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-entercriticalsection), které počká, dokud vlákno může převzít vlastnictví kritický oddíl objektů obsažených v [m_sec](#m_sec) datový člen.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu, E_OUTOFMEMORY nebo E_FAIL při selhání.

### <a name="remarks"></a>Poznámky

Objekt kritický oddíl musí nejprve inicializovat pomocí volání [Init](#init) metody. Po dokončení provádění chráněné kódu vlákna musí volat [odemknout](#unlock) uvolnit vlastnictví kritický oddíl.

##  <a name="m_sec"></a>  CComCriticalSection::m_sec

Obsahuje objekt kritický oddíl, který se používá ve všech `CComCriticalSection` metody.

```
CRITICAL_SECTION m_sec;
```

##  <a name="term"></a>  CComCriticalSection::Term

Volá funkci Win32 [DeleteCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-deletecriticalsection), což uvolní všechny prostředky používané objektem kritický oddíl součástí [m_sec](#m_sec) datový člen.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Jednou `Term` byla volána, důležité části může již nebude používán k synchronizaci.

##  <a name="unlock"></a>  CComCriticalSection::Unlock

Volá funkci Win32 [LeaveCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-leavecriticalsection), která uvolní vlastnictví objektu kritický oddíl součástí [m_sec](#m_sec) datový člen.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Nejdřív získat vlastnictví, musí volat vlákno [Zámek](#lock) metody. Každé volání `Lock` vyžaduje odpovídající volání `Unlock` uvolnit vlastnictví kritický oddíl.

## <a name="see-also"></a>Viz také:

[CComFakeCriticalSection – třída](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[CComCritSecLock – třída](../../atl/reference/ccomcritseclock-class.md)
