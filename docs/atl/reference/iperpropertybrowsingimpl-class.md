---
title: Iperpropertybrowsingimpl – třída
ms.date: 11/04/2016
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
ms.openlocfilehash: 54c475e736425718e954b0e954ea2b327d938556
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299449"
---
# <a name="iperpropertybrowsingimpl-class"></a>Iperpropertybrowsingimpl – třída

Tato třída implementuje `IUnknown` a umožňuje klientům přístup k informacím na stránkách vlastností objektu.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IPerPropertyBrowsingImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|Načte řetězec popisující dané vlastnosti.|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|Načte pole řetězce odpovídající hodnoty, které přijímají dané vlastnosti.|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Načte hodnotu typu VARIANT obsahující hodnotu vlastnosti identifikovaný daný identifikátor DISPID. Hodnota DISPID souvisí s názvem řetězec získaných `GetPredefinedStrings`. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|Načte identifikátor CLSID stránky vlastností, které jsou přidružené k dané vlastnosti.|

## <a name="remarks"></a>Poznámky

[IPerPropertyBrowsing](/windows/desktop/api/ocidl/nn-ocidl-iperpropertybrowsing) rozhraní umožňuje klientům přístup k informacím na stránkách vlastností objektu. Třída `IPerPropertyBrowsingImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

> [!NOTE]
>  Pokud používáte Microsoft Access jako aplikace typu kontejner, musíte odvodit třídu z `IPerPropertyBrowsingImpl`. V opačném případě přístup nenačte ovládacího prvku.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="getdisplaystring"></a>  IPerPropertyBrowsingImpl::GetDisplayString

Načte řetězec popisující dané vlastnosti.

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IPerPropertyBrowsing::GetDisplayString](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) ve Windows SDK.

##  <a name="getpredefinedstrings"></a>  IPerPropertyBrowsingImpl::GetPredefinedStrings

Vyplní jednotlivá pole s nulovou položky.

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>Návratová hodnota

Implementace ATL [GetPredefinedValue](#getpredefinedvalue) vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IPerPropertyBrowsing::GetPredefinedStrings](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) ve Windows SDK.

##  <a name="getpredefinedvalue"></a>  IPerPropertyBrowsingImpl::GetPredefinedValue

Načte hodnotu typu VARIANT obsahující hodnotu vlastnosti identifikovaný daný identifikátor DISPID. Hodnota DISPID souvisí s názvem řetězec získaných `GetPredefinedStrings`.

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Implementace ATL [GetPredefinedStrings](#getpredefinedstrings) načte žádné odpovídající řetězce.

Zobrazit [IPerPropertyBrowsing::GetPredefinedValue](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) ve Windows SDK.

##  <a name="mappropertytopage"></a>  IPerPropertyBrowsingImpl::MapPropertyToPage

Načte identifikátor CLSID stránky vlastností související se zadanou vlastností.

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>Poznámky

Mapy vlastností objektu ATL používá pro získání těchto informací.

Zobrazit [IPerPropertyBrowsing::MapPropertyToPage](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) ve Windows SDK.

## <a name="see-also"></a>Viz také:

[IPropertyPageImpl – třída](../../atl/reference/ipropertypageimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
