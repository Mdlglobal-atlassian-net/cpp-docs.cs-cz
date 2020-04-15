---
title: Třída IperPropertyBrowsingImpl
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
ms.openlocfilehash: f8fb80cc38e775b9b26afa033647faac694e968a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326505"
---
# <a name="iperpropertybrowsingimpl-class"></a>Třída IperPropertyBrowsingImpl

Tato třída `IUnknown` implementuje a umožňuje klientovi přístup k informacím na stránkách vlastností objektu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IPerPropertyBrowsingImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[iperpropertybrowsingimpl::GetDisplayString](#getdisplaystring)|Načte řetězec popisující danou vlastnost.|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|Načte pole řetězců odpovídající hodnotám, které může daná vlastnost přijmout.|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Načte VARIANTa obsahující hodnotu vlastnosti identifikované daným DISPID. Číslo DISPID je přidruženo k `GetPredefinedStrings`názvu řetězce načtenému z . Implementace ATL vrátí E_NOTIMPL.|
|[iperpropertybrowsingimpl::mappropertytopage](#mappropertytopage)|Načte CLSID stránky vlastností přidružené k dané vlastnosti.|

## <a name="remarks"></a>Poznámky

Rozhraní [IPerPropertyBrowsing](/windows/win32/api/ocidl/nn-ocidl-iperpropertybrowsing) umožňuje klientovi přístup k informacím na stránkách vlastností objektu. Třída `IPerPropertyBrowsingImpl` poskytuje výchozí implementaci tohoto rozhraní `IUnknown` a implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

> [!NOTE]
> Pokud používáte aplikaci Microsoft Access jako aplikaci `IPerPropertyBrowsingImpl`kontejneru, je nutné odvodit třídu z . V opačném případě aplikace Access nenačte ovládací prvek.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="iperpropertybrowsingimplgetdisplaystring"></a><a name="getdisplaystring"></a>iperpropertybrowsingimpl::GetDisplayString

Načte řetězec popisující danou vlastnost.

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>Poznámky

Viz [IPerPropertyBrowsing::GetDisplayString](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) v sadě Windows SDK.

## <a name="iperpropertybrowsingimplgetpredefinedstrings"></a><a name="getpredefinedstrings"></a>IPerPropertyBrowsingImpl::GetPredefinedStrings

Vyplní každé pole nulovými položkami.

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>Návratová hodnota

Atl implementace [GetPredefinedValue](#getpredefinedvalue) vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IPerPropertyBrowsing::GetPredefinedStrings](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) v sadě Windows SDK.

## <a name="iperpropertybrowsingimplgetpredefinedvalue"></a><a name="getpredefinedvalue"></a>IPerPropertyBrowsingImpl::GetPredefinedValue

Načte VARIANTa obsahující hodnotu vlastnosti identifikované daným DISPID. Číslo DISPID je přidruženo k `GetPredefinedStrings`názvu řetězce načtenému z .

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

ATL implementace [GetPredefinedStrings](#getpredefinedstrings) načte žádné odpovídající řetězce.

Viz [IPerPropertyBrowsing::GetPredefinedValue](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) v sadě Windows SDK.

## <a name="iperpropertybrowsingimplmappropertytopage"></a><a name="mappropertytopage"></a>iperpropertybrowsingimpl::mappropertytopage

Načte CLSID stránky vlastností přidružené k zadané vlastnosti.

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>Poznámky

Knihovna ATL používá mapu vlastností objektu k získání těchto informací.

Viz [IPerPropertyBrowsing::MapPropertyToPage](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Třída iPropertyPageimpl](../../atl/reference/ipropertypageimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
