---
title: CMFCToolTipCtrl – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetIconSize
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetParams
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawBorder
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawLabel
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnFillBackground
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetFixedWidth
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetHotRibbonButton
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetLocation
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetParams
helpviewer_keywords:
- CMFCToolTipCtrl [MFC], GetIconSize
- CMFCToolTipCtrl [MFC], GetParams
- CMFCToolTipCtrl [MFC], OnDrawBorder
- CMFCToolTipCtrl [MFC], OnDrawDescription
- CMFCToolTipCtrl [MFC], OnDrawIcon
- CMFCToolTipCtrl [MFC], OnDrawLabel
- CMFCToolTipCtrl [MFC], OnDrawSeparator
- CMFCToolTipCtrl [MFC], OnFillBackground
- CMFCToolTipCtrl [MFC], SetDescription
- CMFCToolTipCtrl [MFC], SetFixedWidth
- CMFCToolTipCtrl [MFC], SetHotRibbonButton
- CMFCToolTipCtrl [MFC], SetLocation
- CMFCToolTipCtrl [MFC], SetParams
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
ms.openlocfilehash: aecd03371f0dfd4b4af5886bea6c6202c40b5236
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445557"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl – třída

Rozšířená implementace tooltipu na základě [třídy CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) Popis tlačítka na základě třídy `CMFCToolTipCtrl` může zobrazit ikonu, popisek a popis. Můžete přizpůsobit jeho vizuální vzhled pomocí přechodové výplně, vlastního textu a barev ohraničení, tučného textu, zaoblených rohů nebo stylu bubliny.

Další podrobnosti najdete ve zdrojovém kódu, který se nachází ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|Výchozí konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|Vrátí velikost ikony v popisu tlačítka.|
|[CMFCToolTipCtrl:: GetParam](#getparams)|Vrátí nastavení zobrazení popisku.|
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|Vykreslí ohraničení popisu tlačítka.|
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|Zobrazí ikonu v popisu tlačítka.|
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|Nakreslí popisek popisku nebo vypočítá velikost popisku.|
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|Nakreslí oddělovač mezi popiskem a popisem v popisu tlačítka.|
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|Vyplní pozadí popisku.|
|[CMFCToolTipCtrl::SetDescription](#setdescription)|Nastaví popis, který má být zobrazen pomocí popisu tlačítka.|
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl::SetLocation](#setlocation)||
|[CMFCToolTipCtrl::SetParams](#setparams)|Určuje vizuální vzhled popisu tlačítka pomocí objektu `CMFCToolTipInfo`.|

## <a name="remarks"></a>Poznámky

Použijte objekty třídy `CMFCToolTipCtrl`, `CMFCToolTipInfo`a [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) společně k implementaci přizpůsobených popisů v aplikaci.

Chcete-li například použít popisky ve stylu bubliny, postupujte takto:

1. Použijte metodu [třídy CWinAppEx](../../mfc/reference/cwinappex-class.md) k inicializaci správce popisů v aplikaci.

2. Vytvořte strukturu `CMFCToolTipInfo` pro určení vizuálního stylu, který chcete:

```
CMFCToolTipInfo params;
params.m_bBoldLabel = FALSE;
params.m_bDrawDescription = FALSE;
params.m_bDrawIcon = FALSE;
params.m_bRoundedCorners = TRUE;
params.m_bDrawSeparator = FALSE;
if (m_bCustomColors)
{
    params.m_clrFill = RGB (255, 255, 255);
    params.m_clrFillGradient = RGB (228, 228, 240);
    params.m_clrText = RGB (61, 83, 80);
    params.m_clrBorder = RGB (144, 149, 168);

}
```

3. Pomocí metody [CTooltipManager:: SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) nastavte styl vizuálu pro všechny popisy v aplikaci pomocí stylů definovaných v objektu `CMFCToolTipInfo`:

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```

Můžete také odvodit novou třídu z `CMFCToolTipCtrl` pro řízení chování a vykreslování popisu tlačítka. Chcete-li určit novou třídu ovládacího prvku ToolTip, použijte metodu `CTooltipManager::SetTooltipParams`:

```
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```

Chcete-li obnovit výchozí třídu ToolTip Control a resetovat vzhled popisku na jeho výchozí stav, zadejte hodnotu NULL v parametrech běhové třídy a v informacích popisku `SetTooltipParams`:

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCToolTipCtrl`, nastavit popis, který se zobrazí pomocí popisku, a nastavit šířku ovládacího prvku ToolTip.

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxToolTipCtrl. h

##  <a name="cmfctooltipctrl"></a>CMFCToolTipCtrl::CMFCToolTipCtrl

```
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>Parametry

pro *pParams*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="geticonsize"></a>CMFCToolTipCtrl::GetIconSize

Vrátí velikost ikony v popisu tlačítka.

```
virtual CSize GetIconSize();
```

### <a name="return-value"></a>Návratová hodnota

Velikost ikony v pixelech

##  <a name="getparams"></a>CMFCToolTipCtrl:: GetParam

Vrátí nastavení zobrazení popisku.

```
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální nastavení zobrazení popisu, která jsou uložena v objektu [třídy CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) .

##  <a name="ondrawborder"></a>CMFCToolTipCtrl::OnDrawBorder

Vykreslí ohraničení popisu tlačítka.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
pro Ukazatel na kontext zařízení.

*OBD*<br/>
pro Ohraničující obdélník popisku.

*clrLine*<br/>
pro Barva ohraničení

### <a name="remarks"></a>Poznámky

Přepsáním této metody v odvozené třídě upravíte vzhled ohraničení popisku.

##  <a name="ondrawdescription"></a>CMFCToolTipCtrl::OnDrawDescription

```
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parametry

pro *primární řadič domény*<br/>
pro *Rect*<br/>
pro *bCalcOnly*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="ondrawicon"></a>CMFCToolTipCtrl::OnDrawIcon

Zobrazí ikonu v popisu tlačítka.

```
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
pro Ukazatel na kontext zařízení.

*rectImage*<br/>
pro Souřadnice ikony

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla ikona vykreslena. V opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Přepište tuto metodu v odvozené třídě, aby se zobrazila vlastní ikona. Je také nutné přepsat [CMFCToolTipCtrl:: GetIconSize](#geticonsize) , aby popis mohl správně vypočítat rozložení textu a popisu.

##  <a name="ondrawlabel"></a>CMFCToolTipCtrl::OnDrawLabel

Nakreslí popisek popisku nebo vypočítá velikost popisku.

```
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
pro Ukazatel na kontext zařízení.

*OBD*<br/>
pro Ohraničující obdélník oblasti popisku.

*bCalcOnly*<br/>
pro Při hodnotě TRUE se popisek nevykresluje.

### <a name="return-value"></a>Návratová hodnota

Velikost popisku v pixelech

### <a name="remarks"></a>Poznámky

Tuto metodu přepište v odvozené třídě, pokud chcete přizpůsobit vzhled popisku ToolTip.

##  <a name="ondrawseparator"></a>CMFCToolTipCtrl::OnDrawSeparator

Nakreslí oddělovač mezi popiskem a popisem v popisu tlačítka.

```
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
pro Ukazatel na kontext zařízení.

*x1*<br/>
pro Vodorovná souřadnice levého konce oddělovače

*X2*<br/>
pro Vodorovná souřadnice pravého konce oddělovače

*Požadované*<br/>
pro Svislá souřadnice oddělovače

### <a name="remarks"></a>Poznámky

Výchozí implementace nakreslí čáru od bodu (x1, y) k bodu (X2, y).

Přepsáním této metody v odvozené třídě upravíte vzhled oddělovače.

##  <a name="onfillbackground"></a>CMFCToolTipCtrl::OnFillBackground

Vyplní pozadí popisku.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
pro Ukazatel na kontext zařízení.

*OBD*<br/>
pro Určuje ohraničující obdélník oblasti, která má být vyplněna.

*clrText*<br/>
pro Barva popředí tlačítka

*clrLine*<br/>
pro Barva ohraničení a oddělovací čára mezi popiskem a popisem

### <a name="remarks"></a>Poznámky

Výchozí implementace vyplní obdélník, který je určen jako *Rect* , barvou nebo vzorkem určeným posledním voláním metody [CMFCToolTipCtrl:: setparams](#setparams).

Tuto metodu přepište v odvozené třídě, pokud chcete přizpůsobit vzhled popisu tlačítka.

##  <a name="setdescription"></a>CMFCToolTipCtrl::SetDescription

Nastaví popis, který má být zobrazen pomocí popisu tlačítka.

```
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>Parametry

*strDesrciption*<br/>
pro Text popisu

### <a name="remarks"></a>Poznámky

Text popisu se zobrazí v popisku pod oddělovačem.

##  <a name="setfixedwidth"></a>CMFCToolTipCtrl::SetFixedWidth

```
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>Parametry

pro *nWidthRegular*<br/>
pro *nWidthLargeImage*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="sethotribbonbutton"></a>CMFCToolTipCtrl::SetHotRibbonButton

```
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>Parametry

pro *pRibbonButton*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setlocation"></a>CMFCToolTipCtrl::SetLocation

```
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>Parametry

pro *PT*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setparams"></a>CMFCToolTipCtrl::SetParams

Určuje vizuální vzhled popisu tlačítka pomocí objektu [třídy CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) .

```
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>Parametry

*pParams*<br/>
pro Ukazatel na objekt [třídy CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) , který obsahuje parametry zobrazení.

### <a name="remarks"></a>Poznámky

Pokaždé, když se zobrazí popisek, vykreslí se pomocí barev a vizuálních stylů, které *pParams* určuje. Hodnota *pParams* je uložena v chráněném členu `m_Params`, který je k dispozici v odvozené třídě, která přepisuje [CMFCToolTipCtrl:: OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl:: OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl:: OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl:: OnDrawSeparator](#ondrawseparator)nebo [CMFCToolTipCtrl:: OnFillBackground](#onfillbackground) pro zachování zadaného vzhledu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CToolTipCtrl – třída](../../mfc/reference/ctooltipctrl-class.md)<br/>
[CTooltipManager – třída](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipInfo – třída](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)
