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
ms.openlocfilehash: 04de8141469f82bdd1fbb6adc1bae94d6026324c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506449"
---
# <a name="cfontholder-class"></a>CFontHolder – třída

Implementuje vlastnost burzovního písma a zapouzdřuje funkce objektu písma systému Windows a `IFont` rozhraní.

## <a name="syntax"></a>Syntaxe

```
class CFontHolder
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CFontHolder::CFontHolder](#cfontholder)|`CFontHolder` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CFontHolder::GetDisplayString](#getdisplaystring)|Načte řetězec zobrazený v prohlížeči vlastností kontejneru.|
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Vrátí `IDispatch` rozhraní písma.|
|[CFontHolder::GetFontHandle](#getfonthandle)|Vrátí popisovač na písmo systému Windows.|
|[CFontHolder::InitializeFont](#initializefont)|`CFontHolder` Inicializuje objekt.|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Načte informace o souvisejícím písmu.|
|[CFontHolder::ReleaseFont](#releasefont)|Odpojí `CFontHolder` objekt `IFont` od rozhraní a `IFontNotification` .|
|[CFontHolder:: SELECT](#select)|Vybere prostředek písma do kontextu zařízení.|
|[CFontHolder::SetFont](#setfont)|`CFontHolder` Připojí objekt`IFont` k rozhraní.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|Ukazatel na `CFontHolder` `IFont` rozhraní objektu.|

## <a name="remarks"></a>Poznámky

`CFontHolder`nemá základní třídu.

Tato třída slouží k implementaci vlastních vlastností písma pro ovládací prvek. Informace o vytváření takových vlastností najdete v článku [ovládací prvky ActiveX: Používání písem](../../mfc/mfc-activex-controls-using-fonts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CFontHolder`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXCTL. h

##  <a name="cfontholder"></a>CFontHolder::CFontHolder

`CFontHolder` Vytvoří objekt.

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>Parametry

*pNotify*<br/>
Ukazatel na `IPropertyNotifySink` rozhraní písma.

### <a name="remarks"></a>Poznámky

Před použitím je `InitializeFont` nutné zavolat k inicializaci výsledného objektu.

##  <a name="getdisplaystring"></a>CFontHolder::GetDisplayString

Načte řetězec, který lze zobrazit v prohlížeči vlastností kontejneru.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parametry

*strValue*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který je držitelem zobrazovaného řetězce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je řetězec úspěšně načten; v opačném případě 0.

##  <a name="getfontdispatch"></a>CFontHolder::GetFontDispatch

Voláním této funkce načtete ukazatel na rozhraní pro expedici písma.

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CFontHolder` `IFontDisp` rozhraní objektu. Všimněte si, že funkce, `GetFontDispatch` kterou volání `IUnknown::Release` musí volat na tento ukazatel rozhraní, když s ním skončí.

### <a name="remarks"></a>Poznámky

Zavolejte `InitializeFont` před voláním `GetFontDispatch`.

##  <a name="getfonthandle"></a>CFontHolder::GetFontHandle

Voláním této funkce získáte popisovač pro písmo Windows.

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parametry

*cyLogical*<br/>
Height (v logických jednotkách) obdélníku, ve kterém je ovládací prvek vykreslen.

*cyHimetric*<br/>
Výška v MM_HIMETRIC jednotkách ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Popisovač objektu písma; jinak NULL.

### <a name="remarks"></a>Poznámky

Poměr hodnot *cyLogical* a *cyHimetric* se používá k výpočtu správné velikosti zobrazení v logických jednotkách pro velikost bodu písma vyjádřenou v jednotkách MM_HIMETRIC:

Velikost zobrazení = ( *cyLogical* / *cyHimetric*) X velikost písma

Verze bez parametrů vrátí popisovač pro správnou velikost písma pro obrazovku.

##  <a name="initializefont"></a>CFontHolder::InitializeFont

`CFontHolder` Inicializuje objekt.

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parametry

*pFontDesc*<br/>
Ukazatel na strukturu písma Description ( [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)), která určuje charakteristiky písma.

*pFontDispAmbient*<br/>
Ukazatel na vlastnost okolního písma kontejneru

### <a name="remarks"></a>Poznámky

Pokud *pFontDispAmbient* není null, `CFontHolder` je objekt připojen k klonu `IFont` rozhraní používaného vlastností okolního písma kontejneru.

Pokud má *pFontDispAmbient* hodnotu null, vytvoří se nový objekt Font buď z popisu písma, na který odkazuje *pFontDesc* , nebo, pokud *pFontDesc* má hodnotu null, od výchozího popisu.

Po vytvoření `CFontHolder` objektu volejte tuto funkci.

##  <a name="m_pfont"></a>CFontHolder::m_pFont

Ukazatel na `CFontHolder` `IFont` rozhraní objektu.

```
LPFONT m_pFont;
```

##  <a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics

Načte informace o fyzickém písmu reprezentovaném `CFontHolder` objektem.

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>Parametry

*lptm*<br/>
Ukazatel na strukturu [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) , která bude tyto informace přijímat.

##  <a name="releasefont"></a>CFontHolder::ReleaseFont

Tato funkce odpojí `CFontHolder` objekt od jeho `IFont` rozhraní.

```
void ReleaseFont();
```

##  <a name="select"></a>CFontHolder:: SELECT

Voláním této funkce vyberete písmo ovládacího prvku do určeného kontextu zařízení.

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Kontext zařízení, do kterého se vybere písmo

*cyLogical*<br/>
Height (v logických jednotkách) obdélníku, ve kterém je ovládací prvek vykreslen.

*cyHimetric*<br/>
Výška v MM_HIMETRIC jednotkách ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na písmo, které se nahrazuje.

### <a name="remarks"></a>Poznámky

Diskuzi o parametrech *cyLogical* a *cyHimetric* najdete v tématu [GetFontHandle](#getfonthandle) .

##  <a name="setfont"></a>CFontHolder::SetFont

Uvolní jakékoli existující písmo a připojí `CFontHolder` objekt `IFont` k rozhraní.

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>Parametry

*pNewFont*<br/>
Ukazatel na nové `IFont` rozhraní.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange – třída](../../mfc/reference/cpropexchange-class.md)
