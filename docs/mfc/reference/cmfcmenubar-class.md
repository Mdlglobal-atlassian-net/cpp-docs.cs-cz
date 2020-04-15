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
ms.openlocfilehash: 50dd488d1f59c99b8fee1eb96acf6d0041547df9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369692"
---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar – třída

Řádek nabídek, který implementuje ukotvení.
Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCMenubar::Adjustlocations](#adjustlocations)|(Přepíše `CMFCToolBar::AdjustLocations`.)|
|[CMFCPanel menu::AllowChangeTextLabels](#allowchangetextlabels)|Určuje, zda lze textové popisky zobrazit pod obrázky na tlačítkách panelu nástrojů. (Přepíše [CMFCToolBar::AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).)|
|[CMFCMenubar::AllowShowonpaneMenu](#allowshowonpanemenu)|(Přepíše `CPane::AllowShowOnPaneMenu`.)|
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|Vypočítá vodorovnou velikost panelu nástrojů. (Přepíše [CMFCToolBar::CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).)|
|[CMFCMenuBar::Rozložení čáry](#calclayout)|(Přepíše `CMFCToolBar::CalcLayout`.)|
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Vypočítá maximální výšku tlačítek v panelu nástrojů. (Přepíše [CMFCToolBar::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).)|
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|Určuje, zda může uživatel zavřít panel nástrojů. (Přepíše [CMFCToolBar::CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).)|
|[CMFCMenuBar::CanBeRestored](#canberestored)|Určuje, zda může systém po vlastním nastavení obnovit původní stav panelu nástrojů. (Přepíše [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCMenubar::Vytvořit](#create)|Vytvoří ovládací prvek nabídky a `CMFCMenuBar` připojí jej k objektu.|
|[CMFCMenubar::CreateEx](#createex)|Vytvoří `CMFCMenuBar` objekt s dalšími možnostmi stylu.|
|[CMFCPanelmenu::CreateFromMenu](#createfrommenu)|Inicializuje `CMFCMenuBar` objekt. Přijme parametr HMENU, který funguje jako šablona pro naplněnou `CMFCMenuBar`.|
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|Povolí pole se seznamem **nápovědy,** které je umístěno na pravé straně panelu nabídek.|
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|Určuje, zda se mají zobrazit stíny pro rozbalovací nabídky.|
|[CMFCMenubar::GetavailableExpandSize](#getavailableexpandsize)|(Přepíše [CPane::GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize).)|
|[CMFCMenubar::GetColumnWidth](#getcolumnwidth)|Vrátí šířku tlačítek panelu nástrojů. (Přepíše [CMFCToolBar::GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).)|
|[CMFCPanel menu::GetDefaultMenu](#getdefaultmenu)|Vrátí popisovač původní nabídky v souboru prostředků.|
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|Vrátí identifikátor prostředku pro původní nabídku v souboru prostředků.|
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|Vrátí ukazatel na pole se seznamem **Nápověda.**|
|[CMFCMenubar::GetHMenu](#gethmenu)|Vrátí popisovač do nabídky, která `CMFCMenuBar` je připojena k objektu.|
|[CMFCMenubar::GetMenuFont](#getmenufont)|Vrátí aktuální globální písmo pro objekty nabídky.|
|[CMFCPanelmenu::GetMenuItem](#getmenuitem)|Vrátí tlačítko panelu nástrojů přidružené k zadaný index položky.|
|[CMFCMenubar::GetRowHeight](#getrowheight)|Vrátí výšku tlačítek panelu nástrojů. (Přepíše [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCPanelmenu::GetSystemButton](#getsystembutton)||
|[CMFCPanel menu::GetSystemButtonsCount](#getsystembuttonscount)||
|[CMFCPanel menu::GetSystemMenu](#getsystemmenu)||
|[CMFCPanel menu::ZvýrazněníZakázané položky](#highlightdisableditems)|Označuje, zda jsou zvýrazněny zakázané položky nabídky.|
|[CMFCMenuBar::isbuttonextrasizek dispozici](#isbuttonextrasizeavailable)|Určuje, zda lze na panelu nástrojů zobrazovat tlačítka s rozšířenými ohraničeními. (Přepíše [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|Označuje, zda jsou zvýrazněny zakázané položky.|
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|Označuje, zda jsou pro rozbalovací nabídky vykresleny stíny.|
|[CMFCMenuBar::Nabídky nabídek](#isrecentlyusedmenus)|Označuje, zda jsou na řádku nabídek zobrazeny naposledy použité příkazy nabídky.|
|[CMFCMenuBar::Příkazy IsShowAllCommands](#isshowallcommands)|Označuje, zda se v rozbalovacích nabídkách zobrazují všechny příkazy.|
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|Označuje, zda nabídky zobrazují všechny příkazy po krátké prodlevě.|
|[CMFCPanel menu::LoadState](#loadstate)|Načte stav `CMFCMenuBar` objektu z registru.|
|[CMFCMenuBar::OnChangeHot](#onchangehot)|Volat rámci při uživatel vybere tlačítko na panelu nástrojů. (Přepíše [CMFCToolBar::OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot).)|
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|Volat rámci při okno rámce načte výchozí nabídku ze souboru prostředků.|
|[CMFCPanel menu::Příkaz OnSendCommand](#onsendcommand)|(Přepíše `CMFCToolBar::OnSendCommand`.)|
|[CMFCPanelmenu::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Volat rámci, když je nabídka v režimu přizpůsobení a uživatel změní text položky nabídky.|
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(Přepíše `CMFCToolBar::OnToolHitTest`.)|
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|(Přepíše `CMFCToolBar::PreTranslateMessage`.)|
|[CMFCMenuBar::Obnovit původní stav](#restoreoriginalstate)|Volat rámci, když je nabídka v režimu přizpůsobení a uživatel vybere **Obnovit** pro řádek nabídek.|
|[CMFCMenubar::SaveState](#savestate)|Uloží stav objektu `CMFCMenuBar` do registru.|
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|Nastaví původní nabídku v souboru prostředků.|
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||
|[CMFCPanel menu::SetMaximizeMode](#setmaximizemode)|Volat rámci při podřízené okno MDI změní svůj režim zobrazení. Pokud podřízené okno MDI je nově maximalizované nebo již není maximalizováno, tato metoda aktualizuje řádek nabídek.|
|[CMFCPanel menu::SetMenuButtonRTC](#setmenubuttonrtc)|Nastaví informace o třídě runtime, které jsou generovány, když uživatel dynamicky vytvoří tlačítka nabídky.|
|[CMFCPanel menu::SetMenuFont](#setmenufont)|Nastaví písmo pro všechny nabídky v aplikaci.|
|[CMFCMenuBar::Nastavitnabídky naposledy použitých](#setrecentlyusedmenus)|Určuje, zda se na panelu nabídek zobrazí naposledy použité příkazy nabídek.|
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|Určuje, zda se na řádku nabídek zobrazí všechny příkazy.|

## <a name="remarks"></a>Poznámky

Třída `CMFCMenuBar` je řádek nabídek, který implementuje funkce ukotvení. Podobá se panelu nástrojů, i když jej nelze zavřít - je vždy zobrazen.

`CMFCMenuBar`podporuje možnost zobrazení naposledy použitých objektů položek nabídky. Pokud je tato možnost `CMFCMenuBar` povolena, zobrazí se při prvním zobrazení pouze podmnožina dostupných příkazů. Poté jsou naposledy použité příkazy zobrazeny společně s původní podmnožinou příkazů. Kromě toho může uživatel vždy rozbalit nabídku a zobrazit všechny dostupné příkazy. Každý dostupný příkaz je tedy nakonfigurován tak, aby se zobrazoval neustále nebo pouze v případě, že byl nedávno vybrán.

Chcete-li `CMFCMenuBar` použít objekt, vložte jej do objektu rámce hlavního okna. Při zpracování `WM_CREATE` zprávy `CMFCMenuBar::Create` volejte `CMFCMenuBar::CreateEx`nebo . Bez ohledu na to, kterou funkci vytvoříte, předáte ukazatel do okna hlavního rámce. Potom povolte ukotvení voláním [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Ukotvit tuto nabídku voláním [CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCMenuBar` metody ve třídě. Příklad ukazuje, jak nastavit styl podokna, povolit tlačítko přizpůsobit, povolit pole nápovědy, povolit stíny pro rozbalovací nabídky a aktualizovat řádek nabídek. Tento fragment kódu je součástí [ukázky ukázky aplikace IE .](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCPanel](../../mfc/reference/cmfctoolbar-class.md)

`CMFCMenuBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmenubar.h

## <a name="cmfcmenubaradjustlocations"></a><a name="adjustlocations"></a>CMFCMenubar::Adjustlocations

Upraví pozice položek nabídky na řádku nabídek.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCPanel menu::AllowChangeTextLabels

Určuje, zda jsou textové popisky povoleny pod obrázky v řádku nabídek.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se uživatel může rozhodnout zobrazit textové popisky pod obrázky.

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCMenubar::AllowShowonpaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCMenuBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

[v] *bÚsek*<br/>

[v] *bHorz*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarcalclayout"></a><a name="calclayout"></a>CMFCMenuBar::Rozložení čáry

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>Parametry

[v] *dwMode*<br/>

[v] *nDélka*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarcalcmaxbuttonheight"></a><a name="calcmaxbuttonheight"></a>CMFCMenuBar::CalcMaxButtonHeight

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarcanbeclosed"></a><a name="canbeclosed"></a>CMFCMenuBar::CanBeClosed

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarcanberestored"></a><a name="canberestored"></a>CMFCMenuBar::CanBeRestored

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarcreate"></a><a name="create"></a>CMFCMenubar::Vytvořit

Vytvoří ovládací prvek nabídky a připojí jej k objektu [CMFCMenuBar.](../../mfc/reference/cmfcmenubar-class.md)

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[v] Ukazatel na nadřazené okno pro nový `CMFCMenuBar` objekt.

*dwStyl*<br/>
[v] Styl nového řádku nabídek.

*Nid*<br/>
[v] ID pro podřízené okno panelu nabídek.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

### <a name="remarks"></a>Poznámky

Po vytvoření `CMFCMenuBar` objektu je `Create`nutné volat . Tato metoda `CMFCMenuBar` vytvoří ovládací prvek a `CMFCMenuBar` připojí jej k objektu.

Další informace o stylech panelů nástrojů naleznete v [tématu CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).

## <a name="cmfcmenubarcreateex"></a><a name="createex"></a>CMFCMenubar::CreateEx

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
[v] Ukazatel na nadřazené okno nového `CMFCMenuBar` objektu.

*dwCtrlStyl*<br/>
[v] Další styly pro nový řádek nabídek.

*dwStyl*<br/>
[v] Hlavní styl nového panelu nabídek.

*rcBorders*<br/>
[v] Parametr, `CRect` který určuje velikosti ohraničení `CMFCMenuBar` objektu.

*Nid*<br/>
[v] ID pro podřízené okno panelu nabídek.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je metoda úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tuto funkci byste měli použít místo [CMFCMenuBar::Create,](#create) pokud chcete kromě stylu panelu nástrojů zadat styly. Některé často používané další styly jsou TBSTYLE_TRANSPARENT a CBRS_TOP.

Seznamy dalších stylů naleznete v [tématu Ovládací prvek panelu nástrojů a Styly tlačítek](/windows/win32/Controls/toolbar-control-and-button-styles), [Běžné styly ovládacích prvků](/windows/win32/Controls/common-control-styles)a Běžné [styly oken](/windows/win32/winmsg/window-styles).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CreateEx` používat metodu třídy. `CMFCMenuBar` Tento fragment kódu je součástí [ukázky ukázky aplikace IE .](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

## <a name="cmfcmenubarcreatefrommenu"></a><a name="createfrommenu"></a>CMFCPanelmenu::CreateFromMenu

Inicializuje objekt [CMFCMenuBar.](../../mfc/reference/cmfcmenubar-class.md) Tato metoda `CMFCMenuBar` modeluje objekt za parametrem HMENU.

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>Parametry

*hNabídka*<br/>
[v] Popisovač prostředku nabídky. `CreateFromMenu`Používá tento prostředek jako `CMFCMenuBar`šablonu pro .

*bNabídka Výchozí*<br/>
[v] Logická hodnota označující, zda je nová nabídka výchozí nabídkou.

*bForceUpdate*<br/>
[v] Logická hodnota, která označuje, zda tato metoda vynutí aktualizaci nabídky.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, pokud chcete, aby ovládací prvek nabídky měl stejné položky nabídky jako prostředek nabídky. Tuto metodu zavoláte po volání [cmfcmenubar::Create](#create) nebo [CMFCMenuBar::CreateEx](#createex).

## <a name="cmfcmenubarenablehelpcombobox"></a><a name="enablehelpcombobox"></a>CMFCMenuBar::EnableHelpCombobox

Povolí pole se seznamem **nápovědy,** které je umístěno na pravé straně panelu nabídek.

```
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[v] ID příkazu pro tlačítko pole se seznamem **Nápověda**

*lpszPrompt*<br/>
[v] Řetězec, který obsahuje text, který rozhraní zobrazí v poli se seznamem, pokud je prázdný a není aktivní. Například "Zadejte text zde".

*nComboBoxWidth*<br/>
[v] Šířka tlačítka pro pole se seznamem v pixelech.

### <a name="remarks"></a>Poznámky

Pole se seznamem **Nápověda** se podobá poli se seznamem **Nápověda** v panelu nabídek aplikace Microsoft Word.

Při volání této metody s *uiID* nastavena na 0, tato metoda skryje pole se seznamem. V opačném případě tato metoda automaticky zobrazí pole se seznamem na pravé straně panelu nabídek. Po volání této metody volejte [CMFCMenuBar::GetHelpCombobox](#gethelpcombobox) získat ukazatel na vložený objekt [CMFCToolBarComboBox.](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="cmfcmenubarenablemenushadows"></a><a name="enablemenushadows"></a>CMFCMenuBar::EnableMenuShadows

Povolí stíny pro rozbalovací nabídky.

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] Logický parametr, který označuje, zda mají být pro rozbalovací nabídky povoleny stíny.

### <a name="remarks"></a>Poznámky

Algoritmus, který používá tato metoda je složitý a může snížit výkon aplikace v pomalejších systémech.

## <a name="cmfcmenubargetavailableexpandsize"></a><a name="getavailableexpandsize"></a>CMFCMenubar::GetavailableExpandSize

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubargetcolumnwidth"></a><a name="getcolumnwidth"></a>CMFCMenubar::GetColumnWidth

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubargetdefaultmenu"></a><a name="getdefaultmenu"></a>CMFCPanel menu::GetDefaultMenu

Načte popisovač do původní nabídky. Rozhraní framework načte původní nabídku ze souboru prostředků.

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač prostředku nabídky.

### <a name="remarks"></a>Poznámky

Pokud aplikace přizpůsobí nabídku, můžete tuto metodu použít k načtení popisovače do původní nabídky.

## <a name="cmfcmenubargetdefaultmenuresid"></a><a name="getdefaultmenuresid"></a>CMFCMenuBar::GetDefaultMenuResId

Načte identifikátor prostředku pro výchozí nabídku.

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor prostředku nabídky.

### <a name="remarks"></a>Poznámky

Rozhraní framework načte výchozí `CMFCMenuBar` nabídku objektu ze souboru prostředků.

## <a name="cmfcmenubargetfloatpopupdirection"></a><a name="getfloatpopupdirection"></a>CMFCMenuBar::GetFloatPopupDirection

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>Parametry

[v] *pTlačítko*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubargetforcedownarrows"></a><a name="getforcedownarrows"></a>CMFCMenuBar::GetForceDownArrows

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubargethelpcombobox"></a><a name="gethelpcombobox"></a>CMFCMenuBar::GetHelpCombobox

Vrátí ukazatel na pole se seznamem **Nápověda.**

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole se seznamem **Nápověda.** Null, pokud je pole se seznamem **nápovědy** skryté nebo není povoleno.

### <a name="remarks"></a>Poznámky

Pole se seznamem **Nápověda** se nachází na pravé straně panelu nabídek. Volání metody [CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox) povolte toto pole se seznamem.

## <a name="cmfcmenubargethmenu"></a><a name="gethmenu"></a>CMFCMenubar::GetHMenu

Načte popisovač do nabídky připojené k objektu [CMFCMenuBar.](../../mfc/reference/cmfcmenubar-class.md)

```
HMENU GetHMenu() const;
```

## <a name="cmfcmenubargetmenufont"></a><a name="getmenufont"></a>CMFCMenubar::GetMenuFont

Načte aktuální písmo nabídky.

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*bHorz*<br/>
[v] Logický parametr, který určuje, zda má být vráceno vodorovné nebo svislé písmo. TRUE označuje vodorovné písmo.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na parametr [CFont,](../../mfc/reference/cfont-class.md) který obsahuje aktuální písmo řádku nabídek.

### <a name="remarks"></a>Poznámky

Vrácené písmo je globální parametr pro aplikaci. Pro všechny `CMFCMenuBar` objekty jsou zachována dvě globální písma. Tato samostatná písma se používají pro vodorovné a svislé panely nabídek.

## <a name="cmfcmenubargetmenuitem"></a><a name="getmenuitem"></a>CMFCPanelmenu::GetMenuItem

Načte objekt [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) na řádku nabídek na základě indexu položky.

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>Parametry

*iPoložka*<br/>
[v] Index položky nabídky vrátit.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CMFCToolBarButton` objekt, který odpovídá indexu určenému *iItem*. Null, pokud je index neplatný.

## <a name="cmfcmenubargetrowheight"></a><a name="getrowheight"></a>CMFCMenubar::GetRowHeight

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubargetsystembutton"></a><a name="getsystembutton"></a>CMFCPanelmenu::GetSystemButton

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>Parametry

[v] *uiBtn*<br/>

[v] *bPříkaz b*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubargetsystembuttonscount"></a><a name="getsystembuttonscount"></a>CMFCPanel menu::GetSystemButtonsCount

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubargetsystemmenu"></a><a name="getsystemmenu"></a>CMFCPanel menu::GetSystemMenu

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarhighlightdisableditems"></a><a name="highlightdisableditems"></a>CMFCPanel menu::ZvýrazněníZakázané položky

Určuje, zda rozhraní zvýrazní zakázané položky nabídky.

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>Parametry

*bZvýraznění*<br/>
[v] Logický parametr, který označuje, zda rozhraní zvýrazní nedostupné položky nabídky.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení rozhraní framework nezvýrazní nedostupné položky nabídky, když na ně uživatel umístí ukazatel myši.

## <a name="cmfcmenubarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFCMenuBar::isbuttonextrasizek dispozici

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarishighlightdisableditems"></a><a name="ishighlightdisableditems"></a>CMFCMenuBar::IsHighlightDisabledItems

Označuje, zda rozhraní zvýrazní nedostupné položky nabídky.

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud jsou zvýrazněny nedostupné položky nabídky; jinak FALSE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení rozhraní framework nezvýrazní nedostupné položky nabídky, když na ně uživatel umístí ukazatel myši. Tuto funkci povolte pomocí metody [CMFCMenuBar::HighlightDisabledItems.](#highlightdisableditems)

## <a name="cmfcmenubarismenushadows"></a><a name="ismenushadows"></a>CMFCMenuBar::IsMenuShadows

Označuje, zda rozhraní kreslí stíny pro rozbalovací nabídky.

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud rozhraní kreslí stíny nabídky; jinak FALSE.

### <a name="remarks"></a>Poznámky

Pomocí metody [CMFCMenuBar::EnableMenuShadows](#enablemenushadows) tuto funkci povolte nebo zakažte.

## <a name="cmfcmenubarisrecentlyusedmenus"></a><a name="isrecentlyusedmenus"></a>CMFCMenuBar::Nabídky nabídek

Označuje, zda jsou na řádku nabídek zobrazeny naposledy použité příkazy nabídky.

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, `CMFCMenuBar` pokud objekt zobrazuje naposledy použité příkazy nabídky; jinak 0.

### <a name="remarks"></a>Poznámky

Pomocí funkce [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus) můžete určit, zda se na panelu nabídek zobrazí naposledy použité příkazy nabídky.

## <a name="cmfcmenubarisshowallcommands"></a><a name="isshowallcommands"></a>CMFCMenuBar::Příkazy IsShowAllCommands

Označuje, zda nabídky zobrazují všechny příkazy.

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, `CMFCMenuBar` pokud se zobrazí všechny příkazy; jinak 0.

### <a name="remarks"></a>Poznámky

Objekt `CMFCMenuBar` lze nakonfigurovat tak, aby zobrazoval všechny příkazy nebo pouze podmnožinu příkazů. Další informace o této funkci naleznete v [tématu CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md).

`IsShowAllCommands`vám řekne, jak je tato `CMFCMenuBar` funkce konfigurována pro objekt. Chcete-li určit, které příkazy nabídky jsou zobrazeny, použijte metody [CMFCMenuBar::SetShowAllCommands](#setshowallcommands) a [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus).

## <a name="cmfcmenubarisshowallcommandsdelay"></a><a name="isshowallcommandsdelay"></a>CMFCMenuBar::IsShowAllCommandsDelay

Označuje, zda objekt [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) zobrazí všechny příkazy po krátké prodlevě.

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud se na řádku nabídek po krátké prodlevě zobrazí úplné nabídky; jinak 0.

### <a name="remarks"></a>Poznámky

Když nakonfigurujete řádek nabídek tak, aby zobrazoval naposledy použité položky, zobrazí se na řádku nabídek úplná nabídka jedním ze dvou způsobů:

- Zobrazí úplnou nabídku po naprogramovaném zpoždění, kdy uživatel najeví kurzorem nad šipkou v dolní části nabídky.

- Zobrazí celou nabídku poté, co uživatel klikne na šipku v dolní části nabídky.

Ve výchozím `CMFCMenuBar` nastavení všechny objekty používají možnost k zobrazení celé nabídky po krátké prodlevě. Tuto možnost nelze ve `CMFCMenuBar` třídě programově změnit. Uživatel však může změnit chování během přizpůsobení panelu nástrojů pomocí dialogového okna **Přizpůsobit.**

## <a name="cmfcmenubarloadstate"></a><a name="loadstate"></a>CMFCPanel menu::LoadState

Načte stav řádku nabídek z registru systému Windows.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Řetězec, který obsahuje cestu klíče registru systému Windows.

*nIndex*<br/>
[v] ID ovládacího prvku pro řádek nabídek.

*uiID*<br/>
[v] Rezervovaná hodnota.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Pomocí metody [CMFCMenuBar::SaveState](#savestate) uložte stav řádku nabídek do registru. Uložené informace zahrnují položky nabídky, stav ukotvení a umístění panelu nabídek.

Ve většině případů aplikace `LoadState`nevolá . Rozhraní framework volá tuto metodu při inicializaci pracovního prostoru.

## <a name="cmfcmenubaronchangehot"></a><a name="onchangehot"></a>CMFCMenuBar::OnChangeHot

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>Parametry

[v] *iHot*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarondefaultmenuloaded"></a><a name="ondefaultmenuloaded"></a>CMFCMenuBar::OnDefaultMenuLoaded

Rozhraní Framework volá tuto metodu při načtení prostředku nabídky ze souboru prostředků.

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hNabídka*<br/>
[v] Úchyt pro nabídku `CMFCMenuBar` připojenou k objektu.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádné provádění. Přepsat tuto funkci spustit vlastní kód po rozhraní načte prostředek nabídky ze souboru prostředků.

## <a name="cmfcmenubaronsendcommand"></a><a name="onsendcommand"></a>CMFCPanel menu::Příkaz OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

[v] *pTlačítko*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubaronsetdefaultbuttontext"></a><a name="onsetdefaultbuttontext"></a>CMFCPanelmenu::OnSetDefaultButtonText

Framework volá tuto metodu, když uživatel změní text položky na řádku nabídek.

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

*pTlačítko*<br/>
[v] Ukazatel na objekt [CMFCToolBarButton,](../../mfc/reference/cmfctoolbarbutton-class.md) který chce uživatel přizpůsobit.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud rozhraní platí uživatel změní na řádku nabídek; jinak FALSE.

### <a name="remarks"></a>Poznámky

Výchozí implementace pro tuto metodu změní text tlačítka na text, který uživatel zadává.

## <a name="cmfcmenubarontoolhittest"></a><a name="ontoolhittest"></a>CMFCMenuBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parametry

[v] *bod*<br/>

[v] *pTI*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuBar::PreTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

[v] *pMsg*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarrestoreoriginalstate"></a><a name="restoreoriginalstate"></a>CMFCMenuBar::Obnovit původní stav

Volat rámci, když uživatel vybere **Obnovit** z dialogového okna **Přizpůsobit.**

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je metoda úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, když uživatel vybere **obnovit** z nabídky přizpůsobení. Tuto metodu můžete také ručně volat a programově obnovit stav panelu nabídek. Tato metoda načte původní stav ze souboru prostředků.

Přepsat tuto metodu, pokud chcete provést jakékoli zpracování, když uživatel vybere možnost **Obnovit.**

## <a name="cmfcmenubarsavestate"></a><a name="savestate"></a>CMFCMenubar::SaveState

Uloží stav objektu [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) do registru systému Windows.

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Řetězec, který obsahuje cestu klíče registru systému Windows.

*nIndex*<br/>
[v] ID ovládacího prvku pro řádek nabídek.

*uiID*<br/>
[v] Rezervovaná hodnota.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak NEPRAVDA;

### <a name="remarks"></a>Poznámky

Aplikace obvykle nevolá `SaveState`. Rozhraní Framework volá tuto metodu při serializace pracovního prostoru. Další informace naleznete v tématu [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).

Uložené informace zahrnují položky nabídky, stav ukotvení a umístění panelu nabídek.

## <a name="cmfcmenubarsetdefaultmenuresid"></a><a name="setdefaultmenuresid"></a>CMFCMenuBar::SetDefaultMenuResId

Nastaví výchozí nabídku objektu [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) na základě ID prostředku.

```
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>Parametry

*uiResId*<br/>
[v] ID prostředku pro novou výchozí nabídku.

### <a name="remarks"></a>Poznámky

Metoda [CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate) obnoví výchozí nabídku ze souboru prostředků.

Použijte metodu [CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid) k načtení výchozí nabídky bez obnovení.

## <a name="cmfcmenubarsetforcedownarrows"></a><a name="setforcedownarrows"></a>CMFCMenuBar::SetForceDownArrows

```
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>Parametry

[v] *bHodnota*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubarsetmaximizemode"></a><a name="setmaximizemode"></a>CMFCPanel menu::SetMaximizeMode

Rozhraní Framework volá tuto metodu, když Rozhraní MDI změní režim zobrazení a řádek nabídek musí být aktualizován.

```
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>Parametry

*bMax*<br/>
[v] Logická hodnota, která určuje režim. Další informace naleznete v části Poznámky.

*pWnd*<br/>
[v] Ukazatel na podřízené okno MDI, které se mění.

*bRozložení a rozložení*<br/>
[v] Logická hodnota, která určuje, zda má být rozložení panelu nabídek okamžitě přepočítáno.

### <a name="remarks"></a>Poznámky

Když je podřízené okno MDI maximalizováno, panel nabídek připojený k hlavnímu oknu mdi zobrazí systémové menu a tlačítka **Minimalizovat**, **Maximalizovat** a **Zavřít.** Pokud *bMax* je TRUE a *pWnd* není NULL, podřízené okno MDI je maximalizována a řádek nabídek musí obsahovat další ovládací prvky. V opačném případě se řádek nabídek vrátí do normálního stavu.

## <a name="cmfcmenubarsetmenubuttonrtc"></a><a name="setmenubuttonrtc"></a>CMFCPanel menu::SetMenuButtonRTC

Nastaví informace o třídě runtime, které rozhraní používá, když uživatel vytvoří tlačítka nabídky.

```
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>Parametry

*pMenuButtonRTC*<br/>
[v] Informace [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pro třídu odvozenou z [třídy CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md).

### <a name="remarks"></a>Poznámky

Když uživatel přidá nová tlačítka do řádku nabídek, rozhraní vytvoří tlačítka dynamicky. Ve výchozím nastavení `CMFCMenuButton` vytváří objekty. Přepsat tuto metodu změnit typ button objekty, které vytvoří rámci.

## <a name="cmfcmenubarsetmenufont"></a><a name="setmenufont"></a>CMFCPanel menu::SetMenuFont

Nastaví písmo pro všechny panely nabídek v aplikaci.

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
[v] Ukazatel na strukturu [LOGFONT,](/windows/win32/api/dimm/ns-dimm-logfonta) která definuje písmo, které má být nastaveno.

*bHorz*<br/>
[v] TRUE, pokud *chcete, aby lpLogFont* parametr, který má být použit pro svislé písmo, FALSE, pokud chcete, aby byl použit pro vodorovné písmo.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Pro všechny `CMFCMenuBar` objekty se používají dvě písma. Tato samostatná písma se používají pro vodorovné a svislé panely nabídek.

Nastavení písma jsou globální proměnné `CMFCMenuBar` a ovlivňují všechny objekty.

## <a name="cmfcmenubarsetrecentlyusedmenus"></a><a name="setrecentlyusedmenus"></a>CMFCMenuBar::Nastavitnabídky naposledy použitých

Určuje, zda se na panelu nabídek zobrazí naposledy použité příkazy nabídek.

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*Bon*<br/>
[v] Logická hodnota, která určuje, zda jsou zobrazeny naposledy použité příkazy nabídky.

## <a name="cmfcmenubarsetshowallcommands"></a><a name="setshowallcommands"></a>CMFCMenuBar::SetShowAllCommands

Určuje, zda nabídka zobrazuje všechny dostupné příkazy.

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>Parametry

*bZobrazitAllPříkazy*<br/>
[v] Logický parametr, který určuje, zda rozbalovací nabídka zobrazuje všechny příkazy nabídky.

### <a name="remarks"></a>Poznámky

Pokud nabídka nezobrazuje všechny příkazy nabídky, skryje příkazy, které se používají jen zřídka. Další informace o zobrazení příkazů nabídky naleznete v [tématu CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)
