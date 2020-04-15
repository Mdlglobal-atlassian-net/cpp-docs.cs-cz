---
title: Třída iObjectWithSiteImpl
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
ms.openlocfilehash: 034e5dd42f6e10286520bb2a08effc40b0aca71a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329646"
---
# <a name="iobjectwithsiteimpl-class"></a>Třída iObjectWithSiteImpl

Tato třída poskytuje metody umožňující objektu komunikovat s jeho webu.

## <a name="syntax"></a>Syntaxe

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IObjectWithSiteImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[iObjectWithSiteImpl::GetSite](#getsite)|Dotazuje web pro ukazatel rozhraní.|
|[iObjectWithSiteImpl::SetChildSite](#setchildsite)|Poskytuje objektu `IUnknown` ukazatel webu.|
|[iObjectWithSiteImpl::SetSite](#setsite)|Poskytuje objektu `IUnknown` ukazatel webu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Spravuje `IUnknown` ukazatel webu.|

## <a name="remarks"></a>Poznámky

Rozhraní [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) umožňuje objektu komunikovat s jeho webem. Třída `IObjectWithSiteImpl` poskytuje výchozí implementaci tohoto rozhraní `IUnknown` a implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

`IObjectWithSiteImpl`specifikuje dvě metody. Klient nejprve `SetSite`volá , předávání `IUnknown` ukazatele webu. Tento ukazatel je uložen v objektu a později `GetSite`lze načíst prostřednictvím volání .

Obvykle odvodit třídy z `IObjectWithSiteImpl` při vytváření objektu, který není ovládací prvek. Pro ovládací prvky odvodit třídu z [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), který také poskytuje ukazatel webu. Neodvodvozujte `IObjectWithSiteImpl` třídu z obou a `IOleObjectImpl`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="iobjectwithsiteimplgetsite"></a><a name="getsite"></a>iObjectWithSiteImpl::GetSite

Dotazuje web na ukazatel na `riid`rozhraní určené rozhraním .

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>Poznámky

Pokud web podporuje toto rozhraní, `ppvSite`ukazatel je vrácen a vrácen pomocí . V `ppvSite` opačném případě je nastavena na hodnotu NULL.

Viz [IObjectWithSite::GetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite) v sadě Windows SDK.

## <a name="iobjectwithsiteimplm_spunksite"></a><a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite

Spravuje `IUnknown` ukazatel webu.

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>Poznámky

`m_spUnkSite`zpočátku obdrží tento ukazatel prostřednictvím volání [SetSite](#setsite).

## <a name="iobjectwithsiteimplsetchildsite"></a><a name="setchildsite"></a>iObjectWithSiteImpl::SetChildSite

Poskytuje objektu `IUnknown` ukazatel webu.

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>Parametry

*pUnkSite*<br/>
[v] Ukazatel `IUnknown` rozhraní webu, který tento objekt spravuje. Pokud null, objekt `IUnknown::Release` by měl volat na jakékoli existující lokality, v tomto okamžiku objekt již zná jeho webu.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

## <a name="iobjectwithsiteimplsetsite"></a><a name="setsite"></a>iObjectWithSiteImpl::SetSite

Poskytuje objektu `IUnknown` ukazatel webu.

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>Poznámky

Viz [IObjectWithSite::SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
