---
title: CComApartment – třída
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
ms.openlocfilehash: 5f4c7fc356e61210e9b99bf9989b1bb3f0abc98a
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821672"
---
# <a name="ccomapartment-class"></a>CComApartment – třída

Tato třída poskytuje podporu pro správu objektů Apartment v modulu EXE ve fondu vláken.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComApartment
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComApartment::CComApartment](#ccomapartment)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComApartment:: Apartment](#apartment)|Označí počáteční adresu vlákna.|
|[CComApartment::GetLockCount](#getlockcount)|Vrátí aktuální počet zámků vlákna.|
|[CComApartment:: Lock](#lock)|Zvýší počet zámků vlákna.|
|[CComApartment:: Unlock](#unlock)|Sníží počet zámků vlákna.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Obsahuje identifikátor vlákna.|
|[CComApartment::m_hThread](#m_hthread)|Obsahuje popisovač vlákna.|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Obsahuje aktuální počet zámků vlákna.|

## <a name="remarks"></a>Poznámky

`CComApartment` používá [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) ke správě objektů Apartment v modulu exe ve fondu vláken. `CComApartment` poskytuje metody pro zvýšení a snížení počtu zámků ve vlákně.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="apartment"></a>CComApartment:: Apartment

Označí počáteční adresu vlákna.

```
DWORD Apartment();
```

### <a name="return-value"></a>Návratová hodnota

Vždycky 0.

### <a name="remarks"></a>Poznámky

Automaticky nastaveno během [CComAutoThreadModule:: init](../../atl/reference/ccomautothreadmodule-class.md#init).

##  <a name="ccomapartment"></a>CComApartment::CComApartment

Konstruktor

```
CComApartment();
```

### <a name="remarks"></a>Poznámky

Inicializuje datové členy `CComApartment` [m_nLockCnt](#m_nlockcnt) a [m_hThread](#m_hthread).

##  <a name="getlockcount"></a>CComApartment::GetLockCount

Vrátí aktuální počet zámků vlákna.

```
LONG GetLockCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet zámků ve vlákně.

##  <a name="lock"></a>CComApartment:: Lock

Zvýší počet zámků vlákna.

```
LONG Lock();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

### <a name="remarks"></a>Poznámky

Volá se [CComAutoThreadModule:: Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Počet zámků ve vlákně se používá ke statistickým účelům.

##  <a name="m_dwthreadid"></a>CComApartment:: m_dwThreadID

Obsahuje identifikátor vlákna.

```
DWORD m_dwThreadID;
```

##  <a name="m_hthread"></a>CComApartment:: m_hThread

Obsahuje popisovač vlákna.

```
HANDLE m_hThread;
```

##  <a name="m_nlockcnt"></a>CComApartment:: m_nLockCnt

Obsahuje aktuální počet zámků vlákna.

```
LONG m_nLockCnt;
```

##  <a name="unlock"></a>CComApartment:: Unlock

Sníží počet zámků vlákna.

```
LONG Unlock();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

### <a name="remarks"></a>Poznámky

Voláno pomocí [CComAutoThreadModule:: Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Počet zámků ve vlákně se používá ke statistickým účelům.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
