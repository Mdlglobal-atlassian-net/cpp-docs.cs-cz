---
title: CMFCOutlookBar – třída
ms.date: 06/25/2018
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
ms.openlocfilehash: fc1281db0271393ec0538e26c2a2d2af09c99f7a
ms.sourcegitcommit: 39debf8c525c3951af6913ee5e514617658f8859
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2019
ms.locfileid: "58775254"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar – třída

Podokno s kartami s vzhled **navigačním podokně** v aplikaci Microsoft Outlook 2000 nebo Outlook 2003. `CMFCOutlookBar` Obsahuje objekt [cmfcoutlookbartabctrl – třída](../../mfc/reference/cmfcoutlookbartabctrl-class.md) objektu a řadu karet. Karty mohou být buď [cmfcoutlookbarpane – třída](../../mfc/reference/cmfcoutlookbarpane-class.md) objekty nebo `CWnd`-odvozené objekty. Pro uživatele panel aplikace Outlook zobrazí jako řada tlačítek a zobrazení plochy. Když uživatel klikne na tlačítko, zobrazí se odpovídající ovládací prvek nebo podokno tlačítek.

## <a name="syntax"></a>Syntaxe

```cpp
class CMFCOutlookBar : public CBaseTabbedPane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|`CMFCOutlookBar::CMFCOutlookBar`|Výchozí konstruktor.|
|`CMFCOutlookBar::~CMFCOutlookBar`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Určuje, zda lze zničit prázdné podokno s kartami. (Přepíše [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Určuje, zda lze ukotvit jiného podokna na podokno panelu aplikace Outlook. (Přepíše CDockablePane::CanAcceptPane.)|
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Určuje, zda Titulek podokna s kartami zobrazí stejný text jako na aktivní kartě. (Přepíše [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|
|[CMFCOutlookBar::Create](#create)|Vytvoří ovládací prvek panel aplikace Outlook.|
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|Vytvoří vlastní kartu panel aplikace Outlook.|
|`CMFCOutlookBar::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Určuje, zda uživatele lze ukotvit panel ovládacího prvku na vnější okraj panelu aplikace Outlook.|
|[CMFCOutlookBar::FloatTab](#floattab)|Podokno, ale pouze čísel s plovoucí čárkou, pokud se v podokně se aktuálně nachází odpojitelných kartě. (Přepíše [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Vrátí písmo textu na tlačítka na panelu aplikace Outlook.|
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Vrátí velikost a umístění oblasti kartu na panelu aplikace Outlook. (Přepíše [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|
|`CMFCOutlookBar::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Určuje, zda napodobuje chování panel aplikace Outlook, které aplikace Microsoft Office Outlook 2003 (viz poznámky).|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Volané [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) po byla nastavena na aktivní kartě pomocí animace.|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Volané [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) před na kartě stránky nastavená jako aktivní karty pomocí animace.|
|[CMFCOutlookBar::OnScroll](#onscroll)|Volá se rozhraním, pokud je panel aplikace Outlook Posun směrem nahoru nebo dolů.|
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|Odebere vlastní karty panelu aplikace Outlook.|
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Nastaví písmo textu tlačítka na panelu aplikace Outlook.|
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Určuje, zda napodobuje chování panel aplikace Outlook, která aplikace Outlook 2003 (viz poznámky).|

## <a name="remarks"></a>Poznámky

Příklad panel aplikace Outlook, najdete v článku [OutlookDemo vzorku: Aplikace MFC OutlookDemo](../../overview/visual-cpp-samples.md).

## <a name="implementing-the-outlook-bar"></a>Implementace panelu aplikace Outlook

Použít `CMFCOutlookBar` ovládací prvek ve vaší aplikaci, postupujte podle těchto kroků:

1. Vložit `CMFCOutlookBar` objekt do třídy okna hlavního rámce.

    ```cpp
    class CMainFrame : public CMDIFrameWnd
    {
        // ...
        CMFCOutlookBar m_wndOutlookBar;
        CMFCOutlookBarPane m_wndOutlookPane;
        // ...
    };
    ```

1. Při zpracování zprávy WM_CREATE v hlavního rámce, zavolejte [CMFCOutlookBar::Create](#create) metodu pro vytvoření aplikace Outlook panelu ovládacího prvku karta.

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. Získání ukazatele na základní `CMFCOutlookBarTabCtrl` pomocí [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. Vytvoření [cmfcoutlookbarpane – třída](../../mfc/reference/cmfcoutlookbarpane-class.md) objekt pro každou kartu, která obsahuje tlačítka.

    ```cpp
    m_wndOutlookPane.Create(&m_wndOutlookBar,
        AFX_DEFAULT_TOOLBAR_STYLE,
        ID_OUTLOOK_PANE_GENERAL,
        AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);

    // make the Outlook pane detachable (enable docking)
    m_wndOutlookPane.EnableDocking(CBRS_ALIGN_ANY);

    // add buttons
    m_wndOutlookPane.AddButton(theApp.LoadIcon (IDR_MAINFRAME),
        "About",
        ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON),
        "Open",
        ID_FILE_OPEN);
    ```

1. Volání [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) přidáte každou novou kartu. Nastavte *bDetachable* parametr na hodnotu FALSE, aby stránka bez odpojitelných. Nebo použijte [CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) přidat odpojitelných stránky.

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. Chcete-li přidat `CWnd`– ovládací prvek odvozený (například [CMFCShellTreeCtrl – třída](../../mfc/reference/cmfcshelltreectrl-class.md)) jako karta, vytvořit ovládací prvek a volání [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) ho přidat na panel aplikace Outlook.

> [!NOTE]
>  Jedinečné ID ovládacích prvků byste měli použít pro každý [cmfcoutlookbarpane – třída](../../mfc/reference/cmfcoutlookbarpane-class.md) objekt a pro každou `CWnd`-odvozenému objektu.

Chcete-li dynamicky přidat nebo odstranit nových stránek za běhu, použijte [CMFCOutlookBar::CreateCustomPage](#createcustompage) a [CMFCOutlookBar::RemoveCustomPage](#removecustompage).

## <a name="outlook-2003-mode"></a>Režim aplikace Outlook 2003

V aplikaci Outlook 2003 režimu jsou umístěny na kartu tlačítka dolní podokno panelu aplikace Outlook. Když není k dispozici dostatek místa pro zobrazení tlačítka, jsou zobrazeny jako ikony v panelu nástrojů jako oblast v dolní části podokna.

Použití [CMFCOutlookBar::SetMode2003](#setmode2003) pro povolení režimu Outlook 2003. Použití [CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) nastavit rastrový obrázek, který obsahuje ikony, které jsou zobrazeny v dolní části panelu aplikace Outlook. Ikony rastrového obrázku nastaven musí provést řazení podle pořadové číslo prvku.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget –](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxoutlookbar.h

##  <a name="allowdestroyemptytabbedpane"></a>  CMFCOutlookBar::AllowDestroyEmptyTabbedPane

Určuje, zda lze zničit prázdné podokno s kartami.

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud lze zničit prázdné podokno s kartami; v opačném případě hodnota FALSE. Výchozí implementace vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Pokud nelze zničit prázdné podokno s kartami, rozhraní skrývá ho. místo toho.

##  <a name="canacceptpane"></a>  CMFCOutlookBar::CanAcceptPane

Určuje, zda lze ukotvit jiného podokna na podokno panelu aplikace Outlook.

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Ukazatel na další podokno, které ukotven na tomto podokně.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud lze ukotvit jiného podokna na podokno panelu Outlook; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud není podporován v Outlooku panel je v režimu Outlook 2003 ukotvení, takže návratová hodnota je FALSE.

Pokud *pBar* parametr hodnotu NULL, tato metoda vrátí hodnotu FALSE.

Jinak tato metoda chová jako základní metoda [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane), s tím rozdílem, že i když ukotvení není povolená, panel aplikace Outlook stále umožňují jiný panel aplikace Outlook ukotvit nad ním.

##  <a name="cansetcaptiontexttotabname"></a>  CMFCOutlookBar::CanSetCaptionTextToTabName

Určuje, zda Titulek podokna s kartami zobrazí stejný text jako na aktivní kartě.

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě Outlooku panelu titulek okna se automaticky nastaví na text na aktivní kartě; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Použití [CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) k povolení nebo zakázání této funkce.

V aplikaci Outlook 2003 režimu je toto nastavení vždy povolené.

##  <a name="create"></a>  CMFCOutlookBar::Create

Vytvoří ovládací prvek panel aplikace Outlook.

```cpp
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

*lpszCaption*<br/>
[in] Určuje titulek okna.

*pParentWnd*<br/>
[in] Určuje ukazatel do nadřazeného okna. Nesmí být NULL.

*rect*<br/>
[in] Určuje velikost a pozice v pixelech panelu aplikace outlook.

*nID*<br/>
[in] Určuje ID ovládacího prvku. Musí být odlišný od jiného ovládacího prvku ID používaných v aplikaci.

*dwStyle*<br/>
[in] Určuje styl pruhu požadovaný ovládací prvek. Možné hodnoty najdete v části [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwControlBarStyle*<br/>
[in] Určuje zvláštní knihovně definovány styly.

*pContext*<br/>
[in] Vytvořte kontext.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je metoda úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CMFCOutlookBar` objektu ve dvou krocích. Nejprve volat konstruktor a následně zavolat `Create`, což vytvoří ovládací prvek panel aplikace outlook a připojí ho k `CMFCOutlookBar` objektu.

Zobrazit [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) seznam dostupných stylů definované knihovny počtem *dwControlBarStyle*.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `Create` metodu `CMFCOutlookBar` třídy. Tento fragment kódu je součástí [ukázkové aplikace Outlook s více zobrazení](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

##  <a name="createcustompage"></a>  CMFCOutlookBar::CreateCustomPage

Vytvoří vlastní kartu panel aplikace Outlook.

```cpp
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,
    BOOL bActivatePage=TRUE,
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,
    BOOL bEnableTextLabels=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszPageName*<br/>
[in] Popisek stránky.

*bActivatePage*<br/>
[in] Při hodnotě TRUE se aktivují při vytvoření stránky.

*dwEnabledDocking*<br/>
[in] Kombinace příznaků CBRS_ALIGN_, který určuje povolené ukotvení strana, když je odpojená stránky.

*bEnableTextLabels*<br/>
[in] Při hodnotě TRUE textové popisky jsou povoleny pro tlačítka, které jsou umístěny na stránce.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený stránky, nebo hodnota NULL, pokud vytvoření se nezdařilo.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k povolení uživatelům vytvářet vlastní stránky panelu aplikace Outlook. Můžete vytvořit až 100 stránky na aplikaci. Ovládací prvek stránky ID začíná od 0xF000. Vytváření nezdaří, pokud celkový počet vlastních stránek panelu aplikace Outlook překročí 100.

Použití [CMFCOutlookBar::RemoveCustomPage](#removecustompage) odstranit vlastní stránky.

##  <a name="doesallowdyninsertbefore"></a>  CMFCOutlookBar::DoesAllowDynInsertBefore

Určuje, zda uživatele lze ukotvit podokně ve vnější okraj panelu aplikace Outlook.

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Rámec volá `DoesAllowDynInsertBefore` metoda při umístění ukotvení na dynamické stavového řádku. Pokud funkce vrátí hodnotu FALSE, nepovoluje rozhraní ukotvení žádné dynamické podokně ve vnější hrany v podokně.

Obvykle vytvoříte jako statický ovládací prvek s plovoucí panel aplikace Outlook. Můžete tuto funkci v odvozené třídě přepsat a vrátí TRUE, pokud chcete toto chování změnit.

> [!NOTE]
>  Protože dynamická podokna zkontrolovat stav statické ukotveného podokna při ukotvení, by měl ukotvit dynamické podokna po statické podoken, kdykoli je to možné.

##  <a name="floattab"></a>  CMFCOutlookBar::FloatTab

Čísel s plovoucí čárkou podokno.

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Ukazatel na podokně s plovoucí desetinnou čárkou.

*nTabID*<br/>
[in] Index založený na nule na kartu pro plovoucí desetinnou čárkou.

*dockMethod*<br/>
[in] Určuje způsob, kterým uvolnit podokně.  Další informace najdete v tématu [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).

*bHide*<br/>
[in] TRUE, pokud chcete skrýt podokno před plovoucí; v opačném případě hodnota FALSE. Na rozdíl od verze základní třídy tuto metodu tento parametr nemá výchozí hodnotu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se v podokně obtékané; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda je jako [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab) s tím rozdílem, že neumožňuje poslední zbývající karty na ovládací prvek panel aplikace Outlook pro plovoucí desetinnou čárkou.

##  <a name="getbuttonsfont"></a>  CMFCOutlookBar::GetButtonsFont

Vrátí písmo textu na stránce tlačítko karty panelu aplikace Outlook.

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt písma, který se používá k zobrazení textu v Outlooku. panelu karet tlačítko stránek.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte k načtení písma, která se používá k zobrazení textu v kartách tlačítko stránky aplikace Outlook. Můžete nastavit písmo získaný pomocí funkce [CMFCOutlookBar::SetButtonsFont](#setbuttonsfont).

##  <a name="gettabarea"></a>  CMFCOutlookBar::GetTabArea

Určuje velikost a umístění oblasti kartu na panelu aplikace Outlook.

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parametry

*rectTabAreaTop*<br/>
[out] Po návratu funkce obsahuje velikost a umístění (v souřadnicích klientů) v oblasti horní kartě.

*rectTabAreaBottom*<br/>
[out] Po návratu funkce obsahuje velikost a umístění (v souřadnicích klienta) do oblasti dolní části karty.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu za účelem určení typu ukotvení do podokna cíl. Rozhraní určuje, že uživatel přetáhne podokno ukotvit na kartě oblast podokně cíl, se pokusí přidat první podokně jako na nové kartě v podokně cíl. V opačném případě se pokusí ukotvit první podokno v příslušné části podokna cíl. Rozhraní vytvoří nový kontejner s posuvníkem pro plnění dalších ukotvené podokno.

Výchozí implementace `GetTabArea` vrátí celou klientskou oblast panel aplikace Outlook, pokud panel aplikace Outlook je statická; který je v případě, že nelze plovoucí panel aplikace Outlook. V opačném případě vrátí oblasti, které využívají stránky, tlačítka v horní a dolní ovládací prvek panel aplikace Outlook.

Potlačí tuto metodu v třídě odvozené z `CMFCOutlookBar` ke změně tohoto chování.

##  <a name="ismode2003"></a>  CMFCOutlookBar::IsMode2003

Určuje, zda napodobuje chování panel aplikace Outlook, Microsoft Office Outlook 2003.

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud panel aplikace Outlook je spuštěn v režimu Microsoft Office 2003. jinak 0.

### <a name="remarks"></a>Poznámky

Tento režim můžete povolit pomocí [CMFCOutlookBar::SetMode2003](#setmode2003).

##  <a name="onafteranimation"></a>  CMFCOutlookBar::OnAfterAnimation

Volané [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) po byla nastavena na aktivní kartě pomocí animace.

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>Parametry

*nPage*<br/>
[in] Index založený na nule stránky karty, které byly provedeny aktivní.

### <a name="remarks"></a>Poznámky

Vizuální efekt nastavení na aktivní kartě závisí na tom, jestli jste povolili animace. Další informace najdete v tématu [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).

##  <a name="onbeforeanimation"></a>  CMFCOutlookBar::OnBeforeAnimation

Volané [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) před na kartě stránky nastavená jako aktivní karty pomocí animace.

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>Parametry

*nPage*<br/>
[in] Index založený na nule, který se chystáte se nastavit aktivní kartu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se má používat při nastavení na nové aktivní kartě animace, nebo hodnotu FALSE, pokud by mělo být zakázáno animace.

### <a name="remarks"></a>Poznámky

##  <a name="onscroll"></a>  CMFCOutlookBar::OnScroll

Volá se rozhraním, pokud je panel aplikace Outlook Posun směrem nahoru nebo dolů.

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>Parametry

*bDown*<br/>
[in] TRUE, pokud panel aplikace Outlook se posunete dolů, nebo hodnotu FALSE, pokud se posouvání nahoru.

### <a name="remarks"></a>Poznámky

##  <a name="removecustompage"></a>  CMFCOutlookBar::RemoveCustomPage

Odebere vlastní stránky karty panelu aplikace Outlook.

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>Parametry

*Element uiPage*<br/>
[in] Z nuly vycházející index stránky v nadřazené okno aplikace Outlook.

*pTargetWnd*<br/>
[in] Pointerto nadřazené okno aplikace Outlook.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je vlastní stránka byla odebrána úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Voláním této funkce se odstranit vlastní stránky. Při odebrání stránky jeho ID ovládacího prvku je vrácen do fondu dostupných identifikátorů.

Je nutné zadat ukazatel na [cmfcoutlookbartabctrl – třída](../../mfc/reference/cmfcoutlookbartabctrl-class.md) ve které se nachází na stránce odebrat aktuálně objekt. Vezměte na vědomí, že uživatel může přesunout odpojitelných stránky mezi panely různé aplikace Outlook, ale informace o vlastní stránku se nachází v objektu panel aplikace Outlook, pro kterou jste volali [CMFCOutlookBar::CreateCustomPage](#createcustompage).

Použití [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) k získání ukazatele na okno aplikace Outlook.

##  <a name="setbuttonsfont"></a>  CMFCOutlookBar::SetButtonsFont

Nastaví písmo textu tlačítka na panelu aplikace Outlook.

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
[in] Určuje písmo pro nové.

*bRedraw*<br/>
[in] Pokud je hodnota TRUE, bude se měl překreslit panel aplikace Outlook.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete nastavit typ písma textu zobrazeného na tlačítka kartu stránky aplikace outlook.

##  <a name="setmode2003"></a>  CMFCOutlookBar::SetMode2003

Určuje, zda napodobuje chování panel aplikace Outlook, která aplikace Outlook 2003.

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>Parametry

*bMode2003*<br/>
[in] Při hodnotě TRUE je povolený režim Office 2003.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k povolení nebo zakázání režimu Office 2003. V tomto režimu se panel aplikace Outlook dalších nástrojů pomocí tlačítka přizpůsobení. Chování panel aplikace Outlook odpovídá chování panel aplikace Outlook v aplikaci Microsoft Office 2003.

Tento režim je ve výchozím nastavení zakázána.

> [!NOTE]
>  Tato funkce musí být volána před [CMFCOutlookBar::Create](#create).

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Cbasetabbedpane – třída](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[Cmfcoutlookbartabctrl – třída](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[Cmfcoutlookbarpane – třída](../../mfc/reference/cmfcoutlookbarpane-class.md)
