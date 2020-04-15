---
title: CMFCDropDownToolBar – třída
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
ms.openlocfilehash: 68dd976471b39d7f50c2f0378b2fce99ad3feeca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367593"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar – třída

Panel nástrojů, který se zobrazí, když uživatel stiskne a podrží tlačítko panelu nástrojů nejvyšší úrovně.

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCDropDownToolBar::AllowShowonPaneMenu](#allowshowonpanemenu)|(Přepíše `CPane::AllowShowOnPaneMenu`.)|
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Přepíše [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Přepíše [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Přepíše `CMFCToolBar::OnSendCommand`.)|
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Přepíše [CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md).|

### <a name="remarks"></a>Poznámky

Objekt `CMFCDropDownToolBar` kombinuje vizuální vzhled panelu nástrojů s chováním místní nabídky. Když uživatel stiskne a podrží rozevírací panel nástrojů (viz [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), zobrazí se rozevírací panel nástrojů a uživatel může vybrat tlačítko z rozevíracího panelu nástrojů posouváním na něj a uvolněním tlačítka myši. Poté, co uživatel vybere tlačítko v rozevíracím panelu nástrojů, se toto tlačítko zobrazí jako aktuální tlačítko na panelu nástrojů nejvyšší úrovně.

Rozevírací panel nástrojů nelze přizpůsobit ani ukotvit a nemá stav odtržení.

Následující obrázek `CMFCDropDownToolBar` znázorňuje objekt:

![Příklad panelu NÁSTROJŮ CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "Příklad panelu NÁSTROJŮ CMFCDropDownToolbar")

Objekt vytvoříte `CMFCDropDownToolBar` stejným způsobem jako běžný panel nástrojů (viz [třída CMFCToolBar ).](../../mfc/reference/cmfctoolbar-class.md)

Vložení rozevíracího panelu nástrojů do nadřazeného panelu nástrojů:

1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.

2. Vytvořte `CMFCDropDownToolBarButton` objekt, který obsahuje rozevírací panel nástrojů (další informace naleznete v tématu [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).

3. Nahraďte fiktivní tlačítko `CMFCDropDownToolBarButton` objektem pomocí [cmfctoolbar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Další informace o tlačítkách panelu nástrojů naleznete v [tématu Návod: Uvedení ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md). Příklad rozevíracího panelu nástrojů naleznete v ukázkovém projektu VisualStudioDemo.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `Create` používat metodu ve `CMFCDropDownToolBar` třídě. Tento fragment kódu je součástí [ukázky ukázky aplikace Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCPanel](../../mfc/reference/cmfctoolbar-class.md)

[CmFCDropDownPanelnástrojů](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCDropDownToolBar::AllowShowonPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcdropdowntoolbarloadbitmap"></a><a name="loadbitmap"></a>CMFCDropDownToolBar::LoadBitmap

Načte obrazy panelu nástrojů z prostředků aplikace.

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
[v] ID prostředku bitmapy, která odkazuje na horké obrazy panelu nástrojů.

*uiColdResID*<br/>
[v] ID prostředku bitmapy, která odkazuje na studené obrazy panelu nástrojů.

*uiMenuResID*<br/>
[v] ID prostředku rastrového obrázku, který odkazuje na běžné obrazy nabídky.

*Blokován*<br/>
[v] TRUE pro uzamčení panelu nástrojů; jinak FALSE.

*uiDisabledResID*<br/>
[v] ID prostředku bitmapy, která odkazuje na zakázané obrazy panelu nástrojů.

*uiMenuDisabledResID*<br/>
[v] ID prostředku bitmapy, která odkazuje na zakázané obrazy nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je metoda úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Metoda [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) volá tuto metodu k načtení bitových kopií, které jsou přidruženy k panelu nástrojů. Přepsat tuto metodu provádět vlastní načítání prostředků bitové kopie.

Volání `LoadBitmapEx` metody načíst další obrázky po vytvoření panelu nástrojů.

## <a name="cmfcdropdowntoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CMFCDropDownToolBar::LoadToolBar

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

[v] *uiResID*<br/>

[v] *uiColdResID*<br/>

[v] *uiMenuResID*<br/>

[v] *BOOL*<br/>

[v] *uiDisabledResID*<br/>

[v] *uiMenuDisabledResID*<br/>

[v] *uiHotResID*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcdropdowntoolbaronlbuttonup"></a><a name="onlbuttonup"></a>CMFCDropDownToolBar::OnLButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parametry

[v] *nPříznaky*<br/>

[v] *bod*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcdropdowntoolbaronmousemove"></a><a name="onmousemove"></a>CMFCDropDownToolBar::OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parametry

[v] *nPříznaky*<br/>

[v] *bod*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcdropdowntoolbaronsendcommand"></a><a name="onsendcommand"></a>CMFCDropDownToolBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

[v] *pTlačítko*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcdropdowntoolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCDropDownToolBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

[v] *pCíl*<br/>

[v] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar::Vytvořit](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[CMFCDropDownToolbarButton – třída](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
