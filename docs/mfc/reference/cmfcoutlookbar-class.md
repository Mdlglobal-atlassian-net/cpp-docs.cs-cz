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
ms.openlocfilehash: fe328cb0d857ff9154624d218b1b56362890ce81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369657"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar – třída

Podokno s kartami s vizuálním vzhledem **navigačního podokna** v aplikaci Microsoft Outlook 2000 nebo Outlook 2003. Objekt `CMFCOutlookBar` obsahuje objekt [třídy CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md) a řadu karet. Karty mohou být objekty [třídy CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) nebo `CWnd`odvozené objekty. Uživateli se panel aplikace Outlook zobrazí jako řada tlačítek a oblast zobrazení. Když uživatel klepne na tlačítko, zobrazí se odpovídající ovládací prvek nebo podokno tlačítek.

## <a name="syntax"></a>Syntaxe

```cpp
class CMFCOutlookBar : public CBaseTabbedPane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCOutlookBar::CMFCOutlookBar`|Výchozí konstruktor.|
|`CMFCOutlookBar::~CMFCOutlookBar`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Určuje, zda lze zničit prázdné podokno s kartami. (Přepíše [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Určuje, zda lze do podokna panelu aplikace Outlook ukotvit jiné podokno. (Přepíše CDockablePane::CanAcceptPane.)|
|[CMFCOutlookBar::CanSetcaptionTextToTabName](#cansetcaptiontexttotabname)|Určuje, zda se v titulku podokna s kartami zobrazí [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname)stejný text jako aktivní karta.|
|[CMFCOutlookBar::Vytvořit](#create)|Vytvoří ovládací prvek panelu aplikace Outlook.|
|[CMFCOutlookBar::Vytvořit vlastní stránku](#createcustompage)|Vytvoří vlastní kartu panelu aplikace Outlook.|
|`CMFCOutlookBar::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCOutlookBar::DoesAllowDynInsertPřed](#doesallowdyninsertbefore)|Určuje, zda může uživatel ukotvit ovládací panel na vnějším okraji panelu aplikace Outlook.|
|[CMFCOutlookBar::FloatTab](#floattab)|Plovoucí podokno, ale pouze v případě, že podokno aktuálně umístěnna [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)odpojitelné karty.|
|[CMFCOutlookBar::Písmo GetButtonsFont](#getbuttonsfont)|Vrátí písmo textu na tlačítkách panelu aplikace Outlook.|
|[CMFCOutlookBar::Gettabarea](#gettabarea)|Vrátí velikost a umístění oblastí tabulátoru na panelu aplikace Outlook. (Přepíše [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|
|`CMFCOutlookBar::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Určuje, zda chování panelu aplikace Outlook napodobuje chování aplikace Microsoft Office Outlook 2003 (viz poznámky).|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Volat [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) po aktivní kartu byla nastavena pomocí animace.|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Volat [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) před stránka karty je nastaven jako aktivní kartu pomocí animace.|
|[CMFCOutlookBar::OnScroll](#onscroll)|Volat rámci, pokud panel aplikace Outlook je posouvání nahoru nebo dolů.|
|[CMFCOutlookBar::Odstranit vlastní stránku](#removecustompage)|Odebere vlastní kartu panelu aplikace Outlook.|
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Nastaví písmo textu na tlačítkách panelu aplikace Outlook.|
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Určuje, zda chování panelu aplikace Outlook napodobuje chování aplikace Outlook 2003 (viz Poznámky).|

## <a name="remarks"></a>Poznámky

Příklad panelu aplikace Outlook naleznete v [tématu OutlookDemo Sample: MFC OutlookDemo Application](../../overview/visual-cpp-samples.md).

## <a name="implementing-the-outlook-bar"></a>Implementace panelu aplikace Outlook

Chcete-li `CMFCOutlookBar` použít ovládací prvek v aplikaci, postupujte takto:

1. Vlož `CMFCOutlookBar` objekt do třídy okna hlavního rámce.

    ```cpp
    class CMainFrame : public CMDIFrameWnd
    {
        // ...
        CMFCOutlookBar m_wndOutlookBar;
        CMFCOutlookBarPane m_wndOutlookPane;
        // ...
    };
    ```

1. Při zpracování zprávy WM_CREATE v hlavním rámci volejte metodu [CMFCOutlookBar::Create](#create) a vytvořte ovládací prvek panelové karty aplikace Outlook.

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. Získat ukazatel na `CMFCOutlookBarTabCtrl` podkladové pomocí [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. Vytvořte objekt [třídy CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) pro každou kartu, která obsahuje tlačítka.

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

1. Volání [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) pro přidání každé *bDetachable* nové karty. Nebo použijte [CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) pro přidání oddělitelných stránek.

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. Chcete-li `CWnd`přidat -derived ovládací prvek (například [CMFCShellTreeCtrl Class](../../mfc/reference/cmfcshelltreectrl-class.md)) jako kartu, vytvořte ovládací prvek a volání [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) přidat do panelu aplikace Outlook.

> [!NOTE]
> Pro každý objekt [třídy CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) a pro každý `CWnd`odvozený objekt byste měli použít jedinečná ID ovládacího prvku.

Chcete-li dynamicky přidávat nebo odstraňovat nové stránky za běhu, použijte [CMFCOutlookBar::CreateCustomPage](#createcustompage) a [CMFCOutlookBar::RemoveCustomPage](#removecustompage).

## <a name="outlook-2003-mode"></a>Režim aplikace Outlook 2003

V režimu Aplikace Outlook 2003 jsou tlačítka karet umístěna v dolní části podokna panelu panelu aplikace Outlook. Pokud není dostatek místa pro zobrazení tlačítek, zobrazí se jako ikony v oblasti podobné panelu nástrojů v dolní části podokna.

Režim aplikace Outlook 2003 umožňuje povolení režimu aplikace [OutlookOutlookBar::SetMode2003.](#setmode2003) Pomocí [cmfcoutlookbartabctrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) nastavte bitmapu, která obsahuje ikony zobrazené v dolní části panelu aplikace Outlook. Ikony v bitmapách musí být seřazeny podle indexu tabulátoru.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CmFCOutlookPanel](../../mfc/reference/cmfcoutlookbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxoutlookbar.h

## <a name="cmfcoutlookbarallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CMFCOutlookBar::AllowDestroyEmptyTabbedPane

Určuje, zda lze zničit prázdné podokno s kartami.

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud lze zničit prázdné podokno s kartami; jinak NEPRAVDA. Výchozí implementace vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Pokud prázdné podokno s kartami nelze zničit, rozhraní framework jej místo toho skryje.

## <a name="cmfcoutlookbarcanacceptpane"></a><a name="canacceptpane"></a>CMFCOutlookBar::CanAcceptPane

Určuje, zda lze do podokna panelu aplikace Outlook ukotvit jiné podokno.

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[v] Ukazatel na jiné podokno, které je ukotveno do tohoto podokna.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud lze do podokna panelu aplikace Outlook ukotvit jiné podokno; jinak FALSE.

### <a name="remarks"></a>Poznámky

Pokud je panel aplikace Outlook v režimu aplikace Outlook 2003, ukotvení není podporováno, takže vrácená hodnota je FALSE.

Pokud je parametr *pBar* NULL, vrátí tato metoda hodnotu NEPRAVDA.

V opačném případě se tato metoda chová jako základní metoda [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane), s tím rozdílem, že i v případě, že ukotvení není povoleno, panel aplikace Outlook může stále povolit další panel aplikace Outlook, který má být ukotven nad ním.

## <a name="cmfcoutlookbarcansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CMFCOutlookBar::CanSetcaptionTextToTabName

Určuje, zda se v titulku podokna s kartami zobrazí stejný text jako aktivní karta.

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je titulek okna panelu aplikace Outlook automaticky nastaven na text aktivní karty; jinak FALSE.

### <a name="remarks"></a>Poznámky

Pomocí [funkce CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) tuto funkci povolte nebo zakažte.

V režimu aplikace Outlook 2003 je toto nastavení vždy povoleno.

## <a name="cmfcoutlookbarcreate"></a><a name="create"></a>CMFCOutlookBar::Vytvořit

Vytvoří ovládací prvek panelu aplikace Outlook.

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

*lpszTitulek*<br/>
[v] Určuje popisek okna.

*pParentWnd*<br/>
[v] Určuje ukazatel na nadřazené okno. Nesmí být null.

*Rect*<br/>
[v] Určuje velikost a umístění panelu aplikace Outlook v obrazových bodech.

*Nid*<br/>
[v] Určuje ID ovládacího prvku. Musí se odlišit od jiných ID ovládacího prvku, která se používají v aplikaci.

*dwStyl*<br/>
[v] Určuje požadovaný styl ovládacího panelu. Možné hodnoty naleznete [v tématu Styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwControlBarStyle*<br/>
[v] Určuje speciální styly definované knihovnou.

*pKontext*<br/>
[v] Vytvořte kontext.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je metoda úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CMFCOutlookBar` dvou krocích. Nejprve volání konstruktoru `Create`a potom volání , který vytvoří ovládací `CMFCOutlookBar` prvek panelu aplikace Outlook a připojí jej k objektu.

Seznam dostupných stylů definovaných knihovnou určených *pomocí dwControlBarStyle*naleznete v tématu [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex)

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `Create` používat metodu třídy. `CMFCOutlookBar` Tento fragment kódu je součástí [ukázky více zobrazení aplikace Outlook](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

## <a name="cmfcoutlookbarcreatecustompage"></a><a name="createcustompage"></a>CMFCOutlookBar::Vytvořit vlastní stránku

Vytvoří vlastní kartu panelu aplikace Outlook.

```cpp
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,
    BOOL bActivatePage=TRUE,
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,
    BOOL bEnableTextLabels=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszPageName*<br/>
[v] Popisek stránky.

*bActivatePage*<br/>
[v] Pokud true, stránka se stane aktivní při vytváření.

*dwEnabledDocking*<br/>
[v] Kombinace příznaků CBRS_ALIGN_, která určuje povolené dokovací strany při odpojení stránky.

*bEnableTextLabels*<br/>
[v] Pokud true, textové popisky jsou povoleny pro tlačítka, které jsou umístěny na stránce.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořenou stránku nebo hodnotu NULL, pokud se vytvoření nezdařilo.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k tomu, aby uživatelé mohli vytvářet vlastní stránky pruhů aplikace Outlook. V aplikaci můžete vytvořit až 100 stránek. ID ovládacího prvku stránky začínají od 0xF000. Vytvoření se nezdaří, pokud celkový počet vlastních pruhových stránek aplikace Outlook překročí 100.

K odstranění vlastních stránek použijte [CMFCOutlookBar::RemoveCustomPage.](#removecustompage)

## <a name="cmfcoutlookbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCOutlookBar::DoesAllowDynInsertPřed

Určuje, zda může uživatel ukotvit podokno na vnějším okraji panelu aplikace Outlook.

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu NEPRAVDA.

### <a name="remarks"></a>Poznámky

Rozhraní framework `DoesAllowDynInsertBefore` volá metodu, když hledá umístění ukotvit dynamické podokno. Pokud funkce vrátí hodnotu NEPRAVDA, rozhraní framework neumožňuje ukotvení žádného dynamického podokna na vnějších okrajích podokna.

Panel aplikace Outlook se obvykle vytváří jako statický neplovoucí ovládací prvek. Tuto funkci můžete přepsat v odvozené třídě a vrátit hodnotu TRUE, chcete-li toto chování změnit.

> [!NOTE]
> Vzhledem k tomu, že dynamická podokna kontrolují stav ukotvených statických podoken při ukotvení, měli byste dynamická podokna ukotvit za statickými podokny, kdykoli je to možné.

## <a name="cmfcoutlookbarfloattab"></a><a name="floattab"></a>CMFCOutlookBar::FloatTab

Plovoucí podokno.

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[v] Ukazatel na podokno float.

*nTabID*<br/>
[v] Index na základě nuly na kartě float.

*dockMethod*<br/>
[v] Určuje metodu, která má být používána k nastavení plovoucího panelu.  Další informace naleznete v [tématu CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).

*bSkrýt*<br/>
[v] TRUE skrýt podokno před plovoucí; jinak NEPRAVDA. Na rozdíl od verze základní třídy této metody tento parametr nemá výchozí hodnotu.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud se podokno vznášelo; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda je jako [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab) s tím rozdílem, že neumožňuje poslední zbývající kartu na ovládacím prvku panelu aplikace Outlook float.

## <a name="cmfcoutlookbargetbuttonsfont"></a><a name="getbuttonsfont"></a>CMFCOutlookBar::Písmo GetButtonsFont

Vrátí písmo textu na kartách tlačítek stránky na panelu aplikace Outlook.

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt písma, který se používá k zobrazení textu na kartách tlačítek panelu stránky aplikace Outlook.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k načtení písma, které se používá k zobrazení textu na kartách tlačítek stránky aplikace Outlook. Písmo můžete nastavit voláním na [CMFCOutlookBar::SetButtonsFont](#setbuttonsfont).

## <a name="cmfcoutlookbargettabarea"></a><a name="gettabarea"></a>CMFCOutlookBar::Gettabarea

Určuje velikost a umístění oblastí tabulátoru na panelu aplikace Outlook.

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parametry

*rectTabAreaTop*<br/>
[out] Obsahuje velikost a umístění (v souřadnicích klienta) v oblasti horní karty, když se funkce vrátí.

*rectTabAreaBottom*<br/>
[out] Obsahuje velikost a umístění (v souřadnicích klienta) v oblasti dolní karty, když se vrátí funkce.

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto metodu k určení typu ukotvení do cílového podokna. Když rozhraní framework usoudí, že uživatel přetáhne podokno, které má být ukotveno nad oblastí tabulátoru cílového podokna, pokusí se přidat první podokno jako novou kartu cílového podokna. V opačném případě se pokusí ukotvit první podokno na příslušné straně cílového podokna. Rozhraní framework vytvoří nový kontejner s posuvníkem pro další ukotvené podokno.

Výchozí implementace `GetTabArea` vrátí celou klientskou oblast panelu aplikace Outlook, pokud je pruh aplikace Outlook statický; to znamená, pokud panel aplikace Outlook nemůže plavat. V opačném případě vrátí oblast, kterou tlačítka stránky převezmou v horní a dolní části ovládacího prvku panelu aplikace Outlook.

Přepsat tuto metodu ve `CMFCOutlookBar` třídě odvozené od změnit toto chování.

## <a name="cmfcoutlookbarismode2003"></a><a name="ismode2003"></a>CMFCOutlookBar::IsMode2003

Určuje, zda chování panelu aplikace Outlook napodobuje chování aplikace Microsoft Office Outlook 2003.

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je panel aplikace Outlook spuštěn v režimu sady Microsoft Office 2003. jinak 0.

### <a name="remarks"></a>Poznámky

Tento režim můžete povolit pomocí [cmfcoutlookbaru::SetMode2003](#setmode2003).

## <a name="cmfcoutlookbaronafteranimation"></a><a name="onafteranimation"></a>CMFCOutlookBar::OnAfterAnimation

Volat [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) po aktivní kartu byla nastavena pomocí animace.

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>Parametry

*nStránka*<br/>
[v] Nulový index stránky karty, která byla aktivní.

### <a name="remarks"></a>Poznámky

Vizuální efekt nastavení aktivní karty závisí na tom, zda jste povolili animaci. Další informace naleznete v tématu [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).

## <a name="cmfcoutlookbaronbeforeanimation"></a><a name="onbeforeanimation"></a>CMFCOutlookBar::OnBeforeAnimation

Volat [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) před stránka karty je nastaven jako aktivní kartu pomocí animace.

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>Parametry

*nStránka*<br/>
[v] Index na základě nuly na stránce karty, která se chystá nastavit aktivní.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud má být animace použita při nastavování nové aktivní karty, nebo NEPRAVDA, pokud má být animace zakázána.

### <a name="remarks"></a>Poznámky

## <a name="cmfcoutlookbaronscroll"></a><a name="onscroll"></a>CMFCOutlookBar::OnScroll

Volat rámci, pokud panel aplikace Outlook je posouvání nahoru nebo dolů.

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>Parametry

*b Dolů*<br/>
[v] PRAVDA, pokud se panel aplikace Outlook posouvá dolů, nebo NEPRAVDA, pokud se posouvá nahoru.

### <a name="remarks"></a>Poznámky

## <a name="cmfcoutlookbarremovecustompage"></a><a name="removecustompage"></a>CMFCOutlookBar::Odstranit vlastní stránku

Odebere vlastní stránku karty panelu aplikace Outlook.

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>Parametry

*uiPage*<br/>
[v] Nulový index stránky v nadřazeném okně aplikace Outlook

*pTargetWnd*<br/>
[v] Ukazatel na nadřazené okno aplikace Outlook

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla vlastní stránka úspěšně odebrána. jinak 0.

### <a name="remarks"></a>Poznámky

Volánítéto funkce odstranit vlastní stránky. Po odebrání stránky je id ovládacího prvku vráceno do fondu dostupných ID.

Je nutné zadat ukazatel na objekt [třídy CMFCOutlookBarTabCtrl Class,](../../mfc/reference/cmfcoutlookbartabctrl-class.md) ve kterém se aktuálně nachází odebraná stránka. Všimněte si, že uživatel může přesunout odnímatelné stránky mezi různými pruhy aplikace Outlook, ale informace o vlastní stránce jsou umístěny v objektu panelu aplikace Outlook, pro který jste nazvali [CMFCOutlookBar::CreateCustomPage](#createcustompage).

Pomocí [cbasetabbedpane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) získat ukazatel na okno aplikace Outlook.

## <a name="cmfcoutlookbarsetbuttonsfont"></a><a name="setbuttonsfont"></a>CMFCOutlookBar::SetButtonsFont

Nastaví písmo textu na tlačítkách panelu aplikace Outlook.

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*písmo*<br/>
[v] Určuje nové písmo.

*bPřekreslit*<br/>
[v] Pokud true, bude panel aplikace Outlook překreslen.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete nastavit písmo pro text zobrazený na tlačítkách stránky karty aplikace Outlook.

## <a name="cmfcoutlookbarsetmode2003"></a><a name="setmode2003"></a>CMFCOutlookBar::SetMode2003

Určuje, zda chování panelu aplikace Outlook napodobuje chování aplikace Outlook 2003.

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>Parametry

*bMode2003*<br/>
[v] Pokud je true, je povolen režim Office 2003.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k povolení nebo zakázání režimu sady Office 2003. V tomto režimu má panel aplikace Outlook další panel nástrojů s tlačítkem přizpůsobení. Chování panelu aplikace Outlook odpovídá chování panelu aplikace Outlook v sadě Microsoft Office 2003.

Ve výchozím nastavení je tento režim zakázán.

> [!NOTE]
> Tato funkce musí být volána před [CMFCOutlookBar::Create](#create).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[Třída CMFCOutlookBarTabctrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[CMFCOutlookBarPane – třída](../../mfc/reference/cmfcoutlookbarpane-class.md)
