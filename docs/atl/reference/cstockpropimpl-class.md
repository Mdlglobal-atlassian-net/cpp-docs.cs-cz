---
title: CStockPropImpl Class
ms.date: 05/06/2019
f1_keywords:
- CStockPropImpl
- ATLCTL/ATL::CStockPropImpl
- ATLCTL/ATL::get_Appearance
- ATLCTL/ATL::get_AutoSize
- ATLCTL/ATL::get_BackColor
- ATLCTL/ATL::get_BackStyle
- ATLCTL/ATL::get_BorderColor
- ATLCTL/ATL::get_BorderStyle
- ATLCTL/ATL::get_BorderVisible
- ATLCTL/ATL::get_BorderWidth
- ATLCTL/ATL::get_Caption
- ATLCTL/ATL::get_DrawMode
- ATLCTL/ATL::get_DrawStyle
- ATLCTL/ATL::get_DrawWidth
- ATLCTL/ATL::get_Enabled
- ATLCTL/ATL::get_FillColor
- ATLCTL/ATL::get_FillStyle
- ATLCTL/ATL::get_Font
- ATLCTL/ATL::get_ForeColor
- ATLCTL/ATL::get_HWND
- ATLCTL/ATL::get_MouseIcon
- ATLCTL/ATL::get_MousePointer
- ATLCTL/ATL::get_Picture
- ATLCTL/ATL::get_ReadyState
- ATLCTL/ATL::get_TabStop
- ATLCTL/ATL::get_Text
- ATLCTL/ATL::getvalid
- ATLCTL/ATL::get_Window
- ATLCTL/ATL::put_Appearance
- ATLCTL/ATL::put_AutoSize
- ATLCTL/ATL::put_BackColor
- ATLCTL/ATL::put_BackStyle
- ATLCTL/ATL::put_BorderColor
- ATLCTL/ATL::put_BorderStyle
- ATLCTL/ATL::put_BorderVisible
- ATLCTL/ATL::put_BorderWidth
- ATLCTL/ATL::put_Caption
- ATLCTL/ATL::put_DrawMode
- ATLCTL/ATL::put_DrawStyle
- ATLCTL/ATL::put_DrawWidth
- ATLCTL/ATL::put_Enabled
- ATLCTL/ATL::put_FillColor
- ATLCTL/ATL::put_FillStyle
- ATLCTL/ATL::put_Font
- ATLCTL/ATL::put_ForeColor
- ATLCTL/ATL::put_HWND
- ATLCTL/ATL::put_MouseIcon
- ATLCTL/ATL::put_MousePointer
- ATLCTL/ATL::put_Picture
- ATLCTL/ATL::put_ReadyState
- ATLCTL/ATL::put_TabStop
- ATLCTL/ATL::put_Text
- ATLCTL/ATL::putvalid
- ATLCTL/ATL::put_Window
- ATLCTL/ATL::putref_Font
- ATLCTL/ATL::putref_MouseIcon
- ATLCTL/ATL::putref_Picture
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
ms.openlocfilehash: bc349137661d7026e48688f8ef510958de270280
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075222"
---
# <a name="cstockpropimpl-class"></a>CStockPropImpl Class

Tato třída poskytuje metody pro podporu hodnot uložených vlastností.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <
    class T,
    class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE CStockPropImpl :
    public IDispatchImpl<InterfaceName, piid, plibid, wMajor, wMinor, tihclass>
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Třída, která implementuje ovládací prvek a který je odvozen z `CStockPropImpl`.

*InterfaceName*<br/>
Duální rozhraní, které zveřejňuje základní vlastnosti.

*piid*<br/>
Ukazatel na IID `InterfaceName`.

*plibid*<br/>
Ukazatel na LIBID knihovny typů obsahující definici `InterfaceName`.

*wMajor*<br/>
Hlavní verze knihovny typů. Výchozí hodnota je 1.

*wMinor*<br/>
Vedlejší verze knihovny typů. Výchozí hodnota je 0.

*tihclass*<br/>
Třída, která slouží ke správě informací o typu pro *T*. Výchozí hodnota je `CComTypeInfoHolder`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|[get_Appearance](#get_appearance)|Voláním této metody získáte styl Malování, který je použit ovládacím prvkem, například plochý nebo 3D.|
|[get_AutoSize](#get_autosize)|Voláním této metody získáte stav příznaku, který označuje, zda ovládací prvek nemůže být jinou velikostí.|
|[get_BackColor](#get_backcolor)|Voláním této metody Získá barvu pozadí ovládacího prvku.|
|[get_BackStyle](#get_backstyle)|Voláním této metody získáte styl pozadí ovládacího prvku, buď transparentního, nebo neprůhledný.|
|[get_BorderColor](#get_bordercolor)|Voláním této metody Získá barvu ohraničení ovládacího prvku.|
|[get_BorderStyle](#get_borderstyle)|Voláním této metody Získá styl ohraničení ovládacího prvku.|
|[get_BorderVisible](#get_bordervisible)|Voláním této metody získáte stav příznaku, který označuje, zda je ohraničení ovládacího prvku viditelné nebo ne.|
|[get_BorderWidth](#get_borderwidth)|Voláním této metody získáte šířku ohraničení ovládacího prvku (v pixelech).|
|[get_Caption](#get_caption)|Voláním této metody získáte text zadaný v titulku objektu.|
|[get_DrawMode](#get_drawmode)|Voláním této metody získáte režim kreslení ovládacího prvku, například barvu pera nebo invertování barev XOR.|
|[get_DrawStyle](#get_drawstyle)|Voláním této metody získáte styl kreslení ovládacího prvku, například Solid, čárkovaný nebo tečkovaný.|
|[get_DrawWidth](#get_drawwidth)|Voláním této metody získáte šířku kresby (v pixelech), kterou používají metody kreslení ovládacího prvku.|
|[get_Enabled](#get_enabled)|Voláním této metody získáte stav příznaku, který označuje, zda je ovládací prvek povolen.|
|[get_FillColor](#get_fillcolor)|Voláním této metody Získá barvu výplně ovládacího prvku.|
|[get_FillStyle](#get_fillstyle)|Voláním této metody získáte styl výplně ovládacího prvku, například plná, průhledná nebo křížově šrafované.|
|[get_Font](#get_font)|Voláním této metody získá ukazatel na vlastnosti písma ovládacího prvku.|
|[get_ForeColor](#get_forecolor)|Voláním této metody Získá barvu popředí ovládacího prvku.|
|[get_HWND](#get_hwnd)|Voláním této metody získáte popisovač okna přidruženého k ovládacímu prvku.|
|[get_MouseIcon](#get_mouseicon)|Voláním této metody získáte vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metasoubor), které se zobrazí, když je ukazatel myši nad ovládacím prvkem.|
|[get_MousePointer](#get_mousepointer)|Voláním této metody získáte typ ukazatele myši, který se zobrazí, když je ukazatel myši nad ovládacím prvkem, například šipky, příčně nebo přesýpací hodiny.|
|[get_Picture](#get_picture)|Voláním této metody načtete ukazatel na vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metasoubor), které se mají zobrazit.|
|[get_ReadyState](#get_readystate)|Voláním této metody získáte stav připravenosti ovládacího prvku, například načítání nebo načtení.|
|[get_TabStop](#get_tabstop)|Voláním této metody získáte příznak, který označuje, zda je ovládací prvek zarážka tabulátoru nebo ne.|
|[get_Text](#get_text)|Voláním této metody získáte text, který se zobrazí s ovládacím prvkem.|
|[GetValID](#get_valid)|Voláním této metody získáte stav příznaku, který označuje, zda je ovládací prvek platný nebo nikoli.|
|[get_Window](#get_window)|Voláním této metody získáte popisovač okna přidruženého k ovládacímu prvku. Stejné jako [CStockPropImpl:: get_HWND](#get_hwnd).|
|[put_Appearance](#put_appearance)|Voláním této metody nastavíte styl Malování používaný ovládacím prvkem, například plochý nebo 3D.|
|[put_AutoSize](#put_autosize)|Voláním této metody nastavíte hodnotu příznaku, která označuje, zda ovládací prvek nemůže být jinou velikostí.|
|[put_BackColor](#put_backcolor)|Voláním této metody nastavíte barvu pozadí ovládacího prvku.|
|[put_BackStyle](#put_backstyle)|Voláním této metody nastavíte styl pozadí ovládacího prvku.|
|[put_BorderColor](#put_bordercolor)|Voláním této metody nastavíte barvu ohraničení ovládacího prvku.|
|[put_BorderStyle](#put_borderstyle)|Voláním této metody nastavíte styl ohraničení ovládacího prvku.|
|[put_BorderVisible](#put_bordervisible)|Voláním této metody nastavíte hodnotu příznaku, která označuje, zda je okraj ovládacího prvku viditelný nebo nikoli.|
|[put_BorderWidth](#put_borderwidth)|Voláním této metody nastavíte šířku ohraničení ovládacího prvku.|
|[put_Caption](#put_caption)|Voláním této metody nastavíte text, který má být zobrazen s ovládacím prvkem.|
|[put_DrawMode](#put_drawmode)|Voláním této metody nastavíte režim kreslení ovládacího prvku, například barvu pera nebo invertování barev XOR.|
|[put_DrawStyle](#put_drawstyle)|Voláním této metody nastavíte styl vykreslování ovládacího prvku, například Solid, čárkovaný nebo tečkovaný.|
|[put_DrawWidth](#put_drawwidth)|Voláním této metody nastavíte šířku (v pixelech), kterou používají metody kreslení ovládacího prvku.|
|[put_Enabled](#put_enabled)|Voláním této metody nastavíte příznak, který označuje, zda je ovládací prvek povolen.|
|[put_FillColor](#put_fillcolor)|Voláním této metody nastavíte barvu výplně ovládacího prvku.|
|[put_FillStyle](#put_fillstyle)|Voláním této metody nastavíte styl výplně ovládacího prvku, například Solid, Průhledný nebo mřížkovaný.|
|[put_Font](#put_font)|Voláním této metody nastavíte vlastnosti písma ovládacího prvku.|
|[put_ForeColor](#put_forecolor)|Voláním této metody nastavíte barvu popředí ovládacího prvku.|
|[put_HWND](#put_hwnd)|Tato metoda vrací E_FAIL.|
|[put_MouseIcon](#put_mouseicon)|Voláním této metody nastavíte vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metasoubor), které se zobrazí, když je ukazatel myši nad ovládacím prvkem.|
|[put_MousePointer](#put_mousepointer)|Voláním této metody nastavíte typ ukazatele myši, který se zobrazí, když je ukazatel myši nad ovládacím prvkem, například šipky, příčně nebo přesýpací hodiny.|
|[put_Picture](#put_picture)|Voláním této metody nastavíte zobrazení vlastností obrázku grafiky (ikona, rastrový obrázek nebo metasoubor).|
|[put_ReadyState](#put_readystate)|Voláním této metody nastavíte stav připravenosti ovládacího prvku, například načítání nebo načtení.|
|[put_TabStop](#put_tabstop)|Voláním této metody nastavíte hodnotu příznaku, která označuje, zda je ovládací prvek zarážka tabulátoru nebo ne.|
|[put_Text](#put_text)|Voláním této metody nastavíte text, který se zobrazí s ovládacím prvkem.|
|[putvalid](#put_valid)|Voláním této metody nastavíte příznak, který označuje, zda je ovládací prvek platný nebo nikoli.|
|[put_Window](#put_window)|Tato metoda volá [CStockPropImpl::p ut_HWND](#put_hwnd), která vrací E_FAIL.|
|[putref_Font](#putref_font)|Zavolejte tuto metodu pro nastavení vlastností písma ovládacího prvku s počtem odkazů.|
|[putref_MouseIcon](#putref_mouseicon)|Voláním této metody nastavíte vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metasoubor), které se zobrazí, když je ukazatel myši nad ovládacím prvkem, s počtem odkazů.|
|[putref_Picture](#putref_picture)|Voláním této metody nastavíte zobrazení vlastností obrázku (ikona, rastrový obrázek nebo metasoubor) na hodnotu počet odkazů.|

## <a name="remarks"></a>Poznámky

`CStockPropImpl` poskytuje metody **Put** a **Get** pro každou vlastnost akcie. Tyto metody poskytují kód potřebný k nastavení nebo získání datového členu přidruženého k jednotlivým vlastnostem a k oznamování a synchronizaci s kontejnerem při změně jakékoli vlastnosti.

Visual Studio poskytuje podporu pro vlastnosti akcií prostřednictvím průvodců. Další informace o přidání uložených vlastností do ovládacího prvku naleznete v [kurzu ATL](../../atl/active-template-library-atl-tutorial.md).

Z důvodu zpětné kompatibility `CStockPropImpl` také zpřístupňuje metody `get_Window` a `put_Window`, které jednoduše volají `get_HWND` a `put_HWND`v uvedeném pořadí. Výchozí implementace `put_HWND` vrátí E_FAIL, protože HWND by měla být vlastnost jen pro čtení.

Následující vlastnosti mají také implementaci **PUTREF** :

- Písma

- MouseIcon

- Obrázek

Stejné tři uložené vlastnosti vyžadují, aby jejich odpovídající datový člen byl typu `CComPtr` nebo jinou třídou, která poskytuje správné počítání odkazů rozhraní prostřednictvím operátoru přiřazení.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="cstockpropimplget_appearance"></a><a name="get_appearance"></a>CStockPropImpl:: get_Appearance

Voláním této metody získáte styl Malování, který je použit ovládacím prvkem, například plochý nebo 3D.

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>Parametry

*pnAppearance*<br/>
Proměnná, která přijímá styl Malování ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_autosize"></a><a name="get_autosize"></a>CStockPropImpl:: get_AutoSize

Voláním této metody získáte stav příznaku, který označuje, zda ovládací prvek nemůže být jinou velikostí.

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>Parametry

*pbAutoSize*<br/>
Proměnná, která přijímá stav příznaku Hodnota TRUE označuje, že ovládací prvek nemůže být jinou velikostí.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_backcolor"></a><a name="get_backcolor"></a>CStockPropImpl:: get_BackColor

Voláním této metody Získá barvu pozadí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>Parametry

*pclrBackColor*<br/>
Proměnná, která obdrží barvu pozadí ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_backstyle"></a><a name="get_backstyle"></a>CStockPropImpl:: get_BackStyle

Voláním této metody získáte styl pozadí ovládacího prvku, buď transparentního, nebo neprůhledný.

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>Parametry

*pnBackStyle*<br/>
Proměnná, která přijímá styl pozadí ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_bordercolor"></a><a name="get_bordercolor"></a>CStockPropImpl:: get_BorderColor

Voláním této metody Získá barvu ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>Parametry

*pclrBorderColor*<br/>
Proměnná, která obdrží barvu ohraničení ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_borderstyle"></a><a name="get_borderstyle"></a>CStockPropImpl:: get_BorderStyle

Voláním této metody Získá styl ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>Parametry

*pnBorderStyle*<br/>
Proměnná, která přijímá styl ohraničení ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_bordervisible"></a><a name="get_bordervisible"></a>CStockPropImpl:: get_BorderVisible

Voláním této metody získáte stav příznaku, který označuje, zda je ohraničení ovládacího prvku viditelné nebo ne.

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>Parametry

*pbBorderVisible*<br/>
Proměnná, která přijímá stav příznaku Hodnota TRUE označuje, že je ohraničení ovládacího prvku viditelné.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_borderwidth"></a><a name="get_borderwidth"></a>CStockPropImpl:: get_BorderWidth

Voláním této metody získáte šířku ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>Parametry

*pnBorderWidth*<br/>
Proměnná, která přijímá šířku ohraničení ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_caption"></a><a name="get_caption"></a>CStockPropImpl:: get_Caption

Voláním této metody získáte text zadaný v titulku objektu.

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>Parametry

*pbstrCaption*<br/>
Text, který se má zobrazit v ovládacím prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_drawmode"></a><a name="get_drawmode"></a>CStockPropImpl:: get_DrawMode

Voláním této metody získáte režim kreslení ovládacího prvku, například barvu pera nebo invertování barev XOR.

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>Parametry

*pnDrawMode*<br/>
Proměnná, která přijímá režim kreslení ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_drawstyle"></a><a name="get_drawstyle"></a>CStockPropImpl:: get_DrawStyle

Voláním této metody získáte styl kreslení ovládacího prvku, například Solid, čárkovaný nebo tečkovaný.

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>Parametry

*pnDrawStyle*<br/>
Proměnná, která přijímá styl vykreslování ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_drawwidth"></a><a name="get_drawwidth"></a>CStockPropImpl:: get_DrawWidth

Voláním této metody získáte šířku kresby (v pixelech), kterou používají metody kreslení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>Parametry

*pnDrawWidth*<br/>
Proměnná, která přijímá hodnotu šířky ovládacího prvku v pixelech

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_enabled"></a><a name="get_enabled"></a>CStockPropImpl:: get_Enabled

Voláním této metody získáte stav příznaku, který označuje, zda je ovládací prvek povolen.

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>Parametry

*pbEnabled*<br/>
Proměnná, která přijímá stav příznaku Hodnota TRUE označuje, že je ovládací prvek povolen.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_fillcolor"></a><a name="get_fillcolor"></a>CStockPropImpl:: get_FillColor

Voláním této metody Získá barvu výplně ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>Parametry

*pclrFillColor*<br/>
Proměnná, která přijímá barvu výplně ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_fillstyle"></a><a name="get_fillstyle"></a>CStockPropImpl:: get_FillStyle

Voláním této metody získáte styl výplně ovládacího prvku, například Solid, Průhledný nebo crosshatched.

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>Parametry

*pnFillStyle*<br/>
Proměnná, která přijímá styl výplně ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_font"></a><a name="get_font"></a>CStockPropImpl:: get_Font

Voláním této metody získá ukazatel na vlastnosti písma ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont*<br/>
Proměnná, která přijímá ukazatel na vlastnosti písma ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_forecolor"></a><a name="get_forecolor"></a>CStockPropImpl:: get_ForeColor

Voláním této metody Získá barvu popředí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>Parametry

*pclrForeColor*<br/>
Proměnná, která obdrží barvu popředí ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_hwnd"></a><a name="get_hwnd"></a>CStockPropImpl:: get_HWND

Voláním této metody získáte popisovač okna přidruženého k ovládacímu prvku.

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parametry

*phWnd*<br/>
Popisovač okna přidružený k ovládacímu prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_mouseicon"></a><a name="get_mouseicon"></a>CStockPropImpl:: get_MouseIcon

Voláním této metody získáte vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metasoubor), které se zobrazí, když je ukazatel myši nad ovládacím prvkem.

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parametry

*ppPicture*<br/>
Proměnná, která obdrží ukazatel na vlastnosti obrázku grafiky.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_mousepointer"></a><a name="get_mousepointer"></a>CStockPropImpl:: get_MousePointer

Voláním této metody získáte typ ukazatele myši, který se zobrazí, když je ukazatel myši nad ovládacím prvkem, například šipky, příčně nebo přesýpací hodiny.

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>Parametry

*pnMousePointer*<br/>
Proměnná, která přijímá typ ukazatele myši.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_picture"></a><a name="get_picture"></a>CStockPropImpl:: get_Picture

Voláním této metody načtete ukazatel na vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metasoubor), které se mají zobrazit.

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parametry

*ppPicture*<br/>
Proměnná, která přijímá ukazatel na vlastnosti obrázku Další podrobnosti najdete v tématu [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) .

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_readystate"></a><a name="get_readystate"></a>CStockPropImpl:: get_ReadyState

Voláním této metody získáte stav připravenosti ovládacího prvku, například načítání nebo načtení.

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>Parametry

*pnReadyState*<br/>
Proměnná, která přijímá stav připravenosti ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_tabstop"></a><a name="get_tabstop"></a>CStockPropImpl:: get_TabStop

Voláním této metody získáte stav příznaku, který označuje, zda je ovládací prvek zarážka tabulátoru nebo ne.

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>Parametry

*pbTabStop*<br/>
Proměnná, která přijímá stav příznaku Hodnota TRUE označuje, že ovládací prvek je zarážka tabulátoru.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_text"></a><a name="get_text"></a>CStockPropImpl:: get_Text

Voláním této metody získáte text, který se zobrazí s ovládacím prvkem.

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>Parametry

*pbstrText*<br/>
Text zobrazený s ovládacím prvkem

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplgetvalid"></a><a name="get_valid"></a>CStockPropImpl:: GetValID

Voláním této metody získáte stav příznaku, který označuje, zda je ovládací prvek platný nebo nikoli.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>Parametry

*pbValid*<br/>
Proměnná, která přijímá stav příznaku Hodnota TRUE označuje, že ovládací prvek je platný.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplget_window"></a><a name="get_window"></a>CStockPropImpl:: get_Window

Voláním této metody získáte popisovač okna přidruženého k ovládacímu prvku. Stejné jako [CStockPropImpl:: get_HWND](#get_hwnd).

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parametry

*phWnd*<br/>
Popisovač okna přidružený k ovládacímu prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_appearance"></a><a name="put_appearance"></a>CStockPropImpl::p ut_Appearance

Voláním této metody nastavíte styl Malování používaný ovládacím prvkem, například plochý nebo 3D.

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>Parametry

*nAppearance*<br/>
Nový styl Malování, který má být použit ovládacím prvkem.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_autosize"></a><a name="put_autosize"></a>CStockPropImpl::p ut_AutoSize

Voláním této metody nastavíte hodnotu příznaku, která označuje, zda ovládací prvek nemůže být jinou velikostí.

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>Parametry

*bAutoSize*<br/>
TRUE, pokud ovládací prvek nemůže být jinou velikostí.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_backcolor"></a><a name="put_backcolor"></a>CStockPropImpl::p ut_BackColor

Voláním této metody nastavíte barvu pozadí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>Parametry

*clrBackColor*<br/>
Nová barva pozadí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_backstyle"></a><a name="put_backstyle"></a>CStockPropImpl::p ut_BackStyle

Voláním této metody nastavíte styl pozadí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>Parametry

*nBackStyle*<br/>
Nový styl pozadí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_bordercolor"></a><a name="put_bordercolor"></a>CStockPropImpl::p ut_BorderColor

Voláním této metody nastavíte barvu ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>Parametry

*clrBorderColor*<br/>
Nová barva ohraničení Datový typ OLE_COLOR je interně reprezentován jako 32 dlouhé celé číslo.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_borderstyle"></a><a name="put_borderstyle"></a>CStockPropImpl::p ut_BorderStyle

Voláním této metody nastavíte styl ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>Parametry

*nBorderStyle*<br/>
Nový styl ohraničení.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_bordervisible"></a><a name="put_bordervisible"></a>CStockPropImpl::p ut_BorderVisible

Voláním této metody nastavíte hodnotu příznaku, která označuje, zda je okraj ovládacího prvku viditelný nebo nikoli.

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>Parametry

*bBorderVisible*<br/>
TRUE, pokud má být ohraničení viditelné.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_borderwidth"></a><a name="put_borderwidth"></a>CStockPropImpl::p ut_BorderWidth

Voláním této metody nastavíte šířku ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>Parametry

*nBorderWidth*<br/>
Nová šířka ohraničení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_caption"></a><a name="put_caption"></a>CStockPropImpl::p ut_Caption

Voláním této metody nastavíte text, který má být zobrazen s ovládacím prvkem.

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>Parametry

*bstrCaption*<br/>
Text, který se má zobrazit v ovládacím prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_drawmode"></a><a name="put_drawmode"></a>CStockPropImpl::p ut_DrawMode

Voláním této metody nastavíte režim kreslení ovládacího prvku, například barvu pera nebo invertování barev XOR.

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>Parametry

*nDrawMode*<br/>
Nový režim kreslení pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_drawstyle"></a><a name="put_drawstyle"></a>CStockPropImpl::p ut_DrawStyle

Voláním této metody nastavíte styl vykreslování ovládacího prvku, například Solid, čárkovaný nebo tečkovaný.

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>Parametry

*nDrawStyle*<br/>
Nový styl vykreslování ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_drawwidth"></a><a name="put_drawwidth"></a>CStockPropImpl::p ut_DrawWidth

Voláním této metody nastavíte šířku (v pixelech), kterou používají metody kreslení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>Parametry

*nDrawWidth*<br/>
Nová šířka, kterou mají použít metody kreslení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_enabled"></a><a name="put_enabled"></a>CStockPropImpl::p ut_Enabled

Voláním této metody nastavíte hodnotu příznaku, která označuje, zda je ovládací prvek povolen.

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*bEnabled*<br/>
TRUE, pokud je ovládací prvek povolen.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_fillcolor"></a><a name="put_fillcolor"></a>CStockPropImpl::p ut_FillColor

Voláním této metody nastavíte barvu výplně ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>Parametry

*clrFillColor*<br/>
Nová barva výplně ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_fillstyle"></a><a name="put_fillstyle"></a>CStockPropImpl::p ut_FillStyle

Voláním této metody nastavíte styl výplně ovládacího prvku, například Solid, Průhledný nebo mřížkovaný.

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>Parametry

*nFillStyle*<br/>
Nový styl výplně ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_font"></a><a name="put_font"></a>CStockPropImpl::p ut_Font

Voláním této metody nastavíte vlastnosti písma ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Ukazatel na vlastnosti písma ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_forecolor"></a><a name="put_forecolor"></a>CStockPropImpl::p ut_ForeColor

Voláním této metody nastavíte barvu popředí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>Parametry

*clrForeColor*<br/>
Nová barva popředí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_hwnd"></a><a name="put_hwnd"></a>CStockPropImpl::p ut_HWND

Tato metoda vrací E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Rezervovaný.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_FAIL.

### <a name="remarks"></a>Poznámky

Popisovač okna je hodnota jen pro čtení.

##  <a name="cstockpropimplput_mouseicon"></a><a name="put_mouseicon"></a>CStockPropImpl::p ut_MouseIcon

Voláním této metody nastavíte vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metasoubor), které se zobrazí, když je ukazatel myši nad ovládacím prvkem.

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Ukazatel na vlastnosti obrázku grafiky.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_mousepointer"></a><a name="put_mousepointer"></a>CStockPropImpl::p ut_MousePointer

Voláním této metody nastavíte typ ukazatele myši, který se zobrazí, když je ukazatel myši nad ovládacím prvkem, například šipky, příčně nebo přesýpací hodiny.

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>Parametry

*nMousePointer*<br/>
Typ ukazatele myši

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_picture"></a><a name="put_picture"></a>CStockPropImpl::p ut_Picture

Voláním této metody nastavíte zobrazení vlastností obrázku grafiky (ikona, rastrový obrázek nebo metasoubor).

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Ukazatel na vlastnosti obrázku. Další podrobnosti najdete v tématu [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) .

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_readystate"></a><a name="put_readystate"></a>CStockPropImpl::p ut_ReadyState

Voláním této metody nastavíte stav připravenosti ovládacího prvku, například načítání nebo načtení.

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>Parametry

*nReadyState*<br/>
Stav připraveno pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_tabstop"></a><a name="put_tabstop"></a>CStockPropImpl::p ut_TabStop

Voláním této metody nastavíte příznak, který označuje, zda je ovládací prvek zarážka tabulátoru nebo ne.

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>Parametry

*bTabStop*<br/>
TRUE, pokud je ovládací prvek zarážka tabulátoru.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_text"></a><a name="put_text"></a>CStockPropImpl::p ut_Text

Voláním této metody nastavíte text, který se zobrazí s ovládacím prvkem.

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>Parametry

*bstrText*<br/>
Text zobrazený s ovládacím prvkem

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplputvalid"></a><a name="put_valid"></a>CStockPropImpl::p utvalid

Voláním této metody nastavíte příznak, který označuje, zda je ovládací prvek platný nebo nikoli.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>Parametry

*bValid*<br/>
TRUE, pokud je ovládací prvek platný.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="cstockpropimplput_window"></a><a name="put_window"></a>CStockPropImpl::p ut_Window

Tato metoda volá [CStockPropImpl::p ut_HWND](#put_hwnd), která vrací E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Popisovač okna.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_FAIL.

### <a name="remarks"></a>Poznámky

Popisovač okna je hodnota jen pro čtení.

##  <a name="cstockpropimplputref_font"></a><a name="putref_font"></a>CStockPropImpl::p utref_Font

Zavolejte tuto metodu pro nastavení vlastností písma ovládacího prvku s počtem odkazů.

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Ukazatel na vlastnosti písma ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Stejné jako [CStockPropImpl::p ut_Font](#put_font), ale s počtem odkazů.

##  <a name="cstockpropimplputref_mouseicon"></a><a name="putref_mouseicon"></a>CStockPropImpl::p utref_MouseIcon

Voláním této metody nastavíte vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metasoubor), které se zobrazí, když je ukazatel myši nad ovládacím prvkem, s počtem odkazů.

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Ukazatel na vlastnosti obrázku grafiky.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Stejné jako [CStockPropImpl::p ut_MouseIcon](#put_mouseicon), ale s počtem odkazů.

##  <a name="cstockpropimplputref_picture"></a><a name="putref_picture"></a>CStockPropImpl::p utref_Picture

Voláním této metody nastavíte zobrazení vlastností obrázku (ikona, rastrový obrázek nebo metasoubor) na hodnotu počet odkazů.

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Ukazatel na vlastnosti obrázku. Další podrobnosti najdete v tématu [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) .

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Stejné jako [CStockPropImpl::p ut_Picture](#put_picture), ale s počtem odkazů.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[IDispatchImpl – třída](../../atl/reference/idispatchimpl-class.md)
