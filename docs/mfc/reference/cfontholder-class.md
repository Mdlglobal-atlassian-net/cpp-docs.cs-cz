---
title: CFontHolder – třída
ms.date: 11/04/2016
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
helpviewer_keywords:
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
ms.openlocfilehash: 6a053f127123a9ca21853189b9458738b217ee2b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373814"
---
# <a name="cfontholder-class"></a>CFontHolder – třída

Implementuje vlastnost stock Font a zapouzdřuje funkce `IFont` objektu písma systému Windows a rozhraní.

## <a name="syntax"></a>Syntaxe

```
class CFontHolder
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CFontHolder::CFontHolder](#cfontholder)|Vytvoří `CFontHolder` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFontHolder::GetDisplayString](#getdisplaystring)|Načte řetězec zobrazený v prohlížeči vlastností kontejneru.|
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Vrátí rozhraní písma. `IDispatch`|
|[CFontHolder::GetFontHandle](#getfonthandle)|Vrátí popisovač písma systému Windows.|
|[CFontHolder::Inicializovat písmo](#initializefont)|Inicializuje `CFontHolder` objekt.|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Načte informace pro související písmo.|
|[CFontHolder::ReleaseFont](#releasefont)|Odpojí `CFontHolder` objekt `IFont` od `IFontNotification` rozhraní a.|
|[CFontHolder::Vybrat](#select)|Vybere prostředek písma do kontextu zařízení.|
|[CFontHolder::SetFont](#setfont)|Připojí objekt `CFontHolder` k `IFont` rozhraní.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|Ukazatel na `CFontHolder` `IFont` rozhraní objektu.|

## <a name="remarks"></a>Poznámky

`CFontHolder`nemá základní třídu.

Tato třída slouží k implementaci vlastních vlastností písma pro ovládací prvek. Informace o vytváření těchto vlastností naleznete v článku [Ovládací prvky ActiveX: Použití písem](../../mfc/mfc-activex-controls-using-fonts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CFontHolder`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="cfontholdercfontholder"></a><a name="cfontholder"></a>CFontHolder::CFontHolder

Vytvoří `CFontHolder` objekt.

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>Parametry

*pNotify*<br/>
Ukazatel na rozhraní `IPropertyNotifySink` písma.

### <a name="remarks"></a>Poznámky

Před použitím `InitializeFont` je nutné volat inicializaci výsledného objektu.

## <a name="cfontholdergetdisplaystring"></a><a name="getdisplaystring"></a>CFontHolder::GetDisplayString

Načte řetězec, který lze zobrazit v prohlížeči vlastností kontejneru.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parametry

*strValue*<br/>
Odkaz na [CString,](../../atl-mfc-shared/reference/cstringt-class.md) který je držet řetězec zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je řetězec úspěšně načten; jinak 0.

## <a name="cfontholdergetfontdispatch"></a><a name="getfontdispatch"></a>CFontHolder::GetFontDispatch

Volání této funkce načíst ukazatel na rozhraní odeslání písma.

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CFontHolder` `IFontDisp` rozhraní objektu. Všimněte si, `GetFontDispatch` že `IUnknown::Release` funkce, která volá musí volat na tento ukazatel rozhraní, když se provádí s ním.

### <a name="remarks"></a>Poznámky

Volejte `InitializeFont` před `GetFontDispatch`voláním .

## <a name="cfontholdergetfonthandle"></a><a name="getfonthandle"></a>CFontHolder::GetFontHandle

Volání této funkce získat popisovač písma systému Windows.

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parametry

*cyLogical*<br/>
Výška v logických jednotkách obdélníku, ve kterém je nakreslena ovládací prvek.

*cyhimetrický*<br/>
Výška ovládacího prvku v MM_HIMETRIC jednotkách.

### <a name="return-value"></a>Návratová hodnota

Úchyt k objektu Font; jinak NULL.

### <a name="remarks"></a>Poznámky

Poměr *cyLogical* a *cyHimetric k* výpočtu správné velikosti zobrazení v logických jednotkách pro velikost bodu písma vyjádřenou v MM_HIMETRIC jednotkách:

Velikost displeje = ( *cyLogical* / *cyHimetrický*) Velikost písma X

Verze bez parametrů vrátí popisovač písma velikosti správně pro obrazovku.

## <a name="cfontholderinitializefont"></a><a name="initializefont"></a>CFontHolder::Inicializovat písmo

Inicializuje `CFontHolder` objekt.

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parametry

*pFontDesc*<br/>
Ukazatel na strukturu popisu písma ( [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)), která určuje vlastnosti písma.

*pFontDispAmbient*<br/>
Ukazatel na okolní vlastnost písma kontejneru.

### <a name="remarks"></a>Poznámky

Pokud *pFontDispAmbient* není NULL, `CFontHolder` objekt je připojen ke `IFont` klonrozhraní používané okolí vlastnost kontejneru Font.

Pokud *pFontDispAmbient* je NULL, nový Font objekt je vytvořen buď z popisu písma ukázal *pFontDesc* nebo, pokud *pFontDesc* je NULL, z výchozípopis.

Volání této funkce po `CFontHolder` vytvoření objektu.

## <a name="cfontholderm_pfont"></a><a name="m_pfont"></a>CFontHolder::m_pFont

Ukazatel na `CFontHolder` `IFont` rozhraní objektu.

```
LPFONT m_pFont;
```

## <a name="cfontholderquerytextmetrics"></a><a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics

Načte informace o fyzické písmo reprezentované objektem. `CFontHolder`

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>Parametry

*lptm*<br/>
Ukazatel na [strukturu TEXTMETRIC,](/windows/win32/api/wingdi/ns-wingdi-textmetricw) která obdrží informace.

## <a name="cfontholderreleasefont"></a><a name="releasefont"></a>CFontHolder::ReleaseFont

Tato funkce odpojí `CFontHolder` `IFont` objekt od jeho rozhraní.

```
void ReleaseFont();
```

## <a name="cfontholderselect"></a><a name="select"></a>CFontHolder::Vybrat

Voláním této funkce vyberte písmo ovládacího prvku do zadaného kontextu zařízení.

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Kontext zařízení, do kterého je vybráno písmo.

*cyLogical*<br/>
Výška v logických jednotkách obdélníku, ve kterém je nakreslena ovládací prvek.

*cyhimetrický*<br/>
Výška ovládacího prvku v MM_HIMETRIC jednotkách.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na písmo, které je nahrazováno.

### <a name="remarks"></a>Poznámky

Viz [GetFontHandle](#getfonthandle) pro diskusi o *cyLogical* a *cyHimetric parameters.*

## <a name="cfontholdersetfont"></a><a name="setfont"></a>CFontHolder::SetFont

Uvolní všechny existující písmo `CFontHolder` a připojí `IFont` objekt k rozhraní.

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>Parametry

*pNewFont*<br/>
Ukazatel na `IFont` nové rozhraní.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange – třída](../../mfc/reference/cpropexchange-class.md)
