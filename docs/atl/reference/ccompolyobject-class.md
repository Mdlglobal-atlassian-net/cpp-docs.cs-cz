---
title: Třída CComPolyObject
ms.date: 11/04/2016
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
ms.openlocfilehash: e30afef455db5f83afca8ff9e515f39f015c3b8a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327559"
---
# <a name="ccompolyobject-class"></a>Třída CComPolyObject

Tato třída `IUnknown` implementuje pro agregovaný nebo neagregovaný objekt.

## <a name="syntax"></a>Syntaxe

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*Obsažené*<br/>
Vaše třída, odvozená z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), stejně jako z jiných rozhraní, které chcete podporovat na objektu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Konstruktor|
|[CComPolyObject::~CComPolyObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|Zintáží počet odkazů objektu.|
|[CComPolyObject::CreateInstance](#createinstance)|(Statické) Umožňuje vytvořit nový **objekt CComPolyObject<** `contained` **>** bez režie [coCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Provede konečnou inicializaci . `m_contained`|
|[CComPolyObject::FinalRelease](#finalrelease)|Provede konečné `m_contained`zničení .|
|[CComPolyObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComPolyObject::Vydání](#release)|Sníží počet odkazů objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|Delegáti `IUnknown` volání vnější neznámý, pokud je objekt `IUnknown` agregována nebo objektu, pokud objekt není agregována.|

## <a name="remarks"></a>Poznámky

`CComPolyObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro agregovaný nebo neagregovaný objekt.

Při vytvoření `CComPolyObject` instance je zaškrtnuta hodnota vnější neznámý. Pokud je NULL, `IUnknown` je implementována pro neagregovaný objekt. Pokud vnější neznámý není `IUnknown` NULL, je implementována pro agregovaný objekt.

Výhodou použití `CComPolyObject` je, že se vyhnete tomu, abyste v modulu zvládali agregované a neagregované případy [cComAggObject](../../atl/reference/ccomaggobject-class.md) a [CComObject.](../../atl/reference/ccomobject-class.md) Jeden `CComPolyObject` objekt zpracovává oba případy. To znamená, že ve vašem modulu existuje pouze jedna kopie vtable a jedna kopie funkcí. Pokud je vaše vtable je velký, to může podstatně snížit velikost modulu. Pokud je však vaše vtable malá, může použití `CComPolyObject` způsobit o něco větší velikost modulu, protože není `CComAggObject` optimalizována pro agregovaný nebo neagregovaný objekt, jako jsou a . `CComObject`

Pokud je makro DECLARE_POLY_AGGREGATABLE zadáno v definici třídy objektu, `CComPolyObject` bude použito k vytvoření objektu. DECLARE_POLY_AGGREGATABLE bude automaticky deklarována, pokud pomocí Průvodce projektem ATL vytvoříte úplný ovládací prvek nebo ovládací prvek aplikace Internet Explorer.

Pokud agregována, `CComPolyObject` objekt `IUnknown`má své vlastní , `IUnknown`oddělené od vnějšího objektu a udržuje svůj vlastní počet odkazů. `CComPolyObject`používá [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) k delegování na vnější neznámý.

Další informace o agregaci naleznete v článku [Základy objektů ATL COM](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccompolyobjectaddref"></a><a name="addref"></a>CComPolyObject::AddRef

Zintáží počet odkazů na objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

## <a name="ccompolyobjectccompolyobject"></a><a name="ccompolyobject"></a>CComPolyObject::CComPolyObject

Konstruktor

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
[v] Ukazatel na vnější neznámý, pokud má být objekt agregován, nebo NULL, pokud objekt není agregován.

### <a name="remarks"></a>Poznámky

Inicializuje `CComContainedObject` datový člen, [m_contained](#m_contained)a zintáží počet zámků modulu.

Destruktor sníží počet zámek modulu.

## <a name="ccompolyobjectccompolyobject"></a><a name="dtor"></a>CComPolyObject::~CComPolyObject

Destruktor.

```
~CComPolyObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, volá [FinalRelease](#finalrelease)a sníží počet zámek modulu.

## <a name="ccompolyobjectcreateinstance"></a><a name="createinstance"></a>CComPolyObject::CreateInstance

Umožňuje vytvořit nový **objekt CComPolyObject<** `contained` **>** bez režie [coCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Parametry

*Stran*<br/>
[out] Ukazatel na **ukazatel ccompolyobject<.** `contained` **>** Pokud `CreateInstance` je neúspěšný, *pp* je nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vrácený objekt má počet odkazů nula, takže okamžitě volat, `AddRef` pak použijte `Release` k uvolnění odkazu na ukazatel objektu, když jste hotovi.

Pokud nepotřebujete přímý přístup k objektu, ale přesto chcete vytvořit nový `CoCreateInstance`objekt bez režie , použijte [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) místo.

## <a name="ccompolyobjectfinalconstruct"></a><a name="finalconstruct"></a>CComPolyObject::FinalConstruct

Volána během závěrečné fáze konstrukce objektu, tato metoda provede konečnou inicializaci na [m_contained](#m_contained) datového člena.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ccompolyobjectfinalrelease"></a><a name="finalrelease"></a>CComPolyObject::FinalRelease

Volána během zničení objektu, tato metoda uvolní [m_contained](#m_contained) datový člen.

```
void FinalRelease();
```

## <a name="ccompolyobjectm_contained"></a><a name="m_contained"></a>CComPolyObject::m_contained

[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objekt odvozený z vaší třídy.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parametry

*Obsažené*<br/>
[v] Vaše třída, odvozená z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), stejně jako z jiných rozhraní, které chcete podporovat na objektu.

### <a name="remarks"></a>Poznámky

`IUnknown`volání `m_contained` prostřednictvím jsou delegovány na vnější neznámé, pokud `IUnknown` je objekt agregován, nebo na tento objekt, pokud objekt není agregován.

## <a name="ccompolyobjectqueryinterface"></a><a name="queryinterface"></a>CComPolyObject::QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parametry

*Q*<br/>
Rozhraní COM.

*Iid*<br/>
[v] Identifikátor požadovaného rozhraní.

*ppvObjekt*<br/>
[out] Ukazatel rozhraní identifikovaný *iid*. Pokud objekt nepodporuje toto rozhraní, *je hodnota ppvObject* nastavena na hodnotu NULL.

*Stran*<br/>
[out] Ukazatel na rozhraní označené `__uuidof(Q)`rozhraním .

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pro agregovaný objekt, pokud `IUnknown`je `QueryInterface` požadované rozhraní , vrátí ukazatel `IUnknown` na vlastní agregované objektu a přírůstky počet odkazů. Jinak tato metoda dotazuje rozhraní `CComContainedObject` prostřednictvím datového člena, [m_contained](#m_contained).

## <a name="ccompolyobjectrelease"></a><a name="release"></a>CComPolyObject::Vydání

Sníží počet odkazů na objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V sestavení ladění `Release` vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování. V neladivěné `Release` sestavení, vždy vrátí 0.

## <a name="see-also"></a>Viz také

[Třída CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
