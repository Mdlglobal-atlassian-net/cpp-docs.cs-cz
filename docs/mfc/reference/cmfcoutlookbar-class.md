---
title: Třída CMFCOutlookBar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar::AllowDestroyEmptyTabbedPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanAcceptPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanSetCaptionTextToTabName
- AFXOUTLOOKBAR/CMFCOutlookBar::Create
- AFXOUTLOOKBAR/CMFCOutlookBar::CreateCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::DoesAllowDynInsertBefore
- AFXOUTLOOKBAR/CMFCOutlookBar::FloatTab
- AFXOUTLOOKBAR/CMFCOutlookBar::GetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::GetTabArea
- AFXOUTLOOKBAR/CMFCOutlookBar::IsMode2003
- AFXOUTLOOKBAR/CMFCOutlookBar::OnAfterAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnBeforeAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnScroll
- AFXOUTLOOKBAR/CMFCOutlookBar::RemoveCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::SetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::SetMode2003
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBar [MFC], AllowDestroyEmptyTabbedPane
- CMFCOutlookBar [MFC], CanAcceptPane
- CMFCOutlookBar [MFC], CanSetCaptionTextToTabName
- CMFCOutlookBar [MFC], Create
- CMFCOutlookBar [MFC], CreateCustomPage
- CMFCOutlookBar [MFC], DoesAllowDynInsertBefore
- CMFCOutlookBar [MFC], FloatTab
- CMFCOutlookBar [MFC], GetButtonsFont
- CMFCOutlookBar [MFC], GetTabArea
- CMFCOutlookBar [MFC], IsMode2003
- CMFCOutlookBar [MFC], OnAfterAnimation
- CMFCOutlookBar [MFC], OnBeforeAnimation
- CMFCOutlookBar [MFC], OnScroll
- CMFCOutlookBar [MFC], RemoveCustomPage
- CMFCOutlookBar [MFC], SetButtonsFont
- CMFCOutlookBar [MFC], SetMode2003
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5640f634276f87d0a41633354a7dde0ed65a2940
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar – třída
Podokno s kartami s vzhled **navigačním podokně** v aplikaci Microsoft Outlook 2000 nebo 2003 aplikace Outlook. `CMFCOutlookBar` Objekt obsahuje [CMFCOutlookBarTabCtrl třída](../../mfc/reference/cmfcoutlookbartabctrl-class.md) objekt a řadu karty. Karty může být buď [CMFCOutlookBarPane třída](../../mfc/reference/cmfcoutlookbarpane-class.md) objekty nebo `CWnd`-odvozené objekty. Pro uživatele se zobrazí na panelu aplikace Outlook jako řadu tlačítek a zobrazení oblasti. Když uživatel klikne na tlačítko, se zobrazí tlačítko podokna nebo odpovídající ovládacího prvku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCOutlookBar : public CBaseTabbedPane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCOutlookBar::CMFCOutlookBar`|Výchozí konstruktor.|  
|`CMFCOutlookBar::~CMFCOutlookBar`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Určuje, zda může být zničený záložkách podokně aplikace prázdný. (Přepisuje [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|  
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Určuje, zda lze ukotvit jiného podokna do podokna panelu aplikace Outlook. (Přepisuje CDockablePane::CanAcceptPane.)|  
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Určuje, zda titulek pro záložkách podokně zobrazí stejný text jako aktivní karty. (Přepisuje [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|  
|[CMFCOutlookBar::Create](#create)|Vytvoří ovládací prvek panelu aplikace Outlook.|  
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|Vytvoří vlastní karty panelu aplikace Outlook.|  
|`CMFCOutlookBar::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Určuje, jestli uživatel může ukotvení ovládacích pruhů na vnější hranici panelu aplikace Outlook.|  
|[CMFCOutlookBar::FloatTab](#floattab)|Obtéká podokno, ale pouze, pokud se v podokně se aktuálně nachází v odpojitelných kartě. (Přepisuje [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|  
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Vrací písmo textu tlačítek panelu aplikace Outlook.|  
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Vrátí velikost a umístění oblasti karty na panelu aplikace Outlook. (Přepisuje [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|  
|`CMFCOutlookBar::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Určuje, zda napodobuje chování panelu aplikace Outlook, aplikaci Microsoft Office Outlook 2003 (viz poznámky).|  
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Voláno rozhraním [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) po kartě active byla nastavena pomocí animace.|  
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Voláno rozhraním [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) před na kartě stránky nastavená jako aktivní karty pomocí animace.|  
|[CMFCOutlookBar::OnScroll](#onscroll)|Voláno rámcem, pokud je na panelu aplikace Outlook posouvání nahoru nebo dolů.|  
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|Odebere vlastní karty panelu aplikace Outlook.|  
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Nastaví písmo textu tlačítka panelu aplikace Outlook.|  
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Určuje, zda napodobuje chování panelu aplikace Outlook, aplikace Outlook 2003 (viz poznámky).|  
  
## <a name="remarks"></a>Poznámky  
 Příklad panel aplikace Outlook, naleznete v části [OutlookDemo ukázka: aplikace knihovny MFC OutlookDemo](../../visual-cpp-samples.md).  
  
## <a name="implementing-the-outlook-bar"></a>Implementace panelu aplikace Outlook  
 Použít `CMFCOutlookBar` řízení ve vaší aplikaci, postupujte takto:  
  
1.  Vložení `CMFCOutlookBar` objekt do třídy hlavního rámce okna.  
  
 ```  
    class CMainFrame : public CMDIFrameWnd  
 { ...  
    CMFCOutlookBar m_wndOutlookBar;  
    CMFCOutlookBarPane m_wndOutlookPane;  
 ... };  
 ```  
2.  Při zpracování `WM_CREATE` zprávy v hlavního rámce, volání [CMFCOutlookBar::Create](#create) metodu pro vytvoření aplikace Outlook panelu Ovládací prvek karty.  
  
 ```  
    m_wndOutlookBar.Create (_T("Shortcuts"),
    this,
    CRect (0,
    0,
    100,
    100),
    ID_VIEW_OUTLOOKBAR,
    WS_CHILD | WS_VISIBLE | CBRS_LEFT);

 ```  
3.  Získání ukazatele na základní `CMFCOutlookBarTabCtrl` pomocí [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).  
  
 ```  
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();

 ```  
4.  Vytvoření [CMFCOutlookBarPane třída](../../mfc/reference/cmfcoutlookbarpane-class.md) objekt pro každou kartu, která obsahuje tlačítka.  
  
 ```  
    m_wndOutlookPane.Create (&m_wndOutlookBar,
    AFX_DEFAULT_TOOLBAR_STYLE,
    ID_OUTLOOK_PANE_GENERAL,
    AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);
*// make the Outlook pane detachable (enable docking)  
    m_wndOutlookPane.EnableDocking (CBRS_ALIGN_ANY);
*// add buttons  
    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_MAINFRAME), "About",
    ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON), "Open",
    ID_FILE_OPEN);

 ```  
5.  Volání [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) přidat každou novou kartu. Nastavte `bDetachable` parametru `FALSE` aby bez odpojitelných stránky. Nebo použijte [CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) přidat odpojitelných stránky.  
  
 ```  
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1,
    TRUE);

 ```  
6.  Chcete-li přidat `CWnd`-odvozené ovládací prvek (například [CMFCShellTreeCtrl třída](../../mfc/reference/cmfcshelltreectrl-class.md)) jako na kartě vytvoření ovládacího prvku a volání [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) tím ho přidáte do panelu aplikace Outlook.  
  
> [!NOTE]
>  Měli byste použít řízení jedinečné identifikátory pro každý [CMFCOutlookBarPane – třída](../../mfc/reference/cmfcoutlookbarpane-class.md) objektu a pro každou `CWnd`-odvozené objektu.  
  
 Chcete-li dynamicky přidat nebo odstranit nových stránek za běhu, použijte [CMFCOutlookBar::CreateCustomPage](#createcustompage) a [CMFCOutlookBar::RemoveCustomPage](#removecustompage).  
  
## <a name="outlook-2003-mode"></a>Režim 2003 aplikace Outlook  
 V aplikaci Outlook 2003 režimu tlačítka karta umístěné v dolní části podokně panelu aplikace Outlook. Pokud není k dispozici dostatek místa pro zobrazení tlačítka, jsou zobrazeny jako ikony v panelu nástrojů jako oblasti ve spodní části podokna.  
  
 Použití [CMFCOutlookBar::SetMode2003](#setmode2003) chcete povolit režim Outlook 2003. Použití [CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) nastavit rastrový obrázek, který obsahuje ikony, které se zobrazí v dolní části panelu aplikace Outlook. Ikony v souboru bitové mapy musejí být seřazeny podle karta indexu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxoutlookbar.h  
  
##  <a name="allowdestroyemptytabbedpane"></a>  CMFCOutlookBar::AllowDestroyEmptyTabbedPane  
 Určuje, zda může být zničený záložkách podokně aplikace prázdný.  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud prázdnou – záložkami může být zničený podokně; v opačném `FALSE`. Výchozí implementace vždy vrátí `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud podokně aplikace prázdný záložkách nemůže být zničený, rozhraní skryjete místo.  
  
##  <a name="canacceptpane"></a>  CMFCOutlookBar::CanAcceptPane  
 Určuje, zda lze ukotvit jiného podokna do podokna panelu aplikace Outlook.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
 Ukazatel na další podokno, které ukotven na tomto podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud jiného podokna lze ukotvit do podokna panelu Outlook; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud na panelu aplikace Outlook je v režimu Outlook 2003, ukotvení se nepodporuje, tak, aby návratovou hodnotu `FALSE`.  
  
 Pokud `pBar` parametr `NULL`, vrátí tato metoda `FALSE`.  
  
 Jinak tato metoda chová jako základní metody [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane)kromě toho, že i v případě, že ukotvení není povolen, panel aplikace Outlook stále umožňují jiný panel aplikace Outlook k ukotvit nad ním.  
  
##  <a name="cansetcaptiontexttotabname"></a>  CMFCOutlookBar::CanSetCaptionTextToTabName  
 Určuje, zda titulek pro záložkách podokně zobrazí stejný text jako aktivní karty.  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud aplikace Outlook panelu titulek, který se automaticky nastaví na text kartě active; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) chcete povolit nebo zakázat tuto funkci.  
  
 V aplikaci Outlook 2003 režimu je toto nastavení vždy povolena.  
  
##  <a name="create"></a>  CMFCOutlookBar::Create  
 Vytvoří ovládací prvek panelu aplikace Outlook.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszCaption`  
 Určuje titulek okna.  
  
 [v] `pParentWnd`  
 Určuje ukazatel do nadřazeného okna. Nesmí být NULL.  
  
 [v] `rect`  
 Určuje outlook panelu velikost a umístění v pixelech.  
  
 [v] `nID`  
 Určuje ID ovládacího prvku. Musí být odlišný od jiných řízení ID používaná v aplikaci.  
  
 [v] `dwStyle`  
 Určuje styl panelu požadovaný ovládací prvek. Možné hodnoty, najdete v části [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [v] `dwControlBarStyle`  
 Určuje zvláštní styly definované knihovny.  
  
 [v] `pContext`  
 Vytvoření kontextu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je metoda úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CMFCOutlookBar` objektu ve dvou krocích. První volání konstruktoru a pak zavolají `Create`, který vytvoří ovládací prvek panelu aplikace outlook a připojí jej k `CMFCOutlookBar` objektu.  
  
 V tématu [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) seznam dostupné styly definované knihovny počtem `dwControlBarStyle`.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `Create` metodu `CMFCOutlookBar` třídy. Tento fragment kódu je součástí [ukázkové aplikace Outlook více zobrazení](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]  
  
##  <a name="createcustompage"></a>  CMFCOutlookBar::CreateCustomPage  
 Vytvoří vlastní karty panelu aplikace Outlook.  
  
```  
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,  
    BOOL bActivatePage=TRUE,  
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,  
    BOOL bEnableTextLabels=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszPageName`  
 Název stránky.  
  
 [v] `bActivatePage`  
 Pokud `TRUE`, stane aktivní po vytvoření stránky.  
  
 [v] `dwEnabledDocking`  
 Kombinace příznaků CBRS_ALIGN_, který určuje povolené ukotvení postranní při stránky je odpojená.  
  
 [v] `bEnableTextLabels`  
 Pokud `TRUE`, textové popisky jsou povoleny pro tlačítka nacházející se na stránce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořené stránky, nebo `NULL` Pokud vytvoření se nezdařilo.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, chcete-li povolit uživatelům vytvářet vlastní stránky panelu aplikace Outlook. Můžete vytvořit až 100 stránky na aplikaci. Ovládací prvek stránku ID začínají 0xF000. Vytvoření selže, pokud celkový počet vlastní stránky Outlook panelu překročí 100.  
  
 Použití [CMFCOutlookBar::RemoveCustomPage](#removecustompage) odstranit vlastní stránky.  
  
##  <a name="doesallowdyninsertbefore"></a>  CMFCOutlookBar::DoesAllowDynInsertBefore  
 Určuje, jestli uživatel může ukotvení panelu v vnějšího okraje panelu aplikace Outlook.  
  
```  
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volání framework `DoesAllowDynInsertBefore` metoda při umístění, kam chcete ukotvit dynamické podokno. Pokud funkce vrátí `FALSE`, rozhraní neumožňuje ukotvení žádné dynamické panelu v částí v podokně.  
  
 Obvykle vytvoříte jako statické ovládací prvek s plovoucí panel aplikace Outlook. Můžete přepsat tuto funkci v odvozené třídě a vrátí `TRUE` toto chování změnit.  
  
> [!NOTE]
>  Protože dynamická podokna zkontrolujte stav ukotveného statické podokna při ukotvení, by měl ukotvení dynamické podokna po statické podokna, kdykoli je to možné.  
  
##  <a name="floattab"></a>  CMFCOutlookBar::FloatTab  
 Obtéká podokno.  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
 Ukazatel na podokno float.  
  
 [v] `nTabID`  
 Index založený na nule karty na float.  
  
 [v] `dockMethod`  
 Určuje metodu sloužící k uvolnit podokně.  Další informace najdete v tématu [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).  
  
 [v] `bHide`  
 `TRUE` Chcete-li skrýt podokno před plovoucí; v opačném `FALSE`. Na rozdíl od základní třídy verzi tuto metodu tento parametr nemá výchozí hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně obtékané; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je jako [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab) s tím rozdílem, že neumožňuje kartě poslední zbývající ovládacího prvku panel Outlook na float.  
  
##  <a name="getbuttonsfont"></a>  CMFCOutlookBar::GetButtonsFont  
 Vrátí písma textu na stránce karet tlačítko panelu aplikace Outlook.  
  
```  
CFont* GetButtonsFont() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na objekt písma, který se používá k zobrazení textu v aplikaci Outlook panelu karet tlačítko stránek.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete načíst písma, který se používá k zobrazení textu na kartách tlačítko stránky aplikace Outlook. Písmo můžete nastavit tak, že zavoláte na [CMFCOutlookBar::SetButtonsFont](#setbuttonsfont).  
  
##  <a name="gettabarea"></a>  CMFCOutlookBar::GetTabArea  
 Určuje velikost a umístění oblasti karty na panelu aplikace Outlook.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `rectTabAreaTop`  
 Pokud funkce vrátí hodnotu obsahuje velikost a umístění (v souřadnicích klienta) oblast nejvyšší karty.  
  
 [out] `rectTabAreaBottom`  
 Obsahuje velikost a umístění (v souřadnicích klienta) oblast karty dolní při funkce vrátí hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se zjistit typ ukotvení do podokna cíl volá framework. Když systém určuje uživatel nastavuje tažením podokno ukotvit přes oblast karty podokna cíl, pokusí se přidání první podokna jako novou kartu cíl podokna. Jinak pokusí se ukotvení první panelu v příslušné části podokna cíl. Rozhraní framework vytvoří nový kontejner s jezdce zohlednit na další ukotveného panelu.  
  
 Výchozí implementaci `GetTabArea` vrátí celé klientské oblasti panelu aplikace Outlook, pokud panelu aplikace Outlook je statická; který je v případě, že nelze float panelu aplikace Outlook. Jinak vrátí k oblasti, která trvat stránky tlačítka v horní a dolní ovládací prvek panelu aplikace Outlook.  
  
 Potlačí tuto metodu do třídy odvozené od `CMFCOutlookBar` toto chování změnit.  
  
##  <a name="ismode2003"></a>  CMFCOutlookBar::IsMode2003  
 Určuje, zda napodobuje chování panelu aplikace Outlook, Microsoft Office Outlook 2003.  
  
```  
BOOL IsMode2003() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud na panelu aplikace Outlook běží v režimu Microsoft Office 2003; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tento režim můžete povolit pomocí [CMFCOutlookBar::SetMode2003](#setmode2003).  
  
##  <a name="onafteranimation"></a>  CMFCOutlookBar::OnAfterAnimation  
 Voláno rozhraním [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) po kartě active byla nastavena pomocí animace.  
  
```  
virtual void OnAfterAnimation(int nPage);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nPage`  
 Index založený na nule stránce karty, který byl změněn aktivní.  
  
### <a name="remarks"></a>Poznámky  
 Visual účinek nastavení na kartě active závisí na tom, jestli jste povolili animace. Další informace najdete v tématu [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).  
  
##  <a name="onbeforeanimation"></a>  CMFCOutlookBar::OnBeforeAnimation  
 Voláno rozhraním [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) před na kartě stránky nastavená jako aktivní karty pomocí animace.  
  
```  
virtual BOOL OnBeforeAnimation(int nPage);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nPage`  
 Index založený na nule kartě stránky, která má být nastaveno jako aktivní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud se má používat animace v nastavení na nové kartě active nebo `FALSE` Pokud animace by mělo být zakázáno.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onscroll"></a>  CMFCOutlookBar::OnScroll  
 Voláno rámcem, pokud je na panelu aplikace Outlook posouvání nahoru nebo dolů.  
  
```  
virtual void OnScroll(BOOL bDown);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bDown`  
 `TRUE` Pokud je na panelu aplikace Outlook posouvání dolů, nebo `FALSE` Pokud je posouvání nahoru.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removecustompage"></a>  CMFCOutlookBar::RemoveCustomPage  
 Odebere vlastní stránky karty panelu aplikace Outlook.  
  
```  
BOOL RemoveCustomPage(
    UINT uiPage,  
    CMFCOutlookBarTabCtrl* pTargetWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiPage`  
 Index stránky v okně aplikace Outlook nadřazené nule.  
  
 [v] `pTargetWnd`  
 Pointerto nadřazeného okna aplikace Outlook.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud vlastní stránka byla odebrána úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se odstranit vlastní stránky. Při odebrání stránky jeho ID ovládacího prvku se vrátí do fondu identifikátorů k dispozici.  
  
 Je nutné zadat ukazatel na [CMFCOutlookBarTabCtrl třída](../../mfc/reference/cmfcoutlookbartabctrl-class.md) objekt v které stránku a odeberou se aktuálně nachází. Všimněte si, že uživatel můžete přesunout odpojitelných stránky mezi různé panely aplikace Outlook, ale informace o vlastní stránky se nachází v objektu panelu aplikace Outlook, pro kterou mají volat [CMFCOutlookBar::CreateCustomPage](#createcustompage).  
  
 Použití [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) k získání ukazatele na okno aplikace Outlook.  
  
##  <a name="setbuttonsfont"></a>  CMFCOutlookBar::SetButtonsFont  
 Nastaví písmo textu tlačítka panelu aplikace Outlook.  
  
```  
void SetButtonsFont(
    CFont* pFont,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pFont`  
 Určuje písmo nové.  
  
 [v] `bRedraw`  
 Pokud `TRUE`, bude překreslit panelu aplikace Outlook.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k nastavení písmo pro text zobrazený na tlačítka stránky karty aplikace outlook.  
  
##  <a name="setmode2003"></a>  CMFCOutlookBar::SetMode2003  
 Určuje, zda chování panelu aplikace Outlook napodobuje u aplikací Outlook 2003.  
  
```  
void SetMode2003(BOOL bMode2003=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bMode2003`  
 V případě hodnoty TRUE je povolen režim Office 2003.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete povolit nebo zakázat režim Office 2003. V tomto režimu má panelu aplikace Outlook další panel nástrojů s tlačítkem na vlastní nastavení. Chování panelu aplikace Outlook vyhovuje chování panelu aplikace Outlook v aplikaci Microsoft Office 2003.  
  
 Tento režim je ve výchozím nastavení zakázaná.  
  
> [!NOTE]
>  Tato funkce musí být volána před [CMFCOutlookBar::Create](#create).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CBaseTabbedPane – třída](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBarTabCtrl – třída](../../mfc/reference/cmfcoutlookbartabctrl-class.md)   
 [CMFCOutlookBarPane – třída](../../mfc/reference/cmfcoutlookbarpane-class.md)
