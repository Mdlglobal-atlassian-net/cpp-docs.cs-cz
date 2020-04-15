---
title: Třída CComCritSecLock
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
ms.openlocfilehash: 24d141c5b0ec703feadcd7db96da33f9de940dda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327955"
---
# <a name="ccomcritseclock-class"></a>Třída CComCritSecLock

Tato třída poskytuje metody pro zamykání a odemknutí objektu kritického oddílu.

## <a name="syntax"></a>Syntaxe

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>Parametry

*Blokování*<br/>
Objekt, který má být uzamčen a odemčen.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComCritSecLock::CComCritSecZámek](#ctor)|Konstruktor|
|[CComCritSecLock::~CComCritSecLock](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComCritSecLock::Zamknout](#lock)|Volání této metody k uzamčení objektu kritické části.|
|[CComCritSecLock::Odemknout](#unlock)|Volání této metody odemknout objekt kritické části.|

## <a name="remarks"></a>Poznámky

Tato třída slouží k uzamknutí a odemknutí objektů bezpečnějším způsobem než u [třídy CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) nebo [CComAutoCriticalSection .](../../atl/reference/ccomautocriticalsection-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccomcritseclockccomcritseclock"></a><a name="ctor"></a>CComCritSecLock::CComCritSecZámek

Konstruktor

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>Parametry

*Cs*<br/>
Objekt kritické části.

*bInitialLock*<br/>
Počáteční stav zámku: **true** znamená uzamčen.

### <a name="remarks"></a>Poznámky

Inicializuje objekt kritického oddílu.

## <a name="ccomcritseclockccomcritseclock"></a><a name="dtor"></a>CComCritSecLock::~CComCritSecLock

Destruktor.

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>Poznámky

Odemkne objekt kritického oddílu.

## <a name="ccomcritseclocklock"></a><a name="lock"></a>CComCritSecLock::Zamknout

Volání této metody k uzamčení objektu kritické části.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK pokud byl objekt úspěšně uzamčen, nebo chyba HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pokud je objekt již uzamčen, dojde k chybě ASSERT v sestaveních ladění.

## <a name="ccomcritseclockunlock"></a><a name="unlock"></a>CComCritSecLock::Odemknout

Volání této metody odemknout objekt kritické části.

```
void Unlock() throw();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt již odemknut, dojde k chybě ASSERT v sestaveních ladění.

## <a name="see-also"></a>Viz také

[Třída CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Třída CComautocriticalsection](../../atl/reference/ccomautocriticalsection-class.md)
