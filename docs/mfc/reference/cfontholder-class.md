---
title: Cfontholder – třída
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
ms.openlocfilehash: 24a33aafa279f47bcfabd1ac3f3ee8d4abd4c731
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659639"
---
# <a name="cfontholder-class"></a>Cfontholder – třída

Implementuje vlastnost běžného písma a zapouzdřuje funkce objektu písma Windows a `IFont` rozhraní.

## <a name="syntax"></a>Syntaxe

```
class CFontHolder
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFontHolder::CFontHolder](#cfontholder)|Vytvoří `CFontHolder` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFontHolder::GetDisplayString](#getdisplaystring)|Načte řetězec zobrazený v prohlížeči vlastností kontejneru.|
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Vrátí písma `IDispatch` rozhraní.|
|[CFontHolder::GetFontHandle](#getfonthandle)|Vrátí popisovač do Windows písma.|
|[CFontHolder::InitializeFont](#initializefont)|Inicializuje `CFontHolder` objektu.|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Načtení informací o související písma.|
|[CFontHolder::ReleaseFont](#releasefont)|Odpojí `CFontHolder` objektu z `IFont` a `IFontNotification` rozhraní.|
|[CFontHolder::Select](#select)|Vybere písmo zdroj do kontextu zařízení.|
|[CFontHolder::SetFont](#setfont)|Připojuje `CFontHolder` objektu `IFont` rozhraní.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|Ukazatel `CFontHolder` objektu `IFont` rozhraní.|

## <a name="remarks"></a>Poznámky

`CFontHolder` nemá základní třídu.

Tato třída slouží k implementaci vlastnosti vlastní písma pro ovládací prvek. Informace o vytvoření těchto vlastností najdete v článku [ovládací prvky ActiveX: použití písem](../../mfc/mfc-activex-controls-using-fonts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CFontHolder`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

##  <a name="cfontholder"></a>  CFontHolder::CFontHolder

Vytvoří `CFontHolder` objektu.

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>Parametry

*pNotify*<br/>
Ukazatel na písmo `IPropertyNotifySink` rozhraní.

### <a name="remarks"></a>Poznámky

Je nutné volat `InitializeFont` inicializovat výsledný objekt před jeho použitím.

##  <a name="getdisplaystring"></a>  CFontHolder::GetDisplayString

Načte řetězec, který lze zobrazit v prohlížeči vlastností kontejneru.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parametry

*strValue*<br/>
Odkaz [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který je pro uložení řetězce zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud řetězec je úspěšně načíst. jinak 0.

##  <a name="getfontdispatch"></a>  CFontHolder::GetFontDispatch

Volání této funkce načtete ukazatel na rozhraní odbavení písma.

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CFontHolder` objektu `IFontDisp` rozhraní. Všimněte si, že funkce, která volá `GetFontDispatch` musí volat `IUnknown::Release` na tento ukazatel rozhraní, až budete hotovi s ním.

### <a name="remarks"></a>Poznámky

Volání `InitializeFont` před voláním `GetFontDispatch`.

##  <a name="getfonthandle"></a>  CFontHolder::GetFontHandle

Voláním této funkce se získat popisovač Windows písma.

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parametry

*cyLogical*<br/>
Výška v logických jednotkách, ve kterém ovládací prvek vykreslen obdélníku.

*cyHimetric*<br/>
Výška v jednotkách MM_HIMETRIC ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Popisovač pro objekt písma. v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Poměr *cyLogical* a *cyHimetric* se používá k výpočtu správného zobrazovanou velikostí, logické jednotky pro velikost písma vyjádřena v jednotkách MM_HIMETRIC:

Velikost zobrazení = ( *cyLogical* / *cyHimetric*) X velikost písma

Verze bez parametrů vrátí popisovač do písmo správnou velikost obrazovky.

##  <a name="initializefont"></a>  CFontHolder::InitializeFont

Inicializuje `CFontHolder` objektu.

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parametry

*pFontDesc*<br/>
Ukazatel na strukturu popis písma ( [FONTDESC](/windows/desktop/api/olectl/ns-olectl-tagfontdesc)), která určuje charakteristiky písma.

*pFontDispAmbient*<br/>
Ukazatel na kontejneru okolí Font – vlastnost

### <a name="remarks"></a>Poznámky

Pokud *pFontDispAmbient* nemá hodnotu NULL, `CFontHolder` klon je připojený objekt `IFont` rozhraní kontejneru okolí Font – vlastnost.

Pokud *pFontDispAmbient* je NULL, nové písmo objekt je vytvořen buď z popisu písma, na které odkazuje *pFontDesc* nebo pokud *pFontDesc* má hodnotu NULL, z výchozí Popis.

Voláním této funkce za vytváření `CFontHolder` objektu.

##  <a name="m_pfont"></a>  CFontHolder::m_pFont

Ukazatel `CFontHolder` objektu `IFont` rozhraní.

```
LPFONT m_pFont;
```

##  <a name="querytextmetrics"></a>  CFontHolder::QueryTextMetrics

Načte informace o fyzických písma reprezentována `CFontHolder` objektu.

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>Parametry

*lptm*<br/>
Ukazatel [TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica) struktura, která bude dostávat informace.

##  <a name="releasefont"></a>  CFontHolder::ReleaseFont

Tato funkce odpojí `CFontHolder` objekt z jeho `IFont` rozhraní.

```
void ReleaseFont();
```

##  <a name="select"></a>  CFontHolder::Select

Voláním této funkce vyberte písmo ovládacího prvku do kontextu zařízení.

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Kontext zařízení, do které je vybrané písmo.

*cyLogical*<br/>
Výška v logických jednotkách, ve kterém ovládací prvek vykreslen obdélníku.

*cyHimetric*<br/>
Výška v jednotkách MM_HIMETRIC ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Ukazatel, který se nahrazuje písmo.

### <a name="remarks"></a>Poznámky

Zobrazit [GetFontHandle](#getfonthandle) diskuzi o *cyLogical* a *cyHimetric* parametry.

##  <a name="setfont"></a>  CFontHolder::SetFont

Uvolní všechny existující písma a připojí `CFontHolder` objektu `IFont` rozhraní.

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>Parametry

*pNewFont*<br/>
Ukazatel na novou `IFont` rozhraní.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange – třída](../../mfc/reference/cpropexchange-class.md)
