---
title: Třída CMFCTabCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTabCtrl
- AFXTABCTRL/CMFCTabCtrl
- AFXTABCTRL/CMFCTabCtrl::ActivateMDITab
- AFXTABCTRL/CMFCTabCtrl::AllowDestroyEmptyTabbedPane
- AFXTABCTRL/CMFCTabCtrl::AutoSizeWindow
- AFXTABCTRL/CMFCTabCtrl::CalcRectEdit
- AFXTABCTRL/CMFCTabCtrl::Create
- AFXTABCTRL/CMFCTabCtrl::EnableActiveTabCloseButton
- AFXTABCTRL/CMFCTabCtrl::EnableInPlaceEdit
- AFXTABCTRL/CMFCTabCtrl::EnableTabDocumentsMenu
- AFXTABCTRL/CMFCTabCtrl::EnsureVisible
- AFXTABCTRL/CMFCTabCtrl::GetDocumentIcon
- AFXTABCTRL/CMFCTabCtrl::GetFirstVisibleTabNum
- AFXTABCTRL/CMFCTabCtrl::GetResizeMode
- AFXTABCTRL/CMFCTabCtrl::GetScrollBar
- AFXTABCTRL/CMFCTabCtrl::GetTabArea
- AFXTABCTRL/CMFCTabCtrl::GetTabMaxWidth
- AFXTABCTRL/CMFCTabCtrl::GetTabsHeight
- AFXTABCTRL/CMFCTabCtrl::GetTabsRect
- AFXTABCTRL/CMFCTabCtrl::GetWndArea
- AFXTABCTRL/CMFCTabCtrl::HideActiveWindowHorzScrollBar
- AFXTABCTRL/CMFCTabCtrl::HideInactiveWindow
- AFXTABCTRL/CMFCTabCtrl::HideNoTabs
- AFXTABCTRL/CMFCTabCtrl::HideSingleTab
- AFXTABCTRL/CMFCTabCtrl::IsActiveInMDITabGroup
- AFXTABCTRL/CMFCTabCtrl::IsActiveTabBoldFont
- AFXTABCTRL/CMFCTabCtrl::IsActiveTabCloseButton
- AFXTABCTRL/CMFCTabCtrl::IsDrawFrame
- AFXTABCTRL/CMFCTabCtrl::IsFlatFrame
- AFXTABCTRL/CMFCTabCtrl::IsFlatTab
- AFXTABCTRL/CMFCTabCtrl::IsLeftRightRounded
- AFXTABCTRL/CMFCTabCtrl::IsMDITabGroup
- AFXTABCTRL/CMFCTabCtrl::IsOneNoteStyle
- AFXTABCTRL/CMFCTabCtrl::IsSharedScroll
- AFXTABCTRL/CMFCTabCtrl::IsTabDocumentsMenu
- AFXTABCTRL/CMFCTabCtrl::IsVS2005Style
- AFXTABCTRL/CMFCTabCtrl::ModifyTabStyle
- AFXTABCTRL/CMFCTabCtrl::OnDragEnter
- AFXTABCTRL/CMFCTabCtrl::OnDragOver
- AFXTABCTRL/CMFCTabCtrl::OnShowTabDocumentsMenu
- AFXTABCTRL/CMFCTabCtrl::SetActiveInMDITabGroup
- AFXTABCTRL/CMFCTabCtrl::SetActiveTab
- AFXTABCTRL/CMFCTabCtrl::SetActiveTabBoldFont
- AFXTABCTRL/CMFCTabCtrl::SetDrawFrame
- AFXTABCTRL/CMFCTabCtrl::SetFlatFrame
- AFXTABCTRL/CMFCTabCtrl::SetImageList
- AFXTABCTRL/CMFCTabCtrl::SetResizeMode
- AFXTABCTRL/CMFCTabCtrl::SetTabMaxWidth
- AFXTABCTRL/CMFCTabCtrl::StopResize
- AFXTABCTRL/CMFCTabCtrl::SynchronizeScrollBar
- AFXTABCTRL/CMFCTabCtrl::m_bEnableActivate
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabCtrl [MFC], ActivateMDITab
- CMFCTabCtrl [MFC], AllowDestroyEmptyTabbedPane
- CMFCTabCtrl [MFC], AutoSizeWindow
- CMFCTabCtrl [MFC], CalcRectEdit
- CMFCTabCtrl [MFC], Create
- CMFCTabCtrl [MFC], EnableActiveTabCloseButton
- CMFCTabCtrl [MFC], EnableInPlaceEdit
- CMFCTabCtrl [MFC], EnableTabDocumentsMenu
- CMFCTabCtrl [MFC], EnsureVisible
- CMFCTabCtrl [MFC], GetDocumentIcon
- CMFCTabCtrl [MFC], GetFirstVisibleTabNum
- CMFCTabCtrl [MFC], GetResizeMode
- CMFCTabCtrl [MFC], GetScrollBar
- CMFCTabCtrl [MFC], GetTabArea
- CMFCTabCtrl [MFC], GetTabMaxWidth
- CMFCTabCtrl [MFC], GetTabsHeight
- CMFCTabCtrl [MFC], GetTabsRect
- CMFCTabCtrl [MFC], GetWndArea
- CMFCTabCtrl [MFC], HideActiveWindowHorzScrollBar
- CMFCTabCtrl [MFC], HideInactiveWindow
- CMFCTabCtrl [MFC], HideNoTabs
- CMFCTabCtrl [MFC], HideSingleTab
- CMFCTabCtrl [MFC], IsActiveInMDITabGroup
- CMFCTabCtrl [MFC], IsActiveTabBoldFont
- CMFCTabCtrl [MFC], IsActiveTabCloseButton
- CMFCTabCtrl [MFC], IsDrawFrame
- CMFCTabCtrl [MFC], IsFlatFrame
- CMFCTabCtrl [MFC], IsFlatTab
- CMFCTabCtrl [MFC], IsLeftRightRounded
- CMFCTabCtrl [MFC], IsMDITabGroup
- CMFCTabCtrl [MFC], IsOneNoteStyle
- CMFCTabCtrl [MFC], IsSharedScroll
- CMFCTabCtrl [MFC], IsTabDocumentsMenu
- CMFCTabCtrl [MFC], IsVS2005Style
- CMFCTabCtrl [MFC], ModifyTabStyle
- CMFCTabCtrl [MFC], OnDragEnter
- CMFCTabCtrl [MFC], OnDragOver
- CMFCTabCtrl [MFC], OnShowTabDocumentsMenu
- CMFCTabCtrl [MFC], SetActiveInMDITabGroup
- CMFCTabCtrl [MFC], SetActiveTab
- CMFCTabCtrl [MFC], SetActiveTabBoldFont
- CMFCTabCtrl [MFC], SetDrawFrame
- CMFCTabCtrl [MFC], SetFlatFrame
- CMFCTabCtrl [MFC], SetImageList
- CMFCTabCtrl [MFC], SetResizeMode
- CMFCTabCtrl [MFC], SetTabMaxWidth
- CMFCTabCtrl [MFC], StopResize
- CMFCTabCtrl [MFC], SynchronizeScrollBar
- CMFCTabCtrl [MFC], m_bEnableActivate
ms.assetid: d441385d-2c72-4203-96fa-deae2273da35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad7a5331a2826df9dd6804e5c6a0f918bfeeb9d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmfctabctrl-class"></a>CMFCTabCtrl – třída
`CMFCTabCtrl` Třída poskytuje funkce pro ovládacího prvku karta. Ovládacího prvku karta zobrazí okno lze ukotvit ploché nebo trojrozměrné karty v její horní nebo dolní. Karet můžete zobrazit text a bitovou kopii a můžete změnit barvu, když je aktivní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCTabCtrl : public CMFCBaseTabCtrl  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCTabCtrl::CMFCTabCtrl`|Výchozí konstruktor.|  
|`CMFCTabCtrl::~CMFCTabCtrl`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCTabCtrl::ActivateMDITab](#activatemditab)|Zobrazí kartu zadaný aktuální ovládacího prvku karta a nastaví fokus na této kartě.|  
|[CMFCTabCtrl::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)||  
|[CMFCTabCtrl::AutoSizeWindow](#autosizewindow)|Určuje, zda rozhraní ke změně velikosti klientské oblasti všechny karty ovládacího prvku systému windows, když element uživatelského rozhraní ovládacího prvku karta změní.|  
|[CMFCTabCtrl::CalcRectEdit](#calcrectedit)|Snížení kapacity velikost oblast zadaný karty. (Přepisuje `CMFCBaseTabCtrl::CalcRectEdit`.)|  
|[CMFCTabCtrl::Create](#create)|Vytvoří ovládacího prvku karta a připojí jej k `CMFCTabCtrl` objektu.|  
|`CMFCTabCtrl::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|[CMFCTabCtrl::EnableActiveTabCloseButton](#enableactivetabclosebutton)|Zobrazí nebo skryje tlačítko Zavřít ( **X**) na kartě aktivní.|  
|[CMFCTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|Povolí nebo zakáže upravitelné kartě popisky. (Přepisuje [CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|  
|[CMFCTabCtrl::EnableTabDocumentsMenu](#enabletabdocumentsmenu)|Nahradí dvě tlačítka, která přejděte na okno karty s tlačítko, které se otevře nabídka záložkách windows.|  
|[CMFCTabCtrl::EnsureVisible](#ensurevisible)|Zajišťuje, že na kartě viditelné.|  
|[CMFCTabCtrl::GetDocumentIcon](#getdocumenticon)|Načte symbol, který je přidružen na kartě v místní nabídce záložkách Windows.|  
|[CMFCTabCtrl::GetFirstVisibleTabNum](#getfirstvisibletabnum)|Načte index první kartě, které se zobrazuje v aktuální ovládací prvek karty.|  
|[CMFCTabCtrl::GetResizeMode](#getresizemode)|Načte hodnotu, která určuje, jak jde změnit aktuální ovládací prvek karty.|  
|[CMFCTabCtrl::GetScrollBar](#getscrollbar)|Načte ukazatel na posuvníku panelu objekt, který je přidružen ovládacího prvku karta.|  
|[CMFCTabCtrl::GetTabArea](#gettabarea)|Načte ohraničující obdélník oblast popisek karty v horní nebo dolní části ovládacího prvku karta. (Přepisuje [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|  
|`CMFCTabCtrl::GetTabFromPoint`|Načte kartu, která obsahuje zadaný bod. (Přepisuje [CMFCBaseTabCtrl::GetTabFromPoint](../../mfc/reference/cmfcbasetabctrl-class.md#gettabfrompoint).)|  
|[CMFCTabCtrl::GetTabMaxWidth](#gettabmaxwidth)|Načte maximální šířka karty.|  
|[CMFCTabCtrl::GetTabsHeight](#gettabsheight)|Načte výšku oblasti karta aktuální ovládacího prvku karta.|  
|[CMFCTabCtrl::GetTabsRect](#gettabsrect)|Načte obdélníku bounds oblast karty aktuální ovládacího prvku karta. (Přepisuje [CMFCBaseTabCtrl::GetTabsRect](../../mfc/reference/cmfcbasetabctrl-class.md#gettabsrect).)|  
|`CMFCTabCtrl::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCTabCtrl::GetWndArea](#getwndarea)|Načte hranice klientské oblasti aktuální ovládací prvek karty.|  
|[CMFCTabCtrl::HideActiveWindowHorzScrollBar](#hideactivewindowhorzscrollbar)|Skryje vodorovného posuvníku, pokud existuje aktivní okno.|  
|[CMFCTabCtrl::HideInactiveWindow](#hideinactivewindow)|Určuje, zda rozhraní zobrazit neaktivní karta ovládací prvek windows.|  
|[CMFCTabCtrl::HideNoTabs](#hidenotabs)|Povolí nebo zakáže kreslení oblast karty, pokud nejsou žádné viditelné karty.|  
|[CMFCTabCtrl::HideSingleTab](#hidesingletab)|Povolí nebo zakáže kreslení na kartě, pokud je v jednom okně s kartami. (Přepisuje [CMFCBaseTabCtrl::HideSingleTab](../../mfc/reference/cmfcbasetabctrl-class.md#hidesingletab).)|  
|[CMFCTabCtrl::IsActiveInMDITabGroup](#isactiveinmditabgroup)|Určuje, zda je aktuální kartě ovládacího prvku karta kartě active ve skupině karta rozhraní více dokumentů.|  
|[CMFCTabCtrl::IsActiveTabBoldFont](#isactivetabboldfont)|Označuje, zda text kartě active zobrazuje pomocí tučným písmem.|  
|[CMFCTabCtrl::IsActiveTabCloseButton](#isactivetabclosebutton)|Určuje, zda tlačítko Zavřít ( **X**) se zobrazí na aktivní karty nebo pravém horním rohu oblast karty.|  
|[CMFCTabCtrl::IsDrawFrame](#isdrawframe)|Určuje, zda okno s kartami nevykresluje obdélníku rámce kolem embedded podokna.|  
|[CMFCTabCtrl::IsFlatFrame](#isflatframe)|Určuje, zda je rámečku kolem oblast karty ploché nebo 3D.|  
|[CMFCTabCtrl::IsFlatTab](#isflattab)|Určuje, zda je vzhled karty v aktuální ovládací prvek karty ploché nebo ne.|  
|[CMFCTabCtrl::IsLeftRightRounded](#isleftrightrounded)|Určuje, zda se zaokrouhlí vzhled levé a pravé straně karty v aktuální ovládací prvek karty.|  
|[CMFCTabCtrl::IsMDITabGroup](#ismditabgroup)|Určuje, zda je aktuální ovládací prvek karty obsažené v klientské oblasti okno rozhraní více dokumentů.|  
|[CMFCTabCtrl::IsOneNoteStyle](#isonenotestyle)|Označuje, zda aktuální ovládacího prvku karta je zobrazena v styl Microsoft OneNote.|  
|`CMFCTabCtrl::IsPtInTabArea`|Určuje, zda bod uvnitř oblasti karet. (Přepisuje [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|  
|[CMFCTabCtrl::IsSharedScroll](#issharedscroll)|Označuje, zda má aktuální ovládací prvek karty posuvník, která můžete posouvat jeho karty jako skupina.|  
|[CMFCTabCtrl::IsTabDocumentsMenu](#istabdocumentsmenu)|Určuje, zda se má zobrazit ovládacího prvku karta Posunutí tlačítek nebo tlačítko, které se zobrazí nabídka záložkách Windows.|  
|[CMFCTabCtrl::IsVS2005Style](#isvs2005style)|Určuje, zda se zobrazí ve stylu sady Visual Studio .NET 2005.|  
|[CMFCTabCtrl::ModifyTabStyle](#modifytabstyle)|Určuje vzhled karet v aktuální ovládací prvek karty.|  
|`CMFCTabCtrl::MoveTab`|Na kartě přesune na jinou pracovní pozici kartě. (Přepisuje [CMFCBaseTabCtrl::MoveTab](../../mfc/reference/cmfcbasetabctrl-class.md#movetab).)|  
|[CMFCTabCtrl::OnDragEnter](#ondragenter)|Voláno rámcem, když ukazatel je nejdřív přetažen okno ovládacího prvku karta.|  
|[CMFCTabCtrl::OnDragOver](#ondragover)|Voláno rámcem během operace přetažení po přesunutí myši cílové okno vyřaďte. (Přepisuje [CMFCBaseTabCtrl::OnDragOver](../../mfc/reference/cmfcbasetabctrl-class.md#ondragover).)|  
|[CMFCTabCtrl::OnShowTabDocumentsMenu](#onshowtabdocumentsmenu)|Zobrazí místní nabídky systému windows s kartami, počká, až uživatel vybere na kartě a díky vybraná karta aktivní karty.|  
|`CMFCTabCtrl::PreTranslateMessage`|Přeloží zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. (Přepisuje [CMFCBaseTabCtrl::PreTranslateMessage](../../mfc/reference/cmfcbasetabctrl-class.md#pretranslatemessage).)|  
|`CMFCTabCtrl::RecalcLayout`|Přepočítá rozložení interní ovládacího prvku karta. (Přepisuje [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|  
|[CMFCTabCtrl::SetActiveInMDITabGroup](#setactiveinmditabgroup)|Nastaví aktuální kartě ovládacího prvku karta jako aktivní karty ve skupině karta rozhraní více dokumentů.|  
|[CMFCTabCtrl::SetActiveTab](#setactivetab)|Aktivuje na kartě. (Přepisuje [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|  
|[CMFCTabCtrl::SetActiveTabBoldFont](#setactivetabboldfont)|Povolí nebo zakáže použití tučným písmem na aktivní karty.|  
|[CMFCTabCtrl::SetDrawFrame](#setdrawframe)|Povolí nebo zakáže drawinga rámce obdélníku kolem vloženého řádku.|  
|[CMFCTabCtrl::SetFlatFrame](#setflatframe)|Určuje, jestli se k vykreslení dvojrozměrném nebo 3D rámečku kolem oblast karty.|  
|[CMFCTabCtrl::SetImageList](#setimagelist)|Určuje seznamu obrázků. (Přepisuje [CMFCBaseTabCtrl::SetImageList](../../mfc/reference/cmfcbasetabctrl-class.md#setimagelist).)|  
|[CMFCTabCtrl::SetResizeMode](#setresizemode)|Určuje, jak jde změnit aktuální ovládací prvek karty a pak znovu zobrazí ovládací prvek.|  
|[CMFCTabCtrl::SetTabMaxWidth](#settabmaxwidth)|Určuje šířku maximální karta okno s kartami.|  
|[CMFCTabCtrl::StopResize](#stopresize)|Ukončí aktuální operace změny velikosti ovládacího prvku karta.|  
|`CMFCTabCtrl::SwapTabs`|Zamění pár karty. (Přepisuje [CMFCBaseTabCtrl::SwapTabs](../../mfc/reference/cmfcbasetabctrl-class.md#swaptabs).)|  
|[CMFCTabCtrl::SynchronizeScrollBar](#synchronizescrollbar)|Na ovládacím prvkem karta zobrazující ploché karty nevykresluje vodorovného posuvníku.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCTabCtrl::m_bEnableActivate](#m_benableactivate)|Zabrání ztrátě fokus, když je na nové kartě Vložit a povolený aktivního zobrazení.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCTabCtrl` Třídy podporuje:  
  
-   Kartě styly ovládacího prvku, které obsahují 3D, ploché a nestrukturované s sdílené vodorovného posuvníku.  
  
-   Karty v horní nebo dolní části okna.  
  
-   Karty, které zobrazují text, obrázky, nebo textu a obrázků.  
  
-   Karty, které změnit barvu, když na kartě je aktivní.  
  
-   Ohraničení změny velikosti pro měnitelné karty.  
  
-   Odpojitelných záložkách systému windows.  
  
 `CMFCTabCtrl` Třídu lze použít se dialogové okno, ale je určená pro aplikace, které používají ukotvení řídicím řádky jako [!INCLUDE[ofprexcel](../../mfc/reference/includes/ofprexcel_md.md)] a [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]. Další informace najdete v tématu [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).  
  
 Použijte následující postup přidání umožňující změnu velikosti, ukotvení ovládací prvek karty ve vaší aplikaci:  
  
1.  Vytvoření instance [CTabbedPane třída](../../mfc/reference/ctabbedpane-class.md).  
  
2.  Volání [CDockablePane::Create](../../mfc/reference/cdockablepane-class.md#create).  
  
3.  Použití [CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) nebo [CMFCBaseTabCtrl::InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) přidat nové karty.  
  
4.  Volání [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking) tak, aby aktuální ukotvení ovládacího prvku karta lze ukotvení v hlavním okně rámce.  
  
5.  Volání [CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane) na ukotvení v hlavním rámci záložkách okno.  
  
 Příklad vytvoření okno s kartami jako ukotvení ovládacích pruhů, naleznete v části [CTabbedPane třída](../../mfc/reference/ctabbedpane-class.md). Použít `CMFCTabCtrl` jako ovládací prvek ukotvení, vytvoření `CMFCTabCtrl` objektu a pak zavolají [CMFCTabCtrl::Create](#create).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCTabCtrl` třída ke konfiguraci `CMFCTabCtrl` objektu. Příklad vysvětluje, jak přidat na kartě, zobrazit na kartě aktivní tlačítko Zavřít, povolte upravitelné kartě popisky a zobrazit místní nabídky popisků okno s kartami. Tato ukázka je součástí [vzorek sběru stavu](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StateCollection#1](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection#3](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_2.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtabctrl.h  
  
##  <a name="activatemditab"></a>  CMFCTabCtrl::ActivateMDITab  
 Zobrazí kartu zadaný aktuální ovládacího prvku karta a nastaví fokus na této kartě.  
  
```  
void ActivateMDITab(int nTab = -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nTab`  
 Index založený na nule karty zobrazení nebo -1, aby zadejte kartu momentálně aktivní.  
  
##  <a name="allowdestroyemptytabbedpane"></a>  CMFCTabCtrl::AllowDestroyEmptyTabbedPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="autosizewindow"></a>  CMFCTabCtrl::AutoSizeWindow  
 Určuje, zda rozhraní ke změně velikosti klientské oblasti všechny karty ovládacího prvku systému windows, když element uživatelského rozhraní ovládacího prvku karta změní.  
  
```  
void AutoSizeWindow(BOOL bAutoSize = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bAutoSize`  
 `TRUE` Chcete-li automatická změna velikosti windows ovládacího prvku karta; v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="create"></a>  CMFCTabCtrl::Create  
 Vytvoří ovládacího prvku karta a připojí jej k `CMFCTabCtrl` objektu.  
  
```  
BOOL Create(
    Style style,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    Location location=LOCATION_BOTTOM,  
    BOOL bCloseBtn=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `style`  
 Styl ovládacího prvku karta. Další informace najdete v části poznámky.  
  
 [v] `rect`  
 Obdélníku, která bounds ovládacího prvku karta.  
  
 [v] `pParentWnd`  
 Ukazatel do nadřazeného okna. Nesmí být `NULL`.  
  
 [v] `nID`  
 ID ovládacího prvku karta.  
  
 [v] `location`  
 Umístění karty. Výchozí hodnota je `LOCATION_BOTTOM`. Další informace najdete v části poznámky.  
  
 [v] `bCloseBtn`  
 `TRUE` Chcete-li zobrazit tlačítko Zavřít na kartě. v opačném `FALSE`. Výchozí hodnota je `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` v případě úspěšného; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Následující tabulka popisuje hodnoty, můžete zadat pro `style` parametr.  
  
|Styl|Popis|  
|-----------|-----------------|  
|STYLE_3D|Vytvoří ovládacího prvku karta aplikaci.|  
|STYLE_FLAT|Vytvoří ovládacího prvku karta ploché karty.|  
|STYLE_FLAT_SHARED_HORZ_SCROLL|Vytvoří ovládacího prvku karta s plochým karty a posuvník, který může měnit karty, pokud jsou oříznut podle nadřazeného okna.|  
|STYLE_3D_ONENOTE|Vytvoří ovládacího prvku karta ve stylu Microsoft OneNote.|  
|STYLE_3D_VS2005|Vytvoří ovládacího prvku karta ve stylu sady Microsoft Visual Studio 2005.|  
|STYLE_3D_ROUNDED|Vytvoří ovládacího prvku karta zaokrouhlené karty ve stylu sady Microsoft Visual Studio 2005.|  
|STYLE_3D_ROUNDED_SCROLL|Vytvoří ovládacího prvku karta s zaokrouhlené karty a posunutí tlačítek ve stylu sady Microsoft Visual Studio 2005.|  
  
 V následující tabulce jsou uvedeny hodnoty, můžete zadat pro `location` parametr.  
  
|Umístění|Popis|  
|--------------|-----------------|  
|LOCATION_BOTTOM|Karty jsou umístěné v dolní části ovládacího prvku karta.|  
|LOCATION_TOP|Karty jsou umístěné v horní části ovládacího prvku karta.|  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `Create` metoda v `CMFCTabCtrl` třídy. Tato ukázka je součástí [vzorek sběru stavu](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StateCollection#1](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection#2](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_3.cpp)]  
  
##  <a name="calcrectedit"></a>  CMFCTabCtrl::CalcRectEdit  
 Snížení kapacity velikost oblast zadaný karty.  
  
```  
virtual void CalcRectEdit(CRect& rectEdit);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `rectEdit`  
 Obdélníku, která určuje oblasti karty.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, když změníte popisek karty. Tato metoda snížení kapacity levé a pravé straně určeného obdélníku podle půl aktuální výška karty a snížení kapacity horní a dolní o jednu jednotku.  
  
##  <a name="enableactivetabclosebutton"></a>  CMFCTabCtrl::EnableActiveTabCloseButton  
 Zobrazí nebo skryje tlačítko Zavřít ( **X**) na kartě aktivní.  
  
```  
void EnableActiveTabCloseButton(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bEnable`  
 `TRUE` Chcete-li zobrazit tlačítko Zavřít na kartě active; `FALSE` zobrazíte tlačítko Zavřít v pravém horním rohu oblast karty. Výchozí hodnota je `TRUE`.  
  
##  <a name="enableinplaceedit"></a>  CMFCTabCtrl::EnableInPlaceEdit  
 Povolí nebo zakáže upravitelné kartě popisky.  
  
```  
virtual void EnableInPlaceEdit(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bEnable`  
 `TRUE` Chcete-li povolit upravovat kartě popisky; `FALSE` zakázat upravitelné kartě popisky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enabletabdocumentsmenu"></a>  CMFCTabCtrl::EnableTabDocumentsMenu  
 Přepne mezi uživatelské rozhraní, které používá dvě tlačítka posouvání okno karty a rozhraní, které se zobrazí místní nabídka záložkách Windows.  
  
```  
void EnableTabDocumentsMenu(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bEnable`  
 `TRUE` Chcete-li zobrazit místní nabídky popisků okno s kartami; `FALSE` zobrazíte Posunutí vpřed a zpět tlačítek. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Po kliknutí na kartu štítek, rozhraní zobrazí odpovídající okno s kartami. Pokud popisek karty je viditelná, je otevřít okno s kartami beze změny jeho umístění. Pokud uživatel vybere dokumentu z místní nabídky a odpovídající okno s kartami vypnuté obrazovky, okno s kartami se změní na první kartě.  
  
##  <a name="ensurevisible"></a>  CMFCTabCtrl::EnsureVisible  
 Zajišťuje, že na kartě viditelné.  
  
```  
virtual BOOL EnsureVisible(int iTab);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iTab`  
 Index založený na nule karty.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud neproběhne úspěšně; `FALSE` Pokud `iTab` parametr index není platný.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, chcete-li zaručit, že zadaný karta je zobrazena. Ovládací prvek karty se posuňte se v případě potřeby.  
  
##  <a name="getdocumenticon"></a>  CMFCTabCtrl::GetDocumentIcon  
 Načte bitovou kopii, která souvisí s na kartě v místní nabídce záložkách Windows.  
  
```  
static HICON __stdcall GetDocumentIcon(UINT nCmdID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nCmdID`  
 ID příkazu karty v místní nabídce záložkách Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač rastrového obrázku.  
  
##  <a name="getfirstvisibletabnum"></a>  CMFCTabCtrl::GetFirstVisibleTabNum  
 Načte index první kartě, které se zobrazuje v aktuální ovládací prvek karty.  
  
```  
virtual int GetFirstVisibleTabNum() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule karty v ovládacího prvku karta.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, jenom v případě, že ovládacího prvku karta se zobrazí ve stylu Microsoft OneNote. Použití [CMFCTabCtrl::IsOneNoteStyle](#isonenotestyle) metoda k určení stylu.  
  
##  <a name="getresizemode"></a>  CMFCTabCtrl::GetResizeMode  
 Načte hodnotu, která určuje, jak jde změnit aktuální ovládací prvek karty.  
  
```  
ResizeMode GetResizeMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden z `CMFCTabCtrl::ResizeMode` hodnot výčtu, která určuje, jak jde změnit, ovládacího prvku karta. Seznamu možných hodnot, najdete v části poznámky [CMFCTabCtrl::SetResizeMode](#setresizemode) metoda.  
  
##  <a name="getscrollbar"></a>  CMFCTabCtrl::GetScrollBar  
 Načte ukazatel na posuvníku panelu objekt, který je přidružen ovládacího prvku karta.  
  
```  
CScrollBar* GetScrollBar();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A ukazatele na objekt scrollbar nebo `NULL` Pokud ovládacího prvku karta nebyla vytvořena pomocí `STYLE_FLAT_SHARED_HORZ_SCROLL` stylu.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte pro přístup k ovládacího prvku karta vložená posuvníku. Jenom v případě, že má ovládacího prvku karta je vytvořen objekt panelu přejděte `STYLE_FLAT_SHARED_HORZ_SCROLL` stylu.  
  
##  <a name="gettabarea"></a>  CMFCTabCtrl::GetTabArea  
 Načte ohraničující obdélník oblast popisek karty v horní nebo dolní části ovládacího prvku karta.  
  
```  
void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `rectTabAreaTop`  
 Po návratu tato metoda obsahuje odkaz na tento obdélníku bounds oblast popisek nejvyšší karty. Rámeček je v souřadnicích klienta. Tento odkaz je prázdný, pokud neexistuje žádné oblast popisek karty v horní části ovládacího prvku karta.  
  
 [out] `rectTabAreaBottom`  
 Po návratu tato metoda obsahuje odkaz na tento obdélníku bounds dolní oblast popisek karty. Rámeček je v souřadnicích klienta. Tento odkaz je prázdný, pokud žádné oblast popisek karty existuje v dolní části ovládacího prvku karta.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k určení velikosti a pozice oblast karty v okně s kartami.  
  
##  <a name="gettabmaxwidth"></a>  CMFCTabCtrl::GetTabMaxWidth  
 Načte maximální šířka karty.  
  
```  
int GetTabMaxWidth() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální šířka karty, v pixelech. Pokud návratovou hodnotu 0, neomezená šířka karty.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCTabCtrl::SetTabMaxWidth](#settabmaxwidth) metodu a nastavit maximální karta šířku.  
  
##  <a name="gettabsheight"></a>  CMFCTabCtrl::GetTabsHeight  
 Načte výšku oblasti karta aktuální ovládacího prvku karta.  
  
```  
virtual int GetTabsHeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška oblast karty, pokud žádné karta je zobrazena nebo nula v případě žádné karta je viditelné.  
  
##  <a name="gettabsrect"></a>  CMFCTabCtrl::GetTabsRect  
 Načte obdélníku bounds oblast karty aktuální ovládacího prvku karta.  
  
```  
virtual void GetTabsRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `rect`  
 Po návratu tato metoda `rect` parametr obsahuje obdélníku bounds oblast karty.  
  
##  <a name="getwndarea"></a>  CMFCTabCtrl::GetWndArea  
 Načte hranice klientské oblasti aktuální ovládací prvek karty.  
  
```  
void GetWndArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [ve out] `rect`  
 Po návratu tato metoda tento parametr obsahuje obdélníku bounds aktuální ovládací prvek karty.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hideactivewindowhorzscrollbar"></a>  CMFCTabCtrl::HideActiveWindowHorzScrollBar  
 Skryje vodorovného posuvníku, pokud existuje, v okně aktivní.  
  
```  
void HideActiveWindowHorzScrollBar();
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, pokud chcete zabránit blikat, když uživatel přepíná mezi stránkami ovládacího prvku karta ovládacího prvku karta.  
  
##  <a name="hideinactivewindow"></a>  CMFCTabCtrl::HideInactiveWindow  
 Určuje, zda se má zobrazit rozhraní neaktivní karta ovládacího prvku windows.  
  
```  
void HideInactiveWindow(BOOL bHide = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bHide`  
 `TRUE` aby se zobrazí okno s neaktivní; `FALSE` zobrazit okno s neaktivní. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hidenotabs"></a>  CMFCTabCtrl::HideNoTabs  
 Povolí nebo zakáže kreslení oblasti kartě, pokud nejsou žádné viditelné karty.  
  
```  
void HideNoTabs(BOOL bHide=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bHide`  
 `TRUE` Chcete-li povolit kreslení oblast karty; `FALSE` zakázat kreslení. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hidesingletab"></a>  CMFCTabCtrl::HideSingleTab  
 Povolí nebo zakáže kreslení kartě, pokud je v jednom okně s kartami.  
  
```  
virtual void HideSingleTab(BOOL bHide=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bHide`  
 `TRUE` není kreslení na kartě pro jeden okno s kartami; `FALSE` kreslení jedné karty. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isactiveinmditabgroup"></a>  CMFCTabCtrl::IsActiveInMDITabGroup  
 Určuje, zda je aktuální kartě ovládacího prvku karta kartě active ve skupině karta rozhraní více dokumentů.  
  
```  
BOOL IsActiveInMDITabGroup() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je aktivní karty ve skupině karta MDI; aktuální karta ovládacího prvku karta v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Můžete uspořádat více oken dokumentu do skupin buď svislé nebo vodorovné kartě a snadno náhodně dokumenty z jedné karty skupiny do jiného.  
  
##  <a name="isactivetabboldfont"></a>  CMFCTabCtrl::IsActiveTabBoldFont  
 Označuje, zda text kartě active zobrazuje pomocí tučným písmem.  
  
```  
BOOL IsActiveTabBoldFont() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud aktivní karty se zobrazí pomocí tučným písmem; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCTabCtrl::SetActiveTabBoldFont](#setactivetabboldfont) metoda Změna písma aktivní karty.  
  
##  <a name="isactivetabclosebutton"></a>  CMFCTabCtrl::IsActiveTabCloseButton  
 Určuje, zda tlačítko Zavřít ( **X**) se zobrazí na aktivní kartu nebo v pravém horním rohu oblast karty.  
  
```  
virtual BOOL IsActiveTabCloseButton() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se zobrazí tlačítko Zavřít na kartě active; `FALSE` Pokud v pravém horním rohu oblasti karet se zobrazí tlačítko Zavřít.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isdrawframe"></a>  CMFCTabCtrl::IsDrawFrame  
 Určuje, zda okno s kartami nevykresluje obdélníku rámce kolem embedded podokna.  
  
```  
BOOL IsDrawFrame() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se nevykreslí obdélníku rámce; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCTabCtrl::SetDrawFrame](#setdrawframe) metoda k povolení nebo zakázání kreslení obdélníků rámce.  
  
##  <a name="isflatframe"></a>  CMFCTabCtrl::IsFlatFrame  
 Určuje, zda je rámečku kolem oblast karty ploché nebo 3D.  
  
```  
BOOL IsFlatFrame() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je rámeček kolem oblast karty ploché; `FALSE` Pokud trojrozměrné rámečku.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCTabCtrl::SetFlatFrame](#setflatframe) metoda změnit, jakým způsobem se vykresluje rámečku.  
  
##  <a name="isflattab"></a>  CMFCTabCtrl::IsFlatTab  
 Určuje, zda je vzhled karty v aktuální ovládací prvek karty ploché nebo ne.  
  
```  
virtual BOOL IsFlatTab() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je plochý; vzhled karty v aktuální ovládacího prvku karta v opačném `FALSE`.  
  
##  <a name="isleftrightrounded"></a>  CMFCTabCtrl::IsLeftRightRounded  
 Určuje, zda se zaokrouhlí vzhled levé a pravé straně karty v aktuální ovládací prvek karty.  
  
```  
virtual BOOL IsLeftRightRounded() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se zaokrouhlí postranní každé kartě; v opačném `FALSE`.  
  
##  <a name="ismditabgroup"></a>  CMFCTabCtrl::IsMDITabGroup  
 Určuje, zda je aktuální ovládací prvek karty obsažené v klientské oblasti okno rozhraní více dokumentů.  
  
```  
virtual BOOL IsMDITabGroup() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je aktuální ovládací prvek karty v oblasti okna MDI klienta; v opačném `FALSE`.  
  
##  <a name="isonenotestyle"></a>  CMFCTabCtrl::IsOneNoteStyle  
 Označuje, zda aktuální ovládacího prvku karta je zobrazena v styl Microsoft OneNote.  
  
```  
virtual BOOL IsOneNoteStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud ovládacího prvku karta se zobrazí ve stylu Microsoft OneNote; v opačném `FALSE`.  
  
##  <a name="issharedscroll"></a>  CMFCTabCtrl::IsSharedScroll  
 Označuje, zda má aktuální ovládací prvek karty posuvník, která můžete posouvat jeho karty jako skupina.  
  
```  
BOOL IsSharedScroll() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud má sdílené posuvníku; ovládacího prvku karta v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu `TRUE` Pokud `style` parametr [CMFCTabCtrl::Create](#create) STYLE_FLAT_SHARED_HORZ_SCROLL je metoda.  
  
##  <a name="istabdocumentsmenu"></a>  CMFCTabCtrl::IsTabDocumentsMenu  
 Určuje, zda se má zobrazit ovládacího prvku karta Posunutí tlačítek nebo tlačítko, které se zobrazí nabídka záložkách Windows.  
  
```  
BOOL IsTabDocumentsMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud přešla oblasti s kartami windows pomocí místní nabídky popisků okno s kartami; `FALSE` Pokud přešla oblasti s kartami windows pomocí tlačítka dopředu a dozadu posuvníku.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCTabCtrl::EnableTabDocumentsMenu](#enabletabdocumentsmenu) metody určíte metodu posouvání – záložkami systému windows.  
  
##  <a name="isvs2005style"></a>  CMFCTabCtrl::IsVS2005Style  
 Určuje, zda jsou vykreslovány karty pomocí styl sady Visual Studio 2005.  
  
```  
virtual BOOL IsVS2005Style() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud karty jsou vykreslovány pomocí styl sady Visual Studio 2005; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Použití `style` parametr [CMFCTabCtrl::Create](#create) metoda k určení, jak jsou vykreslovány karty.  
  
##  <a name="m_benableactivate"></a>  CMFCTabCtrl::m_bEnableActivate  
 Zabrání ztrátě fokus, když je na nové kartě Vložit a povolený aktivního zobrazení.  
  
```  
static BOOL m_bEnableActivate;  
```  
  
### <a name="remarks"></a>Poznámky  
 Zaměřuje se obvykle provedenou nové okno s kartami, pokud je na kartě Vložit a aktivní. Nastavte `CMFCTabCtrl::m_bEnableActivate` členské proměnné na `FALSE` chcete zachovat původní fokus. Výchozí hodnota je `TRUE`.  
  
##  <a name="modifytabstyle"></a>  CMFCTabCtrl::ModifyTabStyle  
 Určuje vzhled karet v aktuální ovládací prvek karty.  
  
```  
BOOL ModifyTabStyle(Style style);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `style`  
 Jedna z hodnot výčtu, která určuje vzhled ovládacího prvku karta. Další informace najdete v tabulce v poznámky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota `style` parametr může být jedna z následujících `CMFCTabCtrl::Style` výčty.  
  
|Název|Popis|  
|----------|-----------------|  
|STYLE_3D|Zobrazí trojrozměrné, obdélníková karty se.|  
|STYLE_3D_ONENOTE|Zobrazí trojrozměrné karty, které mají zaokrouhlené rozích, které mají jeden svislé straně a na jedné straně zkosený symbol.|  
|STYLE_3D_ROUNDED|Zobrazí trojrozměrné karty, které zkoseným stranách a zaokrouhlené rozích.|  
|STYLE_3D_ROUNDED_SCROLL|Zobrazí trojrozměrné karty, které zkoseným stranách a zaokrouhlené rozích. Pokud existují další karty, než lze zobrazit ve stejnou dobu, rozhraní se zobrazí šipku rozevíracího seznamu a nabídky karty na aktivní.|  
|STYLE_3D_SCROLLED|Zobrazí trojrozměrné, obdélníková karty. Pokud existují další karty, než lze zobrazit ve stejnou dobu, rozhraní se zobrazí šipku rozevíracího seznamu a nabídky karty na aktivní.|  
|STYLE_3D_VS2005|Zobrazí trojrozměrné, zaoblenými karty, které mají jeden zkosené straně a na jedné straně svislé.|  
|STYLE_FLAT|Zobrazí dvourozměrná karty, které mají zkoseným levé a pravé straně.|  
|STYLE_FLAT_SHARED_HORZ_SCROLL|Zobrazí dvourozměrná karty. Pokud existují další karty, než lze zobrazit ve stejnou dobu, zobrazí rozhraní posouvacích šipek na koncích oblast karty.|  
  
##  <a name="ondragenter"></a>  CMFCTabCtrl::OnDragEnter  
 Voláno rámcem během operace přetažení myší Když kurzor nejprve zadá okno aktuální ovládací prvek karty.  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDataObject`  
 Bodů na datový objekt, který obsahuje data, která uživatel nastavuje tažením.  
  
 [v] `dwKeyState`  
 Obsahuje stav modifikační klávesy. Tento parametr je bitová kombinace (nebo) z následujících hodnot: `MK_CONTROL`, `MK_SHIFT`, `MK_ALT`, `MK_LBUTTON`, `MK_MBUTTON`, a `MK_RBUTTON`. Další informace najdete v tématu **zpráva parametry** části [o vstup z myši](http://msdn.microsoft.com/library/windows/desktop/ms645601).  
  
 [v] `point`  
 Obsahuje aktuální umístění kurzoru v souřadnice klienta.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `DROPEFFECT_NONE`, což znamená, že cíle přetažení nemůže přijímat data.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte pro podporu operaci přetažení myší. Potlačí tuto metodu implementovat vlastní vlastní chování.  
  
 Ve výchozím nastavení, tato metoda pouze volá `CMFCTabCtrl::OnDragOver`, které vždy vrátí hodnotu `DROPEFFECT_NONE`.  
  
##  <a name="ondragover"></a>  CMFCTabCtrl::OnDragOver  
 Voláno rámcem během operace přetažení po přesunutí myši cílové okno vyřaďte.  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDataObject`  
 Ukazatel na [COleDataObject](../../mfc/reference/coledataobject-class.md) objekt, který je právě přetáhli přes cíle přetažení.  
  
 [v] `dwKeyState`  
 Stav systému modifikační klávesy, které je bitová kombinace (nebo) z `MK_CONTROL`, `MK_SHIFT`, `MK_ALT`, `MK_LBUTTON`, `MK_MBUTTON`, a `MK_RBUTTON`. Další informace najdete v tématu "Parametry zpráva" v [o vstup z myši](http://msdn.microsoft.com/library/windows/desktop/ms645601).  
  
 [v] `point`  
 Aktuální umístění myši.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `DROPEFFECT_NONE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu s vlastní implementaci. Další informace najdete v tématu [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover) metoda.  
  
##  <a name="onshowtabdocumentsmenu"></a>  CMFCTabCtrl::OnShowTabDocumentsMenu  
 Zobrazí místní nabídky systému windows s kartami, počká, až uživatel vybere na kartě a díky vybraná karta aktivní karty.  
  
```  
virtual void OnShowTabDocumentsMenu(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Souřadnice místa zobrazení v místní nabídce.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setactiveinmditabgroup"></a>  CMFCTabCtrl::SetActiveInMDITabGroup  
 Nastaví aktuální kartě ovládacího prvku karta jako aktivní karty ve skupině karta rozhraní více dokumentů.  
  
```  
void SetActiveInMDITabGroup(BOOL bActive);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bActive`  
 `TRUE` Chcete-li aktuální karta kartě active; `FALSE` aby aktuální karta neaktivní.  
  
### <a name="remarks"></a>Poznámky  
 Můžete uspořádat více oken dokumentu do skupin buď svislé nebo vodorovné kartě a snadno náhodně dokumenty z jedné karty skupiny do jiného.  
  
##  <a name="setactivetab"></a>  CMFCTabCtrl::SetActiveTab  
 Aktivuje na kartě.  
  
```  
virtual BOOL SetActiveTab(int iTab);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iTab`  
 Určuje index založený na nule karty aktivovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se zadaný karta byla aktivní; `FALSE` Pokud zadaný `iTab` hodnota parametru je neplatná.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda neodešle `AFX_WM_CHANGE_ACTIVE_TAB` oznámení do nadřazeného okna ovládacího prvku karta.  
  
 `SetActiveTab` Metoda automaticky volá [CMFCTabCtrl::HideActiveWindowHorzScrollBar](#hideactivewindowhorzscrollbar) metoda zabránit blikat na obrazovce.  
  
##  <a name="setactivetabboldfont"></a>  CMFCTabCtrl::SetActiveTabBoldFont  
 Povolí nebo zakáže použití tučným písmem na aktivní karty.  
  
```  
void SetActiveTabBoldFont(BOOL bIsBold=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bIsBold`  
 `TRUE` použití tučné písmo pro zobrazení popisek kartě active; `FALSE` používat standardní písmo zobrazíte popisek. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setdrawframe"></a>  CMFCTabCtrl::SetDrawFrame  
 Určuje, zda obdélníku rámce vykreslením kolem vloženého řádku.  
  
```  
void SetDrawFrame(BOOL bDraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bDraw`  
 `TRUE` Chcete-li zobrazit rámce obdélníku kolem vložený řádek. v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setflatframe"></a>  CMFCTabCtrl::SetFlatFrame  
 Určuje, jestli se k vykreslení dvojrozměrném nebo 3D rámečku kolem oblast karty.  
  
```  
void SetFlatFrame(
    BOOL bFlat=TRUE,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bFlat`  
 `TRUE` Kreslení rámce dvojrozměrném (2D) kolem oblast karty; `FALSE` k vykreslení trojrozměrné rámce (3D). Výchozí hodnota je `TRUE`.  
  
 [v] `bRepaint`  
 `TRUE` Chcete-li ho překreslit okno okamžitě; v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setimagelist"></a>  CMFCTabCtrl::SetImageList  
 Určuje seznamu obrázků.  
  
```  
virtual BOOL SetImageList(
    UINT uiID,  
    int cx=15,  
    COLORREF clrTransp=RGB(255, 0, 255));  
  
virtual BOOL SetImageList(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiID`  
 ID prostředku bitové mapy, který obsahuje seznam obrázků.  
  
 [v] `cx`  
 Šířka každého obrázku v pixelech. Výchozí hodnota je 15.  
  
 [v] `clrTransp`  
 Barva průhledný obrázek. Části bitové kopie, které jsou tato barva bude průhledná. Výchozí hodnota je purpurová barva, RGB(255,0,255).  
  
 [v] `hImageList`  
 Popisovač pro seznam předem načtené bitové kopie.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda je úspěšné. `FALSE` Pokud ovládacího prvku karta je vytvořená pomocí ploché styl nebo pokud první přetížení metody nelze načíst rastrového obrázku, která je zadána `uiID` parametr.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k nastavení seznamu obrázků pro ovládací prvek karty. Bitové kopie ze seznamu obrázků jsou zobrazeny vedle popisek karty. Tato metoda přepočítá výška karty tak, aby na kartě je velikost tak, aby obsahovala bitové kopie a text.  
  
 Použití [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) metoda, která zdědí ovládacího prvku karta určete index bitové kopie k zobrazení.  
  
##  <a name="setresizemode"></a>  CMFCTabCtrl::SetResizeMode  
 Určuje, jak jde změnit aktuální ovládací prvek karty a pak znovu zobrazí ovládací prvek.  
  
```  
void SetResizeMode(ResizeMode resizeMode);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `resizeMode`  
 Jeden z `CMFCTabCtrl::ResizeMode` hodnot výčtu, která určuje, jak jde změnit, ovládacího prvku karta. Seznam možných hodnot najdete v tabulce v poznámky.  
  
### <a name="remarks"></a>Poznámky  
 `resizeMode` Parametr může být jedna z následujících `ResizeMode` hodnot výčtu.  
  
|Název|Popis|  
|----------|-----------------|  
|RESIZE_NO|Velikost ovládacího prvku karta nelze změnit.|  
|RESIZE_VERT|Velikost ovládacího prvku karta lze změnit, svisle, ale ne vodorovně.|  
|RESIZE_HORIZ|Velikost ovládacího prvku karta lze změnit, vodorovně, ale není svisle.|  
  
##  <a name="settabmaxwidth"></a>  CMFCTabCtrl::SetTabMaxWidth  
 Určuje šířku maximální karta okno s kartami.  
  
```  
void SetTabMaxWidth(int nTabMaxWidth);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nTabMaxWidth`  
 Karta maximální šířku v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, chcete-li omezit šířku každé kartě okno s kartami. Tato metoda je užitečná, pokud máte hodně dlouhém popisky karty. [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md) třída – konstruktor inicializuje maximální karta šířku 0, která ve skutečnosti znamená, že šířka není omezen.  
  
##  <a name="stopresize"></a>  CMFCTabCtrl::StopResize  
 Ukončí aktuální operace změny velikosti ovládacího prvku karta.  
  
```  
void StopResize(BOOL bCancel);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bCancel`  
 `TRUE` ukončil aktuální operace změny velikosti; `FALSE` k dokončení resize aktuální operaci. V obou případech rozhraní zastaví kreslení obdélníku změny velikosti.  
  
##  <a name="synchronizescrollbar"></a>  CMFCTabCtrl::SynchronizeScrollBar  
 Na ovládacím prvkem karta zobrazující ploché karty nevykresluje vodorovného posuvníku.  
  
```  
BOOL SynchronizeScrollBar(SCROLLINFO* pScrollInfo = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [out] `pScrollInfo`  
 Ukazatel na [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) struktura nebo `NULL`. Když tato metoda vrátí a pokud tento parametr není `NULL`, struktura obsahuje všechny parametry posuvníku. Výchozí hodnota je `NULL`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda bude úspěšná; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda ovlivňuje pouze ovládacího prvku Karta zobrazující ploché karty. Posuvník ovlivňuje všechny karty ve stejnou dobu.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)   
 [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)   
 [CMFCBaseTabCtrl – třída](../../mfc/reference/cmfcbasetabctrl-class.md)
