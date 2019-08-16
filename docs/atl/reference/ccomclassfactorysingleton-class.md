---
title: CComClassFactorySingleton – třída
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: 71705d02140f0392a9ce023c64e7b4125c14443f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497380"
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton – třída

Tato třída je odvozena z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída.

`CComClassFactorySingleton`je odvozen z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu. Každé volání `CreateInstance` metody jednoduše dotazuje tento objekt na ukazatel rozhraní.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Dotazy `m_spObj` na ukazatel rozhraní|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|Objekt [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) , který je `CComClassFactorySingleton`vytvořen pomocí.|

## <a name="remarks"></a>Poznámky

Objekty ATL normálně získávají objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída zahrnuje makro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), které deklaruje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Chcete- `CComClassFactorySingleton`li použít, zadejte makro [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) v definici třídy vašeho objektu. Příklad:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="createinstance"></a>CComClassFactorySingleton:: CreateInstance

Volá `QueryInterface` prostřednictvím [m_spObj](#m_spobj) k načtení ukazatele rozhraní.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
pro Pokud se objekt vytváří jako součást agregace, pak musí být *pUnkOuter* vnějším neznámý. V opačném případě *pUnkOuter* musí mít hodnotu null.

*riid*<br/>
pro IID požadovaného rozhraní. Pokud *pUnkOuter* je jiný než null, musí být `IID_IUnknown`riid.

*ppvObj*<br/>
mimo Ukazatel na ukazatel rozhraní identifikovaný *riid*. Pokud objekt nepodporuje toto rozhraní, je *ppvObj* nastaveno na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="m_spobj"></a>  CComClassFactorySingleton::m_spObj

Objekt [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) , který je `CComClassFactorySingleton`vytvořen pomocí.

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Poznámky

Každé volání metody [CreateInstance](#createinstance) jednoduše dotazuje tento objekt na ukazatel rozhraní.

Všimněte si, že aktuální forma `m_spObj` sady představuje zásadní změnu od způsobu, `CComClassFactorySingleton` jak pracovala v předchozích verzích ATL. V předchozích verzích `CComClassFactorySingleton` byl během inicializace serveru vytvořen objekt ve stejnou dobu jako objekt pro vytváření tříd. V jazyce C++Visual .NET 2003 a novějším je objekt vytvořen laxně vytvářená při první žádosti. Tato změna by mohla způsobit chyby v programech, které spoléhají na prvotní inicializaci.

## <a name="see-also"></a>Viz také:

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 – třída](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactoryAutoThread – třída](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
