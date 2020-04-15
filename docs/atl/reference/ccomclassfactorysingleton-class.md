---
title: Třída CComClassFactorySingleton
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: ec860f7ef59b7d3289bf2e18fea0f0e064a7c8f9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320832"
---
# <a name="ccomclassfactorysingleton-class"></a>Třída CComClassFactorySingleton

Tato třída je odvozena od [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída.

`CComClassFactorySingleton`pochází z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu. Každé volání `CreateInstance` metody jednoduše dotazuje tento objekt na ukazatel rozhraní.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Dotazy `m_spObj` na ukazatel rozhraní.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|Objekt [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) vytvořený `CComClassFactorySingleton`společností .|

## <a name="remarks"></a>Poznámky

Objekty ATL obvykle získávají třídu odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída zahrnuje [makro DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) `CComClassFactory` , který deklaruje jako výchozí třídy factory. Chcete-li použít `CComClassFactorySingleton`, zadejte [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) makro v definici třídy objektu. Příklad:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomclassfactorysingletoncreateinstance"></a><a name="createinstance"></a>CComClassFactorySingleton::CreateInstance

Volání `QueryInterface` prostřednictvím [m_spObj](#m_spobj) načíst ukazatel rozhraní.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
[v] Pokud je objekt vytvářen jako součást agregace, pak *pUnkOuter* musí být vnější neznámý. V opačném případě *pUnkOuter* musí být NULL.

*riid řekl:*<br/>
[v] IID požadovanérozhraní. Pokud *pUnkOuter* není null, *riid* musí být `IID_IUnknown`.

*ppvObj*<br/>
[out] Ukazatel rozhraní určený *riid*. Pokud objekt nepodporuje toto rozhraní, *je hodnota ppvObj* nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ccomclassfactorysingletonm_spobj"></a><a name="m_spobj"></a>CComClassFactorySingleton::m_spObj

Objekt [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) vytvořený `CComClassFactorySingleton`společností .

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Poznámky

Každé volání metody [CreateInstance](#createinstance) jednoduše zjidní tomuto objektu na ukazatel rozhraní.

Všimněte si, `m_spObj` že aktuální forma představuje `CComClassFactorySingleton` narušující změnu ze způsobu, který pracoval v předchozích verzích atl. V předchozích `CComClassFactorySingleton` verzích byl objekt vytvořen současně s továrnou třídy během inicializace serveru. V jazyce Visual C++.NET 2003 a novější objekt je vytvořen líně, na první požadavek. Tato změna může způsobit chyby v programech, které spoléhají na včasnou inicializaci.

## <a name="see-also"></a>Viz také

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[Třída CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)<br/>
[Třída CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[Třída CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
