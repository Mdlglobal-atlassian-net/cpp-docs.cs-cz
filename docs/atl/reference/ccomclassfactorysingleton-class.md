---
title: CComClassFactorySingleton Class
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: c415da15341f7800a706379d991cb753f5991170
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221172"
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton Class

Tato třída je odvozena z [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) a používá [ccomobjectglobal –](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Třída.

`CComClassFactorySingleton` je odvozen od [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) a používá [ccomobjectglobal –](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu. Každé volání `CreateInstance` metoda jednoduše dotazuje tohoto objektu pro ukazatel rozhraní.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Dotazy `m_spObj` pro ukazatel rozhraní.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|[Ccomobjectglobal –](../../atl/reference/ccomobjectglobal-class.md) přiřazený objekt vytvořený pomocí `CComClassFactorySingleton`.|

## <a name="remarks"></a>Poznámky

Objekty knihovny ATL obvykle získat objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makra [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), který deklaruje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Chcete-li použít `CComClassFactorySingleton`, zadejte [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) makra v definici třídy objektu. Příklad:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="createinstance"></a>  CComClassFactorySingleton::CreateInstance

Volání `QueryInterface` prostřednictvím [m_spObj](#m_spobj) načíst ukazatel rozhraní.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
[in] Pokud se objekt vytváří jako součást agregace, pak *pUnkOuter* musí být vnější neznámá. V opačném případě *pUnkOuter* musí mít hodnotu NULL.

*riid*<br/>
[in] Identifikátor IID požadované rozhraní. Pokud *pUnkOuter* je jiná než NULL, *riid* musí být `IID_IUnknown`.

*ppvObj*<br/>
[out] Ukazatel na ukazatel rozhraní, který je identifikován *riid*. Pokud objekt nepodporuje toto rozhraní *ppvObj* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="m_spobj"></a>  CComClassFactorySingleton::m_spObj

[Ccomobjectglobal –](../../atl/reference/ccomobjectglobal-class.md) přiřazený objekt vytvořený pomocí `CComClassFactorySingleton`.

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Poznámky

Každé volání [CreateInstance](#createinstance) metoda jednoduše dotazuje tohoto objektu pro ukazatel rozhraní.

Všimněte si, že aktuální formu `m_spObj` uvede k zásadní změně z způsob, který `CComClassFactorySingleton` pracovali v předchozích verzích ATL. V předchozích verzích `CComClassFactorySingleton` objekt byl vytvořen ve stejnou dobu jako objekt pro vytváření tříd, během inicializace serveru. Ve Vizuálu C++.NET 2003 a novějším, objekt je vytvořen laxně, na první požadavek. Tato změna může způsobit chyby v programech, které jsou závislé na dřívější inicializace.

## <a name="see-also"></a>Viz také:

[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 – třída](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactoryAutoThread – třída](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
