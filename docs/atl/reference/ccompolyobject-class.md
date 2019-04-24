---
title: CComPolyObject – třída
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
ms.openlocfilehash: a8dbbc06d35d2606cc76e89cc555ba7f8577daa9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246254"
---
# <a name="ccompolyobject-class"></a>CComPolyObject – třída

Tato třída implementuje `IUnknown` agregované nebo neagregovaná objektu.

## <a name="syntax"></a>Syntaxe

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*obsažené*<br/>
Vaše třída odvozena od [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře jako z jiných rozhraní, které chcete podporovat na objekt.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Konstruktor|
|[CComPolyObject::~CComPolyObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|Zvýší počet odkazů na objekt.|
|[CComPolyObject::CreateInstance](#createinstance)|(Statické) Umožňuje vytvořit novou **CComPolyObject <** `contained` **>** objektu bez režie [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Provede konečnou inicializaci `m_contained`.|
|[CComPolyObject::FinalRelease](#finalrelease)|Provádí konečné zničení `m_contained`.|
|[CComPolyObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComPolyObject::Release](#release)|Sníží počet odkaz objekt.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|Delegáti `IUnknown` volání vnější neznámá nebo, pokud objekt je agregován do `IUnknown` objektu, pokud není agregovaný objekt.|

## <a name="remarks"></a>Poznámky

`CComPolyObject` implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) agregované nebo neagregovaná objektu.

Pokud instance `CComPolyObject` se vytvoří hodnota vnější Neznámá je zaškrtnuté políčko. Pokud má hodnotu NULL, `IUnknown` je implementován pro neagregovaná objektu. Pokud není NULL, vnější Neznámá `IUnknown` je implementován pro agregovaného objektu.

Výhodou použití `CComPolyObject` je, že se vyhnete nutnosti obě [CComAggObject](../../atl/reference/ccomaggobject-class.md) a [CComObject](../../atl/reference/ccomobject-class.md) v modulu pro zpracování agregované a neagregovaná případech. Jediný `CComPolyObject` objekt zpracovává obou případech. To znamená, že existují jenom jednu kopii tabulku vtable a jedna kopie funkce v modulu. Pokud je vaše vtable velký, to může výrazně zkrátit velikost vašeho modulu. Nicméně pokud je vaše vtable malá, pomocí `CComPolyObject` může vést o něco větší velikost modulu, protože není optimalizován pro objekt agregována nebo neagregovaná jsou `CComAggObject` a `CComObject`.

Pokud je zadán DECLARE_POLY_AGGREGATABLE makra v definici třídy objektu, `CComPolyObject` se použije k vytvoření objektu. DECLARE_POLY_AGGREGATABLE bude automaticky deklarovalo, pokud použijete Průvodce projektem ATL k vytvoření úplné řízení nebo ovládacího prvku aplikace Internet Explorer.

Pokud agregován, `CComPolyObject` objekt má své vlastní `IUnknown`, odděleně od vnějšího objektu `IUnknown`a udržuje svůj vlastní počet odkazů. `CComPolyObject` používá [ccomcontainedobject –](../../atl/reference/ccomcontainedobject-class.md) delegovat vnější neznámá.

Další informace o agregaci naleznete v článku [základy ATL COM objekty](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="addref"></a>  CComPolyObject::AddRef

Zvýší počet odkazů na objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečné pro diagnostiku a testování.

##  <a name="ccompolyobject"></a>  CComPolyObject::CComPolyObject

Konstruktor

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
[in] Ukazatel na vnější neznámá, pokud objekt má být agregován, nebo hodnota NULL, pokud objekt, pokud není agregovaný objekt.

### <a name="remarks"></a>Poznámky

Inicializuje `CComContainedObject` datový člen [m_contained](#m_contained)a zvýší počet zámků modulů.

Destruktor sníží počet zámků modulů.

##  <a name="dtor"></a>  CComPolyObject:: ~ CComPolyObject

Destruktor.

```
~CComPolyObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, volání [FinalRelease](#finalrelease), a sníží počet modul zámku.

##  <a name="createinstance"></a>  CComPolyObject::CreateInstance

Umožňuje vytvořit novou **CComPolyObject <** `contained` **>** objektu bez režie [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Parametry

*pp*<br/>
[out] Ukazatel **CComPolyObject <** `contained` **>** ukazatele. Pokud `CreateInstance` neproběhne úspěšně, *pp* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Objekt vrácený má nulový počet odkaz, takže volání `AddRef` okamžitě, pak použijte `Release` uvolnit odkaz na ukazatel objektu, až budete hotovi.

Pokud není nutné přímý přístup k objektu, ale přesto chcete vytvořit nový objekt bez režie `CoCreateInstance`, použijte [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) místo.

##  <a name="finalconstruct"></a>  CComPolyObject::FinalConstruct

Volá se v závěrečných fázích vytváření objektu, tato metoda provádí na všechny konečné inicializace [m_contained](#m_contained) datový člen.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="finalrelease"></a>  CComPolyObject::FinalRelease

Volá se během odstraňování objektů, tato metoda uvolní [m_contained](#m_contained) datový člen.

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComPolyObject::m_contained

A [ccomcontainedobject –](../../atl/reference/ccomcontainedobject-class.md) objekt odvozený od vaší třídy.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parametry

*obsažené*<br/>
[in] Vaše třída odvozena od [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře jako z jiných rozhraní, které chcete podporovat na objekt.

### <a name="remarks"></a>Poznámky

`IUnknown` provádí volání prostřednictvím `m_contained` se deleguje na vnější neznámá, pokud objekt je agregován, nebo k `IUnknown` tohoto objektu, pokud není agregovaný objekt.

##  <a name="queryinterface"></a>  CComPolyObject::QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parametry

*Q*<br/>
Rozhraní COM.

*iid*<br/>
[in] Identifikátor se požadované rozhraní.

*ppvObject*<br/>
[out] Ukazatel na ukazatel rozhraní, který je identifikován *iid*. Pokud objekt nepodporuje toto rozhraní *ppvObject* nastaven na hodnotu NULL.

*pp*<br/>
[out] Ukazatel na rozhraní identifikovaný `__uuidof(Q)`.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pro agregovaného objektu, pokud je požadovaná rozhraní `IUnknown`, `QueryInterface` vrací ukazatel na agregovaný objektu vlastní `IUnknown` a zvýší počet odkazů. Jinak tato metoda dotazuje na rozhraní prostřednictvím `CComContainedObject` datový člen [m_contained](#m_contained).

##  <a name="release"></a>  CComPolyObject::Release

Sníží počet odkaz na objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V ladicím buildu `Release` vrátí hodnotu, která může být užitečné pro diagnostiku a testování. V sestaveních nondebug `Release` vždy vrátí hodnotu 0.

## <a name="see-also"></a>Viz také:

[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
