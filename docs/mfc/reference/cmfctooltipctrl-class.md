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
ms.openlocfilehash: 6c8bb41b82d1dca9235e1184c2152a61c07c8071
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377345"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl – třída

Rozšířené popisek implementace založené na [CToolTipCtrl třídy](../../mfc/reference/ctooltipctrl-class.md). Popis založený na `CMFCToolTipCtrl` třídě může zobrazit ikonu, popisek a popisek. Jeho vizuální vzhled můžete přizpůsobit pomocí výplně přechodem, vlastních barev textu a ohraničení, tučného textu, zaoblených rohů nebo stylu pozice.

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```cpp
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|Vrátí velikost ikony v popisku.|
|[CMFCToolTipCtrl::GetParams](#getparams)|Vrátí nastavení zobrazení popisku.|
|[CMFCToolTipctrl::OnDrawBorder](#ondrawborder)|Nakreslí ohraničení popisku.|
|[CMFCToolTipctrl::OnDrawDescription](#ondrawdescription)||
|[CMFCToolTipctrl::OnDrawIcon](#ondrawicon)|Zobrazí ikonu v popisku.|
|[CMFCToolTipctrl::OnDrawLabel](#ondrawlabel)|Nakreslí popisek popisku nebo vypočítá velikost popisku.|
|[CMFCToolTipCtrl::Oddělovač ondraw](#ondrawseparator)|Nakreslí oddělovač mezi popisek a popis v popisku.|
|[CMFCToolTipctrl::OnFillBackground](#onfillbackground)|Vyplní pozadí popisku.|
|[CMFCToolTipCtrl:SetDescription](#setdescription)|Nastaví popis, který se má zobrazit podle popisku.|
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl::SetLocation](#setlocation)||
|[CMFCToolTipCtrl::SetParams](#setparams)|Určuje vizuální vzhled popisku pomocí objektu. `CMFCToolTipInfo`|

## <a name="remarks"></a>Poznámky

Pomocí `CMFCToolTipCtrl` `CMFCToolTipInfo`objektů , a [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md) společně implementujte vlastní popisky ve vaší aplikaci.

Chcete-li například použít popisky ve stylu pozice, postupujte takto:

1. Pomocí metody [Třídy CWinAppEx](../../mfc/reference/cwinappex-class.md) inicializujte správce popisů ve vaší aplikaci.

2. Vytvořte `CMFCToolTipInfo` strukturu pro určení požadovaného vizuálního stylu:

    ```cpp
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

3. Pomocí metody [CTooltipManager::SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) nastavte vizuální styl pro všechny popisky v aplikaci `CMFCToolTipInfo` pomocí stylů definovaných v objektu:

    ```cpp
    theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
        RUNTIME_CLASS (CMFCToolTipCtrl), &params);
    ```

Můžete také odvodit `CMFCToolTipCtrl` novou třídu z řízení chování popisku a vykreslování. Chcete-li určit novou třídu `CTooltipManager::SetTooltipParams` ovládacího prvku popisku, použijte metodu:

```cpp
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```

Chcete-li obnovit výchozí třídu ovládacího prvku popisu a obnovit výchozí stav popisku, zadejte `SetTooltipParams`hodnotu NULL v parametrech třídy runtime a informace o popiscích :

```cpp
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCToolTipCtrl` vytvořit objekt, nastavte popis, který se zobrazí popis a nastavte šířku ovládacího prvku popisku.

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtooltipctrl.h

## <a name="cmfctooltipctrlcmfctooltipctrl"></a><a name="cmfctooltipctrl"></a>CMFCToolTipCtrl::CMFCToolTipCtrl

```cpp
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>Parametry

[v] *pParams*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfctooltipctrlgeticonsize"></a><a name="geticonsize"></a>CMFCToolTipCtrl::GetIconSize

Vrátí velikost ikony v popisku.

```cpp
virtual CSize GetIconSize();
```

### <a name="return-value"></a>Návratová hodnota

Velikost ikony v pixelech.

## <a name="cmfctooltipctrlgetparams"></a><a name="getparams"></a>CMFCToolTipCtrl::GetParams

Vrátí nastavení zobrazení popisku.

```cpp
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální nastavení zobrazení popisku , které jsou uloženy v objektu [třídy CMFCToolTipInfo.](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="cmfctooltipctrlondrawborder"></a><a name="ondrawborder"></a>CMFCToolTipctrl::OnDrawBorder

Nakreslí ohraničení popisku.

```cpp
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*Rect*<br/>
[v] Ohraničující obdélník popisku.

*clrLine*<br/>
[v] Barva ohraničení.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě přizpůsobit vzhled ohraničení popisku.

## <a name="cmfctooltipctrlondrawdescription"></a><a name="ondrawdescription"></a>CMFCToolTipctrl::OnDrawDescription

```cpp
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parametry

[v] *pDC*<br/>
[v] *rect*<br/>
[v] *bCalcOnly*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfctooltipctrlondrawicon"></a><a name="ondrawicon"></a>CMFCToolTipctrl::OnDrawIcon

Zobrazí ikonu v popisku.

```cpp
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*rectImage*<br/>
[v] Souřadnice ikony.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla nakreslena ikona. Jinak FALSE.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě zobrazit vlastní ikonu. Musíte také přepsat [CMFCToolTipCtrl::GetIconSize](#geticonsize) povolit popisek správně vypočítat rozložení textu a popisu.

## <a name="cmfctooltipctrlondrawlabel"></a><a name="ondrawlabel"></a>CMFCToolTipctrl::OnDrawLabel

Nakreslí popisek popisku nebo vypočítá velikost popisku.

```cpp
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*Rect*<br/>
[v] Ohraničující obdélník oblasti popisku.

*bCalcOnly*<br/>
[v] Pokud true, popisek nebude nakreslena.

### <a name="return-value"></a>Návratová hodnota

Velikost popisku v pixelech.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě, pokud chcete přizpůsobit vzhled popisku popisku.

## <a name="cmfctooltipctrlondrawseparator"></a><a name="ondrawseparator"></a>CMFCToolTipCtrl::Oddělovač ondraw

Nakreslí oddělovač mezi popisek a popis v popisku.

```cpp
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*x1*<br/>
[v] Vodorovná souřadnice levého konce oddělovače.

*x2*<br/>
[v] Vodorovná souřadnice pravého konce oddělovače.

*Ano*<br/>
[v] Svislá souřadnice oddělovače.

### <a name="remarks"></a>Poznámky

Výchozí implementace nakreslí čáru od bodu (x1, y) k bodu (x2, y).

Přepsat tuto metodu v odvozené třídě přizpůsobit vzhled oddělovače.

## <a name="cmfctooltipctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCToolTipctrl::OnFillBackground

Vyplní pozadí popisku.

```cpp
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*Rect*<br/>
[v] Určuje ohraničující obdélník oblasti, kterou chcete vyplnit.

*clrText*<br/>
[v] Barva popředí popisku.

*clrLine*<br/>
[v] Barva ohraničení a čára oddělovače mezi popiskem a popisem.

### <a name="remarks"></a>Poznámky

Výchozí implementace vyplní obdélník, který je určen *rect* s barvou nebo vzorem určeným poslední volání [CMFCToolTipCtrl::SetParams](#setparams).

Přepsat tuto metodu v odvozené třídě, pokud chcete přizpůsobit vzhled popisku.

## <a name="cmfctooltipctrlsetdescription"></a><a name="setdescription"></a>CMFCToolTipCtrl:SetDescription

Nastaví popis, který se má zobrazit podle popisku.

```cpp
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>Parametry

*strDesrciption*<br/>
[v] Popisný text.

### <a name="remarks"></a>Poznámky

Text popisu se zobrazí v popisku pod oddělovačem.

## <a name="cmfctooltipctrlsetfixedwidth"></a><a name="setfixedwidth"></a>CMFCToolTipCtrl::SetFixedWidth

```cpp
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>Parametry

[v] *nWidthRegular*<br/>
[v] *nWidthLargeImage*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfctooltipctrlsethotribbonbutton"></a><a name="sethotribbonbutton"></a>CMFCToolTipCtrl::SetHotRibbonButton

```cpp
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>Parametry

[v] *pRibbonButton*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfctooltipctrlsetlocation"></a><a name="setlocation"></a>CMFCToolTipCtrl::SetLocation

```cpp
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>Parametry

[v] *pt*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfctooltipctrlsetparams"></a><a name="setparams"></a>CMFCToolTipCtrl::SetParams

Určuje vizuální vzhled popisku pomocí objektu [třídy CMFCToolTipInfo.](../../mfc/reference/cmfctooltipinfo-class.md)

```cpp
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>Parametry

*pParams*<br/>
[v] Ukazatel na objekt [třídy CMFCToolTipInfo,](../../mfc/reference/cmfctooltipinfo-class.md) který obsahuje parametry zobrazení.

### <a name="remarks"></a>Poznámky

Vždy, když je popisek zobrazen, je nakreslena pomocí barev a vizuálnístyly, které *určuje pParams.* Hodnota *pParams* je uložena v `m_Params`chráněném členu , ke kterému lze přistupovat odvozenou třídou, která přepíše [CMFCToolTipCtrl::OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl::OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)nebo [CMFCToolTipCtrl::OnFillBackground](#onfillbackground) zachovat zadaný vzhled.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)<br/>
[CTooltipManager – třída](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipInfo – třída](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[Třída CWinAppEx](../../mfc/reference/cwinappex-class.md)
