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
ms.openlocfilehash: deed29b5fb80ea8bbd06b3d50f45e38740b1619f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497156"
---
# <a name="ccompolyobject-class"></a>CComPolyObject – třída

Tato třída implementuje `IUnknown` agregovaný nebo neagregovaný objekt.

## <a name="syntax"></a>Syntaxe

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*uložen*<br/>
Vaše třída odvozená z [třídy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)a také z jiných rozhraní, která chcete pro objekt podporovat.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Konstruktor|
|[CComPolyObject::~CComPolyObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComPolyObject:: AddRef](#addref)|Zvýší počet odkazů objektu.|
|[CComPolyObject:: CreateInstance](#createinstance)|Tras Umožňuje vytvořit nový objekt **<** `contained` **>** CComPolyObject bez režie funkce [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Provede konečnou inicializaci `m_contained`.|
|[CComPolyObject::FinalRelease](#finalrelease)|Provede konečné zničení `m_contained`.|
|[CComPolyObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComPolyObject:: Release](#release)|Sníží počet odkazů objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|Deleguje `IUnknown` volání vnějších neznámých, pokud je objekt agregovaný nebo `IUnknown` k objektu, pokud objekt není agregovaný.|

## <a name="remarks"></a>Poznámky

`CComPolyObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro agregovaný nebo neagregovaný objekt.

Při vytvoření instance `CComPolyObject` je zaškrtnuta hodnota vnějšího neznámého. Pokud je null, `IUnknown` je implementován pro neagregovaný objekt. Pokud není vnější neznámá hodnota null, `IUnknown` je implementována pro agregovaný objekt.

Výhodou použití `CComPolyObject` je, že nemusíte mít v modulu [CComAggObject](../../atl/reference/ccomaggobject-class.md) i [CComObject](../../atl/reference/ccomobject-class.md) , aby bylo možné zpracovávat agregované i neagregované případy. Jeden `CComPolyObject` objekt zpracovává oba případy. To znamená, že ve vašem modulu existují jenom jednu kopii vtable a jednu kopii funkcí. Pokud je tabulka vtable velká, může to podstatně snížit velikost modulu. Pokud je však tabulka vtable malá, použití `CComPolyObject` může mít za následek mírně větší velikost modulu, protože není optimalizována pro agregované nebo neagregované objekty, jako jsou `CComAggObject` a `CComObject`.

Pokud je makro DECLARE_POLY_AGGREGATABLE zadáno v definici třídy vašeho objektu, `CComPolyObject` bude použito k vytvoření objektu. DECLARE_POLY_AGGREGATABLE bude automaticky deklarována, pokud použijete Průvodce projektem ATL k vytvoření úplného řízení nebo ovládacího prvku aplikace Internet Explorer.

Pokud je agregovaná, `CComPolyObject` má objekt vlastní `IUnknown`, oddělený `IUnknown`od vnějšího objektu a udržuje svůj vlastní počet odkazů. `CComPolyObject`používá [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) k delegování na vnější neznámý.

Další informace o agregaci naleznete v článku [Základy objektů ATL modelu COM](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="addref"></a>CComPolyObject:: AddRef

Zvýší počet odkazů na objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

##  <a name="ccompolyobject"></a>CComPolyObject::CComPolyObject

Konstruktor

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
pro Ukazatel na vnější neznámý, pokud má být objekt agregován, nebo hodnotu NULL, pokud objekt není agregovaný.

### <a name="remarks"></a>Poznámky

Inicializuje datový člen, m_contained a zvýší počet zámků modulu. [](#m_contained) `CComContainedObject`

Destruktor snižuje počet zámků modulu.

##  <a name="dtor"></a>CComPolyObject:: ~ CComPolyObject

Destruktor.

```
~CComPolyObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, zavolá [FinalRelease](#finalrelease)a sníží počet zámků modulu.

##  <a name="createinstance"></a>CComPolyObject:: CreateInstance

Umožňuje vytvořit nový objekt **<** `contained` **>** CComPolyObject bez režie funkce [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Parametry

*pp*<br/>
mimo Ukazatel na **CComPolyObject <** `contained` **>** ukazatel. Pokud `CreateInstance` je neúspěšné, je *PP* nastaven na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vrácený objekt má nulový počet odkazů, takže zavolejte `AddRef` hned a pak použijte `Release` k uvolnění odkazu na ukazatel objektu, až budete hotovi.

Pokud nepotřebujete přímý přístup k objektu, ale přesto chcete vytvořit nový objekt bez režie `CoCreateInstance`, použijte raději [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) .

##  <a name="finalconstruct"></a>CComPolyObject::FinalConstruct

Tato metoda je volána během finálních fází konstrukce objektu a provádí jakoukoli konečnou inicializaci na [m_contained](#m_contained) datovém členu.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="finalrelease"></a>CComPolyObject::FinalRelease

Volá se během zničení objektu. Tato metoda uvolní datový člen [m_contained](#m_contained) .

```
void FinalRelease();
```

##  <a name="m_contained"></a>CComPolyObject::m_contained

Objekt [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) odvozený z vaší třídy.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parametry

*uložen*<br/>
pro Vaše třída odvozená z [třídy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)a také z jiných rozhraní, která chcete pro objekt podporovat.

### <a name="remarks"></a>Poznámky

`IUnknown`volání prostřednictvím `m_contained` jsou delegována na vnější neznámý, je-li objekt agregovaný, nebo `IUnknown` na tento objekt, pokud objekt není agregovaný.

##  <a name="queryinterface"></a>CComPolyObject:: QueryInterface

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
pro Identifikátor požadovaného rozhraní.

*ppvObject*<br/>
mimo Ukazatel na ukazatel rozhraní identifikovaný *identifikátorem IID*. Pokud objekt nepodporuje toto rozhraní, je *ppvObject* nastaveno na hodnotu null.

*pp*<br/>
mimo Ukazatel na rozhraní identifikované `__uuidof(Q)`.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pro agregovaný objekt, pokud je `IUnknown`požadované rozhraní, `QueryInterface` vrátí ukazatel na vlastní `IUnknown` agregovaný objekt a zvýší počet odkazů. V opačném případě tato metoda se dotazuje na `CComContainedObject` rozhraní prostřednictvím datového členu [m_contained](#m_contained).

##  <a name="release"></a>CComPolyObject:: Release

Sníží počet odkazů na objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V sestavení `Release` ladění vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování. V neladicích sestaveních `Release` vždy vrátí hodnotu 0.

## <a name="see-also"></a>Viz také:

[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
