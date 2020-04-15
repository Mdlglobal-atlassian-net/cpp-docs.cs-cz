---
title: Třída CComObjectNoLock
ms.date: 11/04/2016
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
ms.openlocfilehash: c190f495e284e98b27a6c6dc2099a8dfc4b1693d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327615"
---
# <a name="ccomobjectnolock-class"></a>Třída CComObjectNoLock

Tato třída `IUnknown` implementuje pro neagregovaný objekt, ale nezpřísťuje počet zámek modulu v konstruktoru.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>Parametry

*Základní*<br/>
Vaše třída, odvozená z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), stejně jako z jakéhokoli jiného rozhraní, které chcete podporovat na objektu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Ccomobjectnolock::ccomobjectnolock](#ccomobjectnolock)|Konstruktor|
|[CcomObjectNolock::~CComObjectNoLock](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CcomObjectNoLock::Addref](#addref)|Zintáží počet odkazů na objekt.|
|[CcomObjectNoLock::QueryInterface](#queryinterface)|Vrátí ukazatel na požadované rozhraní.|
|[CcomObjectNolock::Vydání](#release)|Sníží počet odkazů na objekt.|

## <a name="remarks"></a>Poznámky

`CComObjectNoLock`je podobný [CComObject](../../atl/reference/ccomobject-class.md) v tom, že implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro neagregovaný objekt; však `CComObjectNoLock` nezinkace počet zámek modulu v konstruktoru.

ATL `CComObjectNoLock` používá interně pro třídy továrny. Obecně platí, že nebudete používat tuto třídu přímo.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomobjectnolockaddref"></a><a name="addref"></a>CcomObjectNoLock::Addref

Zintáží počet odkazů na objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="ccomobjectnolock"></a>Ccomobjectnolock::ccomobjectnolock

Konstruktor Na rozdíl od [CComObject](../../atl/reference/ccomobject-class.md), nezinkace počet zámek modulu.

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>Parametry

<em>void\*</em><br/>
[v] Tento nepojmenovaný parametr se nepoužívá. Existuje pro symetrii s jinými `CComXXXObjectXXX` konstruktory.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="dtor"></a>CcomObjectNolock::~CComObjectNoLock

Destruktor.

```
~CComObjectNoLock();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky a volání [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectnolockqueryinterface"></a><a name="queryinterface"></a>CcomObjectNoLock::QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Identifikátor požadovaného rozhraní.

*ppvObjekt*<br/>
[out] Ukazatel rozhraní identifikovaný *iid*. Pokud objekt nepodporuje toto rozhraní, *je hodnota ppvObject* nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ccomobjectnolockrelease"></a><a name="release"></a>CcomObjectNolock::Vydání

Sníží počet odkazů na objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V sestavení ladění `Release` vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování. V sestaveních bez ladění `Release` vždy vrátí 0.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
