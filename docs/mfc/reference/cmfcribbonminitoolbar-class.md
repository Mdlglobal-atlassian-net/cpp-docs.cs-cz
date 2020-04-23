---
title: CmFCRibbonRibbonMiniToolBar třída
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
ms.openlocfilehash: 5e5ac6c923640b7584d89a9c6f75d941deadddf3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754076"
---
# <a name="cmfcribbonminitoolbar-class"></a>CmFCRibbonRibbonMiniToolBar třída

Implementuje kontextový rozbalovací panel nástrojů.

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
|`CMFCRibbonMiniToolBar::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCRibbonMiniToolBar::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||
|[CMFCRibbonRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|(Přepíše `CMFCPopupMenu::IsRibbonMiniToolBar`.)|
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|Nastaví seznam příkazů, které se mají zobrazit na panelu nástrojů.|
|[CMFCRibbonMiniToolBar::Zobrazit](#show)|Zobrazí mini panel nástrojů na určených souřadnicích obrazovky.|
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|Zobrazí mini panel nástrojů spolu s místní nabídkou.|

## <a name="remarks"></a>Poznámky

Mini panel nástrojů se obvykle zobrazí poté, co uživatel vybere objekt v dokumentu. Například poté, co uživatel vybere blok textu v textovém editoru, aplikace zobrazí mini panel nástrojů, který obsahuje příkazy pro formátování textu.

Mini panel nástrojů se stane průhledným, když je ukazatel myši mimo hranice mini panelu nástrojů.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CmFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

`CMFCRibbonPanelMenu`

[CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonMiniToolBar.h

## <a name="cmfcribbonminitoolbarsetcommands"></a><a name="setcommands"></a>CMFCRibbonMiniToolBar::SetCommands

Nastaví seznam příkazů, které se mají zobrazit na panelu nástrojů.

```cpp
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>Parametry

*pPruh*<br/>
[v] Pruh pásu karet, na který mini panel nástrojů vyhledá tlačítka, která se mají zobrazit.

*příkazy lst*<br/>
[v] Seznam příkazů, které mají být zobrazeny na mini panelu nástrojů. Všechny kategorie pásu karet jsou vyhledány a vyhledávají přidružená tlačítka.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k nastavení seznamu příkazů, které se mají zobrazit v mini panelu nástrojů.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `SetCommands` používat metodu třídy. `CMFCRibbonMiniToolBar` Tento fragment kódu je součástí [ukázky ukázky ukázky ukázky ms office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

## <a name="cmfcribbonminitoolbarshow"></a><a name="show"></a>CMFCRibbonMiniToolBar::Zobrazit

Zobrazí mini panel nástrojů na určených souřadnicích obrazovky.

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Určuje vodorovnou polohu minipanelu nástrojů v souřadnicích obrazovky.

*Y*<br/>
[v] Určuje svislou polohu minipanelu nástrojů v souřadnicích obrazovky.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl mini panel nástrojů úspěšně zobrazen; jinak NEPRAVDA.

## <a name="cmfcribbonminitoolbarshowwithcontextmenu"></a><a name="showwithcontextmenu"></a>CMFCRibbonMiniToolBar::ShowWithContextMenu

Zobrazí mini panel nástrojů spolu s místní nabídkou.

```
BOOL ShowWithContextMenu(
    int x,
    int y,
    UINT uiMenuResID,
    CWnd* pWndOwner);
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Určuje vodorovnou polohu kontextové nabídky v souřadnicích obrazovky.

*Y*<br/>
[v] Určuje svislou polohu kontextové nabídky v souřadnicích obrazovky.

*uiMenuResID*<br/>
[v] Určuje ID prostředku kontextové nabídky, které se má zobrazit.

*pWndVlastník*<br/>
[v] Identifikuje okno, ve kterém jsou přijímá zprávy z místní nabídky.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla místní nabídka úspěšně zobrazena; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k zobrazení mini panelu nástrojů, který má místní nabídku. Místní nabídka je umístěna 15 pixelů pod mini panelem nástrojů.

## <a name="cmfcribbonminitoolbariscontextmenumode"></a><a name="iscontextmenumode"></a>CMFCRibbonMiniToolBar::IsContextMenuMode

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonminitoolbarisribbonminitoolbar"></a><a name="isribbonminitoolbar"></a>CMFCRibbonRibbonMiniToolBar::IsRibbonMiniToolBar

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
