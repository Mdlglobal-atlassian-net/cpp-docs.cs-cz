---
title: IPerPropertyBrowsingImpl – třída
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
ms.openlocfilehash: 263f6826ac921d864dee646ef063c8b456b00af1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495717"
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl – třída

Tato třída implementuje `IUnknown` a umožňuje klientovi přístup k informacím na stránkách vlastností objektu.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IPerPropertyBrowsingImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|Načte řetězec popisující danou vlastnost.|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|Načte pole řetězců odpovídající hodnotám, které může daná vlastnost přijmout.|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Načte VARIANTu obsahující hodnotu vlastnosti identifikované daným identifikátorem DISPID. Identifikátor DISPID je přidružený k názvu řetězce načtenému z `GetPredefinedStrings`. Implementace ATL Vrátí E_NOTIMPL.|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|Načte identifikátor CLSID stránky vlastností přidružené k dané vlastnosti.|

## <a name="remarks"></a>Poznámky

Rozhraní [IPerPropertyBrowsing](/windows/win32/api/ocidl/nn-ocidl-iperpropertybrowsing) umožňuje klientovi přístup k informacím na stránkách vlastností objektu. Třída `IPerPropertyBrowsingImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

> [!NOTE]
>  Pokud používáte aplikaci Microsoft Access jako aplikaci typu kontejner, je nutné třídu odvodit z `IPerPropertyBrowsingImpl`. V opačném případě nebude přístup načítat váš ovládací prvek.

**Související články** [Kurz ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="getdisplaystring"></a>IPerPropertyBrowsingImpl::GetDisplayString

Načte řetězec popisující danou vlastnost.

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>Poznámky

Viz [IPerPropertyBrowsing:: GetDisplayString](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) v Windows SDK.

##  <a name="getpredefinedstrings"></a>IPerPropertyBrowsingImpl::GetPredefinedStrings

Vyplní každé pole nulovými položkami.

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>Návratová hodnota

Implementace [GetPredefinedValue](#getpredefinedvalue) knihovny ATL Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IPerPropertyBrowsing:: GetPredefinedStrings](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) v Windows SDK.

##  <a name="getpredefinedvalue"></a>IPerPropertyBrowsingImpl::GetPredefinedValue

Načte VARIANTu obsahující hodnotu vlastnosti identifikované daným identifikátorem DISPID. Identifikátor DISPID je přidružený k názvu řetězce načtenému z `GetPredefinedStrings`.

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Implementace [GetPredefinedStrings](#getpredefinedstrings) knihovny ATL nenačítá žádné odpovídající řetězce.

Viz [IPerPropertyBrowsing:: GetPredefinedValue](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) v Windows SDK.

##  <a name="mappropertytopage"></a>IPerPropertyBrowsingImpl::MapPropertyToPage

Načte identifikátor CLSID stránky vlastností přidružené k zadané vlastnosti.

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>Poznámky

ATL používá k získání těchto informací mapu vlastností objektu.

Viz [IPerPropertyBrowsing:: MapPropertyToPage](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) v Windows SDK.

## <a name="see-also"></a>Viz také:

[IPropertyPageImpl – třída](../../atl/reference/ipropertypageimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
