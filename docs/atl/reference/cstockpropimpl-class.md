---
title: Cstockpropimpl – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 7befbce6e062bdb7944c2ed1f351d6927adfd75a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480857"
---
# <a name="cstockpropimpl-class"></a>Cstockpropimpl – třída

Tato třída poskytuje metody pro podporu uložených vlastností hodnoty.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE CStockPropImpl : public IDispatchImpl<InterfaceName, piid,
plibid,
    wMajor,
wMinor,
    tihclass>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Třída implementace ovládacího prvku a odvozený od `CStockPropImpl`.

*InterfaceName*<br/>
Duální rozhraní vystavení uložených vlastností.

*piid*<br/>
Ukazatel na IID `InterfaceName`.

*plibid*<br/>
Ukazatel na LIBID knihovnu typů obsahující definice `InterfaceName`.

*wMajor*<br/>
Hlavní verze knihovny typů. Výchozí hodnota je 1.

*wMinor*<br/>
Dílčí verze knihovny typů. Výchozí hodnota je 0.

*tihclass*<br/>
Třída, která slouží ke správě informace o typu *T*. Výchozí hodnota je `CComTypeInfoHolder`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|[get_Appearance](#get_appearance)|Volejte tuto metodu za účelem získání malířského styl použit v ovládacím prvku, například ploché nebo 3D.|
|[get_AutoSize](#get_autosize)|Volejte tuto metodu za účelem získání stavu příznak, který určuje, zda ovládací prvek nemůže být libovolné velikosti.|
|[get_BackColor](#get_backcolor)|Volejte tuto metodu za účelem získání barva pozadí ovládacího prvku.|
|[get_BackStyle](#get_backstyle)|Volejte tuto metodu za účelem získání průhledného nebo neprůhledného pozadí styl ovládacího prvku.|
|[get_BorderColor](#get_bordercolor)|Volejte tuto metodu za účelem získání Barva ohraničení ovládacího prvku.|
|[get_BorderStyle](#get_borderstyle)|Volejte tuto metodu za účelem získání styl ohraničení ovládacího prvku.|
|[get_BorderVisible](#get_bordervisible)|Volejte tuto metodu za účelem získání stavu příznak označující, zda je viditelná ohraničení ovládacího prvku, nebo ne.|
|[get_BorderWidth](#get_borderwidth)|Volejte tuto metodu za účelem získání šířku ohraničení ovládacího prvku (v pixelech).|
|[get_Caption](#get_caption)|Volejte tuto metodu za účelem získání textem zadaným v objektu titulek.|
|[get_DrawMode](#get_drawmode)|Voláním této metody k získání ovládacího prvku režim kreslení, například XOR pera nebo Invertovat barvy.|
|[get_DrawStyle](#get_drawstyle)|Volání této metody k získání styl vykreslování ovládacího prvku, například solid přerušovanou nebo tečkovaná.|
|[get_DrawWidth](#get_drawwidth)|Volejte tuto metodu za účelem získání šířku (v pixelech) používané metody vykreslení ovládacího prvku.|
|[get_Enabled](#get_enabled)|Volejte tuto metodu za účelem získání stavu příznak označující, zda je povolen ovládací prvek.|
|[get_FillColor](#get_fillcolor)|Volejte tuto metodu za účelem získání Barva výplně ovládacího prvku.|
|[get_FillStyle](#get_fillstyle)|Volejte tuto metodu za účelem získání styl výplně ovládacího prvku, například plná, transparentní nebo zasílána mezi.|
|[get_Font](#get_font)|Volejte tuto metodu za účelem získání ukazatele na vlastnosti font ovládacího prvku.|
|[get_ForeColor](#get_forecolor)|Volejte tuto metodu za účelem získání Barva popředí ovládacího prvku.|
|[get_HWND](#get_hwnd)|Voláním této metody lze získat ovladač okna přidružený k ovládacímu prvku.|
|[get_MouseIcon](#get_mouseicon)|Volejte tuto metodu za účelem získání vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metafile), který se má zobrazit při přesunutí myši nad ovládací prvek.|
|[get_MousePointer](#get_mousepointer)|Volejte tuto metodu za účelem získání typu ukazatel myši zobrazí, když je ukazatel myši nad ovládací prvek, například, šipku, různé nebo přesýpací hodiny.|
|[get_Picture](#get_picture)|Volejte tuto metodu za účelem získání ukazatele na vlastnosti obrázku grafiky (ikonu, rastrový obrázek nebo metasoubor), který se má zobrazit.|
|[get_ReadyState](#get_readystate)|Volejte tuto metodu za účelem získání stavu Připraveno ovládacího prvku, třeba načítání nebo načíst.|
|[get_TabStop](#get_tabstop)|Volejte tuto metodu za účelem získání příznak označující, zda je ovládací prvek zarážku nebo ne.|
|[get_Text](#get_text)|Volejte tuto metodu za účelem získání textu, který se zobrazí u ovládacího prvku.|
|[getvalid](#get_valid)|Volejte tuto metodu za účelem získání stavu příznak označující, zda ovládací prvek je platný, nebo ne.|
|[get_Window](#get_window)|Voláním této metody lze získat ovladač okna přidružený k ovládacímu prvku. Stejné jako [CStockPropImpl::get_HWND](#get_hwnd).|
|[put_Appearance](#put_appearance)|Voláním této metody lze nastavit styl malířského použit v ovládacím prvku, například ploché nebo 3D.|
|[put_AutoSize](#put_autosize)|Voláním této metody nastavte hodnotu příznaku, který určuje, zda ovládací prvek nemůže být libovolné velikosti.|
|[put_BackColor](#put_backcolor)|Voláním této metody lze nastavit barvu pozadí ovládacího prvku.|
|[put_BackStyle](#put_backstyle)|Voláním této metody lze nastavit styl ovládacího prvku na pozadí.|
|[put_BorderColor](#put_bordercolor)|Voláním této metody lze nastavit barvu ohraničení ovládacího prvku.|
|[put_BorderStyle](#put_borderstyle)|Voláním této metody lze nastavit styl ohraničení ovládacího prvku.|
|[put_BorderVisible](#put_bordervisible)|Voláním této metody nastavte hodnotu příznaku, který určuje, zda je ovládací prvek ohraničení viditelné nebo ne.|
|[put_BorderWidth](#put_borderwidth)|Voláním této metody nastavte šířku ohraničení ovládacího prvku.|
|[put_Caption](#put_caption)|Voláním této metody lze nastavit text, který se má zobrazit pomocí ovládacího prvku.|
|[put_DrawMode](#put_drawmode)|Voláním této metody lze nastavit výkresu režim ovládacího prvku, například XOR pera nebo Invertovat barvy.|
|[put_DrawStyle](#put_drawstyle)|Volání této metody nastavte styl vykreslování ovládacího prvku, například solid přerušovanou nebo tečkovaná.|
|[put_DrawWidth](#put_drawwidth)|Voláním této metody nastavte šířku (v pixelech) používané metody vykreslení ovládacího prvku.|
|[put_Enabled](#put_enabled)|Voláním této metody nastavte příznak označující, zda je povolen ovládací prvek.|
|[put_FillColor](#put_fillcolor)|Voláním této metody lze nastavit barvu výplně ovládacího prvku.|
|[put_FillStyle](#put_fillstyle)|Volání této metody nastavte styl výplně ovládacího prvku, například plná, transparentní nebo zasílána mezi.|
|[put_Font](#put_font)|Voláním této metody lze nastavit vlastnosti font ovládacího prvku.|
|[put_ForeColor](#put_forecolor)|Voláním této metody lze nastavit barvu popředí ovládacího prvku.|
|[put_HWND](#put_hwnd)|Tato metoda vrátí E_FAIL.|
|[put_MouseIcon](#put_mouseicon)|Voláním této metody lze nastavit vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metafile), který se má zobrazit při přesunutí myši nad ovládací prvek.|
|[put_MousePointer](#put_mousepointer)|Voláním této metody lze nastavit typ ukazatele myši zobrazí, když je ukazatel myši nad ovládací prvek, například, šipku, různé nebo přesýpací hodiny.|
|[put_Picture](#put_picture)|Voláním této metody lze nastavit vlastnosti obrázku grafiky (ikonu, rastrový obrázek nebo metasoubor), který se má zobrazit.|
|[put_ReadyState](#put_readystate)|Volání této metody k nastavení stavu Připraveno ovládacího prvku, třeba načítání nebo načíst.|
|[put_TabStop](#put_tabstop)|Voláním této metody nastavte hodnotu příznaku, která určuje, zda je ovládací prvek zarážku nebo ne.|
|[put_Text](#put_text)|Voláním této metody lze nastavit text, který se zobrazí u ovládacího prvku.|
|[putvalid](#put_valid)|Voláním této metody nastavte příznak označující, zda ovládací prvek je platný, nebo ne.|
|[put_Window](#put_window)|Tato metoda volá [CStockPropImpl::put_HWND](#put_hwnd), která vrací E_FAIL.|
|[putref_Font](#putref_font)|Voláním této metody lze nastavit vlastnosti ovládacího prvku písma, se počet odkazů.|
|[putref_MouseIcon](#putref_mouseicon)|Voláním této metody lze nastavit vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metafile), který se má zobrazit při přesunutí myši nad ovládací prvek, se počet odkazů.|
|[putref_Picture](#putref_picture)|Voláním této metody lze nastavit vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metafile), který se má zobrazit, se počet odkazů.|

## <a name="remarks"></a>Poznámky

`CStockPropImpl` poskytuje **umístit** a **získat** metody pro každou uloženou vlastnost. Tyto metody poskytují kód nastavit nebo získat datový člen spojené s každou vlastnost a upozornění a synchronizovat s kontejnerem při libovolné vlastnosti.

Visual C++ poskytuje podporu pro základní vlastnosti prostřednictvím jeho průvodců. Další informace o přidání uložených vlastností do ovládacího prvku, naleznete v tématu [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md).

Z důvodu zpětné kompatibility `CStockPropImpl` také poskytuje `get_Window` a `put_Window` metody, které jednoduše zavoláte `get_HWND` a `put_HWND`v uvedeném pořadí. Výchozí implementace `put_HWND` vrátí E_FAIL od HWND musí být vlastnost jen pro čtení.

Také mít následující vlastnosti **typu putref** implementace:

- Písma

- MouseIcon

- Obrázek

Stejné tři základní vlastnosti vyžadují jejich odpovídající datový člen typu `CComPtr` nebo jiné třídy, který poskytuje odkaz na správné rozhraní počítání prostřednictvím operátoru přiřazení.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

[Idispatchimpl –](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="get_appearance"></a>  CStockPropImpl::get_Appearance

Volejte tuto metodu za účelem získání malířského styl použit v ovládacím prvku, například ploché nebo 3D.

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>Parametry

*pnAppearance*<br/>
Proměnná, která přijímá malířského stylu ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_autosize"></a>  CStockPropImpl::get_AutoSize

Volejte tuto metodu za účelem získání stavu příznak, který určuje, zda ovládací prvek nemůže být libovolné velikosti.

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>Parametry

*pbAutoSize*<br/>
Proměnná, která přijímá stav příznaku. Hodnota TRUE označuje, že ovládací prvek nemůže být libovolné velikosti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_backcolor"></a>  CStockPropImpl::get_BackColor

Volejte tuto metodu za účelem získání barva pozadí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>Parametry

*pclrBackColor*<br/>
Proměnná, která přijímá barva pozadí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_backstyle"></a>  CStockPropImpl::get_BackStyle

Volejte tuto metodu za účelem získání průhledného nebo neprůhledného pozadí styl ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>Parametry

*pnBackStyle*<br/>
Proměnná, která přijímá styl pozadí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_bordercolor"></a>  CStockPropImpl::get_BorderColor

Volejte tuto metodu za účelem získání Barva ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>Parametry

*pclrBorderColor*<br/>
Proměnná, která přijímá Barva ohraničení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_borderstyle"></a>  CStockPropImpl::get_BorderStyle

Volejte tuto metodu za účelem získání styl ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>Parametry

*pnBorderStyle*<br/>
Proměnná, která přijímá styl ohraničení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_bordervisible"></a>  CStockPropImpl::get_BorderVisible

Volejte tuto metodu za účelem získání stavu příznak označující, zda je viditelná ohraničení ovládacího prvku, nebo ne.

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>Parametry

*pbBorderVisible*<br/>
Proměnná, která přijímá stav příznaku. Hodnota TRUE označuje, že je viditelná ohraničení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_borderwidth"></a>  CStockPropImpl::get_BorderWidth

Volejte tuto metodu za účelem získání Tloušťka ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>Parametry

*pnBorderWidth*<br/>
Proměnná, která přijímá šířka ohraničení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_caption"></a>  CStockPropImpl::get_Caption

Volejte tuto metodu za účelem získání textem zadaným v objektu titulek.

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>Parametry

*pbstrCaption*<br/>
Text, který se má zobrazit pomocí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_drawmode"></a>  CStockPropImpl::get_DrawMode

Voláním této metody k získání ovládacího prvku režim kreslení, například XOR pera nebo Invertovat barvy.

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>Parametry

*pnDrawMode*<br/>
Proměnná, která přijímá režim kreslení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_drawstyle"></a>  CStockPropImpl::get_DrawStyle

Volání této metody k získání styl vykreslování ovládacího prvku, například solid přerušovanou nebo tečkovaná.

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>Parametry

*pnDrawStyle*<br/>
Proměnná, která přijímá styl vykreslování ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_drawwidth"></a>  CStockPropImpl::get_DrawWidth

Volejte tuto metodu za účelem získání šířku (v pixelech) používané metody vykreslení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>Parametry

*pnDrawWidth*<br/>
Proměnná, která přijímá hodnotu šířku ovládacího prvku, v pixelech.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_enabled"></a>  CStockPropImpl::get_Enabled

Volejte tuto metodu za účelem získání stavu příznak označující, zda je povolen ovládací prvek.

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>Parametry

*pbEnabled*<br/>
Proměnná, která přijímá stav příznaku. Hodnota TRUE označuje, zda je povoleno ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_fillcolor"></a>  CStockPropImpl::get_FillColor

Volejte tuto metodu za účelem získání Barva výplně ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>Parametry

*pclrFillColor*<br/>
Proměnná, která přijímá Barva výplně ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_fillstyle"></a>  CStockPropImpl::get_FillStyle

Volejte tuto metodu za účelem získání styl výplně ovládacího prvku, například plná, transparentní nebo crosshatched.

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>Parametry

*pnFillStyle*<br/>
Proměnná, která přijímá styl výplně ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_font"></a>  CStockPropImpl::get_Font

Volejte tuto metodu za účelem získání ukazatele na vlastnosti font ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont*<br/>
Proměnná, která přijímá ukazatel na vlastnosti font ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_forecolor"></a>  CStockPropImpl::get_ForeColor

Volejte tuto metodu za účelem získání Barva popředí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>Parametry

*pclrForeColor*<br/>
Proměnná, která přijímá barvu popředí ovládacích prvků.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_hwnd"></a>  CStockPropImpl::get_HWND

Voláním této metody lze získat ovladač okna přidružený k ovládacímu prvku.

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parametry

*phWnd*<br/>
Popisovač okna přidružený k ovládacímu prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_mouseicon"></a>  CStockPropImpl::get_MouseIcon

Volejte tuto metodu za účelem získání vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metafile), který se má zobrazit při přesunutí myši nad ovládací prvek.

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parametry

*ppPicture*<br/>
Proměnná, která přijímá ukazatel na obrázek vlastnosti obrázku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_mousepointer"></a>  CStockPropImpl::get_MousePointer

Volejte tuto metodu za účelem získání typu ukazatel myši zobrazí, když je ukazatel myši nad ovládací prvek, například, šipku, různé nebo přesýpací hodiny.

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>Parametry

*pnMousePointer*<br/>
Proměnná, která přijímá typ ukazatele myši.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_picture"></a>  CStockPropImpl::get_Picture

Volejte tuto metodu za účelem získání ukazatele na vlastnosti obrázku grafiky (ikonu, rastrový obrázek nebo metasoubor), který se má zobrazit.

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parametry

*ppPicture*<br/>
Proměnná, která přijímá ukazatel na vlastnosti obrázku. Zobrazit [IPictureDisp](https://msdn.microsoft.com/library/windows/desktop/ms680762) další podrobnosti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_readystate"></a>  CStockPropImpl::get_ReadyState

Volejte tuto metodu za účelem získání stavu Připraveno ovládacího prvku, třeba načítání nebo načíst.

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>Parametry

*pnReadyState*<br/>
Proměnná, která přijímá připraveném stavu ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_tabstop"></a>  CStockPropImpl::get_TabStop

Volejte tuto metodu za účelem získání stavu příznak označující, zda je ovládací prvek zarážku nebo ne.

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>Parametry

*pbTabStop*<br/>
Proměnná, která přijímá stav příznaku. Hodnota TRUE označuje, že je ovládací prvek zarážku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_text"></a>  CStockPropImpl::get_Text

Volejte tuto metodu za účelem získání textu, který se zobrazí u ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>Parametry

*pbstrText*<br/>
Text, který se zobrazí u ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_valid"></a>  CStockPropImpl::getvalid

Volejte tuto metodu za účelem získání stavu příznak označující, zda ovládací prvek je platný, nebo ne.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>Parametry

*pbValid*<br/>
Proměnná, která přijímá stav příznaku. Hodnota TRUE označuje, že je platný.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="get_window"></a>  CStockPropImpl::get_Window

Voláním této metody lze získat ovladač okna přidružený k ovládacímu prvku. Stejné jako [CStockPropImpl::get_HWND](#get_hwnd).

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parametry

*phWnd*<br/>
Popisovač okna přidružený k ovládacímu prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_appearance"></a>  CStockPropImpl::put_Appearance

Voláním této metody lze nastavit styl malířského použit v ovládacím prvku, například ploché nebo 3D.

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>Parametry

*nAppearance*<br/>
Nový styl malířského používané ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_autosize"></a>  CStockPropImpl::put_AutoSize

Voláním této metody nastavte hodnotu příznaku, která určuje, zda ovládací prvek nemůže být libovolné velikosti.

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>Parametry

*bAutoSize*<br/>
Hodnota TRUE, pokud ovládací prvek nemůže být libovolné velikosti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_backcolor"></a>  CStockPropImpl::put_BackColor

Voláním této metody lze nastavit barvu pozadí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>Parametry

*clrBackColor*<br/>
Nová barva pozadí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_backstyle"></a>  CStockPropImpl::put_BackStyle

Voláním této metody lze nastavit styl ovládacího prvku na pozadí.

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>Parametry

*nBackStyle*<br/>
Nový styl pozadí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_bordercolor"></a>  CStockPropImpl::put_BorderColor

Voláním této metody lze nastavit barvu ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>Parametry

*clrBorderColor*<br/>
Nová barva ohraničení. Datový typ OLE_COLOR interně reprezentována jako 32-bit dlouhé celé číslo.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_borderstyle"></a>  CStockPropImpl::put_BorderStyle

Voláním této metody lze nastavit styl ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>Parametry

*nBorderStyle*<br/>
Nový styl ohraničení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_bordervisible"></a>  CStockPropImpl::put_BorderVisible

Voláním této metody nastavte hodnotu příznaku, který určuje, zda je ovládací prvek ohraničení viditelné nebo ne.

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>Parametry

*bBorderVisible*<br/>
TRUE, pokud má být viditelné ohraničení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_borderwidth"></a>  CStockPropImpl::put_BorderWidth

Voláním této metody nastavte šířku ohraničení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>Parametry

*nBorderWidth*<br/>
Nové Tloušťka ohraničení ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_caption"></a>  CStockPropImpl::put_Caption

Voláním této metody lze nastavit text, který se má zobrazit pomocí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>Parametry

*bstrCaption*<br/>
Text, který se má zobrazit pomocí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_drawmode"></a>  CStockPropImpl::put_DrawMode

Voláním této metody lze nastavit výkresu režim ovládacího prvku, například XOR pera nebo Invertovat barvy.

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>Parametry

*nDrawMode*<br/>
Nový režim vykreslování ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_drawstyle"></a>  CStockPropImpl::put_DrawStyle

Volání této metody nastavte styl vykreslování ovládacího prvku, například solid přerušovanou nebo tečkovaná.

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>Parametry

*nDrawStyle*<br/>
Nový styl vykreslování ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_drawwidth"></a>  CStockPropImpl::put_DrawWidth

Voláním této metody nastavte šířku (v pixelech) používané metody vykreslení ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>Parametry

*nDrawWidth*<br/>
Nové šířku, která má být použit v ovládacím prvku pro kreslení metody.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_enabled"></a>  CStockPropImpl::put_Enabled

Voláním této metody nastavte hodnotu příznaku, která určuje, zda je povolen ovládací prvek.

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*bEnabled*<br/>
TRUE, pokud je povoleno ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_fillcolor"></a>  CStockPropImpl::put_FillColor

Voláním této metody lze nastavit barvu výplně ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>Parametry

*clrFillColor*<br/>
Nová barva výplně ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_fillstyle"></a>  CStockPropImpl::put_FillStyle

Volání této metody nastavte styl výplně ovládacího prvku, například plná, transparentní nebo zasílána mezi.

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>Parametry

*nFillStyle*<br/>
Nový styl výplně ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_font"></a>  CStockPropImpl::put_Font

Voláním této metody lze nastavit vlastnosti font ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Ukazatel na vlastnosti font ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_forecolor"></a>  CStockPropImpl::put_ForeColor

Voláním této metody lze nastavit barvu popředí ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>Parametry

*clrForeColor*<br/>
Nová barva popředí ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_hwnd"></a>  CStockPropImpl::put_HWND

Tato metoda vrátí E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>Parametry

*/&ast; hWnd &ast;/*<br/>
Vyhrazená.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_FAIL.

### <a name="remarks"></a>Poznámky

Popisovač okna je hodnota jen pro čtení.

##  <a name="put_mouseicon"></a>  CStockPropImpl::put_MouseIcon

Voláním této metody lze nastavit vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metafile), který se má zobrazit při přesunutí myši nad ovládací prvek.

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Ukazatel na obrázek vlastnosti obrázku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_mousepointer"></a>  CStockPropImpl::put_MousePointer

Voláním této metody lze nastavit typ ukazatele myši zobrazí, když je ukazatel myši nad ovládací prvek, například, šipku, různé nebo přesýpací hodiny.

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>Parametry

*nMousePointer*<br/>
Typ ukazatele myši.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_picture"></a>  CStockPropImpl::put_Picture

Voláním této metody lze nastavit vlastnosti obrázku grafiky (ikonu, rastrový obrázek nebo metasoubor), který se má zobrazit.

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Ukazatel na vlastnosti obrázku. Zobrazit [IPictureDisp](https://msdn.microsoft.com/library/windows/desktop/ms680762) další podrobnosti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_readystate"></a>  CStockPropImpl::put_ReadyState

Volání této metody k nastavení stavu Připraveno ovládacího prvku, třeba načítání nebo načíst.

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>Parametry

*nReadyState*<br/>
Ovládací prvek stavu Připraveno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_tabstop"></a>  CStockPropImpl::put_TabStop

Voláním této metody nastavte příznak označující, zda je ovládací prvek zarážku nebo ne.

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>Parametry

*bTabStop*<br/>
TRUE, pokud je ovládací prvek zarážku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_text"></a>  CStockPropImpl::put_Text

Voláním této metody lze nastavit text, který se zobrazí u ovládacího prvku.

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>Parametry

*bstrText*<br/>
Text, který se zobrazí u ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_valid"></a>  CStockPropImpl::putvalid

Voláním této metody nastavte příznak označující, zda ovládací prvek je platný, nebo ne.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>Parametry

*bValid*<br/>
TRUE, pokud ovládací prvek je platný.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="put_window"></a>  CStockPropImpl::put_Window

Tato metoda volá [CStockPropImpl::put_HWND](#put_hwnd), která vrací E_FAIL.

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

##  <a name="putref_font"></a>  CStockPropImpl::putref_Font

Voláním této metody lze nastavit vlastnosti ovládacího prvku písma, se počet odkazů.

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Ukazatel na vlastnosti font ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Stejné jako [CStockPropImpl::put_Font](#put_font), ale počet odkazů.

##  <a name="putref_mouseicon"></a>  CStockPropImpl::putref_MouseIcon

Voláním této metody lze nastavit vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metafile), který se má zobrazit při přesunutí myši nad ovládací prvek, se počet odkazů.

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Ukazatel na obrázek vlastnosti obrázku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Stejné jako [CStockPropImpl::put_MouseIcon](#put_mouseicon), ale počet odkazů.

##  <a name="putref_picture"></a>  CStockPropImpl::putref_Picture

Voláním této metody lze nastavit vlastnosti obrázku grafiky (ikona, rastrový obrázek nebo metafile), který se má zobrazit, se počet odkazů.

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Ukazatel na vlastnosti obrázku. Zobrazit [IPictureDisp](https://msdn.microsoft.com/library/windows/desktop/ms680762) další podrobnosti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Stejné jako [CStockPropImpl::put_Picture](#put_picture), ale počet odkazů.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[IDispatchImpl – třída](../../atl/reference/idispatchimpl-class.md)
