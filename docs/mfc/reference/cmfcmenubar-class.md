---
title: Třída CMFCMenuBar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02637017ccd589e093caf29cbfe0c345dfa80316
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar – třída
Panel nabídek, který implementuje ukotvení.  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCMenuBar : public CMFCToolbar  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(Přepisuje `CMFCToolBar::AdjustLocations`.)|  
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|Určuje, zda text popisků lze zobrazit v části Image na tlačítka panelu nástrojů. (Přepisuje [CMFCToolBar::AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).)|  
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Přepisuje `CPane::AllowShowOnPaneMenu`.)|  
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|Vypočítá vodorovné velikost panelu nástrojů. (Přepisuje [CMFCToolBar::CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).)|  
|[CMFCMenuBar::CalcLayout](#calclayout)|(Přepisuje `CMFCToolBar::CalcLayout`.)|  
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Vypočítá maximální výšku tlačítek na panelu nástrojů. (Přepisuje [CMFCToolBar::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).)|  
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|Určuje, zda uživatel můžete zavřít panelu nástrojů. (Přepisuje [CMFCToolBar::CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).)|  
|[CMFCMenuBar::CanBeRestored](#canberestored)|Určuje, zda systém obnovit panelu nástrojů do původního stavu po přizpůsobení. (Přepisuje [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|  
|[CMFCMenuBar::Create](#create)|Vytvoří ovládacího prvku nabídka a připojí jej k `CMFCMenuBar` objektu.|  
|[CMFCMenuBar::CreateEx](#createex)|Vytvoří `CMFCMenuBar` objekt s možností další šablony.|  
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|Inicializuje `CMFCMenuBar` objektu. Přijímá `HMENU` parametr, který funguje jako šablonu pro vyplněná `CMFCMenuBar`.|  
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|Umožňuje **pomoci** pole se seznamem, který se nachází na pravé straně řádku nabídek.|  
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|Určuje, jestli se má zobrazit stínů pro místní nabídky.|  
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(Přepisuje [CPane::GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize).)|  
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|Vrátí šířku tlačítka panelu nástrojů. (Přepisuje [CMFCToolBar::GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).)|  
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|Vrátí popisovač původní nabídky v souboru prostředků.|  
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|Vrátí identifikátor prostředku pro původní nabídky v souboru prostředků.|  
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||  
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||  
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|Vrátí ukazatel **pomoci** – pole se seznamem.|  
|[CMFCMenuBar::GetHMenu](#gethmenu)|Vrátí popisovač do nabídky, který je připojen k `CMFCMenuBar` objektu.|  
|[CMFCMenuBar::GetMenuFont](#getmenufont)|Vrátí aktuální globální písma pro objekty nabídky.|  
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|Vrátí tlačítka panelu nástrojů přidružený index zadané položky.|  
|[CMFCMenuBar::GetRowHeight](#getrowheight)|Vrátí výšku tlačítka panelu nástrojů. (Přepisuje [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|  
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||  
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||  
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||  
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|Určuje, zda jsou vyznačené položky nabídky zakázané.|  
|[CMFCMenuBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Určuje, zda lze panelu nástrojů zobrazovat tlačítka, která rozšířili ohraničení. (Přepisuje [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|  
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|Určuje, zda jsou vyznačené zakázané položky.|  
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|Označuje, zda jsou pro místní nabídky vykreslován stínů.|  
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|Určuje, zda se zobrazí nedávno použité příkazy v řádku nabídek.|  
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|Udává, zda místní nabídky Zobrazit všechny příkazy.|  
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|Udává, zda nabídky Zobrazit všechny příkazy po chvíli trvat.|  
|[CMFCMenuBar::LoadState](#loadstate)|Načte stav `CMFCMenuBar` objekt z registru.|  
|[CMFCMenuBar::OnChangeHot](#onchangehot)|Voláno rámcem, když uživatel vybere tlačítka na panelu nástrojů. (Přepisuje [CMFCToolBar::OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot).)|  
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|Voláno rámcem až okně s rámečkem načte výchozí nabídka ze zdrojového souboru.|  
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(Přepisuje `CMFCToolBar::OnSendCommand`.)|  
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Voláno rámcem při nabídky je v režimu přizpůsobení a uživatel změní text položky nabídky.|  
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(Přepisuje `CMFCToolBar::OnToolHitTest`.)|  
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|(Přepisuje `CMFCToolBar::PreTranslateMessage`.)|  
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|Voláno rámcem při nabídky je v režimu přizpůsobení a uživatel vybere **resetovat** pro řádku nabídek.|  
|[CMFCMenuBar::SaveState](#savestate)|Uloží stav `CMFCMenuBar` objektu do registru.|  
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|Nastaví původní nabídky v souboru prostředků.|  
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||  
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|Voláno rámcem, kdy podřízená okna MDI změní režim zobrazení. Pokud podřízeného okna MDI je nově maximalizované nebo je již Maximalizovaný, tato metoda aktualizace panelu nabídek.|  
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|Nastaví informace o třídě runtime, který se vygeneruje, když uživatel vytvoří dynamicky tlačítka nabídky.|  
|[CMFCMenuBar::SetMenuFont](#setmenufont)|Nastaví písmo pro všechny nabídky v aplikaci.|  
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|Určuje, zda řádku nabídek zobrazí příkazy naposledy použité nabídky.|  
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|Určuje, zda panelu nabídek zobrazuje všechny příkazy.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCMenuBar` Třída je řádku nabídek, která implementuje funkce ukotvení. Je podobná panelu nástrojů, i když jej nelze ukončit – vždy se zobrazí.  
  
 `CMFCMenuBar` podporuje možnost zobrazení objektů položka naposledy použité nabídky. Pokud je tato možnost povolena, `CMFCMenuBar` zobrazí pouze podmnožinu dostupné příkazy v první zobrazení. Následně se zobrazí nedávno použité příkazy spolu s původní podmnožinu příkazy. Kromě toho uživatel může vždy rozbalte nabídku Chcete-li zobrazit všechny dostupné příkazy. Každý příkaz k dispozici je proto nakonfigurován neustále zobrazit, nebo chcete-li zobrazit pouze v případě, že byl nedávno vybrán.  
  
 Použít `CMFCMenuBar` objektu, Vložit v hlavním okně rámce objektu. Při zpracování `WM_CREATE` zprávy, volejte `CMFCMenuBar::Create` nebo `CMFCMenuBar::CreateEx`. Bez ohledu na to, které vytvoří funkci použít, ukazatel předat do hlavního rámce okna. Potom povolte ukotvení voláním [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Ukotvení – v této nabídce voláním [CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCMenuBar` třídy. Příklad ukazuje, jak nastavit styl podokně, povolte na tlačítko přizpůsobit, povolit okno s nápovědou, povolit stínů pro místní nabídky a aktualizovat řádku nabídek. Tento fragment kódu je součástí [IE Demo-ukázka](../../visual-cpp-samples.md).  
  
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
 **Záhlaví:** afxmenubar.h  
  
##  <a name="adjustlocations"></a>  CMFCMenuBar::AdjustLocations  
 Upraví pozic položek nabídek v řádku nabídek.  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="allowchangetextlabels"></a>  CMFCMenuBar::AllowChangeTextLabels  
 Určuje, zda text popisky jsou povoleny v rámci bitové kopie v panelu nabídek.  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud uživatel zobrazit popisky text v rámci bitové kopie.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="allowshowonpanemenu"></a>  CMFCMenuBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="calcfixedlayout"></a>  CMFCMenuBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bStretch`  
 [v] `bHorz`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="calclayout"></a>  CMFCMenuBar::CalcLayout  

  
```  
virtual CSize CalcLayout(
    DWORD dwMode,  
    int nLength = -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwMode`  
 [v] `nLength`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="calcmaxbuttonheight"></a>  CMFCMenuBar::CalcMaxButtonHeight  

  
```  
virtual int CalcMaxButtonHeight();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="canbeclosed"></a>  CMFCMenuBar::CanBeClosed  

  
```  
virtual BOOL CanBeClosed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="canberestored"></a>  CMFCMenuBar::CanBeRestored  

  
```  
virtual BOOL CanBeRestored() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="create"></a>  CMFCMenuBar::Create  
 Vytvoří ovládacího prvku nabídka a připojí jej k [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objektu.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT nID = AFX_IDW_MENUBAR);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pParentWnd`  
 Ukazatel do nadřazeného okna pro novou `CMFCMenuBar` objektu.  
  
 [v] `dwStyle`  
 Styl nového řádku nabídek.  
  
 [v] `nID`  
 ID pro podřízeného okna řádku nabídek.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` v případě úspěšného; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Po sestavení `CMFCMenuBar` objektu, musí volat `Create`. Tato metoda vytvoří `CMFCMenuBar` řízení a připojí jej k `CMFCMenuBar` objektu.  
  
 Další informace o styly nástrojů najdete v tématu [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).  
  
##  <a name="createex"></a>  CMFCMenuBar::CreateEx  
 Vytvoří [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objekt se zadanou rozšířené styly.  
  
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
 [v] `pParentWnd`  
 Ukazatel do nadřazeného okna Nový `CMFCMenuBar` objektu.  
  
 [v] `dwCtrlStyle`  
 Další styly pro nový panel nabídek.  
  
 [v] `dwStyle`  
 Hlavní styl nového řádku nabídek.  
  
 [v] `rcBorders`  
 A `CRect` parametr, který určuje velikostí pro ohraničení `CMFCMenuBar` objektu.  
  
 [v] `nID`  
 ID pro podřízeného okna řádku nabídek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je metoda úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Měli byste použít tuto funkci místo [CMFCMenuBar::Create](#create) Pokud chcete zadat styly kromě styl panelu nástrojů. Jsou některé často používané další styly `TBSTYLE_TRANSPARENT` a `CBRS_TOP`.  
  
 Seznam dalších styly, najdete v části [Toolbar – ovládací prvek a styly tlačítek](http://msdn.microsoft.com/library/windows/desktop/bb760439), [běžné styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775498), a [běžné styly oken](http://msdn.microsoft.com/library/windows/desktop/ms632600).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `CreateEx` metodu `CMFCMenuBar` třídy. Tento fragment kódu je součástí [IE Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]  
  
##  <a name="createfrommenu"></a>  CMFCMenuBar::CreateFromMenu  
 Inicializuje [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objektu. Tato metoda modely `CMFCMenuBar` objektu po `HMENU` parametr.  
  
```  
virtual void CreateFromMenu(
    HMENU hMenu,  
    BOOL bDefaultMenu = FALSE,  
    BOOL bForceUpdate = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `hMenu`  
 Popisovač pro prostředek nabídky. `CreateFromMenu` používá jako šablonu pro tento prostředek `CMFCMenuBar`.  
  
 [v] `bDefaultMenu`  
 Logická hodnota, která určuje, zda je nové nabídky v nabídce výchozí.  
  
 [v] `bForceUpdate`  
 Logická hodnota, která určuje, zda tato metoda vynutí nabídky aktualizace.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, pokud chcete, aby ovládacího prvku nabídka tak, aby měl stejné položky nabídky jako prostředek nabídky. Tuto metodu lze volat po zavolání metody buď [CMFCMenuBar::Create](#create) nebo [CMFCMenuBar::CreateEx](#createex).  
  
##  <a name="enablehelpcombobox"></a>  CMFCMenuBar::EnableHelpCombobox  
 Umožňuje **pomoci** pole se seznamem, který se nachází na pravé straně řádku nabídek.  
  
```  
void EnableHelpCombobox(
    UINT uiID,  
    LPCTSTR lpszPrompt = NULL,  
    int nComboBoxWidth = 150);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiID`  
 ID příkazu pro tlačítko o **pomoci** – pole se seznamem.  
  
 [v] `lpszPrompt`  
 Řetězec, který obsahuje text, který rozhraní zobrazí v seznamu, pokud je prázdný a není aktivní. Například "zadejte text sem".  
  
 [v] `nComboBoxWidth`  
 Šířka tlačítko pro pole se seznamem v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 **Pomoci** vypadá takto: pole se seznamem **pomoci** – pole se seznamem v panelu nabídek z [!INCLUDE[ofprword](../../mfc/reference/includes/ofprword_md.md)].  
  
 Při volání této metody se `uiID` nastaven na hodnotu 0, tato metoda skryje pole se seznamem. Jinak tato metoda zobrazí pole se seznamem automaticky na pravé straně panelu nabídek. Po volání této metody volejte [CMFCMenuBar::GetHelpCombobox](#gethelpcombobox) k získání ukazatele na vloženého [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objektu.  
  
##  <a name="enablemenushadows"></a>  CMFCMenuBar::EnableMenuShadows  
 Umožňuje stínů pro místní nabídky.  
  
```  
static void EnableMenuShadows(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bEnable`  
 Parametr typu Boolean, která určuje, zda se má povolit stínů pro místní nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Algoritmus, který používá tato metoda je složitý a může snížit výkon vaší aplikace v systémech pomalejší.  
  
##  <a name="getavailableexpandsize"></a>  CMFCMenuBar::GetAvailableExpandSize  

  
```  
virtual int GetAvailableExpandSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcolumnwidth"></a>  CMFCMenuBar::GetColumnWidth  

  
```  
virtual int GetColumnWidth() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getdefaultmenu"></a>  CMFCMenuBar::GetDefaultMenu  
 Načte popisovač pro původní nabídky. Rozhraní framework načte původní nabídky ze zdrojového souboru.  
  
```  
HMENU GetDefaultMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro prostředek nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše aplikace přizpůsobí nabídky, můžete použít tuto metodu pro načtení popisovače do původní nabídky.  
  
##  <a name="getdefaultmenuresid"></a>  CMFCMenuBar::GetDefaultMenuResId  
 Načte identifikátor prostředků pro výchozí nabídky.  
  
```  
UINT GetDefaultMenuResId() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor prostředku nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Načte výchozí nabídky pro rozhraní `CMFCMenuBar` objekt ze zdrojového souboru.  
  
##  <a name="getfloatpopupdirection"></a>  CMFCMenuBar::GetFloatPopupDirection  

  
```  
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pButton`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getforcedownarrows"></a>  CMFCMenuBar::GetForceDownArrows  

  
```  
BOOL GetForceDownArrows();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gethelpcombobox"></a>  CMFCMenuBar::GetHelpCombobox  
 Vrátí ukazatel **pomoci** – pole se seznamem.  
  
```  
CMFCToolBarComboBoxButton* GetHelpCombobox();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel **pomoci** – pole se seznamem. `NULL` Pokud **pomoci** – pole se seznamem je skrytý nebo není povolen.  
  
### <a name="remarks"></a>Poznámky  
 **Pomoci** – pole se seznamem se nachází na pravé straně řádku nabídek. Volejte metodu [CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox) povolit toto pole se seznamem.  
  
##  <a name="gethmenu"></a>  CMFCMenuBar::GetHMenu  
 Načte popisovač nabídky připojené k [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objektu.  
  
```  
HMENU GetHMenu() const;  
```  
  
##  <a name="getmenufont"></a>  CMFCMenuBar::GetMenuFont  
 Načte aktuální písmo nabídek.  
  
```  
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bHorz`  
 Logický parametr, který určuje, jestli se mají vracet písmo vodorovně nebo svisle. `TRUE` Určuje vodorovné písmo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CFont](../../mfc/reference/cfont-class.md) parametr, který obsahuje aktuální písmo panelu nabídek.  
  
### <a name="remarks"></a>Poznámky  
 Vrácený písmo je parametr globální pro aplikaci. Dvě globální písma jsou uchovávány všechny `CMFCMenuBar` objekty. Tyto samostatné písma slouží pro vodorovného a svislého nabídek.  
  
##  <a name="getmenuitem"></a>  CMFCMenuBar::GetMenuItem  
 Načte [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) objektu v řádku nabídek podle index položky.  
  
```  
CMFCToolBarButton* GetMenuItem(int iItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iItem`  
 Index položky nabídky vrátit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CMFCToolBarButton` objekt, který odpovídá index zadaný `iItem`. `NULL` Pokud index není platný.  
  
##  <a name="getrowheight"></a>  CMFCMenuBar::GetRowHeight  

  
```  
virtual int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getsystembutton"></a>  CMFCMenuBar::GetSystemButton  

  
```  
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,  
    BOOL bByCommand = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiBtn`  
 [v] `bByCommand`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getsystembuttonscount"></a>  CMFCMenuBar::GetSystemButtonsCount  

  
```  
int GetSystemButtonsCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getsystemmenu"></a>  CMFCMenuBar::GetSystemMenu  

  
```  
CMFCToolBarSystemMenuButton* GetSystemMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="highlightdisableditems"></a>  CMFCMenuBar::HighlightDisabledItems  
 Určuje, zda rozhraní označuje položky nabídky zakázané.  
  
```  
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bHighlight`  
 Parametr typu Boolean, která určuje, zda rozhraní označuje položky nabídky není k dispozici.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení rozhraní není zvýrazněte položky nabídky není k dispozici, když uživatel umístí ukazatel myši nad nimi.  
  
##  <a name="isbuttonextrasizeavailable"></a>  CMFCMenuBar::IsButtonExtraSizeAvailable  

  
```  
virtual BOOL IsButtonExtraSizeAvailable() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ishighlightdisableditems"></a>  CMFCMenuBar::IsHighlightDisabledItems  
 Určuje, zda rozhraní označuje položky nabídky není k dispozici.  
  
```  
static BOOL IsHighlightDisabledItems();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud jsou vyznačené položky k dispozici nabídky; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení rozhraní není zvýrazněte položky nabídky není k dispozici, když uživatel umístí ukazatel myši nad nimi. Použití [CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems) metoda tuto funkci povolíte.  
  
##  <a name="ismenushadows"></a>  CMFCMenuBar::IsMenuShadows  
 Určuje, zda rozhraní nevykresluje stínů pro místní nabídky.  
  
```  
static BOOL IsMenuShadows();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud rozhraní nevykresluje nabídky stínů; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCMenuBar::EnableMenuShadows](#enablemenushadows) metoda k povolení nebo zakázání této funkce.  
  
##  <a name="isrecentlyusedmenus"></a>  CMFCMenuBar::IsRecentlyUsedMenus  
 Určuje, zda se zobrazí nedávno použité příkazy v řádku nabídek.  
  
```  
static BOOL IsRecentlyUsedMenus();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `CMFCMenuBar` objekt zobrazí nedávno použité příkazy nabídky; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí funkce [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus) řídit, jestli panelu nabídek ukazuje nedávno používat příkazy nabídky.  
  
##  <a name="isshowallcommands"></a>  CMFCMenuBar::IsShowAllCommands  
 Udává, zda nabídky Zobrazit všechny příkazy.  
  
```  
static BOOL IsShowAllCommands();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `CMFCMenuBar` zobrazí všechny příkazy; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 A `CMFCMenuBar` objekt lze nakonfigurovat, aby buď zobrazit všechny příkazy nebo zobrazit pouze podmnožinu příkazy. Další informace o této funkci najdete v tématu [CMFCMenuBar třída](../../mfc/reference/cmfcmenubar-class.md).  
  
 `IsShowAllCommands` zjistíte, jak tato funkce je nakonfigurována pro `CMFCMenuBar` objektu. Chcete-li řídit, které příkazy nabídky jsou uvedeny, použijte metody [CMFCMenuBar::SetShowAllCommands](#setshowallcommands) a [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus).  
  
##  <a name="isshowallcommandsdelay"></a>  CMFCMenuBar::IsShowAllCommandsDelay  
 Určuje, zda [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objekt zobrazuje všechny příkazy po chvíli trvat.  
  
```  
static BOOL IsShowAllCommandsDelay();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se v panelu nabídek zobrazí úplné nabídky po krátké prodlevě; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Při konfiguraci řádku nabídek pro zobrazení nedávno použité položky panelu nabídek zobrazí úplnou nabídku v jednom ze dvou způsobů:  
  
-   Zobrazte úplnou nabídku po naprogramovaných zpoždění z když uživatel bude umístěn kurzor nad na šipku v dolní části nabídky.  
  
-   Po kliknutí na šipku v dolní části nabídky, zobrazte úplnou nabídku.  
  
 Ve výchozím nastavení všechny `CMFCMenuBar` objekty pomocí možnosti zobrazit úplnou nabídku po chvíli trvat. Tuto možnost nelze změnit prostřednictvím kódu programu v `CMFCMenuBar` třídy. Nicméně, uživatel může změnit chování při přizpůsobení panelu nástrojů pomocí **přizpůsobit** dialogové okno...  
  
##  <a name="loadstate"></a>  CMFCMenuBar::LoadState  
 Načte stav panelu nabídek z registru systému Windows.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT)-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszProfileName`  
 Řetězec, který obsahuje cestu klíče registru Windows.  
  
 [v] `nIndex`  
 ID ovládacího prvku pro řádku nabídek.  
  
 [v] `uiID`  
 Rezervovaná hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud metoda byla úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCMenuBar::SaveState](#savestate) metody uložte stav panelu nabídek do registru. Uložené informace zahrnují položky nabídky, stav ukotvení a pozice řádku nabídek.  
  
 Ve většině případů se vaše aplikace nevyvolá `LoadState`. Tato metoda volá framework při inicializaci pracovním prostoru.  
  
##  <a name="onchangehot"></a>  CMFCMenuBar::OnChangeHot  

  
```  
virtual void OnChangeHot(int iHot);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iHot`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondefaultmenuloaded"></a>  CMFCMenuBar::OnDefaultMenuLoaded  
 Tato metoda volá framework při načítání prostředků nabídky ze zdrojového souboru.  
  
```  
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `hMenu`  
 Popisovač pro nabídce připojené k `CMFCMenuBar` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce neprovede žádnou akci. Potlačí tuto funkci k provedení vlastní kód po rozhraní načte nabídky prostředků ze zdrojového souboru.  
  
##  <a name="onsendcommand"></a>  CMFCMenuBar::OnSendCommand  

  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pButton`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onsetdefaultbuttontext"></a>  CMFCMenuBar::OnSetDefaultButtonText  
 Rozhraní framework volá tuto metodu, když uživatel změní text položky v řádku nabídek.  
  
```  
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pButton`  
 Ukazatel [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) objekt, který chce uživatel upravit.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se vztahuje rozhraní uživatel změní na panelu nabídek; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této metody se změní text tlačítka na text, který poskytuje uživatele.  
  
##  <a name="ontoolhittest"></a>  CMFCMenuBar::OnToolHitTest  

  
```  
virtual INT_PTR OnToolHitTest(
    CPoint point,  
    TOOLINFO* pTI) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 [v] `pTI`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="pretranslatemessage"></a>  CMFCMenuBar::PreTranslateMessage  

  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pMsg`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="restoreoriginalstate"></a>  CMFCMenuBar::RestoreOriginalstate  
 Voláno rámcem, když uživatel vybere **resetovat** z **přizpůsobit** dialogové okno.  
  
```  
virtual BOOL RestoreOriginalstate();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je metoda úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, když uživatel vybere **resetovat** z nabídky přizpůsobení. Můžete také ručně volat tuto metodu za účelem prostřednictvím kódu programu resetovat stav řádku nabídek. Tato metoda načte původního stavu ze zdrojového souboru.  
  
 Potlačí tuto metodu, pokud chcete provádět žádné zpracovávání, když uživatel vybere **resetovat** možnost.  
  
##  <a name="savestate"></a>  CMFCMenuBar::SaveState  
 Uloží stav [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objektu do registru systému Windows.  
  
```  
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT)-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszProfileName`  
 Řetězec, který obsahuje cestu klíče registru Windows.  
  
 [v] `nIndex`  
 ID ovládacího prvku pro řádku nabídek.  
  
 [v] `uiID`  
 Rezervovaná hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` v případě úspěšného; v opačném případě `FALSE`;  
  
### <a name="remarks"></a>Poznámky  
 Obvykle aplikace nevyvolá `SaveState`. Rozhraní framework volá tuto metodu, když je serializováno pracovním prostoru. Další informace najdete v tématu [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).  
  
 Uložené informace zahrnují položky nabídky, stav ukotvení a pozice řádku nabídek.  
  
##  <a name="setdefaultmenuresid"></a>  CMFCMenuBar::SetDefaultMenuResId  
 Nastaví na výchozí nabídku pro [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objektu podle ID prostředku.  
  
```  
void SetDefaultMenuResId(UINT uiResId);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiResId`  
 ID prostředku pro nové nabídky výchozí.  
  
### <a name="remarks"></a>Poznámky  
 [CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate) metoda obnoví výchozí nabídka ze zdrojového souboru.  
  
 Použití [CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid) metoda pro načtení nabídky výchozí bez jeho obnovení.  
  
##  <a name="setforcedownarrows"></a>  CMFCMenuBar::SetForceDownArrows  

  
```  
void SetForceDownArrows(BOOL bValue);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bValue`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setmaximizemode"></a>  CMFCMenuBar::SetMaximizeMode  
 Tato metoda volá rámec při MDI změní režim zobrazení a řádku nabídek musí být aktualizovány.  
  
```  
void SetMaximizeMode(
    BOOL bMax,  
    CWnd* pWnd = NULL,  
    BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bMax`  
 Logická hodnota, která určuje režim. Další informace naleznete v části Poznámky.  
  
 [v] `pWnd`  
 Ukazatel na podřízeného okna MDI, který mění.  
  
 [v] `bRecalcLayout`  
 Logická hodnota, která určuje, zda rozložení panelu nabídek by měla být přepočítána okamžitě.  
  
### <a name="remarks"></a>Poznámky  
 Při maximalizaci podřízeného okna MDI zobrazíte panel nabídek připojený k hlavního rámce okna MDI nabídku a **minimalizaci**, **Maximalizovat** a **Zavřít** tlačítka. Pokud `bMax` je `TRUE` a `pWnd` není `NULL`, maximalizaci podřízeného okna MDI a řádku nabídek musí obsahovat další ovládací prvky. Řádek nabídek, jinak vrátí do stavu regulární.  
  
##  <a name="setmenubuttonrtc"></a>  CMFCMenuBar::SetMenuButtonRTC  
 Nastaví informace o třídě modul runtime rozhraní používá, když uživatel vytvoří tlačítka nabídky.  
  
```  
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pMenuButtonRTC`  
 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) informace pro třídu odvozenou z [CMFCMenuButton třída](../../mfc/reference/cmfcmenubutton-class.md).  
  
### <a name="remarks"></a>Poznámky  
 Pokud uživatel přidá nová tlačítka na panelu nabídek, vytvoří rozhraní tlačítka dynamicky. Ve výchozím nastavení, vytvoří `CMFCMenuButton` objekty. Potlačí tuto metodu, chcete-li změnit typ tlačítko objekty, které vytvoří rozhraní.  
  
##  <a name="setmenufont"></a>  CMFCMenuBar::SetMenuFont  
 Nastaví písmo pro všechny řádky nabídek v aplikaci.  
  
```  
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpLogFont`  
 Ukazatel [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/bb773327) struktura, která definuje písmo nastavit.  
  
 [v] `bHorz`  
 Hodnota TRUE, pokud chcete, aby `lpLogFont` parametr má být použit pro svislé písmo, FALSE, pokud chcete, který se má použít pro vodorovné písma.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud metoda byla úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Dvě písma se používají pro všechny `CMFCMenuBar` objekty. Tyto samostatné písma slouží pro vodorovného a svislého nabídek.  
  
 Nastavení písma jsou globální proměnné a mít vliv na všechny `CMFCMenuBar` objekty.  
  
##  <a name="setrecentlyusedmenus"></a>  CMFCMenuBar::SetRecentlyUsedMenus  
 Ovládací prvky jestli řádku nabídek zobrazí nedávno použité příkazy nabídky.  
  
```  
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bOn`  
 Logická hodnota, která určuje, zda se zobrazí nedávno použité příkazy.  
  
##  <a name="setshowallcommands"></a>  CMFCMenuBar::SetShowAllCommands  
 Určuje, zda v zobrazí všechny dostupné příkazy.  
  
```  
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bShowAllCommands`  
 Logický parametr, který určuje, zda v rozbalovací nabídce zobrazuje všechny příkazy nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Pokud nabídky nezobrazí všechny příkazy nabídky, skryje příkazy, které jsou používána zřídka. Další informace o zobrazení příkazů nabídky najdete v tématu [CMFCMenuBar třída](../../mfc/reference/cmfcmenubar-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)
