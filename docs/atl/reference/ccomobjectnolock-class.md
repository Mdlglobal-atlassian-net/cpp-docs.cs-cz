---
title: CComObjectNoLock – třída
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
ms.openlocfilehash: 9253c7495f4d13ed6ce609988251d8abd09592ad
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497037"
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock – třída

Tato třída implementuje `IUnknown` neagregovaný objekt, ale nezvyšuje počet zámků modulu v konstruktoru.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>Parametry

*Základ*<br/>
Vaše třída odvozená z [třídy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)a také z jakéhokoliv jiného rozhraní, které chcete pro objekt podporovat.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|Konstruktor|
|[CComObjectNoLock::~CComObjectNoLock](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComObjectNoLock:: AddRef](#addref)|Zvýší počet odkazů na objekt.|
|[CComObjectNoLock::QueryInterface](#queryinterface)|Vrátí ukazatel na požadované rozhraní.|
|[CComObjectNoLock:: Release](#release)|Sníží počet odkazů na objekt.|

## <a name="remarks"></a>Poznámky

`CComObjectNoLock`je podobný jako [CComObject](../../atl/reference/ccomobject-class.md) v tom, že implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro neagregovaný objekt; `CComObjectNoLock` nicméně nezvyšuje počet zámků modulu v konstruktoru.

ATL používá `CComObjectNoLock` interně pro továrny tříd. Obecně platí, že tuto třídu nebudete používat přímo.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="addref"></a>CComObjectNoLock:: AddRef

Zvýší počet odkazů na objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

##  <a name="ccomobjectnolock"></a>CComObjectNoLock::CComObjectNoLock

Konstruktor Na rozdíl od [CComObject](../../atl/reference/ccomobject-class.md)nezvyšuje počet zámků modulu.

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>Parametry

<em>šekem\*</em><br/>
pro Tento nepojmenovaný parametr se nepoužívá. Existuje pro symetrie s jinými `CComXXXObjectXXX` konstruktory.

##  <a name="dtor"></a>CComObjectNoLock:: ~ CComObjectNoLock

Destruktor.

```
~CComObjectNoLock();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky a volá [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Identifikátor požadovaného rozhraní.

*ppvObject*<br/>
mimo Ukazatel na ukazatel rozhraní identifikovaný *identifikátorem IID*. Pokud objekt nepodporuje toto rozhraní, je *ppvObject* nastaveno na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="release"></a>CComObjectNoLock:: Release

Sníží počet odkazů na objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V sestavení `Release` ladění vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování. V sestaveních `Release` bez ladění vždy vrátí hodnotu 0.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
