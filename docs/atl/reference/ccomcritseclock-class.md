---
title: Ccomcritseclock – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d06b34099ecdb9c61d3580586bcb3bcd73eaf709
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755044"
---
# <a name="ccomcritseclock-class"></a>Ccomcritseclock – třída

Tato třída poskytuje metody pro zamknutí a odemknutí objektu kritický oddíl.

## <a name="syntax"></a>Syntaxe

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>Parametry

*TLock*  
Objekt k uzamčení a odemknutí.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|Konstruktor|
|[Ccomcritseclock –:: ~ ccomcritseclock –](#dtor)|Destruktor.|

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

*cs*  
Objekt, který kritický oddíl.

*bInitialLock*  
Stav zámku počáteční: **true** znamená, že uzamčen.

### <a name="remarks"></a>Poznámky

Inicializuje objekt kritický oddíl.

##  <a name="dtor"></a>  Ccomcritseclock –:: ~ ccomcritseclock –

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

## <a name="see-also"></a>Viz také

[Ccomautocriticalsection – třída](../../atl/reference/ccomcriticalsection-class.md)   
[CComAutoCriticalSection – třída](../../atl/reference/ccomautocriticalsection-class.md)
