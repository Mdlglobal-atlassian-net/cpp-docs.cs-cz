---
title: CMFCMenuBar – třída
ms.date: 10/18/2018
f1_keywords:
- CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar::AdjustLocations
- AFXMENUBAR/CMFCMenuBar::AllowChangeTextLabels
- AFXMENUBAR/CMFCMenuBar::AllowShowOnPaneMenu
- AFXMENUBAR/CMFCMenuBar::CalcFixedLayout
- AFXMENUBAR/CMFCMenuBar::CalcLayout
- AFXMENUBAR/CMFCMenuBar::CalcMaxButtonHeight
- AFXMENUBAR/CMFCMenuBar::CanBeClosed
- AFXMENUBAR/CMFCMenuBar::CanBeRestored
- AFXMENUBAR/CMFCMenuBar::Create
- AFXMENUBAR/CMFCMenuBar::CreateEx
- AFXMENUBAR/CMFCMenuBar::CreateFromMenu
- AFXMENUBAR/CMFCMenuBar::EnableHelpCombobox
- AFXMENUBAR/CMFCMenuBar::EnableMenuShadows
- AFXMENUBAR/CMFCMenuBar::GetAvailableExpandSize
- AFXMENUBAR/CMFCMenuBar::GetColumnWidth
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenu
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::GetFloatPopupDirection
- AFXMENUBAR/CMFCMenuBar::GetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::GetHelpCombobox
- AFXMENUBAR/CMFCMenuBar::GetHMenu
- AFXMENUBAR/CMFCMenuBar::GetMenuFont
- AFXMENUBAR/CMFCMenuBar::GetMenuItem
- AFXMENUBAR/CMFCMenuBar::GetRowHeight
- AFXMENUBAR/CMFCMenuBar::GetSystemButton
- AFXMENUBAR/CMFCMenuBar::GetSystemButtonsCount
- AFXMENUBAR/CMFCMenuBar::GetSystemMenu
- AFXMENUBAR/CMFCMenuBar::HighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsButtonExtraSizeAvailable
- AFXMENUBAR/CMFCMenuBar::IsHighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsMenuShadows
- AFXMENUBAR/CMFCMenuBar::IsRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommands
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommandsDelay
- AFXMENUBAR/CMFCMenuBar::LoadState
- AFXMENUBAR/CMFCMenuBar::OnChangeHot
- AFXMENUBAR/CMFCMenuBar::OnDefaultMenuLoaded
- AFXMENUBAR/CMFCMenuBar::OnSendCommand
- AFXMENUBAR/CMFCMenuBar::OnSetDefaultButtonText
- AFXMENUBAR/CMFCMenuBar::OnToolHitTest
- AFXMENUBAR/CMFCMenuBar::PreTranslateMessage
- AFXMENUBAR/CMFCMenuBar::RestoreOriginalstate
- AFXMENUBAR/CMFCMenuBar::SaveState
- AFXMENUBAR/CMFCMenuBar::SetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::SetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::SetMaximizeMode
- AFXMENUBAR/CMFCMenuBar::SetMenuButtonRTC
- AFXMENUBAR/CMFCMenuBar::SetMenuFont
- AFXMENUBAR/CMFCMenuBar::SetRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::SetShowAllCommands
helpviewer_keywords:
- CMFCMenuBar [MFC], AdjustLocations
- CMFCMenuBar [MFC], AllowChangeTextLabels
- CMFCMenuBar [MFC], AllowShowOnPaneMenu
- CMFCMenuBar [MFC], CalcFixedLayout
- CMFCMenuBar [MFC], CalcLayout
- CMFCMenuBar [MFC], CalcMaxButtonHeight
- CMFCMenuBar [MFC], CanBeClosed
- CMFCMenuBar [MFC], CanBeRestored
- CMFCMenuBar [MFC], Create
- CMFCMenuBar [MFC], CreateEx
- CMFCMenuBar [MFC], CreateFromMenu
- CMFCMenuBar [MFC], EnableHelpCombobox
- CMFCMenuBar [MFC], EnableMenuShadows
- CMFCMenuBar [MFC], GetAvailableExpandSize
- CMFCMenuBar [MFC], GetColumnWidth
- CMFCMenuBar [MFC], GetDefaultMenu
- CMFCMenuBar [MFC], GetDefaultMenuResId
- CMFCMenuBar [MFC], GetFloatPopupDirection
- CMFCMenuBar [MFC], GetForceDownArrows
- CMFCMenuBar [MFC], GetHelpCombobox
- CMFCMenuBar [MFC], GetHMenu
- CMFCMenuBar [MFC], GetMenuFont
- CMFCMenuBar [MFC], GetMenuItem
- CMFCMenuBar [MFC], GetRowHeight
- CMFCMenuBar [MFC], GetSystemButton
- CMFCMenuBar [MFC], GetSystemButtonsCount
- CMFCMenuBar [MFC], GetSystemMenu
- CMFCMenuBar [MFC], HighlightDisabledItems
- CMFCMenuBar [MFC], IsButtonExtraSizeAvailable
- CMFCMenuBar [MFC], IsHighlightDisabledItems
- CMFCMenuBar [MFC], IsMenuShadows
- CMFCMenuBar [MFC], IsRecentlyUsedMenus
- CMFCMenuBar [MFC], IsShowAllCommands
- CMFCMenuBar [MFC], IsShowAllCommandsDelay
- CMFCMenuBar [MFC], LoadState
- CMFCMenuBar [MFC], OnChangeHot
- CMFCMenuBar [MFC], OnDefaultMenuLoaded
- CMFCMenuBar [MFC], OnSendCommand
- CMFCMenuBar [MFC], OnSetDefaultButtonText
- CMFCMenuBar [MFC], OnToolHitTest
- CMFCMenuBar [MFC], PreTranslateMessage
- CMFCMenuBar [MFC], RestoreOriginalstate
- CMFCMenuBar [MFC], SaveState
- CMFCMenuBar [MFC], SetDefaultMenuResId
- CMFCMenuBar [MFC], SetForceDownArrows
- CMFCMenuBar [MFC], SetMaximizeMode
- CMFCMenuBar [MFC], SetMenuButtonRTC
- CMFCMenuBar [MFC], SetMenuFont
- CMFCMenuBar [MFC], SetRecentlyUsedMenus
- CMFCMenuBar [MFC], SetShowAllCommands
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
ms.openlocfilehash: 278feca6b64915d0cf789e8f68af3c3fdf9b3129
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420265"
---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar – třída

Řádek nabídek, který implementuje ukotvení.
Další podrobnosti najdete ve zdrojovém kódu, který se nachází ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(Přepisuje `CMFCToolBar::AdjustLocations`.)|
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|Určuje, zda lze textové popisky zobrazit v části obrázky na panelu nástrojů. (Overrides [CMFCToolBar:: AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).)|
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Přepisuje `CPane::AllowShowOnPaneMenu`.)|
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|Vypočítá vodorovnou velikost panelu nástrojů. (Overrides [CMFCToolBar:: CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).)|
|[CMFCMenuBar::CalcLayout](#calclayout)|(Přepisuje `CMFCToolBar::CalcLayout`.)|
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Vypočítá maximální výšku tlačítek na panelu nástrojů. (Overrides [CMFCToolBar:: CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).)|
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|Určuje, zda uživatel může zavřít panel nástrojů. (Overrides [CMFCToolBar:: CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).)|
|[CMFCMenuBar::CanBeRestored](#canberestored)|Určuje, zda systém může po přizpůsobení obnovit původní stav panelu nástrojů. (Overrides [CMFCToolBar:: CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCMenuBar:: Create](#create)|Vytvoří ovládací prvek nabídky a připojí ho k objektu `CMFCMenuBar`.|
|[CMFCMenuBar::CreateEx](#createex)|Vytvoří objekt `CMFCMenuBar` s dalšími možnostmi stylu.|
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|Inicializuje objekt `CMFCMenuBar`. Přijímá parametr HMENU, který funguje jako šablona pro vyplněné `CMFCMenuBar`.|
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|Povolí pole **se seznamem** , které je umístěné na pravé straně řádku nabídek.|
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|Určuje, zda se mají zobrazovat stíny pro místní nabídky.|
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(Overrides [CPane:: GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize).)|
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|Vrátí šířku tlačítek panelu nástrojů. (Overrides [CMFCToolBar:: GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).)|
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|Vrátí popisovač do původní nabídky v souboru prostředků.|
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|Vrátí identifikátor prostředku pro původní nabídku v souboru prostředků.|
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|Vrátí ukazatel na pole se seznamem **help** .|
|[CMFCMenuBar::GetHMenu](#gethmenu)|Vrátí popisovač do nabídky, která je připojena k objektu `CMFCMenuBar`.|
|[CMFCMenuBar::GetMenuFont](#getmenufont)|Vrátí aktuální globální písmo pro objekty nabídky.|
|[CMFCMenuBar:: getmenuitem](#getmenuitem)|Vrátí tlačítko panelu nástrojů přidružené k zadanému indexu položky.|
|[CMFCMenuBar::GetRowHeight](#getrowheight)|Vrátí výšku tlačítek panelu nástrojů. (Overrides [CMFCToolBar:: GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|Označuje, zda jsou zakázané položky nabídky zvýrazněny.|
|[CMFCMenuBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Určuje, zda lze na panelu nástrojů Zobrazit tlačítka, která mají rozšířená ohraničení. (Overrides [CMFCToolBar:: IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|Označuje, zda jsou zakázané položky zvýrazněny.|
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|Určuje, zda jsou vykreslovány stíny pro místní nabídky.|
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|Určuje, zda jsou v řádku nabídek zobrazeny naposledy použité příkazy nabídky.|
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|Určuje, zda se v místních nabídkách zobrazují všechny příkazy.|
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|Označuje, zda jsou po krátké prodlevě zobrazeny všechny příkazy v nabídkách.|
|[CMFCMenuBar:: LoadState](#loadstate)|Načte stav objektu `CMFCMenuBar` z registru.|
|[CMFCMenuBar::OnChangeHot](#onchangehot)|Volá se rozhraním, když uživatel vybere tlačítko na panelu nástrojů. (Overrides [CMFCToolBar:: OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot).)|
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|Volá se rozhraním, když okno rámce načte výchozí nabídku ze zdrojového souboru.|
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(Přepisuje `CMFCToolBar::OnSendCommand`.)|
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Volá se rozhraním, když je nabídka v režimu přizpůsobení a uživatel změní text položky nabídky.|
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(Přepisuje `CMFCToolBar::OnToolHitTest`.)|
|[CMFCMenuBar::P reTranslateMessage](#pretranslatemessage)|(Přepisuje `CMFCToolBar::PreTranslateMessage`.)|
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|Volá se rozhraním, když je nabídka v režimu přizpůsobení a uživatel vybere **obnovit** pro řádek nabídek.|
|[CMFCMenuBar:: SaveState](#savestate)|Uloží stav objektu `CMFCMenuBar` do registru.|
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|Nastaví původní nabídku v souboru prostředků.|
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|Volá se rozhraním, když se v podřízeném okně MDI změní režim zobrazení. Pokud je podřízené okno MDI nově maximalizováno nebo již není maximalizováno, tato metoda aktualizuje panel nabídek.|
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|Nastaví informace třídy modulu runtime, které jsou generovány při dynamickém vytváření tlačítek nabídky uživatelem.|
|[CMFCMenuBar::SetMenuFont](#setmenufont)|Nastaví písmo pro všechny nabídky v aplikaci.|
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|Určuje, zda se na panelu nabídek zobrazují naposledy použité příkazy nabídky.|
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|Určuje, zda se na panelu nabídek zobrazují všechny příkazy.|

## <a name="remarks"></a>Poznámky

Třída `CMFCMenuBar` je řádek nabídek, který implementuje funkce ukotvení. Je podobný panelu nástrojů, i když ho nejde zavřít – je vždycky zobrazený.

`CMFCMenuBar` podporuje možnost zobrazení naposledy použitých objektů položek nabídky. Pokud je tato možnost povolena, `CMFCMenuBar` při prvním zobrazení zobrazí pouze podmnožinu dostupných příkazů. Následně se nedávno použité příkazy zobrazují spolu s původní podmnožinou příkazů. Kromě toho může uživatel vždy rozbalit nabídku a zobrazit všechny dostupné příkazy. Proto se každý dostupný příkaz nakonfiguruje tak, aby se zobrazoval nepřetržitě, nebo se zobrazí jenom v případě, že byl nedávno vybraný.

Chcete-li použít objekt `CMFCMenuBar`, vložte jej do objektu rámce hlavního okna. Při zpracování zprávy `WM_CREATE` volejte `CMFCMenuBar::Create` nebo `CMFCMenuBar::CreateEx`. Bez ohledu na to, kterou funkci vytvoření použijete, předejte ukazatel do hlavního okna rámce. Pak povolte ukotvení voláním [CFrameWndEx:: EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Ukotvit tuto nabídku voláním [CFrameWndEx::D ockpane](../../mfc/reference/cframewndex-class.md#dockpane).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCMenuBar` třídy. Tento příklad ukazuje, jak nastavit styl podokna, povolit tlačítko přizpůsobit, povolit stínové kopie pro místní nabídky a aktualizovat řádek nabídek. Tento fragment kódu je součástí ukázky [Ukázka IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

`CMFCMenuBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmenubar. h

##  <a name="adjustlocations"></a>CMFCMenuBar::AdjustLocations

Upraví umístění položek nabídky na řádku nabídek.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Poznámky

##  <a name="allowchangetextlabels"></a>CMFCMenuBar::AllowChangeTextLabels

Určuje, zda jsou textové popisky povoleny v rámci obrázků v řádku nabídek.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pravda, pokud se uživatel může rozhodnout zobrazit popisky textu v části obrázky.

### <a name="remarks"></a>Poznámky

##  <a name="allowshowonpanemenu"></a>CMFCMenuBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="calcfixedlayout"></a>CMFCMenuBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

pro *bStretch*<br/>

pro *bHorz*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="calclayout"></a>CMFCMenuBar::CalcLayout

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>Parametry

pro *dwMode*<br/>

pro *nLength*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="calcmaxbuttonheight"></a>CMFCMenuBar::CalcMaxButtonHeight

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="canbeclosed"></a>CMFCMenuBar::CanBeClosed

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="canberestored"></a>CMFCMenuBar::CanBeRestored

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="create"></a>CMFCMenuBar:: Create

Vytvoří ovládací prvek nabídky a připojí ho k objektu [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) .

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
pro Ukazatel na nadřazené okno nového objektu `CMFCMenuBar`.

*dwStyle*<br/>
pro Styl nového řádku nabídek

*nID*<br/>
pro ID podřízeného okna řádku nabídek

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Po vytvoření objektu `CMFCMenuBar` musíte volat `Create`. Tato metoda vytvoří ovládací prvek `CMFCMenuBar` a připojí ho k objektu `CMFCMenuBar`.

Další informace o stylech panelů nástrojů naleznete v tématu [CBasePane:: SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).

##  <a name="createex"></a>CMFCMenuBar::CreateEx

Vytvoří objekt [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) se zadanými rozšířenými styly.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    CRect rcBorders = CRect(1,
    1,
    1,
    1),
    UINT nID =AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
pro Ukazatel na nadřazené okno nového objektu `CMFCMenuBar`.

*dwCtrlStyle*<br/>
pro Další styly pro nový řádek nabídek

*dwStyle*<br/>
pro Hlavní styl nového řádku nabídek.

*rcBorders*<br/>
pro Parametr `CRect`, který určuje velikosti ohraničení objektu `CMFCMenuBar`.

*nID*<br/>
pro ID podřízeného okna řádku nabídek

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je metoda úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tuto funkci byste měli použít místo [CMFCMenuBar:: Create](#create) , pokud chcete kromě stylu panelu nástrojů zadat styly. Některé často používané další styly jsou TBSTYLE_TRANSPARENT a CBRS_TOP.

Seznam dalších stylů naleznete v tématech [ovládací prvky panelu nástrojů a styly tlačítek](/windows/win32/Controls/toolbar-control-and-button-styles), [společné styly ovládacích prvků](/windows/win32/Controls/common-control-styles)a [Běžné styly oken](/windows/win32/winmsg/window-styles).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít metodu `CreateEx` třídy `CMFCMenuBar`. Tento fragment kódu je součástí ukázky [Ukázka IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

##  <a name="createfrommenu"></a>CMFCMenuBar::CreateFromMenu

Inicializuje objekt [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) . Tato metoda modeluje objekt `CMFCMenuBar` za parametrem HMENU.

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
pro Popisovač prostředku nabídky `CreateFromMenu` používá tento prostředek jako šablonu pro `CMFCMenuBar`.

*bDefaultMenu*<br/>
pro Logická hodnota, která označuje, zda je nová nabídka výchozí.

*bForceUpdate*<br/>
pro Logická hodnota, která určuje, zda tato metoda vynutí aktualizaci nabídky.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li, aby měl ovládací prvek nabídky stejné položky nabídky jako prostředek nabídky. Tuto metodu zavoláte po volání metody [CMFCMenuBar:: Create](#create) nebo [CMFCMenuBar:: CreateEx](#createex).

##  <a name="enablehelpcombobox"></a>CMFCMenuBar::EnableHelpCombobox

Povolí pole **se seznamem** , které je umístěné na pravé straně řádku nabídek.

```
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
pro ID příkazu pro **tlačítko v poli se seznamem.**

*lpszPrompt*<br/>
pro Řetězec obsahující text, který se v rozhraní zobrazí v poli se seznamem, pokud je prázdný a není aktivní. Například "sem zadejte text."

*nComboBoxWidth*<br/>
pro Šířka tlačítka pro pole se seznamem v pixelech

### <a name="remarks"></a>Poznámky

Pole se seznamem **help** se podobá **poli se seznamem** v aplikaci Microsoft Word v řádku nabídek.

Při volání této metody s *uiID* nastavenou na hodnotu 0 Tato metoda skryje pole se seznamem. V opačném případě tato metoda zobrazí pole se seznamem automaticky na pravé straně řádku nabídek. Po volání této metody zavolejte [CMFCMenuBar:: GetHelpCombobox](#gethelpcombobox) , abyste získali ukazatel na vložený objekt [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) .

##  <a name="enablemenushadows"></a>CMFCMenuBar::EnableMenuShadows

Povoluje stíny pro místní nabídky.

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro Logický parametr určující, zda mají být povoleny stínové nabídky pro místní nabídky.

### <a name="remarks"></a>Poznámky

Algoritmus, který používá tato metoda, je složitý a může snížit výkon aplikace v pomalejších systémech.

##  <a name="getavailableexpandsize"></a>CMFCMenuBar::GetAvailableExpandSize

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getcolumnwidth"></a>CMFCMenuBar::GetColumnWidth

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getdefaultmenu"></a>CMFCMenuBar::GetDefaultMenu

Načte popisovač do původní nabídky. Rozhraní načte původní nabídku ze zdrojového souboru.

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač prostředku nabídky

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace přizpůsobuje nabídku, můžete použít tuto metodu k načtení popisovače do původní nabídky.

##  <a name="getdefaultmenuresid"></a>CMFCMenuBar::GetDefaultMenuResId

Načte identifikátor prostředku pro výchozí nabídku.

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor prostředku nabídky

### <a name="remarks"></a>Poznámky

Rozhraní načte výchozí nabídku pro objekt `CMFCMenuBar` ze souboru prostředků.

##  <a name="getfloatpopupdirection"></a>CMFCMenuBar::GetFloatPopupDirection

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>Parametry

pro *pButton*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getforcedownarrows"></a>CMFCMenuBar::GetForceDownArrows

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="gethelpcombobox"></a>CMFCMenuBar::GetHelpCombobox

Vrátí ukazatel na pole se seznamem **help** .

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole se seznamem **help** . Hodnota NULL, pokud je pole se seznamem **pomocníka** skryté nebo není povoleno.

### <a name="remarks"></a>Poznámky

Pole se seznamem **help** se nachází na pravé straně řádku nabídek. Chcete-li povolit toto pole se seznamem, zavolejte metodu [CMFCMenuBar:: EnableHelpCombobox](#enablehelpcombobox) .

##  <a name="gethmenu"></a>CMFCMenuBar::GetHMenu

Načte popisovač do nabídky připojené k objektu [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) .

```
HMENU GetHMenu() const;
```

##  <a name="getmenufont"></a>CMFCMenuBar::GetMenuFont

Načte aktuální písmo nabídky.

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*bHorz*<br/>
pro Logický parametr, který určuje, zda má být vráceno vodorovné nebo svislé písmo. Hodnota TRUE označuje vodorovné písmo.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na parametr [CFont –](../../mfc/reference/cfont-class.md) , který obsahuje aktuální písmo řádku nabídek.

### <a name="remarks"></a>Poznámky

Vrácený Font je globální parametr pro aplikaci. Pro všechny `CMFCMenuBar` objekty jsou zachována dvě globální písma. Tato samostatná písma se používají pro vodorovné a svislé panely nabídek.

##  <a name="getmenuitem"></a>CMFCMenuBar:: getmenuitem

Načte objekt [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) na panelu nabídek v závislosti na indexu položky.

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>Parametry

*iItem*<br/>
pro Index položky nabídky, která se má vrátit

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `CMFCToolBarButton`, který odpovídá indexu určenému parametrem *iItem*. Hodnota NULL, pokud je index neplatný

##  <a name="getrowheight"></a>CMFCMenuBar::GetRowHeight

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getsystembutton"></a>CMFCMenuBar::GetSystemButton

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>Parametry

pro *uiBtn*<br/>

pro *bByCommand*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getsystembuttonscount"></a>CMFCMenuBar::GetSystemButtonsCount

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getsystemmenu"></a>CMFCMenuBar::GetSystemMenu

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="highlightdisableditems"></a>CMFCMenuBar::HighlightDisabledItems

Určuje, zda se v rozhraní zvýrazní položky nabídky.

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>Parametry

*bHighlight*<br/>
pro Logický parametr, který označuje, zda rozhraní zvýrazní nedostupné položky nabídky.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení rozhraní nezvýrazňuje nedostupné položky nabídky, když uživatel umístí ukazatel myši nad ně.

##  <a name="isbuttonextrasizeavailable"></a>CMFCMenuBar::IsButtonExtraSizeAvailable

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="ishighlightdisableditems"></a>CMFCMenuBar::IsHighlightDisabledItems

Určuje, zda rozhraní zvýrazní nedostupné položky nabídky.

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou zvýrazněny nedostupné položky nabídky; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení rozhraní nezvýrazňuje nedostupné položky nabídky, když uživatel umístí ukazatel myši nad ně. Tuto funkci povolíte pomocí metody [CMFCMenuBar:: HighlightDisabledItems](#highlightdisableditems) .

##  <a name="ismenushadows"></a>CMFCMenuBar::IsMenuShadows

Určuje, zda rozhraní kreslí stíny pro místní nabídky.

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud rozhraní kreslí nabídku stínů; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto funkci povolíte nebo zakážete pomocí metody [CMFCMenuBar:: EnableMenuShadows](#enablemenushadows) .

##  <a name="isrecentlyusedmenus"></a>CMFCMenuBar::IsRecentlyUsedMenus

Určuje, zda jsou v řádku nabídek zobrazeny naposledy použité příkazy nabídky.

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud `CMFCMenuBar` objekt zobrazuje naposledy použité příkazy nabídky; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pomocí funkce [CMFCMenuBar:: SetRecentlyUsedMenus](#setrecentlyusedmenus) určete, zda se na panelu nabídek zobrazují naposledy použité příkazy nabídky.

##  <a name="isshowallcommands"></a>CMFCMenuBar::IsShowAllCommands

Označuje, zda jsou v nabídkách zobrazeny všechny příkazy.

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud `CMFCMenuBar` zobrazí všechny příkazy; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Objekt `CMFCMenuBar` lze nakonfigurovat tak, aby buď zobrazoval všechny příkazy, nebo zobrazil pouze podmnožinu příkazů. Další informace o této funkci naleznete v tématu [Třída CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md).

`IsShowAllCommands` se dozvíte, jak je tato funkce nakonfigurovaná pro objekt `CMFCMenuBar`. Chcete-li určit, které příkazy nabídky jsou zobrazeny, použijte metody [CMFCMenuBar:: SetShowAllCommands](#setshowallcommands) a [CMFCMenuBar:: SetRecentlyUsedMenus](#setrecentlyusedmenus).

##  <a name="isshowallcommandsdelay"></a>CMFCMenuBar::IsShowAllCommandsDelay

Určuje, zda bude objekt [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) po krátké prodlevě zobrazovat všechny příkazy.

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud panel nabídek po krátké prodlevě zobrazuje úplné nabídky; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Když nakonfigurujete panel nabídek pro zobrazení naposledy použitých položek, panel nabídek zobrazí úplnou nabídku jedním ze dvou způsobů:

- Zobrazí celou nabídku po programovém zpoždění od okamžiku, kdy uživatel najede kurzorem na šipku v dolní části nabídky.

- Zobrazí celou nabídku, jakmile uživatel klikne na šipku v dolní části nabídky.

Ve výchozím nastavení všechny `CMFCMenuBar` objekty používají možnost zobrazení úplné nabídky po krátké prodlevě. Tuto možnost nelze změnit programově ve třídě `CMFCMenuBar`. Uživatel však může změnit chování během přizpůsobení panelu nástrojů pomocí dialogového okna **přizpůsobit** .

##  <a name="loadstate"></a>CMFCMenuBar:: LoadState

Načte stav řádku nabídek z registru systému Windows.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
pro Řetězec, který obsahuje cestu ke klíči registru systému Windows.

*nIndex*<br/>
pro ID ovládacího prvku pro panel nabídek

*uiID*<br/>
pro Rezervovaná hodnota.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

K uložení stavu řádku nabídek do registru použijte metodu [CMFCMenuBar:: SaveState](#savestate) . Uložené informace obsahují položky nabídky, stav Docker a umístění řádku nabídek.

Ve většině případů vaše aplikace nevolá `LoadState`. Rozhraní volá tuto metodu, když inicializuje pracovní prostor.

##  <a name="onchangehot"></a>CMFCMenuBar::OnChangeHot

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>Parametry

pro *iHot*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="ondefaultmenuloaded"></a>CMFCMenuBar::OnDefaultMenuLoaded

Rozhraní volá tuto metodu, když načte prostředek nabídky ze souboru prostředků.

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
pro Popisovač pro nabídku připojenou k objektu `CMFCMenuBar`.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádnou akci. Tuto funkci přepište, pokud chcete spustit vlastní kód poté, co rozhraní načte prostředek nabídky ze souboru prostředků.

##  <a name="onsendcommand"></a>CMFCMenuBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

pro *pButton*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="onsetdefaultbuttontext"></a>CMFCMenuBar::OnSetDefaultButtonText

Rozhraní volá tuto metodu, když uživatel změní text položky na řádku nabídek.

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

*pButton*<br/>
pro Ukazatel na objekt [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) , který chce uživatel přizpůsobit.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud rozhraní aplikuje změny uživatele na panel nabídek; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Výchozí implementace této metody změní text tlačítka na text, který uživatel poskytne.

##  <a name="ontoolhittest"></a>CMFCMenuBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parametry

pro *bod*<br/>

pro *PTI*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="pretranslatemessage"></a>CMFCMenuBar::P reTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

pro *pMsg*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="restoreoriginalstate"></a>CMFCMenuBar::RestoreOriginalstate

Volá se rozhraním, když uživatel vybere **reset** v dialogovém okně **přizpůsobit** .

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je metoda úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda se volá, když uživatel vybere **reset** v nabídce vlastní nastavení. Tuto metodu můžete také ručně zavolat, chcete-li obnovit stav řádku nabídek programově. Tato metoda načte původní stav ze souboru prostředků.

Tuto metodu přepište, pokud chcete provádět jakékoli zpracování, když uživatel vybere možnost **resetovat** .

##  <a name="savestate"></a>CMFCMenuBar:: SaveState

Uloží stav objektu [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) do registru systému Windows.

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
pro Řetězec, který obsahuje cestu ke klíči registru systému Windows.

*nIndex*<br/>
pro ID ovládacího prvku pro panel nabídek

*uiID*<br/>
pro Rezervovaná hodnota.

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE;

### <a name="remarks"></a>Poznámky

Obvykle aplikace nevolá `SaveState`. Rozhraní volá tuto metodu, když je pracovní prostor serializován. Další informace najdete v tématu [CWinAppEx:: SaveState](../../mfc/reference/cwinappex-class.md#savestate).

Uložené informace obsahují položky nabídky, stav Docker a umístění řádku nabídek.

##  <a name="setdefaultmenuresid"></a>CMFCMenuBar::SetDefaultMenuResId

Nastaví výchozí nabídku pro objekt [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) na základě ID prostředku.

```
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>Parametry

*uiResId*<br/>
pro ID prostředku nové výchozí nabídky

### <a name="remarks"></a>Poznámky

Metoda [CMFCMenuBar:: RestoreOriginalstate](#restoreoriginalstate) obnoví výchozí nabídku ze souboru prostředků.

Použijte metodu [CMFCMenuBar:: GetDefaultMenuResId](#getdefaultmenuresid) k načtení výchozí nabídky bez obnovení.

##  <a name="setforcedownarrows"></a>CMFCMenuBar::SetForceDownArrows

```
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>Parametry

pro *bValue*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setmaximizemode"></a>CMFCMenuBar::SetMaximizeMode

Rozhraní volá tuto metodu, když objekt MDI změní režim zobrazení a řádek nabídek musí být aktualizován.

```
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>Parametry

*bMax*<br/>
pro Logická hodnota, která určuje režim. Další informace naleznete v části Poznámky.

*pWnd*<br/>
pro Ukazatel na podřízené okno MDI, které se mění.

*bRecalcLayout*<br/>
pro Logická hodnota určující, zda má být rozložení řádku nabídek přepočítáno okamžitě.

### <a name="remarks"></a>Poznámky

Po maximalizaci podřízeného okna MDI se v okně hlavního rámce MDI zobrazí systémová nabídka a tlačítka **minimalizovat**, **maximalizovat** a **Zavřít** . Pokud má *Bmax* hodnotu true a *pWnd* není null, podřízené okno MDI se maximalizuje a řádek nabídek musí zahrnovat nadbytečné ovládací prvky. V opačném případě se řádek nabídek vrátí do jeho normálního stavu.

##  <a name="setmenubuttonrtc"></a>CMFCMenuBar::SetMenuButtonRTC

Nastaví informace třídy modulu runtime, které rozhraní používá při vytváření tlačítek nabídky uživatelem.

```
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>Parametry

*pMenuButtonRTC*<br/>
pro Informace [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pro třídu odvozenou z [třídy CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md).

### <a name="remarks"></a>Poznámky

Když uživatel přidá nová tlačítka do řádku nabídek, rozhraní vytvoří tlačítka dynamicky. Ve výchozím nastavení vytvoří `CMFCMenuButton` objekty. Přepište tuto metodu pro změnu typu objektů tlačítek, které rozhraní vytvoří.

##  <a name="setmenufont"></a>CMFCMenuBar::SetMenuFont

Nastaví písmo pro všechny řádky nabídek ve vaší aplikaci.

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
pro Ukazatel na strukturu [LOGFONT](/windows/win32/api/dimm/ns-dimm-logfonta) , která definuje písmo, které má být nastaveno.

*bHorz*<br/>
pro TRUE, pokud chcete, aby byl parametr *lpLogFont* použit pro vertikální písmo, false, pokud chcete použít pro horizontální písmo.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pro všechny `CMFCMenuBar` objekty se používají dvě písma. Tato samostatná písma se používají pro vodorovné a svislé panely nabídek.

Nastavení písma jsou globální proměnné a ovlivňují všechny `CMFCMenuBar` objekty.

##  <a name="setrecentlyusedmenus"></a>CMFCMenuBar::SetRecentlyUsedMenus

Určuje, zda se na panelu nabídek zobrazují naposledy použité příkazy nabídky.

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*Přání*<br/>
pro Logická hodnota, která určuje, zda jsou zobrazeny naposledy použité příkazy nabídky.

##  <a name="setshowallcommands"></a>CMFCMenuBar::SetShowAllCommands

Určuje, zda se v nabídce zobrazují všechny dostupné příkazy.

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>Parametry

*bShowAllCommands*<br/>
pro Logický parametr, který určuje, zda se v místní nabídce zobrazí všechny příkazy nabídky.

### <a name="remarks"></a>Poznámky

Pokud nabídka nezobrazí všechny příkazy nabídky, skryje příkazy, které se zřídka používají. Další informace o zobrazení příkazů nabídky naleznete v tématu [Třída CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)
