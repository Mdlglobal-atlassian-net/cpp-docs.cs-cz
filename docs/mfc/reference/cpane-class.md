---
title: Třída CPane | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPane
- AFXPANE/CPane
- AFXPANE/CPane::AdjustSizeImmediate
- AFXPANE/CPane::AllocElements
- AFXPANE/CPane::AllowShowOnPaneMenu
- AFXPANE/CPane::CalcAvailableSize
- AFXPANE/CPane::CalcInsideRect
- AFXPANE/CPane::CalcRecentDockedRect
- AFXPANE/CPane::CalcSize
- AFXPANE/CPane::CanBeDocked
- AFXPANE/CPane::CanBeTabbedDocument
- AFXPANE/CPane::ConvertToTabbedDocument
- AFXPANE/CPane::CopyState
- AFXPANE/CPane::Create
- AFXPANE/CPane::CreateDefaultMiniframe
- AFXPANE/CPane::CreateEx
- AFXPANE/CPane::DockByMouse
- AFXPANE/CPane::DockPane
- AFXPANE/CPane::DockPaneStandard
- AFXPANE/CPane::DockToFrameWindow
- AFXPANE/CPane::DoesAllowSiblingBars
- AFXPANE/CPane::FloatPane
- AFXPANE/CPane::GetAvailableExpandSize
- AFXPANE/CPane::GetAvailableStretchSize
- AFXPANE/CPane::GetBorders
- AFXPANE/CPane::GetClientHotSpot
- AFXPANE/CPane::GetDockSiteRow
- AFXPANE/CPane::GetExclusiveRowMode
- AFXPANE/CPane::GetHotSpot
- AFXPANE/CPane::GetMinSize
- AFXPANE/CPane::GetPaneName
- AFXPANE/CPane::GetVirtualRect
- AFXPANE/CPane::IsChangeState
- AFXPANE/CPane::IsDragMode
- AFXPANE/CPane::IsInFloatingMultiPaneFrameWnd
- AFXPANE/CPane::IsLeftOf
- AFXPANE/CPane::IsResizable
- AFXPANE/CPane::IsTabbed
- AFXPANE/CPane::LoadState
- AFXPANE/CPane::MoveByAlignment
- AFXPANE/CPane::MovePane
- AFXPANE/CPane::OnAfterChangeParent
- AFXPANE/CPane::OnBeforeChangeParent
- AFXPANE/CPane::OnPressCloseButton
- AFXPANE/CPane::OnShowControlBarMenu
- AFXPANE/CPane::RecalcLayout
- AFXPANE/CPane::SaveState
- AFXPANE/CPane::SetActiveInGroup
- AFXPANE/CPane::SetBorders
- AFXPANE/CPane::SetClientHotSpot
- AFXPANE/CPane::SetDockState
- AFXPANE/CPane::SetExclusiveRowMode
- AFXPANE/CPane::SetMiniFrameRTC
- AFXPANE/CPane::SetMinSize
- AFXPANE/CPane::SetVirtualRect
- AFXPANE/CPane::StretchPaneDeferWndPos
- AFXPANE/CPane::ToggleAutoHide
- AFXPANE/CPane::UndockPane
- AFXPANE/CPane::UpdateVirtualRect
- AFXPANE/CPane::OnAfterDock
- AFXPANE/CPane::OnAfterFloat
- AFXPANE/CPane::OnBeforeDock
- AFXPANE/CPane::OnBeforeFloat
- AFXPANE/CPane::m_bHandleMinSize
- AFXPANE/CPane::m_recentDockInfo
dev_langs:
- C++
helpviewer_keywords:
- CPane [MFC], AdjustSizeImmediate
- CPane [MFC], AllocElements
- CPane [MFC], AllowShowOnPaneMenu
- CPane [MFC], CalcAvailableSize
- CPane [MFC], CalcInsideRect
- CPane [MFC], CalcRecentDockedRect
- CPane [MFC], CalcSize
- CPane [MFC], CanBeDocked
- CPane [MFC], CanBeTabbedDocument
- CPane [MFC], ConvertToTabbedDocument
- CPane [MFC], CopyState
- CPane [MFC], Create
- CPane [MFC], CreateDefaultMiniframe
- CPane [MFC], CreateEx
- CPane [MFC], DockByMouse
- CPane [MFC], DockPane
- CPane [MFC], DockPaneStandard
- CPane [MFC], DockToFrameWindow
- CPane [MFC], DoesAllowSiblingBars
- CPane [MFC], FloatPane
- CPane [MFC], GetAvailableExpandSize
- CPane [MFC], GetAvailableStretchSize
- CPane [MFC], GetBorders
- CPane [MFC], GetClientHotSpot
- CPane [MFC], GetDockSiteRow
- CPane [MFC], GetExclusiveRowMode
- CPane [MFC], GetHotSpot
- CPane [MFC], GetMinSize
- CPane [MFC], GetPaneName
- CPane [MFC], GetVirtualRect
- CPane [MFC], IsChangeState
- CPane [MFC], IsDragMode
- CPane [MFC], IsInFloatingMultiPaneFrameWnd
- CPane [MFC], IsLeftOf
- CPane [MFC], IsResizable
- CPane [MFC], IsTabbed
- CPane [MFC], LoadState
- CPane [MFC], MoveByAlignment
- CPane [MFC], MovePane
- CPane [MFC], OnAfterChangeParent
- CPane [MFC], OnBeforeChangeParent
- CPane [MFC], OnPressCloseButton
- CPane [MFC], OnShowControlBarMenu
- CPane [MFC], OnShowControlBarMenu
- CPane [MFC], RecalcLayout
- CPane [MFC], SaveState
- CPane [MFC], SetActiveInGroup
- CPane [MFC], SetBorders
- CPane [MFC], SetClientHotSpot
- CPane [MFC], SetDockState
- CPane [MFC], SetExclusiveRowMode
- CPane [MFC], SetMiniFrameRTC
- CPane [MFC], SetMinSize
- CPane [MFC], SetVirtualRect
- CPane [MFC], StretchPaneDeferWndPos
- CPane [MFC], ToggleAutoHide
- CPane [MFC], UndockPane
- CPane [MFC], UpdateVirtualRect
- CPane [MFC], OnAfterDock
- CPane [MFC], OnAfterFloat
- CPane [MFC], OnBeforeDock
- CPane [MFC], OnBeforeFloat
- CPane [MFC], m_bHandleMinSize
- CPane [MFC], m_recentDockInfo
ms.assetid: 5c651a64-3c79-4d94-9676-45f6402a6bc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b764777f33b0ae8ea1521e931ee45740f7057ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378438"
---
# <a name="cpane-class"></a>CPane – třída
`CPane` Třída je vylepšení [ccontrolbar – třída](../../mfc/reference/ccontrolbar-class.md). Pokud provádíte upgrade existujícího projektu knihovny MFC, nahraďte všechny výskyty `CControlBar` s `CPane`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPane : public CBasePane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CPane::~CPane`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPane::AdjustSizeImmediate](#adjustsizeimmediate)|Okamžitě přepočítá rozložení podokno.|  
|[CPane::AllocElements](#allocelements)|Přiděluje úložiště pro interní použití.|  
|[CPane::AllowShowOnPaneMenu](#allowshowonpanemenu)|Určuje, zda v podokně je uvedena v seznamu generované modulem runtime podokna pro aplikaci.|  
|[CPane::CalcAvailableSize](#calcavailablesize)|Vypočítá rozdíl velikostí mezi zadaný obdélníku a aktuální obdélníku okna.|  
|[CPane::CalcInsideRect](#calcinsiderect)|Vypočítá uvnitř obdélníku podokna zohledněním ohraničení a úchyty.|  
|[CPane::CalcRecentDockedRect](#calcrecentdockedrect)|Vypočítá nedávno ukotveného rámeček.|  
|[CPane::CalcSize](#calcsize)|Vypočítá velikost podokna.|  
|[CPane::CanBeDocked](#canbedocked)|Určuje, zda v podokně můžete ukotvení v podokně zadané základní.|  
|[CPane::CanBeTabbedDocument](#canbetabbeddocument)|Určuje, zda v podokně můžete převést na dokumentů s kartami.|  
|[CPane::ConvertToTabbedDocument](#converttotabbeddocument)|Lze ukotvit podokna převede do dokumentů s kartami.|  
|[CPane::CopyState](#copystate)|Zkopíruje stav podokno. (Přepisuje [CBasePane::CopyState](../../mfc/reference/cbasepane-class.md#copystate).)|  
|[CPane::Create](#create)|Vytvoří ovládacích pruhů a připojí jej k `CPane` objektu.|  
|[CPane::CreateDefaultMiniframe](#createdefaultminiframe)|Vytvoří zkrácená rámce okna pro plovoucí podokně.|  
|[CPane::CreateEx](#createex)|Vytvoří ovládacích pruhů a připojí jej k `CPane` objektu.|  
|`CPane::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|[CPane::DockByMouse](#dockbymouse)|Podokno ukotvené pomocí myši ukotvení metoda.|  
|[CPane::DockPane](#dockpane)|V podokně plovoucí ukotvené do základní podokna.|  
|[CPane::DockPaneStandard](#dockpanestandard)|Podokno ukotvené pomocí outline (standardní) ukotvení.|  
|[CPane::DockToFrameWindow](#docktoframewindow)|Lze ukotvit podokně ukotvené na snímek. (Přepisuje `CBasePane::DockToFrameWindow`.)|  
|[CPane::DoesAllowSiblingBars](#doesallowsiblingbars)|Určuje, zda lze ukotvení jiného podokna na stejný řádek, kde je ukotvena podokně aktuální.|  
|[CPane::FloatPane](#floatpane)|Obtéká podokně.|  
|[CPane::GetAvailableExpandSize](#getavailableexpandsize)|Vrátí velikost, v pixelech, které můžete v podokně rozbalte.|  
|[CPane::GetAvailableStretchSize](#getavailablestretchsize)|Vrátí velikost, v pixelech, které můžete v podokně zmenšit.|  
|[CPane::GetBorders](#getborders)|Vrátí šířku ohraničení podokna.|  
|[CPane::GetClientHotSpot](#getclienthotspot)|Vrátí *aktivního bodu* pro podokně.|  
|[CPane::GetDockSiteRow](#getdocksiterow)|Vrátí ukotvení řádek, ve kterém je ukotvena podokně.|  
|[CPane::GetExclusiveRowMode](#getexclusiverowmode)|Určuje, zda se v podokně je v režimu výhradní řádek.|  
|[CPane::GetHotSpot](#gethotspot)|Vrátí aktivního bodu, který je uložen v základní `CMFCDragFrameImpl` objektu.|  
|[CPane::GetMinSize](#getminsize)|Načte minimální povolená velikost podokna.|  
|[CPane::GetPaneName](#getpanename)|Načte název v podokně.|  
|`CPane::GetResizeStep`|Interně.|  
|`CPane::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CPane::GetVirtualRect](#getvirtualrect)|Načte *virtuální obdélníku* podokna.|  
|[CPane::IsChangeState](#ischangestate)|Pohybu v podokně se analyzuje pozici v podokně relativně k další podokna, ukotvení řádků a okna s rámečkem zkrácená tuto metodu a vrátí odpovídající `AFX_CS_STATUS` hodnotu.|  
|[CPane::IsDragMode](#isdragmode)|Určuje, zda je právě přetáhli podokně.|  
|[CPane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|Určuje, zda v podokně v rámci více podokně okna. (Přepisuje `CBasePane::IsInFloatingMultiPaneFrameWnd`.)|  
|[CPane::IsLeftOf](#isleftof)|Určuje, zda je v podokně zleva nástroje (nebo vyšší) zadaný rámeček.|  
|[CPane::IsResizable](#isresizable)|Určuje, zda jde změnit, v podokně. (Přepisuje [CBasePane::IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|  
|[CPane::IsTabbed](#istabbed)|Určuje, zda byl vložen v podokně ovládacího prvku karta záložkách okna. (Přepisuje [CBasePane::IsTabbed](../../mfc/reference/cbasepane-class.md#istabbed).)|  
|[CPane::LoadState](#loadstate)|Stav v podokně načte z registru. (Přepisuje [CBasePane::LoadState](../../mfc/reference/cbasepane-class.md#loadstate).)|  
|[CPane::MoveByAlignment](#movebyalignment)|Přesune podoknem a virtuální rámeček zadanou velikost.|  
|[CPane::MovePane](#movepane)|V podokně se přesune do zadaného rámeček.|  
|[CPane::OnAfterChangeParent](#onafterchangeparent)|Voláno rámcem, pokud došlo ke změně nadřazeného podokno.|  
|[CPane::OnBeforeChangeParent](#onbeforechangeparent)|Voláno rámcem po nadřazeného podokně Chystáte se změnit.|  
|[CPane::OnPressCloseButton](#onpressclosebutton)|Voláno rámcem, když uživatel vybere na titulek pro podokně na tlačítko Zavřít.|  
|`CPane::OnProcessDblClk`|Interně.|  
|[CPane::OnShowControlBarMenu](#onshowcontrolbarmenu)|Voláno rámcem, pokud je speciální podokně nabídka se nezobrazí.|  
|[CPane::OnShowControlBarMenu](#onshowcontrolbarmenu)|Voláno rámcem, pokud je speciální podokně nabídka se nezobrazí.|  
|`CPane::PrepareToDock`|Interně.|  
|[CPane::RecalcLayout](#recalclayout)|Přepočítá rozložení informace o podokně. (Přepisuje [CBasePane::RecalcLayout](../../mfc/reference/cbasepane-class.md#recalclayout).)|  
|[CPane::SaveState](#savestate)|Uloží stav v podokně do registru. (Přepisuje [CBasePane::SaveState](../../mfc/reference/cbasepane-class.md#savestate).)|  
|[CPane::SetActiveInGroup](#setactiveingroup)|Příznaky podokně jako aktivní.|  
|[CPane::SetBorders](#setborders)|Nastaví hodnoty ohraničení podokna.|  
|[CPane::SetClientHotSpot](#setclienthotspot)|Nastaví aktivní bod pro v podokně.|  
|[CPane::SetDockState](#setdockstate)|Obnovení ukotvení informace o stavu pro podokně.|  
|[CPane::SetExclusiveRowMode](#setexclusiverowmode)|Povolí nebo zakáže režimu výhradní řádku.|  
|[CPane::SetMiniFrameRTC](#setminiframertc)|Nastaví informace o třídě modulu runtime pro výchozí zkrácená rámce okna.|  
|[CPane::SetMinSize](#setminsize)|Nastaví minimální povolená velikost podokna.|  
|[CPane::SetVirtualRect](#setvirtualrect)|Nastaví *virtuální obdélníku* podokna.|  
|[CPane::StretchPaneDeferWndPos](#stretchpanedeferwndpos)|Roztahovány podokně vodorovně nebo svisle podle styl ukotvení.|  
|[CPane::ToggleAutoHide](#toggleautohide)|Přepíná režim automaticky skrýt.|  
|[CPane::UndockPane](#undockpane)|V podokně se odebere z webu ukotvení, výchozí posuvníku nebo zkrácená rámec okna, kde je aktuálně ukotven. (Přepisuje [CBasePane::UndockPane](../../mfc/reference/cbasepane-class.md#undockpane).)|  
|[CPane::UpdateVirtualRect](#updatevirtualrect)|Aktualizuje virtuální rámeček.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPane::OnAfterDock](#onafterdock)|Voláno rámcem, pokud byla jej ukotven podokno.|  
|[CPane::OnAfterFloat](#onafterfloat)|Voláno rámcem při podokno je ponechán v neurčitém stavu.|  
|[CPane::OnBeforeDock](#onbeforedock)|Voláno rámcem při podokně je ukotvit.|  
|[CPane::OnBeforeFloat](#onbeforefloat)|Voláno rámcem při podokno je obtékání.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPane::m_bHandleMinSize](#m_bhandleminsize)|Umožňuje konzistentní zpracování minimální velikost podokna.|  
|[CPane::m_recentDockInfo](#m_recentdockinfo)|Obsahuje informace o poslední ukotvení.|  
  
## <a name="remarks"></a>Poznámky  
 Obvykle `CPane` objekty nejsou přímo vytvořeny instance. Pokud budete potřebovat podokno, které jsou ukotvení funkce, odvozovat z objektu [CDockablePane](../../mfc/reference/cdockablepane-class.md). Pokud budete potřebovat nástrojů funkce, odvozovat z objektu [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md).  
  
 Pokud odvodíte třídu od `CPane`, může být ukotveno v [CDockSite](../../mfc/reference/cdocksite-class.md) a může být obtékané v [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxPane.h  
  
##  <a name="adjustsizeimmediate"></a>  CPane::AdjustSizeImmediate  
 Okamžitě přepočítá rozložení podokno.  
  
```  
virtual void AdjustSizeImmediate(BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bRecalcLayout`  
 `TRUE` automaticky přepočítat rozložení podokna. v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu volejte, když dynamicky měnit rozložení podokno. Například můžete volat tuto metodu, když skrytí nebo zobrazení tlačítka panelu nástrojů.  
  
##  <a name="allocelements"></a>  CPane::AllocElements  
 Přiděluje úložiště pro interní použití.  
  
```  
BOOL AllocElements(
    int nElements,  
    int cbElement);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nElements`  
 Počet elementů, u kterého se přidělit úložiště.  
  
 [v] `cbElement`  
 Velikost v bajtech, elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `FALSE` Pokud se nezdaří přidělení paměti; v opačném `TRUE`.  
  
##  <a name="allowshowonpanemenu"></a>  CPane::AllowShowOnPaneMenu  
 Určuje, zda v podokně je uvedena v seznamu generované modulem runtime podokna pro aplikaci.  
  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně se zobrazí v seznamu; v opačném `FALSE`. Základní implementace vždy vrátí `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Generované objekty AppWizard aplikace obsahuje nabídky možnost, která uvádí podokna, které obsahuje. Tato metoda určuje, zda v podokně se zobrazí v seznamu.  
  
##  <a name="calcavailablesize"></a>  CPane::CalcAvailableSize  
 Vypočítá rozdíl velikostí mezi zadaný obdélníku a aktuální obdélníku okna.  
  
```  
virtual CSize CalcAvailableSize(CRect rectRequired);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `rectRequired`  
 Požadované rámeček.  
  
### <a name="return-value"></a>Návratová hodnota  
 Rozdíl ve šířky a výšky mezi `rectRequired` a aktuální obdélníku okna.  
  
##  <a name="calcinsiderect"></a>  CPane::CalcInsideRect  
 Vypočítá uvnitř rámeček panelu, včetně ohraničení a úchyty.  
  
```  
void CalcInsideRect(
    CRect& rect,  
    BOOL bHorz) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `rect`  
 Obsahuje velikost a posun klientské oblasti v podokně.  
  
 [v] `bHorz`  
 `TRUE` Pokud v podokně orientován vodorovně; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem, pokud má přepočítat rozložení pro podokno. `rect` Parametr je vyplněn velikosti a posun klientské oblasti v podokně. To zahrnuje jeho ohraničení a úchyty.  
  
##  <a name="calcrecentdockedrect"></a>  CPane::CalcRecentDockedRect  
 Vypočítá nedávno ukotveného rámeček.  
  
```  
void CalcRecentDockedRect();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda aktualizace [CPane::m_recentDockInfo](#m_recentdockinfo).  
  
##  <a name="calcsize"></a>  CPane::CalcSize  
 Vypočítá velikost podokna.  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bVertDock`  
 `TRUE` Pokud se v podokně ve svislém směru ukotveno `FALSE` jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace této metody vrátí velikost (0, 0).  
  
### <a name="remarks"></a>Poznámky  
 Odvozené třídy by měly přepsat tuto metodu.  
  
##  <a name="canbedocked"></a>  CPane::CanBeDocked  
 Určuje, pokud se v podokně můžete ukotvení v podokně zadané základní.  
  
```  
virtual BOOL CanBeDocked(CBasePane* pDockBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDockBar`  
 Určuje, v podokně, kde má být ukotven v tomto podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v tomto podokně můžete ukotvení v podokně zadaný ukotvení; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána obvykle rámcem k určení, zda lze ukotvit podokno v podokně zadaný ukotvení. K určení, že zda lze ukotvit podokně, vyhodnotí metodu aktuálně v podokně povolené ukotvení zarovnání.  
  
 Povolit ukotvení na různé strany rámce okna voláním [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).  
  
##  <a name="canbetabbeddocument"></a>  CPane::CanBeTabbedDocument  
 Určuje, pokud se v podokně můžete převést na dokumentů s kartami.  
  
```  
virtual BOOL CanBeTabbedDocument() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně můžete převést na záložkách dokument; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě a vrátit `FALSE` Pokud chcete zabránit podokno převodu do dokumentů s kartami. V nabídce umístění okna se neobjeví dokumentů s kartami.  
  
##  <a name="converttotabbeddocument"></a>  CPane::ConvertToTabbedDocument  
 Lze ukotvit podokna převede do dokumentů s kartami.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bActiveTabOnly`  
 Není používán `CPane::ConvertToTabbedDocument`.  
  
### <a name="remarks"></a>Poznámky  
 Do dokumentů s kartami lze převádět pouze lze ukotvit podokna. Informace najdete v tématu [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).  
  
##  <a name="copystate"></a>  CPane::CopyState  
 Zkopíruje stav podokno.  
  
```  
virtual void CopyState(CPane* pOrgBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pOrgBar`  
 Ukazatel na podokno.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zkopíruje stav `pOrgBar` do podokna aktuální.  
  
##  <a name="create"></a>  CPane::Create  
 Vytvoří ovládacích pruhů a připojí jej k [CPane](../../mfc/reference/cpane-class.md) objektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszClassName`  
 Určuje název třídy systému Windows.  
  
 [v] `dwStyle`  
 Určuje styl atributů okna. Další informace najdete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [v] `rect`  
 Určuje počáteční velikost a umístění `pParentWnd` okno, v souřadnice klienta.  
  
 [v] [out] `pParentWnd`  
 Určuje okno nadřazené v tomto podokně.  
  
 [v] `nID`  
 Určuje ID podokna.  
  
 [v] `dwControlBarStyle`  
 Určuje styl pro podokně. Další informace najdete v tématu [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 [v] [out] `pContext`  
 Určuje kontext vytvořit podokna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se v podokně úspěšně; vytvořil v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří podokno Windows a připojí jej k `CPane` objektu.  
  
 Pokud jste neinicializovali explicitně [CPane::m_recentDockInfo](#m_recentdockinfo) před voláním `Create`, parametr `rect` bude použit jako rámeček při číslo s plovoucí čárkou nebo ukotvení v podokně.  
  
##  <a name="createdefaultminiframe"></a>  CPane::CreateDefaultMiniframe  
 Vytvoří zkrácená rámce okna pro plovoucí podokně.  
  
```  
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `rectInitial`  
 Určuje počáteční velikost a umístění, v souřadnice obrazovky zkrácená rámce okna vytvořit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nově vytvořený zkrácená rámce okna.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem vytvoření zkrácená rámce okna při obtékané podokno. Okně s rámečkem zkrácená můžou být typu [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) nebo typu [CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md). Okno zkrácená rámce více se vytvoří, pokud se v podokně `AFX_CBRS_FLOAT_MULTI` stylu.  
  
 Informace o třídě modulu runtime pro zkrácená rámce okna je uložené v `CPane::m_pMiniFrameRTC` člen. Odvozené třídy můžete nastavit tento člen, pokud se rozhodnete vytvořit vlastní zkrácená rámce okna.  
  
##  <a name="createex"></a>  CPane::CreateEx  
 Vytvoří ovládacích pruhů a připojí jej k [CPane](../../mfc/reference/cpane-class.md) objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwStyleEx`  
 Určuje atributy stylu delší okno. Další informace najdete v tématu [rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).  
  
 [v] `lpszClassName`  
 Určuje název třídy systému Windows.  
  
 [v] `dwStyle`  
 Určuje styl atributů okna. Další informace najdete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [v] `rect`  
 Určuje počáteční velikost a umístění `pParentWnd` okno, v souřadnice klienta.  
  
 [v] [out] `pParentWnd`  
 Určuje okno nadřazené v tomto podokně.  
  
 [v] `nID`  
 Určuje ID podokna.  
  
 [v] `dwControlBarStyle`  
 Určuje styl pro podokně. Další informace najdete v tématu [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 [v] [out] `pContext`  
 Určuje kontext vytvořit v podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se v podokně úspěšně; vytvořil v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří podokno Windows a připojí jej k `CPane` objektu.  
  
 Pokud jste neinicializovali explicitně [CPane::m_recentDockInfo](#m_recentdockinfo) před voláním `CreateEx`, parametr `rect` bude použit jako rámeček při číslo s plovoucí čárkou nebo ukotvení v podokně.  
  
##  <a name="dockbymouse"></a>  CPane::DockByMouse  
 Podokno ukotvené pomocí myši.  
  
```  
virtual BOOL DockByMouse(CBasePane* pDockBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDockBar`  
 Určuje základní podokně, do které chcete ukotvit v tomto podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně se ukotven úspěšně; v opačném `FALSE`.  
  
##  <a name="dockpane"></a>  CPane::DockPane  
 V podokně plovoucí ukotvené do základní podokna.  
  
```  
virtual BOOL DockPane(
    CBasePane* pDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out] `pDockBar`  
 Určuje základní podokno ukotvení – v tomto podokně na.  
  
 [v] `lpRect`  
 Určuje rámeček v podokně základní, kde má být ukotven v tomto podokně.  
  
 [v] `dockMethod`  
 Určuje metodu ukotvení používat. Dostupné možnosti jsou následující:  
  
|Možnost|Popis|  
|------------|-----------------|  
|`DM_UNKNOWN`|Rozhraní používá tuto možnost, při ukotvení metoda neznámý. V podokně neukládá jeho poslední plovoucí pozice. Tuto možnost můžete taky použít k prostřednictvím kódu programu ukotvit podokno, když jste k uložení poslední plovoucí pozice.|  
|`DM_MOUSE`|Interně.|  
|`DM_DBL_CLICK`|Tato možnost se používá při poklepání na úchytu. V podokně je změnit jejich umístění na nejnovější pozici ukotvení. Pokud je v podokně nepřipojený dvojitým kliknutím na soubor, je v podokně změnit jejich umístění na nejnovější plovoucí pozici.|  
|`DM_SHOW`|Tato možnost slouží k prostřednictvím kódu programu ukotvení v podokně. V podokně ukládá jeho poslední plovoucí pozice.|  
|`DM_RECT`|V podokně ukotven v oblasti, která je zadána `lpRect`.|  
|`DM_STANDARD`|Pokud použijete tuto možnost, rozhraní během je přesouvání nevykresluje v podokně jako obrys rámečku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně se ukotven úspěšně; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda ukotvené podokně do podokna základní, která je zadána `pDockBar` parametr. Je třeba nejprve povolit ukotvení voláním [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).  
  
##  <a name="dockpanestandard"></a>  CPane::DockPaneStandard  
 Podokno ukotvené pomocí outline (standardní) ukotvení.  
  
```  
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bWasDocked`  
 `TRUE` Pokud v podokně byl úspěšně ukotven; v opačném `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vždy vrátí hodnotu `this` ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se používá pouze pro podokna, které jsou odvozeny od [CDockablePane Class](../../mfc/reference/cdockablepane-class.md). Další informace najdete v tématu [CDockablePane::DockPaneStandard](../../mfc/reference/cdockablepane-class.md#dockpanestandard).  
  
##  <a name="docktoframewindow"></a>  CPane::DockToFrameWindow  
 Lze ukotvit podokně ukotvené na snímek.  
  
```  
virtual BOOL DockToFrameWindow(
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL,  
    DWORD dwDockFlags = DT_DOCK_LAST,  
    CBasePane* pRelativeBar = NULL,  
    int nRelativeIndex = -1,  
    BOOL bOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwAlignment`  
 Na straně nadřazené rámce, který chcete ukotvit podokno.  
  
 [v] `lpRect`  
 Zadaná velikost.  
  
 [v] `dwDockFlags`  
 Ignorovat.  
  
 [v] `pRelativeBar`  
 Ignorovat.  
  
 [v] `nRelativeIndex`  
 Ignorovat.  
  
 [v] `bOuterEdge`  
 Pokud `TRUE` a neexistují další lze ukotvit podokna na stranu, která jsou zadána `dwAlignment`, v podokně ukotven mimo jiné podokna blíže okraje nadřazeného rámce. Pokud `FALSE`, v podokně ukotven blíže k centru klientské oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 `FALSE` Pokud rozdělovací podokně ( [CPaneDivider třída](../../mfc/reference/cpanedivider-class.md)) nemůže být vytvořený, jinak hodnota `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="doesallowsiblingbars"></a>  CPane::DoesAllowSiblingBars  
 Určuje, zda lze ukotvení jiného podokna na stejný řádek, kde je ukotvena podokně aktuální.  
  
```  
virtual BOOL DoesAllowSiblingBars() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v tomto podokně můžete ukotvit jiného podokna na stejném řádku jako samotný; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Můžete povolit nebo zakázat toto chování voláním [CPane::SetExclusiveRowMode](#setexclusiverowmode).  
  
 Ve výchozím nastavení panely nástrojů mít zakázaným režimem výhradní řádek a řádku nabídek má povolen režim výhradní řádek.  
  
##  <a name="floatpane"></a>  CPane::FloatPane  
 Obtéká podokně.  
  
```  
virtual BOOL FloatPane(
    CRect rectFloat,  
    AFX_DOCK_METHOD dockMethod = DM_UNKNOWN,  
    bool bShow = true);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `rectFloat`  
 Určuje umístění, v souřadnice obrazovky, na pozici v podokně, když je obtékané.  
  
 [v] `dockMethod`  
 Určuje metodu ukotvení při obtékané podokně. Seznam možných hodnot najdete v tématu [CPane::DockPane](#dockpane).  
  
 [v] `bShow`  
 `TRUE` Chcete-li zobrazit v podokně při obtékané; v opačném `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud byl úspěšně obtékané podokně nebo pokud se v podokně nelze obtékané, protože [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat) vrátí `FALSE`, jinak hodnota `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu za účelem float podokně na pozici, která je zadána `rectFloat` parametr. Tato metoda vytváří automaticky nadřazené zkrácená rámce okna pro podokně.  
  
##  <a name="getavailableexpandsize"></a>  CPane::GetAvailableExpandSize  
 Vrátí velikost, v pixelech, které můžete v podokně rozbalte.  
  
```  
virtual int GetAvailableExpandSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud v podokně ukotven vodorovně, vrácená hodnota je k dispozici šířku; návratovou hodnotu, jinak hodnota je k dispozici výšku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getavailablestretchsize"></a>  CPane::GetAvailableStretchSize  
 Vrátí velikost, v pixelech, které můžete v podokně zmenšit.  
  
```  
virtual int GetAvailableStretchSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost v pixelech, které můžete v podokně zmenšit. Pokud v podokně ukotven vodorovně, toto množství je k dispozici šířku; jinak je k dispozici výšku.  
  
### <a name="remarks"></a>Poznámky  
 Velikost dostupné stretch se počítá odečtením minimální povolená velikost podokna ( [CPane::GetMinSize](#getminsize)) z aktuální velikost ( [CWnd::GetWindowRect](../../mfc/reference/cwnd-class.md#getwindowrect)).  
  
##  <a name="getborders"></a>  CPane::GetBorders  
 Vrátí šířku ohraničení podokna.  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje aktuální šířku v pixelech každé straně podokna. Například hodnota `left` členem `CRect` objekt je šířka levého ohraničení.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li nastavit velikost ohraničení, volejte [CPane::SetBorders](#setborders).  
  
##  <a name="getclienthotspot"></a>  CPane::GetClientHotSpot  
 Vrátí *aktivního bodu* pro podokně.  
  
```  
CPoint GetClientHotSpot() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 *Aktivního bodu* je bod v podokně, které uživatel vybere a obsahuje přesunout podokně. Aktivní bod se používá pro smooth animace, pokud je v podokně přesunut z pozice ukotveného.  
  
##  <a name="getdocksiterow"></a>  CPane::GetDockSiteRow  
 Vrátí řádek ukotvení ( [CDockingPanesRow třída](../../mfc/reference/cdockingpanesrow-class.md)) v podokně ukotven.  
  
```  
CDockingPanesRow* GetDockSiteRow() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CDockingPanesRow`* který odkazuje na ukotvení řádek, ve kterém je ukotvena podokně, nebo `NULL` Pokud není ukotven podokně.  
  
##  <a name="getexclusiverowmode"></a>  CPane::GetExclusiveRowMode  
 Určuje, zda v podokně v režimu výhradní řádek.  
  
```  
virtual BOOL GetExclusiveRowMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je podokno v režimu row výhradní; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o režimu výhradní řádku, najdete v části [CPane::SetExclusiveRowMode](#setexclusiverowmode).  
  
##  <a name="gethotspot"></a>  CPane::GetHotSpot  
 Vrátí aktivního bodu, který je uložen v základní `CMFCDragFrameImpl` objektu.  
  
```  
CPoint GetHotSpot() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 `CPane` Třída obsahuje `CMFCDragFrameImpl` objekt, `m_dragFrameImpl`, která je zodpovědná za kreslení obdélníku, která se zobrazí, když uživatel přesune podokno ve standardním režimu ukotvení. Aktivní bod slouží k vykreslení obdélník relativní vzhledem k aktuální pozici myši jako uživatel přesune podokně.  
  
##  <a name="getminsize"></a>  CPane::GetMinSize  
 Načte minimální povolená velikost podokna.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `size`  
 A `CSize` objekt, který je vyplněn minimální povolená velikost.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpanename"></a>  CPane::GetPaneName  
 Načte název v podokně.  
  
```  
virtual void GetPaneName(CString& strName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `strName`  
 A `CString` objekt, který je vyplněn název záhlaví.  
  
### <a name="remarks"></a>Poznámky  
 V oblasti titulek je zobrazen název podokně, když se v podokně ukotveného nebo plovoucí. Pokud v podokně je součástí skupiny s kartami, název se zobrazí v oblasti kartě. Pokud je v režimu automaticky skrýt podokno, název se zobrazí na `CMFCAutoHideButton`.  
  
##  <a name="getvirtualrect"></a>  CPane::GetVirtualRect  
 Načte *virtuální obdélníku* podokna.  
  
```  
void GetVirtualRect(CRect& rectVirtual) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `rectVirtual`  
 A `CRect` objekt, který je vyplněn virtuální rámeček.  
  
### <a name="remarks"></a>Poznámky  
 Pokud podokno se přesune, rozhraní framework uloží původní pozice v podokně v obdélníku virtuální. Rozhraní framework můžete použít k obnovení původní pozice v podokně virtuální rámeček.  
  
 Nevolejte metody, které se vztahují k virtuální obdélníků, pokud přesouváte podokna prostřednictvím kódu programu.  
  
##  <a name="ischangestate"></a>  CPane::IsChangeState  
 Pohybu v podokně se analyzuje jeho pozice relativně k další podokna, ukotvení řádků a okna s rámečkem zkrácená tuto metodu a vrátí odpovídající `AFX_CS_STATUS` hodnotu.  
  
```  
virtual AFX_CS_STATUS IsChangeState(
    int nOffset,  
    CBasePane** ppTargetBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nOffset`  
 Určuje ukotvení velkých a malých písmen. Například podokno, v němž je přesunut v rámci `nOffset` budou ukotveny pixelů z řádku ukotvení.  
  
 [v] `ppTargetBar`  
 Po návratu metody `ppTargetBar` obsahuje buď ukazatele na objekt, ke kterému by měl ukotven podokně aktuální, nebo `NULL` Pokud žádné ukotvení provedeno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden z následujících `AFX_CS_STATUS` hodnoty:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CS_NOTHING`|V podokně není téměř lokalitu ukotvení. Rozhraní není ukotvení v podokně.|  
|`CS_DOCK_IMMEDIATELY`|V podokně je nad lokalitu ukotvení a `DT_IMMEDIATE` styl povolen. V podokně ukotvené rozhraní okamžitě.|  
|`CS_DELAY_DOCK`|V podokně je nad ukotvení lokalitu, která je jiného ukotvení panelu nebo okraj hlavního rámce. Rozhraní framework ukotvené podokně, když uživatel uvolní přesunutí.|  
|`CS_DELAY_DOCK_TO_TAB`|V podokně je nad ukotvení lokalitu, která způsobí, že podokno Ukotvit okno s kartami. K tomu dochází, když je podokno přes titulek jiné ukotvení panelu nebo přes oblast karty na kartách panelu. Rozhraní framework ukotvené podokně, když uživatel uvolní přesunutí.|  
  
##  <a name="isdragmode"></a>  CPane::IsDragMode  
 Určuje, zda je přesouvá v podokně.  
  
```  
virtual BOOL IsDragMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se v podokně se přesune; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isinfloatingmultipaneframewnd"></a>  CPane::IsInFloatingMultiPaneFrameWnd  
 Určuje, jestli je v podokně v rámci více podokně okna ( [CMultiPaneFrameWnd třída](../../mfc/reference/cmultipaneframewnd-class.md)).  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně se v rámci více podokně okna; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 V okně s rámečkem více podokně můžete float pouze lze ukotvit podokna. Proto `CPane::IsInFloatingMultiPaneFrameWnd` vždy vrátí hodnotu `FALSE`.  
  
##  <a name="isleftof"></a>  CPane::IsLeftOf  
 Určuje, zda je v podokně zleva nástroje (nebo vyšší) zadaný rámeček.  
  
```  
bool IsLeftOf(
    CRect rect,  
    bool bWindowRect = true) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `rect`  
 A `CRect` objekt, který se používá k porovnání.  
  
 [v] `bWindowRect`  
 Pokud `TRUE`, `rect` se předpokládá, že obsahovat souřadnice obrazovky; Pokud `FALSE`, `rect` obsahuje souřadnice klienta.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Pokud v podokně ukotven vodorovně, tato metoda ověří, zda její umístění je ponechán z `rect`. Jinak tato metoda zkontroluje, jestli umístění výše `rect`.  
  
##  <a name="isresizable"></a>  CPane::IsResizable  
 Určuje, zda je v podokně s možností změny velikosti.  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je v podokně s možností změny velikosti; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Základní `CPane` objekty nejsou s možností změny velikosti.  
  
 Ukotvení manager používá s možností změny velikosti příznak k určení rozložení podokna. Non-umožňující změnu velikosti podokna jsou vždy umístěné na vnější okraje nadřazeného rámce.  
  
 Non-umožňující změnu velikosti podokna se nesmí nacházet v ukotvení kontejnery.  
  
##  <a name="istabbed"></a>  CPane::IsTabbed  
 Určuje, zda v podokně byla vložena do ovládacího prvku karta záložkách okna.  
  
```  
virtual BOOL IsTabbed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je v podokně – se záložkami; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Na kartách stavu je zpracovávat odděleně od procedura ukotven a automaticky skrýt stavy.  
  
##  <a name="loadstate"></a>  CPane::LoadState  
 Stav v podokně načte z registru.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszProfileName`  
 Název profilu.  
  
 [v] `nIndex`  
 Profil index.  
  
 [v] `uiID`  
 ID podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud podokno stavu byl načten úspěšně; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu za účelem načtení stavu podokně z registru. Přepsání v odvozené třídě načíst další informace, který je uložený ve [CPane::SaveState](#savestate).  
  
 Pokud tuto metodu přepíšete, také volat základní metodu a vrátí `FALSE` základní metoda vrátí-li `FALSE`.  
  
##  <a name="m_bhandleminsize"></a>  CPane::m_bHandleMinSize  
 Umožňuje konzistentní zpracování velikostí minimální podokně.  
  
```  
AFX_IMPORT_DATA static BOOL m_bHandleMinSize;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud jeden nebo více ukotvení podokna ve vaší aplikaci přepsat `GetMinSize`, nebo pokud aplikace zavolá `SetMinSize`, můžete chtít nastavit tuto statický člen na `TRUE` Chcete-li povolit rozhraní pro zpracování konzistentně, jak mají velikost podokna.  
  
 Pokud tato hodnota nastavena na `TRUE`, jsou všechny podokna, jejíž aktuální velikost by měla být snížit pod jejich minimální velikost oříznut, není roztažená. Protože rozhraní používá okno oblasti pro účely nastavení velikosti podokně, neměňte velikost okna oblast pro ukotvení podokna, pokud je tato hodnota nastavená `TRUE`.  
  
##  <a name="m_recentdockinfo"></a>  CPane::m_recentDockInfo  
 Obsahuje informace o poslední ukotvení.  
  
```  
CRecentDockSiteInfo m_recentDockInfo;  
```  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework ukládá ukotvení nejnovější informace o stavu v podokně do tohoto člena.  
  
##  <a name="movebyalignment"></a>  CPane::MoveByAlignment  
 Přesune podoknem a virtuální rámeček zadanou velikost.  
  
```  
BOOL MoveByAlignment(
    DWORD dwAlignment,  
    int nOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwAlignment`  
 Určuje zarovnání podokně.  
  
 [v] `nOffset`  
 Velikost v pixelech, kterým se mají přesunout podoknem a virtuální rámeček.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 `dwAlignment` může být jedno z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|Umožňuje podokno ukotvit do horní části klientské oblasti okně s rámečkem.|  
|`CBRS_ALIGN_BOTTOM`|Umožňuje podokno ukotvit k dolnímu okraji klientské oblasti okně s rámečkem.|  
|`CBRS_ALIGN_LEFT`|Umožňuje podokno ukotveny na levé straně klientské oblasti okně s rámečkem.|  
|`CBRS_ALIGN_RIGHT`|Umožňuje podokno ukotveny na pravé straně klientské oblasti okně s rámečkem.|  
|`CBRS_ALIGN_ANY`|Umožňuje podokno ukotveny na žádné straně klientské oblasti okně s rámečkem.|  
  
 Pokud `dwAlignment` obsahuje `CBRS_ALIGN_LEFT` nebo `CBRS_ALIGN_RIGHT` příznak, podokno a virtuální obdélníku přesunou vodorovně; v opačném případě `dwAlignment` obsahuje `CBRS_ALIGN_TOP` nebo `CBRS_ALIGN_BOTTOM` přesunou příznak, podokno a virtuální obdélníku svisle.  
  
##  <a name="movepane"></a>  CPane::MovePane  
 V podokně se přesune do zadaného rámeček.  
  
```  
virtual CSize MovePane(
    CRect rectNew,  
    BOOL bForceMove,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `rectNew`  
 Určuje nové rámeček pro podokně.  
  
 [v] `bForceMove`  
 Pokud `TRUE`, tato metoda se ignoruje velikost minimální povolené podokně ( [CPane::GetMinSize](#getminsize)), jinak hodnota v podokně se upraví, pokud je to nutné k zajištění, že je alespoň minimální povolená velikost.  
  
 [v] `hdwp`  
 Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CSize` objekt, který obsahuje rozdíly v šířky a výšky mezi obdélníky novém i starém (starý obdélníku - `rectNew`).  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se používá pouze pro lze ukotvit podokna.  
  
##  <a name="onafterchangeparent"></a>  CPane::OnAfterChangeParent  
 Voláno rámcem, pokud došlo ke změně nadřazeného podokno.  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out] `pWndOldParent`  
 V podokně předchozí nadřazeného okna.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rozhraním framework, když nadřazený podokno se změnil z důvodu operace ukotvení nebo plovoucí.  
  
##  <a name="onafterdock"></a>  CPane::OnAfterDock  
 Voláno rámcem, pokud byla jej ukotven podokno.  
  
```  
virtual void OnAfterDock(
    CBasePane* pBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
 Tento parametr není používán.  
  
 [v] `lpRect`  
 Tento parametr není používán.  
  
 [v] `dockMethod`  
 Tento parametr není používán.  
  
##  <a name="onafterfloat"></a>  CPane::OnAfterFloat  
 Voláno rámcem po jako plovoucí podokno.  
  
```  
virtual void OnAfterFloat();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete provést jakékoli zpracovávání po jako plovoucí podokno, mohou přepsat tuto metodu v odvozené třídě.  
  
##  <a name="onbeforechangeparent"></a>  CPane::OnBeforeChangeParent  
 Voláno rámcem po nadřazeného podokně Chystáte se změnit.  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out] `pWndNewParent`  
 Určuje nového nadřazeného okna.  
  
 [v] `bDelay`  
 `TRUE` zpoždění globální ukotvení úpravy rozvržení; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem při nadřazeného podokně je změnit, protože se v podokně ukotven nebo obtékané.  
  
 Ve výchozím nastavení, v podokně se zrušit registraci s podokně ukotvení voláním `CDockSite::RemovePane`.  
  
##  <a name="onbeforedock"></a>  CPane::OnBeforeDock  
 Voláno rámcem při podokně je ukotvení.  
  
```  
virtual BOOL OnBeforeDock(
    CBasePane** ppDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out] `ppDockBar`  
 Určuje, v podokně, který je v tomto podokně ukotvení na.  
  
 [v] `lpRect`  
 Určuje ukotvení rámeček.  
  
 [v] `dockMethod`  
 Určuje metodu ukotvení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně lze ukotvit. Pokud funkce vrátí `FALSE`, ukotvení operace bude zrušena.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem při podokno je ukotvit. Pokud chcete provést jakékoli zpracovávání před podokno nakonec ukotven, mohou přepsat tuto metodu v odvozené třídě.  
  
##  <a name="onbeforefloat"></a>  CPane::OnBeforeFloat  
 Voláno rámcem při podokno je o float.  
  
```  
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `rectFloat`  
 Pokud je ve stavu, plovoucí Určuje umístění a velikost podokna.  
  
 [v] `dockMethod`  
 Určuje metodu ukotvení podokna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně můžete obtékané; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem při podokno je o float. Pokud chcete provést jakékoli zpracovávání před podokně nakonec jako plovoucí, mohou přepsat tuto metodu v odvozené třídě.  
  
##  <a name="onpressclosebutton"></a>  CPane::OnPressCloseButton  
 Voláno rámcem, když uživatel na titulek pro podokně stiskne tlačítko Zavřít.  
  
```  
virtual void OnPressCloseButton();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem po stisknutí **Zavřít** tlačítko na titulek v podokně. Pokud chcete dostávat oznámení o **Zavřít** událostí, mohou přepsat tuto metodu v odvozené třídě.  
  
##  <a name="onshowcontrolbarmenu"></a>  CPane::OnShowControlBarMenu  
 Voláno rámcem, pokud je speciální podokně nabídka se nezobrazí.  
  
```  
virtual BOOL OnShowControlBarMenu(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Určuje umístění nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud může být zobrazena v nabídce; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 V nabídce obsahuje několik položek, které vám umožní určit chování v podokně, konkrétně: **plovoucí**, **stabilní umístění**, **autohide –**, a **skrýt**. Tato nabídka pro všechny podokna můžete povolit voláním [CDockingManager::EnableDockSiteMenu](../../mfc/reference/cdockingmanager-class.md#enabledocksitemenu).  
  
##  <a name="recalclayout"></a>  CPane::RecalcLayout  
 Přepočítá rozložení informace o podokně.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je ukotveno podokně, tato metoda aktualizuje virtuální rámeček pro v podokně nastavením jeho velikost na aktuální velikost podokna.  
  
 Pokud je v podokně plovoucí, tato metoda upozorní nadřazeného zkrácená rámce upravit velikost podokna velikosti zkrácená rámečku. Rozhraní framework zajišťuje, že zkrácená rámečku alespoň minimální povolená velikost podokna ( [CPane::GetMinSize](#getminsize)) a v případě potřeby změní velikost zkrácená rámečku.  
  
##  <a name="savestate"></a>  CPane::SaveState  
 Uloží stav v podokně do registru.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszProfileName`  
 Název profilu.  
  
 [v] `nIndex`  
 Profil index.  
  
 [v] `uiID`  
 ID podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud byl úspěšně; uložen stav v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu, když ho uloží stav v podokně do registru. Přepsání `SaveState` v odvozené třídě pro uložení dalších informací.  
  
 Pokud tuto metodu přepíšete, také volat základní metodu a vrátí `FALSE` základní metoda vrátí-li `FALSE`.  
  
##  <a name="setactiveingroup"></a>  CPane::SetActiveInGroup  
 Příznaky podokně jako aktivní.  
  
```  
virtual void SetActiveInGroup(BOOL bActive);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bActive`  
 A `BOOL` určující, zda v podokně je označený jako aktivní.  
  
### <a name="remarks"></a>Poznámky  
 Pokud lze ukotvit podokně se zobrazuje nebo je zvolen automaticky skrýt tlačítko, odpovídající automaticky skrýt podokno je označen jako aktivní.  
  
 Zobrazení automaticky skrýt tlačítka, který je přidružen v podokně je založena na dva faktory. Pokud je aktivní, v podokně a `static BOOL CMFCAutoHideButton::m_bOverlappingTabs` je `TRUE`, rozhraní zobrazí automaticky skrýt tlačítko jako ikonu a štítek. Rozhraní pro neaktivní podokně, zobrazí jenom ikonu automaticky skrýt.  
  
 Pokud `CMFCAutoHideButton::m_bOverlappingTabs` je `FALSE`, nebo pokud není ve skupině v podokně, zobrazí rozhraní přidružené automaticky skrýt tlačítko jako ikonu a štítek.  
  
##  <a name="setborders"></a>  CPane::SetBorders  
 Nastaví hodnoty ohraničení podokna.  
  
```  
void SetBorders(
    int cxLeft = 0,  
    int cyTop = 0,  
    int cxRight = 0,  
    int cyBottom = 0);  
  
void SetBorders(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `cxLeft`  
 Určuje šířku v pixelech levého ohraničení v podokně.  
  
 [v] `cyTop`  
 Určuje šířku v pixelech horního ohraničení podokna.  
  
 [v] `cxRight`  
 Určuje šířku v pixelech pravého ohraničení podokna.  
  
 [v] `cyBottom`  
 Určuje šířku v pixelech dolního ohraničení podokna.  
  
 [v] `lpRect`  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje šířku v pixelech, každý ohraničení podokna.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce Nastavení velikostí v podokně ohraničení.  
  
##  <a name="setclienthotspot"></a>  CPane::SetClientHotSpot  
 Nastaví *aktivního bodu* pro podokně.  
  
```  
void SetClientHotSpot(const CPoint& ptNew);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `ptNew`  
 A `CPoint` objekt, který určuje nové aktivního bodu.  
  
### <a name="remarks"></a>Poznámky  
 *Aktivního bodu* je bod v podokně, které uživatel vybere a obsahuje přesunout podokně. Aktivní body se používá pro smooth animace při přetažení z pozice ukotveného podokně.  
  
##  <a name="setdockstate"></a>  CPane::SetDockState  
 Obnovení ukotvení informace o stavu pro podokně.  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDockManager`  
 Ukazatel na ukotvení správce pro hlavní okno rámce.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem obnovit poslední ukotvení informace o stavu pro podokně. Podokno ukládá poslední ukotvení informace o stavu v [CPane::m_recentDockInfo](#m_recentdockinfo). Další informace najdete v tématu [CRecentDockSiteInfo třída](../../mfc/reference/crecentdocksiteinfo-class.md).  
  
 Také můžete volat tuto metodu a nastavit stav ukotvení při načítání podokně informace z externího zdroje.  
  
##  <a name="setexclusiverowmode"></a>  CPane::SetExclusiveRowMode  
 Povolí nebo zakáže režimu výhradní řádku.  
  
```  
virtual void SetExclusiveRowMode(BOOL bExclusive = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bExclusive`  
 `TRUE` Pokud chcete povolit režim výhradní řádek; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze povolit nebo zakázat režim výhradní řádek. Pokud podokno je v režimu výhradní řádek, ho nemohou sdílet na stejném řádku s jiný panel nástrojů.  
  
 Ve výchozím nastavení všechny panely nástrojů mít zakázaným režimem výhradní řádek a řádku nabídek má povolen režim výhradní řádek.  
  
##  <a name="setminsize"></a>  CPane::SetMinSize  
 Nastaví minimální povolená velikost podokna.  
  
```  
void SetMinSize(const CSize& size);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `size`  
 A `CSize` objekt, který obsahuje minimální povolená velikost podokna.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setvirtualrect"></a>  CPane::SetVirtualRect  
 Nastaví *virtuální obdélníku* podokna.  
  
```  
void SetVirtualRect(
    const CRect& rect,  
    BOOL bMapToParent = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `rect`  
 A `CRect` objekt, který určuje virtuální rámeček nastavit.  
  
 [v] `bMapToParent`  
 Zadejte `TRUE` Pokud `rect` obsahuje v souvislosti s nadřazeného okna.  
  
### <a name="remarks"></a>Poznámky  
 A *virtuální obdélníku* ukládá původní pozice podokno při přesunu. Rozhraní framework můžete použít virtuální rámeček Obnovit původní pozici.  
  
 Nevolejte metody, které se vztahují k virtuální obdélníků, pokud přesouváte podokna prostřednictvím kódu programu.  
  
##  <a name="setminiframertc"></a>  CPane::SetMiniFrameRTC  
 Nastaví informace o třídě modulu runtime pro výchozí zkrácená rámce okna.  
  
```  
void SetMiniFrameRTC(CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out] `pClass`  
 Určuje informace o třídě modulu runtime pro zkrácená rámce okna.  
  
### <a name="remarks"></a>Poznámky  
 Když obtékané podokno se umístí [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) okně (zkrácená rámečkem). Můžete zadat vlastní `CPaneFrameWnd`-odvozené třídy, které se bude použít, když [CPane::CreateDefaultMiniframe](#createdefaultminiframe) je volána.  
  
##  <a name="stretchpanedeferwndpos"></a>  CPane::StretchPaneDeferWndPos  
 Roztahovány podokně vodorovně nebo svisle podle styl ukotvení.  
  
```  
virtual int StretchPaneDeferWndPos(
    int nStretchSize,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nStretchSize`  
 Velikost (v pixelech) k roztahování podokně. Zmenšení podokně použijte zápornou hodnotu.  
  
 [v] `hdwp`  
 Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Skutečná velikost v pixelech, aby byl k roztažení v podokně.  
  
### <a name="remarks"></a>Poznámky  
 Pokud třeba, tato metoda upraví `nStretchSize` zajistit, že v podokně není větší než omezení velikosti. Tato omezení se získá voláním [CPane::GetAvailableStretchSize](#getavailablestretchsize) a [CPane::GetAvailableExpandSize](#getavailableexpandsize).  
  
##  <a name="toggleautohide"></a>  CPane::ToggleAutoHide  
 Přepíná režim automaticky skrýt.  
  
```  
virtual void ToggleAutoHide();
```  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu k přepnutí režimu automaticky skrýt. Podokno musí ukotven do hlavního rámce okna aby přepnout do režimu automaticky skrýt.  
  
##  <a name="undockpane"></a>  CPane::UndockPane  
 V podokně se odebere z webu ukotvení, výchozí posuvníku nebo zkrácená rámec okna, kde je aktuálně ukotven.  
  
```  
virtual void UndockPane(BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bDelay`  
 Pokud `FALSE`, volání framework [CBasePane::AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout) upravit ukotvení rozložení.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k prostřednictvím kódu programu uvolnit podokno.  
  
##  <a name="updatevirtualrect"></a>  CPane::UpdateVirtualRect  
 Aktualizuje virtuální rámeček.  
  
```  
void UpdateVirtualRect();  
void UpdateVirtualRect(CPoint ptOffset);  
  void UpdateVirtualRect(CSize sizeNew);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `ptOffset`  
 A `CPoint` objekt, který určuje posun podle kterého se posunou podokně.  
  
 [v] `sizeNew`  
 A `CSize` objekt, který určuje novou velikost podokna.  
  
### <a name="remarks"></a>Poznámky  
 První přetížení nastaví virtuální rámeček pomocí aktuálního umístění a velikost podokna.  
  
 Druhý přetížení posune virtuální rámeček velikostí, která je zadána `ptOffset`.  
  
 Třetí přetížení nastaví virtuální rámeček pomocí aktuální pozici v podokně a velikosti, která je zadána `sizeNew`.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CBasePane – třída](../../mfc/reference/cbasepane-class.md)
