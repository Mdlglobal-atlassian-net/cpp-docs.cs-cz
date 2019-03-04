---
title: CComCritSecLock Class
ms.date: 11/04/2016
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
ms.openlocfilehash: 045e64504707fa8978c8236b376037d9f57bf12c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261229"
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock Class

Tato třída poskytuje metody pro zamknutí a odemknutí objektu kritický oddíl.

## <a name="syntax"></a>Syntaxe

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>Parametry

*TLock*<br/>
Objekt k uzamčení a odemknutí.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|Konstruktor|
|[CComCritSecLock::~CComCritSecLock](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComCritSecLock::Lock](#lock)|Voláním této metody lze uzamknout objekt kritický oddíl.|
|[CComCritSecLock::Unlock](#unlock)|Volání této metody k odemknutí objektu kritický oddíl.|

## <a name="remarks"></a>Poznámky

Tato třída slouží k uzamčení nebo odemčení způsobem bezpečnější než s objekty [ccomautocriticalsection – třída](../../atl/reference/ccomcriticalsection-class.md) nebo [ccomautocriticalsection – třída](../../atl/reference/ccomautocriticalsection-class.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="ctor"></a>  CComCritSecLock::CComCritSecLock

Konstruktor

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>Parametry

*cs*<br/>
Objekt, který kritický oddíl.

*bInitialLock*<br/>
Stav zámku počáteční: **true** znamená, že uzamčen.

### <a name="remarks"></a>Poznámky

Inicializuje objekt kritický oddíl.

##  <a name="dtor"></a>  CComCritSecLock::~CComCritSecLock

Destruktor.

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>Poznámky

Odemkne objekt kritický oddíl.

##  <a name="lock"></a>  CComCritSecLock::Lock

Voláním této metody lze uzamknout objekt kritický oddíl.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK, pokud objekt má úspěšně uzamčen nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pokud objekt je již uzamčena, dojde k chybě vyhodnocení v sestaveních ladění.

##  <a name="unlock"></a>  CComCritSecLock::Unlock

Volání této metody k odemknutí objektu kritický oddíl.

```
void Unlock() throw();
```

### <a name="remarks"></a>Poznámky

Pokud už je odemknuté objektu, dojde k chybě vyhodnocení v sestaveních ladění.

## <a name="see-also"></a>Viz také:

[CComAutoCriticalSection – třída](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAutoCriticalSection – třída](../../atl/reference/ccomautocriticalsection-class.md)
