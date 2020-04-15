---
title: Třída CComTearoffObject
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
ms.openlocfilehash: de7528d3972991c233ee4b9037f609b89d0f7434
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327313"
---
# <a name="ccomtearoffobject-class"></a>Třída CComTearoffObject

Tato třída implementuje rozhraní odtržení.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>Parametry

*Základní*<br/>
Vaše třída odtržení, odvozená od `CComTearOffObjectBase` a rozhraní, která chcete podporovat objekt odtržení.

KNIHOVNA ATL implementuje svá odtrhávací rozhraní ve dvou fázích `CComTearOffObjectBase` – metody zpracovávají počet odkazů a `QueryInterface`, zatímco `CComTearOffObject` implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CcomtearoffObject::ccomtearoffObject](#ccomtearoffobject)|Konstruktor|
|[CComTearoffObject::~CComTearoffObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComTearoffObject::Addref](#addref)|Zintáží počet odkazů `CComTearOffObject` pro objekt.|
|[CComTearoffObject::QueryInterface](#queryinterface)|Vrátí ukazatel na požadované rozhraní na třídu odtržení nebo třídy vlastníka.|
|[CComTearoffObject::Vydání](#release)|Sníží počet odkazů pro `CComTearOffObject` objekt a zničí jej.|

### <a name="ccomtearoffobjectbase-methods"></a>Metody CComTearoffObjectBase

|||
|-|-|
|[CComTearoffObjectBase](#ccomtearoffobjectbase)|Konstruktor|

### <a name="ccomtearoffobjectbase-data-members"></a>Datové členy CComTearoffObjectBase

|||
|-|-|
|[m_pOwner](#m_powner)|Ukazatel na `CComObject` odvozené z třídy vlastníka.|

## <a name="remarks"></a>Poznámky

`CComTearOffObject`implementuje rozhraní odtržení jako samostatný objekt, který je vytvořena instance pouze v případě, že rozhraní je dotazován. Odtržení se odstraní, když se počet odkazů stane nulou. Obvykle vytvoříte rozhraní odtržení pro rozhraní, které se používá zřídka, protože pomocí odtržení uloží vtable ukazatel ve všech instancích hlavního objektu.

Měli byste odvodit třídu `CComTearOffObjectBase` implementující odtržení z a z rozhraní, které chcete, aby váš odtrhávací objekt podporoval. `CComTearOffObjectBase`je templatized na třídu vlastníka a model podprocesu. Třída vlastníka je třída objektu, pro který je implementována odtržení. Pokud nezadáte model vlákna, použije se výchozí model vlákna.

Měli byste vytvořit mapu COM pro třídu odtržení. Když atl konkretizovat odtržení, `CComTearOffObject<CYourTearOffClass>` `CComCachedTearOffObject<CYourTearOffClass>`vytvoří nebo .

Například ve vzorku BEEPER `CBeeper2` je třída třída odtržení `CBeeper` a třída je třída vlastníka:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComTearOffObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomtearoffobjectaddref"></a><a name="addref"></a>CComTearoffObject::Addref

Zintáží počet odkazů `CComTearOffObject` objektu o jednu.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku a testování.

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="ccomtearoffobject"></a>CcomtearoffObject::ccomtearoffObject

Konstruktor

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
[v] Ukazatel, který bude převeden na `CComObject<Owner>` ukazatel na objekt.

### <a name="remarks"></a>Poznámky

Zvýšení počtu odkazů vlastníka o jednu.

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="dtor"></a>CComTearoffObject::~CComTearoffObject

Destruktor.

```
~CComTearOffObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, volání FinalRelease a sníží počet zámek modulu.

## <a name="ccomtearoffobjectccomtearoffobjectbase"></a><a name="ccomtearoffobjectbase"></a>CcomtearoffObject::ccomtearoffObjectBase

Konstruktor

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>Poznámky

Inicializuje [člen m_pOwner](#m_powner) na hodnotu NULL.

## <a name="ccomtearoffobjectm_powner"></a><a name="m_powner"></a>CComTearOffObject::m_pOwner

Ukazatel na objekt [CComObject](../../atl/reference/ccomobject-class.md) odvozený od *owner*.

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>Parametry

*Vlastník*<br/>
[v] Třída, pro kterou je implementována odtržení.

### <a name="remarks"></a>Poznámky

Ukazatel je inicializován na HODNOTU NULL během výstavby.

## <a name="ccomtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComTearoffObject::QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] IID rozhraní, které je požadováno.

*ppvObjekt*<br/>
[out] Ukazatel rozhraní identifikovaný *iid*nebo NULL, pokud rozhraní není nalezeno.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Nejprve se dotazuje na rozhraní ve třídě odtržení. Pokud rozhraní není k dispozici, dotazy pro rozhraní na objekt vlastníka. Pokud je `IUnknown`požadované rozhraní `IUnknown` , vrátí vlastníka.

## <a name="ccomtearoffobjectrelease"></a><a name="release"></a>CComTearoffObject::Vydání

Sníží počet odkazů o jednu a pokud je počet odkazů `CComTearOffObject`nulový, odstraní .

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>Návratová hodnota

V sestaveních bez ladění vždy vrátí nulu. V sestavení ladění vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování.

## <a name="see-also"></a>Viz také

[Třída CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
