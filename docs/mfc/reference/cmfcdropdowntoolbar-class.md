---
title: CMFCDropDownToolbar – třída
ms.date: 11/19/2018
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
ms.openlocfilehash: f2c4135d2a27928dbde4299fa1f8eda42237d893
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62238062"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolbar – třída

Panel nástrojů, který se zobrazí, když uživatel stiskne a podrží tlačítko panelu nástrojů nejvyšší úrovně.

   Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.
## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Přepíše `CPane::AllowShowOnPaneMenu`.)|
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Přepíše [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Přepíše [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Přepíše `CMFCToolBar::OnSendCommand`.)|
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Přepíše [CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md).|

### <a name="remarks"></a>Poznámky

A `CMFCDropDownToolBar` objekt kombinuje vzhled panelu nástrojů s chováním v místní nabídce. Když uživatel stiskne a podrží tlačítko panelu nástrojů v rozevíracím seznamu (viz [cmfcdropdowntoolbarbutton – třída](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), zobrazí se rozevírací seznam nástrojů, a může uživatel vybrat tlačítko na panelu nástrojů v rozevíracím seznamu posouvání, aby ji mohl a uvolněním tlačítka myši tlačítko. Když uživatele vybere tlačítko na panelu rozevíracího seznamu, toto tlačítko se zobrazí jako aktuální tlačítko na panelu nástrojů nejvyšší úrovně.

Rozevírací seznam nástrojů nelze upravit nebo ukotven a nemá stav odnímatelnými nabídkami.

Následující ilustrace ukazuje `CMFCDropDownToolBar` objektu:

![Příklad CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "CMFCDropDownToolbar – příklad")

Vytváření `CMFCDropDownToolBar` objekt stejným způsobem vytvoření běžný panel nástrojů (naleznete v tématu [cmfctoolbar – třída](../../mfc/reference/cmfctoolbar-class.md)).

Chcete-li vložit rozevírací seznam nástrojů do nadřazeného panelu nástrojů:

1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.

2. Vytvoření `CMFCDropDownToolBarButton` objekt, který obsahuje rozevírací seznam nástrojů (Další informace najdete v tématu [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).

3. Nahraďte zástupné tlačítko s `CMFCDropDownToolBarButton` s použitím [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Další informace o tlačítka na panelu nástrojů najdete v tématu [názorný postup: Vkládání ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md). Příklad rozevírací seznam nástrojů naleznete v tématu ukázkový projekt VisualStudioDemo.

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `Create` metodu `CMFCDropDownToolBar` třídy. Tento fragment kódu je součástí [Visual Studio demonstrační ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdropdowntoolbar.h

##  <a name="allowshowonpanemenu"></a>  CMFCDropDownToolBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="loadbitmap"></a>  CMFCDropDownToolBar::LoadBitmap

Načte obrázky panelu nástrojů ze zdrojů aplikace.

```
virtual BOOL LoadBitmap(
    UINT uiResID,
    UINT uiColdResID=0,
    UINT uiMenuResID=0,
    BOOL bLocked=FALSE,
    UINT uiDisabledResID=0,
    UINT uiMenuDisabledResID=0);
```

### <a name="parameters"></a>Parametry

*uiResID*<br/>
[in] ID prostředku rastrového obrázku, který odkazuje na Image horké nástrojů.

*uiColdResID*<br/>
[in] ID prostředku rastrového obrázku, který odkazuje na Image studenou nástrojů.

*uiMenuResID*<br/>
[in] ID prostředku rastrového obrázku, který odkazuje na regulární nabídky Image.

*bLocked*<br/>
[in] TRUE, pokud chcete zamknout nástrojů; v opačném případě FALSE.

*uiDisabledResID*<br/>
[in] ID prostředku rastrového obrázku, který odkazuje na Image zakázané nástrojů.

*uiMenuDisabledResID*<br/>
[in] ID prostředku rastrového obrázku, který odkazuje na zakázané nabídky Image.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud metoda uspěje; jinak 0.

### <a name="remarks"></a>Poznámky

[CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) metoda volá tuto metodu za účelem načtení bitové kopie, které jsou spojeny s panelem nástrojů. Potlačí tuto metodu za účelem provedení vlastní načítání prostředků obrázků.

Volání `LoadBitmapEx` metodu pro načtení další Image po vytvoření panelu nástrojů.

##  <a name="loadtoolbar"></a>  CMFCDropDownToolBar::LoadToolBar

```
virtual BOOL LoadToolBar(
    UINT uiResID,
    UINT uiColdResID = 0,
    UINT uiMenuResID = 0,
    BOOL = FALSE,
    UINT uiDisabledResID = 0,
    UINT uiMenuDisabledResID = 0,
    UINT uiHotResID = 0);
```

### <a name="parameters"></a>Parametry

[in] *uiResID*<br/>

[in] *uiColdResID*<br/>

[in] *uiMenuResID*<br/>

[in] *BOOL*<br/>

[in] *uiDisabledResID*<br/>

[in] *uiMenuDisabledResID*<br/>

[in] *uiHotResID*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="onlbuttonup"></a>  CMFCDropDownToolBar::OnLButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parametry

[in] *nFlags*<br/>

[in] *bodu*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="onmousemove"></a>  CMFCDropDownToolBar::OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parametry

[in] *nFlags*<br/>

[in] *bodu*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="onsendcommand"></a>  CMFCDropDownToolBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

[in] *pButton*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="onupdatecmdui"></a>  CMFCDropDownToolBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

[in] *pTarget*<br/>

[in] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[CMFCDropDownToolbarButton – třída](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[Návod: Vkládání ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
