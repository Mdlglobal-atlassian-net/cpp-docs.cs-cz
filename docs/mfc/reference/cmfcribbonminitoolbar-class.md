---
title: Cmfcribbonminitoolbar – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
ms.openlocfilehash: 462a4aa04ddc542db8aba734ed93ab0fae905dad
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283836"
---
# <a name="cmfcribbonminitoolbar-class"></a>Cmfcribbonminitoolbar – třída

Implementuje kontextovou nabídku nástrojů.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|Výchozí konstruktor.|
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCRibbonMiniToolBar::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|(Přepíše `CMFCPopupMenu::IsRibbonMiniToolBar`.)|
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|Nastaví seznam příkazů, který se má zobrazit na panelu nástrojů.|
|[CMFCRibbonMiniToolBar::Show](#show)|Zobrazí mini nástrojů na souřadnicích zadanou obrazovku.|
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|Zobrazí mini nástrojů spolu s místní nabídkou.|

## <a name="remarks"></a>Poznámky

Mini nástrojů se obvykle zobrazí, když uživatele vybere objekt v dokumentu. Když uživatele vybere blok textu v textovém editoru, například aplikace zobrazí mini nástrojů, který obsahuje příkazy pro formátování textu.

Mini nástrojů viditelný, když ukazatel myši je mimo rozsah mini nástrojů.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[Cminiframewnd –](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

`CMFCRibbonPanelMenu`

[CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonMiniToolBar.h

##  <a name="setcommands"></a>  CMFCRibbonMiniToolBar::SetCommands

Nastaví seznam příkazů, který se má zobrazit na panelu nástrojů.

```
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>Parametry

*pRibbonBar*<br/>
[in] Na panelu pásu karet, která hledá mini nástrojů pro tlačítka pro zobrazení.

*lstCommands*<br/>
[in] Seznam příkazů, který se má zobrazit na panelu nástrojů mini. Najít související tlačítka jsou prohledány všechny kategorie pásu karet.

### <a name="remarks"></a>Poznámky

Pomocí této funkce můžete nastavit seznam příkazů, který se má zobrazit na panelu nástrojů zkrácené.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `SetCommands` metodu `CMFCRibbonMiniToolBar` třídy. Tento fragment kódu je součástí [MS Office 2007 demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

##  <a name="show"></a>  CMFCRibbonMiniToolBar::Show

Zobrazí mini nástrojů na souřadnicích zadanou obrazovku.

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Určuje vodorovná pozice mini nástrojů v souřadnicovém systému obrazovky.

*y*<br/>
[in] Určuje svislé umístění mini nástrojů v souřadnicovém systému obrazovky.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byl úspěšně; zobrazí mini panel nástrojů v opačném případě hodnota FALSE.

##  <a name="showwithcontextmenu"></a>  CMFCRibbonMiniToolBar::ShowWithContextMenu

Zobrazí mini nástrojů spolu s místní nabídkou.

```
BOOL ShowWithContextMenu(
    int x,
    int y,
    UINT uiMenuResID,
    CWnd* pWndOwner);
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Určuje vodorovné umístění v místní nabídce v souřadnicovém systému obrazovky.

*y*<br/>
[in] Určuje svislé umístění v místní nabídce v souřadnicovém systému obrazovky.

*uiMenuResID*<br/>
[in] Určuje ID prostředku v místní nabídce pro zobrazení.

*pWndOwner*<br/>
[in] Identifikuje okna, která přijímá zprávy z kontextové nabídky.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byl úspěšně; zobrazí místní nabídka v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte, chcete-li zobrazit mini nástrojů, který má místní nabídka. V místní nabídce je umístěné 15 pixelů pod mini nástrojů.

##  <a name="iscontextmenumode"></a>  CMFCRibbonMiniToolBar::IsContextMenuMode

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="isribbonminitoolbar"></a>  CMFCRibbonMiniToolBar::IsRibbonMiniToolBar

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
