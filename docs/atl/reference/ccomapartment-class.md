---
title: Třída CComApartment
ms.date: 11/04/2016
f1_keywords:
- CComApartment
- ATLBASE/ATL::CComApartment
- ATLBASE/ATL::CComApartment::CComApartment
- ATLBASE/ATL::CComApartment::Apartment
- ATLBASE/ATL::CComApartment::GetLockCount
- ATLBASE/ATL::CComApartment::Lock
- ATLBASE/ATL::CComApartment::Unlock
- ATLBASE/ATL::CComApartment::m_dwThreadID
- ATLBASE/ATL::CComApartment::m_hThread
- ATLBASE/ATL::CComApartment::m_nLockCnt
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
ms.openlocfilehash: 13141d27592f6f40ea7b0529c61baba2fe83a10a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321121"
---
# <a name="ccomapartment-class"></a>Třída CComApartment

Tato třída poskytuje podporu pro správu apartment v modulu EXE s družným vláknem.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComApartment
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CcomApartment::CcomApartment](#ccomapartment)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CcomApartment::Apartmán](#apartment)|Označí počáteční adresu vlákna.|
|[CcomApartment::GetlockCount](#getlockcount)|Vrátí aktuální počet zámků vlákna.|
|[CcomApartment::Zámek](#lock)|Zintáží počet zámků vlákna.|
|[CcomApartment::Odemknout](#unlock)|Sníží počet zámků vlákna.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CComApartmán::m_dwThreadID](#m_dwthreadid)|Obsahuje identifikátor vlákna.|
|[CComApartmán::m_hThread](#m_hthread)|Obsahuje popisovač vlákna.|
|[CComApartmán::m_nLockCnt](#m_nlockcnt)|Obsahuje aktuální počet zámků vlákna.|

## <a name="remarks"></a>Poznámky

`CComApartment`používá [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) ke správě apartment v modulu EXE s družným vláknem. `CComApartment`poskytuje metody pro zvýšení a snížení počet zámků na vlákno.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccomapartmentapartment"></a><a name="apartment"></a>CcomApartment::Apartmán

Označí počáteční adresu vlákna.

```
DWORD Apartment();
```

### <a name="return-value"></a>Návratová hodnota

Vždy 0.

### <a name="remarks"></a>Poznámky

Automaticky nastavit během [CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init).

## <a name="ccomapartmentccomapartment"></a><a name="ccomapartment"></a>CcomApartment::CcomApartment

Konstruktor

```
CComApartment();
```

### <a name="remarks"></a>Poznámky

Inicializuje `CComApartment` [m_nLockCnt](#m_nlockcnt) a [m_hThread](#m_hthread)datových členů .

## <a name="ccomapartmentgetlockcount"></a><a name="getlockcount"></a>CcomApartment::GetlockCount

Vrátí aktuální počet zámků vlákna.

```
LONG GetLockCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet zámků ve vlákně.

## <a name="ccomapartmentlock"></a><a name="lock"></a>CcomApartment::Zámek

Zintáží počet zámků vlákna.

```
LONG Lock();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

### <a name="remarks"></a>Poznámky

Volal [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Počet zámků ve vlákně se používá pro statistické účely.

## <a name="ccomapartmentm_dwthreadid"></a><a name="m_dwthreadid"></a>CComApartmán::m_dwThreadID

Obsahuje identifikátor vlákna.

```
DWORD m_dwThreadID;
```

## <a name="ccomapartmentm_hthread"></a><a name="m_hthread"></a>CComApartmán::m_hThread

Obsahuje popisovač vlákna.

```
HANDLE m_hThread;
```

## <a name="ccomapartmentm_nlockcnt"></a><a name="m_nlockcnt"></a>CComApartmán::m_nLockCnt

Obsahuje aktuální počet zámků vlákna.

```
LONG m_nLockCnt;
```

## <a name="ccomapartmentunlock"></a><a name="unlock"></a>CcomApartment::Odemknout

Sníží počet zámků vlákna.

```
LONG Unlock();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

### <a name="remarks"></a>Poznámky

Volal [CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Počet zámků ve vlákně se používá pro statistické účely.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
