---
title: Ccomapartment – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39750bcb6b8852e692e52f163e83bb815ecebe97
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755434"
---
# <a name="ccomapartment-class"></a>Ccomapartment – třída

Tato třída poskytuje podporu pro správu appartment v souboru EXE modulu ve fondu vláken.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComApartment
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComApartment::CComApartment](#ccomapartment)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComApartment::Apartment](#apartment)|Označuje počáteční adresu vlákna.|
|[CComApartment::GetLockCount](#getlockcount)|Vrátí aktuální počet zámků vlákna.|
|[CComApartment::Lock](#lock)|Zvýší počet zámků vlákna.|
|[CComApartment::Unlock](#unlock)|Dekrementuje počet zámků vlákna.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Obsahuje identifikátor vlákna.|
|[CComApartment::m_hThread](#m_hthread)|Obsahuje popisovač vlákna.|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Obsahuje počet zámků aktuálního vlákna.|

## <a name="remarks"></a>Poznámky

`CComApartment` používá [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) ke správě v souboru EXE modulu ve fondu vláken typu apartment. `CComApartment` poskytuje metody pro zvyšování a dekrementace zámek spolehnout na vlákno.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="apartment"></a>  CComApartment::Apartment

Označuje počáteční adresu vlákna.

```
DWORD Apartment();
```

### <a name="return-value"></a>Návratová hodnota

Vždy 0.

### <a name="remarks"></a>Poznámky

Automaticky nastavit během [CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init).

##  <a name="ccomapartment"></a>  CComApartment::CComApartment

Konstruktor

```
CComApartment();
```

### <a name="remarks"></a>Poznámky

Inicializuje `CComApartment` datové členy [m_nLockCnt](#m_nlockcnt) a [m_hThread](#m_hthread).

##  <a name="getlockcount"></a>  CComApartment::GetLockCount

Vrátí aktuální počet zámků vlákna.

```
LONG GetLockCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet zámků ve vlákně.

##  <a name="lock"></a>  CComApartment::Lock

Zvýší počet zámků vlákna.

```
LONG Lock();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečné pro diagnostiku a testování.

### <a name="remarks"></a>Poznámky

Volané [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Počet zámků na vlákno se používá pro statistické účely.

##  <a name="m_dwthreadid"></a>  CComApartment::m_dwThreadID

Obsahuje identifikátor vlákna.

```
DWORD m_dwThreadID;
```

##  <a name="m_hthread"></a>  CComApartment::m_hThread

Obsahuje popisovač vlákna.

```
HANDLE m_hThread;
```

##  <a name="m_nlockcnt"></a>  CComApartment::m_nLockCnt

Obsahuje počet zámků aktuálního vlákna.

```
LONG m_nLockCnt;
```

##  <a name="unlock"></a>  CComApartment::Unlock

Dekrementuje počet zámků vlákna.

```
LONG Unlock();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečné pro diagnostiku a testování.

### <a name="remarks"></a>Poznámky

Volané [CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Počet zámků na vlákno se používá pro statistické účely.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
