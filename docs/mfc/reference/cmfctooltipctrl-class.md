---
title: CMFCToolTipCtrl Class
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
ms.openlocfilehash: aaf9d9570906b7886d8ec78575c39db5d62099f7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293196"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl Class

Implementace rozšířeného popisku na základě [ctooltipctrl – třída](../../mfc/reference/ctooltipctrl-class.md). Popisek na základě `CMFCToolTipCtrl` třída může zobrazit ikonu, popisek a popis. Můžete upravit jeho vzhled pomocí přechodové výplně, vlastní text a barvy ohraničení, tučným písmem, zaoblených rohů nebo stylu bublin.

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|Vrátí velikost ikony v popisku.|
|[CMFCToolTipCtrl::GetParams](#getparams)|Vrátí nastavení zobrazení popisu.|
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|Ohraničení popisku pole.|
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|V popisku se zobrazí ikona.|
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|Kreslení plné popisku popisu tlačítka nebo vypočítá velikost popisku.|
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|Nakreslí oddělovač mezi popisek a popis v popisu tlačítka.|
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|Vyplní pozadí popisu tlačítka.|
|[CMFCToolTipCtrl::SetDescription](#setdescription)|Nastaví popis, který se má zobrazit v popisu tlačítka.|
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl::SetLocation](#setlocation)||
|[CMFCToolTipCtrl::SetParams](#setparams)|Určuje vzhled popisku pomocí `CMFCToolTipInfo` objektu.|

## <a name="remarks"></a>Poznámky

Použití `CMFCToolTipCtrl`, `CMFCToolTipInfo`, a [ctooltipmanager – třída](../../mfc/reference/ctooltipmanager-class.md) objekty společně k implementaci vlastní popisy ve vaší aplikaci.

Například použití prvku tooltips stylu bublin, postupujte podle těchto kroků:

1. Použití [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md) metody k inicializaci správce popisu tlačítka ve vaší aplikaci.

2. Vytvoření `CMFCToolTipInfo` struktury zadat vizuální styl, který chcete:

```
CMFCToolTipInfo params;
    params.m_bBoldLabel = FALSE;
    params.m_bDrawDescription = FALSE;
    params.m_bDrawIcon = FALSE;
    params.m_bRoundedCorners = TRUE;
    params.m_bDrawSeparator = FALSE;
    if (m_bCustomColors)
{
    params.m_clrFill = RGB (255,
    255,
    255);

    params.m_clrFillGradient = RGB (228,
    228,
    240);

    params.m_clrText = RGB (61,
    83,
    80);

    params.m_clrBorder = RGB (144,
    149,
    168);

}
```
3. Použití [CTooltipManager::SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) metoda nastavení stylu pro všechny popisky v aplikaci s použitím styly definované v `CMFCToolTipInfo` objektu:

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```
Můžete také odvodit novou třídu z `CMFCToolTipCtrl` chování ovládací prvek popisku a vykreslování. Pokud chcete nastavit nové třídě ovládacího prvku popisu tlačítka, použijte `CTooltipManager::SetTooltipParams` metody:

```
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```
Chcete-li obnovit výchozí popisek třídu ovládacího prvku a vzhled popisku resetovat do výchozího stavu, zadejte hodnotu NULL v modulu runtime třídy a popis tlačítka informace o parametrech `SetTooltipParams`:

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCToolTipCtrl` objektu, nastavit popis, který se zobrazí popisek a nastavte šířku ovládacího prvku tooltip.

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxtooltipctrl.h

##  <a name="cmfctooltipctrl"></a>  CMFCToolTipCtrl::CMFCToolTipCtrl

```
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>Parametry

[in] *pParams*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="geticonsize"></a>  CMFCToolTipCtrl::GetIconSize

Vrátí velikost ikony v popisku.

```
virtual CSize GetIconSize();
```

### <a name="return-value"></a>Návratová hodnota

Velikost ikony v pixelech.

##  <a name="getparams"></a>  CMFCToolTipCtrl::GetParams

Vrátí nastavení zobrazení popisu.

```
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální nastavení zobrazení popisu tlačítka, které jsou uložené v [cmfctooltipinfo – třída](../../mfc/reference/cmfctooltipinfo-class.md) objektu.

##  <a name="ondrawborder"></a>  CMFCToolTipCtrl::OnDrawBorder

Ohraničení popisku pole.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*Rect*<br/>
[in] Ohraničující obdélník ovládacího prvku tooltip.

*clrLine*<br/>
[in] Barva ohraničení.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě pro přizpůsobení vzhledu ohraničení popisu tlačítka.

##  <a name="ondrawdescription"></a>  CMFCToolTipCtrl::OnDrawDescription

```
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parametry

[in] *pDC*<br/>
[in] *rect*<br/>
[in] *bCalcOnly*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="ondrawicon"></a>  CMFCToolTipCtrl::OnDrawIcon

V popisku se zobrazí ikona.

```
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*rectImage*<br/>
[in] Souřadnice na ikonu.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byl nakreslen ikonu. V opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídy za účelem zobrazení vlastní ikony. Musí také přepsat [CMFCToolTipCtrl::GetIconSize](#geticonsize) umožňující popisek, který správně vypočítat rozložení textu a popis.

##  <a name="ondrawlabel"></a>  CMFCToolTipCtrl::OnDrawLabel

Kreslení plné popisku popisu tlačítka nebo vypočítá velikost popisku.

```
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*Rect*<br/>
[in] Popisek oblasti ohraničující obdélník.

*bCalcOnly*<br/>
[in] Při hodnotě TRUE se nebude vykreslen popisek.

### <a name="return-value"></a>Návratová hodnota

Velikost popisku v pixelech.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě, pokud chcete přizpůsobit vzhled popisku tooltip.

##  <a name="ondrawseparator"></a>  CMFCToolTipCtrl::OnDrawSeparator

Nakreslí oddělovač mezi popisek a popis v popisu tlačítka.

```
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*x1*<br/>
[in] Vodorovné souřadnice levého koncový oddělovač

*x2*<br/>
[in] Vodorovné souřadnice pravého konce oddělovače.

*Y*<br/>
[in] Svislé souřadnice oddělovače.

### <a name="remarks"></a>Poznámky

Výchozí implementace nakreslí čáru z bodu (x1, y) do bodu (x2, y).

Potlačí tuto metodu v odvozené třídě pro přizpůsobení vzhledu oddělovače.

##  <a name="onfillbackground"></a>  CMFCToolTipCtrl::OnFillBackground

Vyplní pozadí popisu tlačítka.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*Rect*<br/>
[in] Určuje ohraničující obdélník oblasti tak, aby vyplnil.

*clrText*<br/>
[in] Barva popředí popisu tlačítka.

*clrLine*<br/>
[in] Barva ohraničení a čára oddělovač mezi popisek a popis.

### <a name="remarks"></a>Poznámky

Výchozí implementace vyplní obdélník, který je určen *rect* s barvu nebo vzorek určené posledního volání [CMFCToolTipCtrl::SetParams](#setparams).

Potlačí tuto metodu v odvozené třídě, pokud chcete přizpůsobit vzhled ovládacího prvku tooltip.

##  <a name="setdescription"></a>  CMFCToolTipCtrl::SetDescription

Nastaví popis, který se má zobrazit v popisu tlačítka.

```
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>Parametry

*strDesrciption*<br/>
[in] Text popisu.

### <a name="remarks"></a>Poznámky

Text popisu, který se zobrazí na ovládacím prvku ToolStrip za oddělovače.

##  <a name="setfixedwidth"></a>  CMFCToolTipCtrl::SetFixedWidth

```
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>Parametry

[in] *nWidthRegular*<br/>
[in] *nWidthLargeImage*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="sethotribbonbutton"></a>  CMFCToolTipCtrl::SetHotRibbonButton

```
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>Parametry

[in] *pRibbonButton*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setlocation"></a>  CMFCToolTipCtrl::SetLocation

```
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>Parametry

[in] *pt*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setparams"></a>  CMFCToolTipCtrl::SetParams

Určuje vzhled popisku pomocí [cmfctooltipinfo – třída](../../mfc/reference/cmfctooltipinfo-class.md) objektu.

```
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>Parametry

*pParams*<br/>
[in] Ukazatel [cmfctooltipinfo – třída](../../mfc/reference/cmfctooltipinfo-class.md) objekt, který obsahuje parametry zobrazení.

### <a name="remarks"></a>Poznámky

Pokaždé, když se zobrazí popis tlačítka, je vykreslen pomocí barvy a styly vizuál, který *pParams* určuje. Hodnota *pParams* je uložen v chráněný člen `m_Params`, který je přístupný prostřednictvím odvozené třídy, která přepíše [CMFCToolTipCtrl::OnDrawBorder](#ondrawborder), [cmfctooltipctrl –: : OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator), nebo [CMFCToolTipCtrl::OnFillBackground](#onfillbackground)udržovat zadané vzhled.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CToolTipCtrl – třída](../../mfc/reference/ctooltipctrl-class.md)<br/>
[CTooltipManager – třída](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipInfo – třída](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)
