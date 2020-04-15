---
title: Třída CStockPropImpl
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
ms.openlocfilehash: 0aaeb1b6de0febfd5fc0d41cbcc7bad41c607af4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330676"
---
# <a name="cstockpropimpl-class"></a>Třída CStockPropImpl

Tato třída poskytuje metody pro podporu hodnot vlastností zásob.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

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

*T*<br/>
Třída, která implementuje ovládací prvek `CStockPropImpl`a odvození od .

*Název rozhraní*<br/>
Duální rozhraní odhalující vlastnosti zásob.

*piid*<br/>
Ukazatel na IID `InterfaceName`.

*plibid*<br/>
Ukazatel na LIBID knihovny typů obsahující definici . `InterfaceName`

*wMajor*<br/>
Hlavní verze knihovny typů. Výchozí hodnota je 1.

*wMenší*<br/>
Dílčí verze knihovny typů. Výchozí hodnota je 0.

*tihclass*<br/>
Třída slouží ke správě informací o typu pro *T*. Výchozí hodnota `CComTypeInfoHolder`je .

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|[get_Appearance](#get_appearance)|Volání této metody získat styl malování používá ovládací prvek, například ploché nebo 3D.|
|[get_AutoSize](#get_autosize)|Volání této metody získat stav příznak, který označuje, pokud ovládací prvek nemůže být žádná jiná velikost.|
|[get_BackColor](#get_backcolor)|Volání této metody získat barvu pozadí ovládacího prvku.|
|[get_BackStyle](#get_backstyle)|Volání této metody získat styl pozadí ovládacího prvku, transparentní nebo neprůhledné.|
|[get_BorderColor](#get_bordercolor)|Volání této metody získat barvu ohraničení ovládacího prvku.|
|[get_BorderStyle](#get_borderstyle)|Volání této metody získat styl ohraničení ovládacího prvku.|
|[get_BorderVisible](#get_bordervisible)|Volání této metody získat stav příznak, který označuje, pokud je zobrazeno ohraničení ovládacího prvku nebo ne.|
|[get_BorderWidth](#get_borderwidth)|Volání této metody získat šířku (v pixelech) ohraničení ovládacího prvku.|
|[get_Caption](#get_caption)|Volání této metody získat text zadaný v titulku objektu.|
|[get_DrawMode](#get_drawmode)|Volání této metody získat režim kreslení ovládacího prvku, například XOR pero nebo invertovat barvy.|
|[get_DrawStyle](#get_drawstyle)|Volánítéto metody získat styl kreslení ovládacího prvku, například plné, přerušované nebo tečkované.|
|[get_DrawWidth](#get_drawwidth)|Volání této metody získat šířku výkresu (v obrazových bodech) používá metody kreslení ovládacího prvku.|
|[get_Enabled](#get_enabled)|Volání této metody získat stav příznak, který označuje, pokud je povolen ovládací prvek.|
|[get_FillColor](#get_fillcolor)|Volání této metody získat barvu výplně ovládacího prvku.|
|[get_FillStyle](#get_fillstyle)|Volánítéto metody získat ovládací prvek styl výplně, například plné, průhledné nebo šrafované.|
|[get_Font](#get_font)|Volání této metody získat ukazatel na vlastnosti písma ovládacího prvku.|
|[get_ForeColor](#get_forecolor)|Volání této metody získat barvu popředí ovládacího prvku.|
|[get_HWND](#get_hwnd)|Volání této metody získat popisovač okna přidružené k ovládacímu prvku.|
|[get_MouseIcon](#get_mouseicon)|Volání této metody získat vlastnosti obrázku (ikona, bitmapa nebo metasoubor), které mají být zobrazeny, když je nad ovládacím prvkem.|
|[get_MousePointer](#get_mousepointer)|Volání této metody získat typ ukazatele myši zobrazí, když je myš nad ovládacím prvkem, například šipka, kříž nebo přesýpací hodiny.|
|[get_Picture](#get_picture)|Volánítéto metody získat ukazatel na vlastnosti obrázku grafiky (ikona, bitmapa nebo metasoubor), které mají být zobrazeny.|
|[get_ReadyState](#get_readystate)|Volání této metody získat ovládacího prvku připraven stavu, například načítání nebo načtení.|
|[get_TabStop](#get_tabstop)|Volání této metody získat příznak, který označuje, pokud je ovládací prvek zarážka tabulátoru nebo ne.|
|[get_Text](#get_text)|Volání této metody získat text, který je zobrazen s ovládacím prvkem.|
|[getvalid](#get_valid)|Volání této metody získat stav příznak, který označuje, pokud je ovládací prvek platný nebo ne.|
|[get_Window](#get_window)|Volání této metody získat popisovač okna přidružené k ovládacímu prvku. Shodné s [CStockPropImpl::get_HWND](#get_hwnd).|
|[put_Appearance](#put_appearance)|Volání této metody nastavit styl malování používá ovládací prvek, například ploché nebo 3D.|
|[put_AutoSize](#put_autosize)|Volání této metody nastavit hodnotu příznak, který označuje, pokud ovládací prvek nemůže mít jinou velikost.|
|[put_BackColor](#put_backcolor)|Volání této metody nastavit barvu pozadí ovládacího prvku.|
|[put_BackStyle](#put_backstyle)|Volání této metody nastavit styl pozadí ovládacího prvku.|
|[put_BorderColor](#put_bordercolor)|Volání této metody nastavit barvu ohraničení ovládacího prvku.|
|[put_BorderStyle](#put_borderstyle)|Volání této metody nastavit styl ohraničení ovládacího prvku.|
|[put_BorderVisible](#put_bordervisible)|Volání této metody nastavit hodnotu příznak, který označuje, pokud je zobrazeno ohraničení ovládacího prvku nebo ne.|
|[put_BorderWidth](#put_borderwidth)|Volání této metody nastavit šířku ohraničení ovládacího prvku.|
|[put_Caption](#put_caption)|Volání této metody nastavit text, který má být zobrazen s ovládacím prvkem.|
|[put_DrawMode](#put_drawmode)|Volání této metody nastavit režim kreslení ovládacího prvku, například XOR Pero nebo Invertovat barvy.|
|[put_DrawStyle](#put_drawstyle)|Volánítéto metody nastavit styl kreslení ovládacího prvku, například plné, přerušované nebo tečkované.|
|[put_DrawWidth](#put_drawwidth)|Volání této metody nastavit šířku (v obrazových bodech) používané metody kreslení ovládacího prvku.|
|[put_Enabled](#put_enabled)|Volání této metody nastavit příznak, který označuje, pokud je povolen ovládací prvek.|
|[put_FillColor](#put_fillcolor)|Volání této metody nastavit barvu výplně ovládacího prvku.|
|[put_FillStyle](#put_fillstyle)|Volánítéto metody nastavit styl výplně ovládacího prvku, například plné, průhledné nebo šrafované.|
|[put_Font](#put_font)|Volání této metody nastavit vlastnosti písma ovládacího prvku.|
|[put_ForeColor](#put_forecolor)|Volání této metody nastavit barvu popředí ovládacího prvku.|
|[put_HWND](#put_hwnd)|Tato metoda vrátí E_FAIL.|
|[put_MouseIcon](#put_mouseicon)|Volánítéto metody nastavit vlastnosti obrázku (ikona, bitmapa nebo metasoubor), které mají být zobrazeny, když je myš nad ovládacím prvkem.|
|[put_MousePointer](#put_mousepointer)|Volání této metody nastavit typ ukazatele myši zobrazí, když je myš nad ovládacím prvkem, například šipka, kříž nebo přesýpací hodiny.|
|[put_Picture](#put_picture)|Voláním této metody nastavte vlastnosti obrázku (ikona, bitmapa nebo metasoubor), který se má zobrazit.|
|[put_ReadyState](#put_readystate)|Volání této metody nastavit stav připravenosti ovládacího prvku, například načítání nebo načtení.|
|[put_TabStop](#put_tabstop)|Volání této metody nastavit hodnotu příznak, který označuje, pokud je ovládací prvek zarážka tabulátoru nebo ne.|
|[put_Text](#put_text)|Volání této metody nastavit text, který je zobrazen s ovládacím prvkem.|
|[putvalid](#put_valid)|Volání této metody nastavit příznak, který označuje, pokud je ovládací prvek platný nebo ne.|
|[put_Window](#put_window)|Tato metoda volá [CStockPropImpl::put_HWND](#put_hwnd), který vrátí E_FAIL.|
|[putref_Font](#putref_font)|Volání této metody nastavit vlastnosti písma ovládacího prvku, s počtem odkazů.|
|[putref_MouseIcon](#putref_mouseicon)|Volánítéto metody nastavit vlastnosti obrázku (ikona, bitmapa nebo metasoubor), které mají být zobrazeny, když je myš nad ovládacím prvkem, s počtem odkazů.|
|[putref_Picture](#putref_picture)|Volánítéto metody nastavit vlastnosti obrázku (ikona, bitmapa nebo metasoubor), které mají být zobrazeny, s počtem odkazů.|

## <a name="remarks"></a>Poznámky

`CStockPropImpl`poskytuje **put a** **get** metody pro každou vlastnost zásob. Tyto metody poskytují kód potřebný k nastavení nebo získání datového člena přidruženého ke každé vlastnosti a k upozornění a synchronizaci s kontejnerem při změně jakékoli vlastnosti.

Visual Studio poskytuje podporu pro vlastnosti zásob prostřednictvím svých průvodců. Další informace o přidání vlastností zásob do ovládacího prvku naleznete v [kurzu atl .](../../atl/active-template-library-atl-tutorial.md)

Pro zpětnou `CStockPropImpl` kompatibilitu `get_Window` `put_Window` také zpřístupňuje a metody, které jednoduše volat `get_HWND` a `put_HWND`, v uvedeném pořadí. Výchozí implementace `put_HWND` vrátí E_FAIL protože HWND by měla být vlastnost jen pro čtení.

Následující vlastnosti mají také implementaci **hniloby:**

- Písmo

- Ikona myši

- Obrázek

Stejné tři vlastnosti zásob vyžadují, aby `CComPtr` jejich odpovídající datový člen byl typu nebo jiné třídy, která poskytuje správné počítání odkazů rozhraní pomocí operátoru přiřazení.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

[IDispatchimpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="cstockpropimplget_appearance"></a><a name="get_appearance"></a>CStockPropImpl::get_Appearance

Volání této metody získat styl malování používá ovládací prvek, například ploché nebo 3D.

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>Parametry

*pnVzhled*<br/>
Proměnná, která přijímá styl malby ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_autosize"></a><a name="get_autosize"></a>CStockPropImpl::get_AutoSize

Volání této metody získat stav příznak, který označuje, pokud ovládací prvek nemůže být žádná jiná velikost.

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>Parametry

*pbAutoSize*<br/>
Proměnná, která obdrží stav příznaku. True označuje, že ovládací prvek nemůže mít jinou velikost.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_backcolor"></a><a name="get_backcolor"></a>CStockPropImpl::get_BackColor

Volání této metody získat barvu pozadí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>Parametry

*pclrBackColor*<br/>
Proměnná, která přijímá barvu pozadí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_backstyle"></a><a name="get_backstyle"></a>CStockPropImpl::get_BackStyle

Volání této metody získat styl pozadí ovládacího prvku, transparentní nebo neprůhledné.

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>Parametry

*pnBackStyle*<br/>
Proměnná, která přijímá styl pozadí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_bordercolor"></a><a name="get_bordercolor"></a>CStockPropImpl::get_BorderColor

Volání této metody získat barvu ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>Parametry

*pclrBorderColor*<br/>
Proměnná, která přijímá barvu ohraničení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_borderstyle"></a><a name="get_borderstyle"></a>CStockPropImpl::get_BorderStyle

Volání této metody získat styl ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>Parametry

*pnBorderStyle*<br/>
Proměnná, která přijímá styl ohraničení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_bordervisible"></a><a name="get_bordervisible"></a>CStockPropImpl::get_BorderVisible

Volání této metody získat stav příznak, který označuje, pokud je zobrazeno ohraničení ovládacího prvku nebo ne.

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>Parametry

*pbBorderVisible*<br/>
Proměnná, která obdrží stav příznaku. True označuje, že ohraničení ovládacího prvku je viditelné.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_borderwidth"></a><a name="get_borderwidth"></a>CStockPropImpl::get_BorderWidth

Volání této metody získat šířku ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>Parametry

*pnBorderWidth*<br/>
Proměnná, která přijímá šířku ohraničení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_caption"></a><a name="get_caption"></a>CStockPropImpl::get_Caption

Volání této metody získat text zadaný v titulku objektu.

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>Parametry

*pbstrCaption*<br/>
Text, který má být zobrazen s ovládacím prvkem.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_drawmode"></a><a name="get_drawmode"></a>CStockPropImpl::get_DrawMode

Volání této metody získat režim kreslení ovládacího prvku, například XOR pero nebo invertovat barvy.

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>Parametry

*pnDrawMode*<br/>
Proměnná, která přijímá režim kreslení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_drawstyle"></a><a name="get_drawstyle"></a>CStockPropImpl::get_DrawStyle

Volánítéto metody získat styl kreslení ovládacího prvku, například plné, přerušované nebo tečkované.

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>Parametry

*pnDrawStyle*<br/>
Proměnná, která přijímá styl kreslení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_drawwidth"></a><a name="get_drawwidth"></a>CStockPropImpl::get_DrawWidth

Volání této metody získat šířku výkresu (v obrazových bodech) používá metody kreslení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>Parametry

*pnŠířka*<br/>
Proměnná, která přijímá hodnotu šířky ovládacího prvku v obrazových bodech.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_enabled"></a><a name="get_enabled"></a>CStockPropImpl::get_Enabled

Volání této metody získat stav příznak, který označuje, pokud je povolen ovládací prvek.

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>Parametry

*funkce pbEnabled*<br/>
Proměnná, která obdrží stav příznaku. True označuje, že ovládací prvek je povolen.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_fillcolor"></a><a name="get_fillcolor"></a>CStockPropImpl::get_FillColor

Volání této metody získat barvu výplně ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>Parametry

*pclrFillColor*<br/>
Proměnná, která přijímá barvu výplně ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_fillstyle"></a><a name="get_fillstyle"></a>CStockPropImpl::get_FillStyle

Volání této metody získat ovládací prvek styl výplně, například plné, průhledné nebo šrafované.

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>Parametry

*pnFillStyle*<br/>
Proměnná, která přijímá styl výplně ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_font"></a><a name="get_font"></a>CStockPropImpl::get_Font

Volání této metody získat ukazatel na vlastnosti písma ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parametry

*ppPísmo*<br/>
Proměnná, která obdrží ukazatel na vlastnosti písma ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_forecolor"></a><a name="get_forecolor"></a>CStockPropImpl::get_ForeColor

Volání této metody získat barvu popředí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>Parametry

*pclrForeColor*<br/>
Proměnná, která přijímá barvu popředí ovládacích prvků.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_hwnd"></a><a name="get_hwnd"></a>CStockPropImpl::get_HWND

Volání této metody získat popisovač okna přidružené k ovládacímu prvku.

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parametry

*phWnd*<br/>
Popisovač okna přidružený k ovládacímu prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_mouseicon"></a><a name="get_mouseicon"></a>CStockPropImpl::get_MouseIcon

Volání této metody získat vlastnosti obrázku (ikona, bitmapa nebo metasoubor), které mají být zobrazeny, když je nad ovládacím prvkem.

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parametry

*ppObrázek*<br/>
Proměnná, která obdrží ukazatel na vlastnosti obrázku grafiky.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_mousepointer"></a><a name="get_mousepointer"></a>CStockPropImpl::get_MousePointer

Volání této metody získat typ ukazatele myši zobrazí, když je myš nad ovládacím prvkem, například šipka, kříž nebo přesýpací hodiny.

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>Parametry

*pnMousePointer*<br/>
Proměnná, která přijímá typ ukazatele myši.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_picture"></a><a name="get_picture"></a>CStockPropImpl::get_Picture

Volánítéto metody získat ukazatel na vlastnosti obrázku grafiky (ikona, bitmapa nebo metasoubor), které mají být zobrazeny.

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parametry

*ppObrázek*<br/>
Proměnná, která obdrží ukazatel na vlastnosti obrázku. Další podrobnosti najdete v [tématu IPictureDisp.](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp)

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_readystate"></a><a name="get_readystate"></a>CStockPropImpl::get_ReadyState

Volání této metody získat ovládacího prvku připraven stavu, například načítání nebo načtení.

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>Parametry

*pnReadyState*<br/>
Proměnná, která přijímá stav připravenosti ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_tabstop"></a><a name="get_tabstop"></a>CStockPropImpl::get_TabStop

Volání této metody získat stav příznak, který označuje, pokud je ovládací prvek zarážka tabulátoru nebo ne.

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>Parametry

*pbTabStop*<br/>
Proměnná, která obdrží stav příznaku. True označuje, že ovládací prvek je zarážka tabulátoru.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_text"></a><a name="get_text"></a>CStockPropImpl::get_Text

Volání této metody získat text, který je zobrazen s ovládacím prvkem.

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>Parametry

*pbstrText*<br/>
Text, který je zobrazen s ovládacím prvkem.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplgetvalid"></a><a name="get_valid"></a>CStockPropImpl::getvalid

Volání této metody získat stav příznak, který označuje, pokud je ovládací prvek platný nebo ne.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>Parametry

*pbValid*<br/>
Proměnná, která obdrží stav příznaku. TRUE označuje, že ovládací prvek je platný.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplget_window"></a><a name="get_window"></a>CStockPropImpl::get_Window

Volání této metody získat popisovač okna přidružené k ovládacímu prvku. Shodné s [CStockPropImpl::get_HWND](#get_hwnd).

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parametry

*phWnd*<br/>
Popisovač okna přidružený k ovládacímu prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_appearance"></a><a name="put_appearance"></a>CStockPropImpl::put_Vzhled

Volání této metody nastavit styl malování používá ovládací prvek, například ploché nebo 3D.

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>Parametry

*nVzhled*<br/>
Nový styl malování, který má být použit ovládacím prvkem.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_autosize"></a><a name="put_autosize"></a>CStockPropImpl::put_AutoSize

Volání této metody nastavit hodnotu příznak, který označuje, pokud ovládací prvek nemůže mít jinou velikost.

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>Parametry

*bVelikost auto*<br/>
TRUE, pokud ovládací prvek nemůže mít jinou velikost.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_backcolor"></a><a name="put_backcolor"></a>CStockPropImpl::put_BackColor

Volání této metody nastavit barvu pozadí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>Parametry

*clrBackColor*<br/>
Nová barva pozadí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_backstyle"></a><a name="put_backstyle"></a>CStockPropImpl::put_BackStyle

Volání této metody nastavit styl pozadí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>Parametry

*nStyl zpět*<br/>
Nový styl pozadí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_bordercolor"></a><a name="put_bordercolor"></a>CStockPropImpl::put_BorderColor

Volání této metody nastavit barvu ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>Parametry

*clrBorderColor*<br/>
Nová barva ohraničení. Datový typ OLE_COLOR je interně reprezentován jako 32bitové celé číslo.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_borderstyle"></a><a name="put_borderstyle"></a>CStockPropImpl::put_BorderStyle

Volání této metody nastavit styl ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>Parametry

*nBorderStyle*<br/>
Nový styl ohraničení.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_bordervisible"></a><a name="put_bordervisible"></a>CStockPropImpl::put_BorderVisible

Volání této metody nastavit hodnotu příznak, který označuje, pokud je zobrazeno ohraničení ovládacího prvku nebo ne.

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>Parametry

*bBorderVisible*<br/>
PRAVDA, pokud má být ohraničení viditelné.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_borderwidth"></a><a name="put_borderwidth"></a>CStockPropImpl::put_BorderWidth

Volání této metody nastavit šířku ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>Parametry

*nŠířka ohraničení*<br/>
Nová šířka ohraničení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_caption"></a><a name="put_caption"></a>CStockPropImpl::put_Caption

Volání této metody nastavit text, který má být zobrazen s ovládacím prvkem.

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>Parametry

*titulek bstr*<br/>
Text, který má být zobrazen s ovládacím prvkem.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_drawmode"></a><a name="put_drawmode"></a>CStockPropImpl::put_DrawMode

Volání této metody nastavit režim kreslení ovládacího prvku, například XOR Pero nebo Invertovat barvy.

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>Parametry

*nRežim drawmode*<br/>
Nový režim kreslení pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_drawstyle"></a><a name="put_drawstyle"></a>CStockPropImpl::put_DrawStyle

Volánítéto metody nastavit styl kreslení ovládacího prvku, například plné, přerušované nebo tečkované.

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>Parametry

*nStyl slosování*<br/>
Nový styl kreslení pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_drawwidth"></a><a name="put_drawwidth"></a>CStockPropImpl::put_DrawWidth

Volání této metody nastavit šířku (v obrazových bodech) používané metody kreslení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>Parametry

*nŠířka_*<br/>
Nová šířka, která má být použita metodami kreslení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_enabled"></a><a name="put_enabled"></a>CStockPropImpl::put_Enabled

Volání této metody nastavit hodnotu příznak, který označuje, pokud je povolen ovládací prvek.

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*bPovoleno*<br/>
TRUE, pokud je ovládací prvek povolen.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_fillcolor"></a><a name="put_fillcolor"></a>CStockPropImpl::put_FillColor

Volání této metody nastavit barvu výplně ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>Parametry

*clrFillColor*<br/>
Nová barva výplně ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_fillstyle"></a><a name="put_fillstyle"></a>CStockPropImpl::put_FillStyle

Volánítéto metody nastavit styl výplně ovládacího prvku, například plné, průhledné nebo šrafované.

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>Parametry

*nFillStyle*<br/>
Nový styl výplně pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_font"></a><a name="put_font"></a>CStockPropImpl::put_Font

Volání této metody nastavit vlastnosti písma ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*písmo*<br/>
Ukazatel na vlastnosti písma ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_forecolor"></a><a name="put_forecolor"></a>CStockPropImpl::put_ForeColor

Volání této metody nastavit barvu popředí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>Parametry

*clrForeColor*<br/>
Nová barva popředí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_hwnd"></a><a name="put_hwnd"></a>CStockPropImpl::put_HWND

Tato metoda vrátí E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Vyhrazeno.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_FAIL.

### <a name="remarks"></a>Poznámky

Popisovač okna je jen pro čtení hodnotu.

## <a name="cstockpropimplput_mouseicon"></a><a name="put_mouseicon"></a>CStockPropImpl::put_MouseIcon

Volánítéto metody nastavit vlastnosti obrázku (ikona, bitmapa nebo metasoubor), které mají být zobrazeny, když je myš nad ovládacím prvkem.

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pObrázek*<br/>
Ukazatel na vlastnosti obrázku grafiky.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_mousepointer"></a><a name="put_mousepointer"></a>CStockPropImpl::put_MousePointer

Volání této metody nastavit typ ukazatele myši zobrazí, když je myš nad ovládacím prvkem, například šipka, kříž nebo přesýpací hodiny.

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>Parametry

*nUkazatel myši*<br/>
Typ ukazatele myši.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_picture"></a><a name="put_picture"></a>CStockPropImpl::put_Picture

Voláním této metody nastavte vlastnosti obrázku (ikona, bitmapa nebo metasoubor), který se má zobrazit.

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pObrázek*<br/>
Ukazatel na vlastnosti obrázku. Další podrobnosti najdete v [tématu IPictureDisp.](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp)

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_readystate"></a><a name="put_readystate"></a>CStockPropImpl::put_ReadyState

Volání této metody nastavit stav připravenosti ovládacího prvku, například načítání nebo načtení.

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>Parametry

*nReadyState*<br/>
Ovládací prvek je připraven.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_tabstop"></a><a name="put_tabstop"></a>CStockPropImpl::put_TabStop

Volání této metody nastavit příznak, který označuje, pokud je ovládací prvek zarážka tabulátoru nebo ne.

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>Parametry

*bTabStop*<br/>
TRUE, pokud je ovládací prvek zarážka tabulátoru.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_text"></a><a name="put_text"></a>CStockPropImpl::put_Text

Volání této metody nastavit text, který je zobrazen s ovládacím prvkem.

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>Parametry

*bstrText*<br/>
Text, který je zobrazen s ovládacím prvkem.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplputvalid"></a><a name="put_valid"></a>CStockPropImpl::putvalid

Volání této metody nastavit příznak, který označuje, pokud je ovládací prvek platný nebo ne.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>Parametry

*bValid*<br/>
TRUE, pokud je ovládací prvek platný.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cstockpropimplput_window"></a><a name="put_window"></a>CStockPropImpl::put_Window

Tato metoda volá [CStockPropImpl::put_HWND](#put_hwnd), který vrátí E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Klika okna.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_FAIL.

### <a name="remarks"></a>Poznámky

Popisovač okna je jen pro čtení hodnotu.

## <a name="cstockpropimplputref_font"></a><a name="putref_font"></a>CStockPropImpl::putref_Font

Volání této metody nastavit vlastnosti písma ovládacího prvku, s počtem odkazů.

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*písmo*<br/>
Ukazatel na vlastnosti písma ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Stejné jako [CStockPropImpl::put_Font](#put_font), ale s počtem odkazů.

## <a name="cstockpropimplputref_mouseicon"></a><a name="putref_mouseicon"></a>CStockPropImpl::putref_MouseIcon

Volánítéto metody nastavit vlastnosti obrázku (ikona, bitmapa nebo metasoubor), které mají být zobrazeny, když je myš nad ovládacím prvkem, s počtem odkazů.

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pObrázek*<br/>
Ukazatel na vlastnosti obrázku grafiky.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Stejné jako [CStockPropImpl::put_MouseIcon](#put_mouseicon), ale s počtem odkazů.

## <a name="cstockpropimplputref_picture"></a><a name="putref_picture"></a>CStockPropImpl::putref_Picture

Volánítéto metody nastavit vlastnosti obrázku (ikona, bitmapa nebo metasoubor), které mají být zobrazeny, s počtem odkazů.

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pObrázek*<br/>
Ukazatel na vlastnosti obrázku. Další podrobnosti najdete v [tématu IPictureDisp.](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp)

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Stejné jako [CStockPropImpl::put_Picture](#put_picture), ale s počtem odkazů.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída IDispatchimpl](../../atl/reference/idispatchimpl-class.md)
