---
title: IObjectWithSiteImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
ms.openlocfilehash: e857f739e3ff7235c473e99abbef6aab0d3f4205
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495838"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl – třída

Tato třída poskytuje metody, které umožňují objektu komunikovat s jeho lokalitou.

## <a name="syntax"></a>Syntaxe

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IObjectWithSiteImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|Zadá dotaz na web pro ukazatel rozhraní.|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Poskytuje objekt s `IUnknown` ukazatelem na webu.|
|[IObjectWithSiteImpl::SetSite](#setsite)|Poskytuje objekt s `IUnknown` ukazatelem na webu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Spravuje `IUnknown` ukazatel na webu.|

## <a name="remarks"></a>Poznámky

Rozhraní [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) umožňuje objektu komunikovat s jeho lokalitou. Třída `IObjectWithSiteImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

`IObjectWithSiteImpl`Určuje dvě metody. Klient nejprve volá `SetSite`a předává `IUnknown` ukazatel na webu. Tento ukazatel je uložen v rámci objektu a lze jej později načíst prostřednictvím volání `GetSite`.

Obvykle je třída odvozena z `IObjectWithSiteImpl` při vytváření objektu, který není ovládací prvek. Pro ovládací prvky odvodíte třídu z [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), která také poskytuje ukazatel na webu. Třídu neodvozujte z obou `IObjectWithSiteImpl` i. `IOleObjectImpl`

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="getsite"></a>IObjectWithSiteImpl:: GetWeb

Zadá dotaz na web pro ukazatel na rozhraní identifikované `riid`.

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>Poznámky

Pokud lokalita podporuje toto rozhraní, ukazatel je vrácen prostřednictvím `ppvSite`. V opačném případě je nastavena na hodnotu null. `ppvSite`

Viz [IObjectWithSite:: GetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite) v Windows SDK.

##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite

Spravuje `IUnknown` ukazatel na webu.

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>Poznámky

`m_spUnkSite`Zpočátku obdrží tento ukazatel prostřednictvím volání [SetSite](#setsite).

##  <a name="setchildsite"></a>IObjectWithSiteImpl::SetChildSite

Poskytuje objekt s `IUnknown` ukazatelem na webu.

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>Parametry

*pUnkSite*<br/>
pro Ukazatel na `IUnknown` ukazatel rozhraní lokality, která spravuje tento objekt. Pokud má hodnotu null, objekt by `IUnknown::Release` měl zavolat na libovolnou existující lokalitu, ve které je objekt již neví o lokalitě.

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

##  <a name="setsite"></a>IObjectWithSiteImpl:: SetSite

Poskytuje objekt s `IUnknown` ukazatelem na webu.

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>Poznámky

Viz [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
