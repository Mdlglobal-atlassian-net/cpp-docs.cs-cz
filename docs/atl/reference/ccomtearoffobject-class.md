---
title: CComTearOffObject – třída
ms.date: 11/04/2016
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
ms.openlocfilehash: 0d27a6fa3c0070cd32c78971a7544327c51d4393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496920"
---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject – třída

Tato třída implementuje odkládací rozhraní.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>Parametry

*Základ*<br/>
Odtrhnout třídu odvozenou z `CComTearOffObjectBase` a rozhraní, které chcete pro odložení objektu podporovat.

ATL implementuje jeho rozhraní ve dvou `CComTearOffObjectBase` fázích – metody zpracovávají počet odkazů a `QueryInterface`při `CComTearOffObject` implementaci rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|Konstruktor|
|[CComTearOffObject::~CComTearOffObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComTearOffObject:: AddRef](#addref)|Zvýší počet odkazů pro `CComTearOffObject` objekt.|
|[CComTearOffObject::QueryInterface](#queryinterface)|Vrátí ukazatel na požadované rozhraní buď na třídu, nebo na třídu Owner.|
|[CComTearOffObject:: Release](#release)|Sníží počet `CComTearOffObject` odkazů objektu a odstraní jej.|

### <a name="ccomtearoffobjectbase-methods"></a>Metody CComTearOffObjectBase

|||
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|Konstruktor|

### <a name="ccomtearoffobjectbase-data-members"></a>Datové členy CComTearOffObjectBase

|||
|-|-|
|[m_pOwner](#m_powner)|Ukazatel na `CComObject` odvozený od třídy Owner.|

## <a name="remarks"></a>Poznámky

`CComTearOffObject`implementuje odkládací rozhraní jako samostatný objekt, jehož instance je vytvořena pouze v případě, že je toto rozhraní dotazováno pro. Trhlina se odstraní, když se jejich počet odkazů stane nula. Obvykle vytvoříte nepoužívané rozhraní pro rozhraní, které se používá zřídka, protože použití trhliny ukládá ukazatel vtable ve všech instancích hlavního objektu.

Měli byste odvodit třídu implementující trhlinu z `CComTearOffObjectBase` a z libovolného rozhraní, které chcete, aby objekt podporoval. `CComTearOffObjectBase`je založena ve třídě Owner a modelu vlákna. Třída Owner je třída objektu, pro kterou je implementována trhlina. Pokud nezadáte model vláken, použije se výchozí model vláken.

Měli byste vytvořit mapu COM pro třídu deaktivovat. Když knihovna ATL vytvoří instanci trhlin, vytvoří `CComTearOffObject<CYourTearOffClass>` nebo. `CComCachedTearOffObject<CYourTearOffClass>`

Například v ukázce `CBeeper2` pípnutí je třída podtrhnout třídu `CBeeper` a třída je vlastníkem třídy:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComTearOffObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="addref"></a>CComTearOffObject:: AddRef

Zvýší počet `CComTearOffObject` odkazů objektu o jeden.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku a testování.

##  <a name="ccomtearoffobject"></a>CComTearOffObject::CComTearOffObject

Konstruktor

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
pro Ukazatel, který bude převeden na ukazatel na `CComObject<Owner>` objekt.

### <a name="remarks"></a>Poznámky

Zvýší počet odkazů na vlastníka o jeden.

##  <a name="dtor"></a>CComTearOffObject:: ~ CComTearOffObject

Destruktor.

```
~CComTearOffObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, zavolá FinalRelease a sníží počet zámků modulu.

##  <a name="ccomtearoffobjectbase"></a>CComTearOffObject::CComTearOffObjectBase

Konstruktor

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>Poznámky

Inicializuje člen [m_pOwner](#m_powner) na hodnotu null.

##  <a name="m_powner"></a>CComTearOffObject::m_pOwner

Ukazatel na objekt [CComObject](../../atl/reference/ccomobject-class.md) odvozený od *vlastníka*.

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>Parametry

*Owner*<br/>
pro Třída, pro kterou je implementována trhlina.

### <a name="remarks"></a>Poznámky

Ukazatel je během vytváření inicializován na hodnotu NULL.

##  <a name="queryinterface"></a>  CComTearOffObject::QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Identifikátor IID přižádaného rozhraní

*ppvObject*<br/>
mimo Ukazatel na ukazatel rozhraní identifikovaný *identifikátorem IID*nebo hodnotu null, pokud rozhraní nebylo nalezeno.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Nejprve se dotazuje na rozhraní ve vaší podtřídě. Pokud rozhraní není, dotazy na rozhraní objektu Owner. Pokud je `IUnknown`požadované rozhraní, `IUnknown` vrátí vlastníka.

##  <a name="release"></a>CComTearOffObject:: Release

Sníží počet odkazů o jednu a, pokud je počet odkazů nula, odstraní `CComTearOffObject`.

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>Návratová hodnota

V sestaveních bez ladění vždy vrátí hodnotu nula. V sestavení ladění vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování.

## <a name="see-also"></a>Viz také:

[CComCachedTearOffObject – třída](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
