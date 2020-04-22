---
title: Třída CMFCOutlookBarTabctrl
ms.date: 10/18/2018
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
ms.openlocfilehash: 9c5d7d5135c3b207bbf113970deb8cbeb186bcca
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749565"
---
# <a name="cmfcoutlookbartabctrl-class"></a>Třída CMFCOutlookBarTabctrl

Ovládací prvek karta, který má vizuální vzhled **navigačního podokna** v aplikaci Microsoft Outlook.
Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|Výchozí konstruktor.|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCOutlookBarTabctrl::AddControl](#addcontrol)|Přidá ovládací prvek systému Windows jako novou kartu na panelu aplikace Outlook.|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Volat rámci k určení rozměry textového pole, které se zobrazí, když `CMFCBaseTabCtrl::CalcRectEdit`uživatel přejmenuje kartu.|
|[CMFCOutlookBarTabctrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|Volat rámci během operací změna velikosti k určení, zda lze zobrazit méně tlačítek panelu aplikace Outlook kartu stránky, než jsou aktuálně viditelné.|
|[CMFCOutlookBarTabctrl::CanShowMorePageButtons](#canshowmorepagebuttons)|Volat rámci během operací změna velikosti k určení, zda více panelu aplikace panel uhlazená tlačítka stránky lze zobrazit, než jsou aktuálně viditelné.|
|[CMFCOutlookBarTabctrl::Vytvořit](#create)|Vytvoří ovládací prvek panelové karty aplikace Outlook.|
|`CMFCOutlookBarTabCtrl::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCOutlookBarTabctrl::EnableAnimation](#enableanimation)|Určuje, zda je povolena animace, ke které dochází při přepínání mezi aktivními kartami.|
|[CMFCOutlookBartabctrl::EnableInplaceEdit](#enableinplaceedit)|Určuje, zda může uživatel upravovat textové popisky na tlačítkách karet na panelu aplikace Outlook. (Přepíše [CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|
|[CMFCOutlookBartabctrl::EnableScrollButtons](#enablescrollbuttons)|Volat rámci povolit tlačítka, která umožňují uživateli procházet tlačítka v podokně panelu aplikace Outlook.|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|Identifikuje podokno, které obsahuje zadaný bod. (Přepíše [CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|
|[CMFCOutlookBartabctrl::GetborderSize](#getbordersize)|Vrátí velikost ohraničení ovládacího prvku karta Outlook.|
|`CMFCOutlookBarTabCtrl::GetTabArea`|Načte velikost a umístění oblasti tabulátoru ovládacího prvku tabulátoru. (Přepíše [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|
|`CMFCOutlookBarTabCtrl::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCOutlookBartabctrl::GetvisiblePageButtons](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabctrl::isanimation](#isanimation)|Určuje, zda je povolena animace, ke které dochází během přepínání mezi aktivními kartami.|
|[CMFCOutlookBarTabctrl::IsMode2003](#ismode2003)|Určuje, zda je ovládací prvek panelové karty aplikace Outlook v režimu, který emuluje aplikaci Microsoft Outlook 2003.|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Určuje, zda je bod uvnitř oblasti tabulátoru. (Přepíše [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Určuje, zda je karta odnímatelná. (Přepíše [CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable).)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Volat rámci při vložení nebo odebrání karty. (Přepíše `CMFCBaseTabCtrl::OnChangeTabs`.)|
|[CMFCOutlookBarTabctrl::onshowFewerPageButtons](#onshowfewerpagebuttons)|Volat rámci snížit počet tlačítek stránky karty, které jsou viditelné.|
|[CMFCOutlookBarTabctrl::onshowMorePageButtons](#onshowmorepagebuttons)|Volat rámci zvýšit počet tlačítek stránky karty, které jsou viditelné.|
|[CMFCOutlookBarTabctrl::onShowOptions](#onshowoptions)|Zobrazí dialogové okno **Možnosti navigačního podokna.**|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Přepočítá vnitřní rozložení ovládacího prvku karta. (Přepíše [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|
|[CMFCOutlookBartabctrl::SetActiveTab](#setactivetab)|Nastaví aktivní kartu.(Přepíše [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|
|[CMFCOutlookBartabctrl::SetBorderSize](#setbordersize)|Nastaví velikost ohraničení ovládacího prvku karta Outlook.|
|[CMFCOutlookBartabctrl::SetPageButtonTextAlign](#setpagebuttontextalign)|Nastaví zarovnání textových popisků na tlačítkách karet na panelu aplikace Outlook.|
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|Nastaví bitmapu obsahující ikony zobrazené v dolní části panelu aplikace Outlook v režimu aplikace Outlook 2003 (viz [třída CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)).|
|[CMFCOutlookBartabctrl::SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>Poznámky

Chcete-li vytvořit panel aplikace Outlook, `CMFCOutlookBar` který podporuje ukotvení, použijte objekt k hostování ovládacího prvku panelu panelu aplikace Outlook. Další informace naleznete v [tématu CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak inicializovat `CMFCOutlookBarTabCtrl` objekt a `CMFCOutlookBarTabCtrl` používat různé metody ve třídě. Příklad ukazuje, jak povolit úpravy textového popisku na tlačítkách stránky karty na panelu aplikace Outlook, povolit animaci, povolit posouvání, které uživateli umožní procházet tlačítka v podokně panelu aplikace Outlook, nastavit velikost ohraničení ovládacího prvku karta Outlook a nastavit zarovnání textových popisků na kartě panelu aplikace Outlook. Tento fragment kódu je součástí [ukázky aplikace Outlook Ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[CmFCOutlookBarTabctrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxoutlookbartabctrl.h

## <a name="cmfcoutlookbartabctrladdcontrol"></a><a name="addcontrol"></a>CMFCOutlookBarTabctrl::AddControl

Přidá ovládací prvek systému Windows jako novou kartu na panelu aplikace Outlook.

```cpp
void AddControl(
    CWnd* pWndCtrl,
    LPCTSTR lpszName,
    int nImageID=-1,
    BOOL bDetachable=TRUE,
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```

### <a name="parameters"></a>Parametry

*pWndCtrl*<br/>
[v] Ukazatel na ovládací prvek, který chcete přidat.

*název lpsz*<br/>
[v] Určuje název karty.

*bOdpojitelný*<br/>
[v] Pokud true, stránka bude vytvořena jako oddělitelné.

*nImageID*<br/>
[v] Index obrázku v seznamu interních obrázků pro obrázek, který má být zobrazen na nové kartě.

*dwControlBarStyle*<br/>
[v] Určuje styl AFX_ CBRS_* pro zabalené dokovací podokna.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k přidání ovládacího prvku jako nové stránky panelu aplikace Outlook.

Tato funkce interně volá [na CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab).

Pokud nastavíte *bOdpojitelný* na `AddControl` `CDockablePaneAdapter` TRUE, interně vytvoří objekt a zalomí přidaný ovládací prvek. Automaticky nastaví třídu runtime okna s kartami `CMFCOutlookBar` na třídu runtime a `CMultiPaneFrameWnd`třídu runtime plovoucího rámce na .

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `AddControl` používat metodu ve `CMFCOutlookBarTabCtrl` třídě. Tento fragment kódu je součástí [ukázky aplikace Outlook Ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

## <a name="cmfcoutlookbartabctrlcanshowfewerpagebuttons"></a><a name="canshowfewerpagebuttons"></a>CMFCOutlookBarTabctrl::CanShowFewerPageButtons

Volat rámci během operací změna velikosti k určení, zda lze zobrazit méně tlačítek panelu aplikace Outlook kartu stránky, než jsou aktuálně viditelné.

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud existuje více než jedno tlačítko; jinak FALSE.

### <a name="remarks"></a>Poznámky

Ovládací prvek panelaplikace Outlook dynamicky přidává nebo odebere karty z displeje v závislosti na tom, kolik místa je k dispozici. Tato metoda se používá v rámci pomoci v tomto procesu.

## <a name="cmfcoutlookbartabctrlcanshowmorepagebuttons"></a><a name="canshowmorepagebuttons"></a>CMFCOutlookBarTabctrl::CanShowMorePageButtons

Volat rámci během operací změna velikosti k určení, zda více panelu aplikace panel uznat tlačítka stránky lze zobrazit, než jsou aktuálně viditelné.

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud existují tlačítka, která nejsou aktuálně viditelná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Ovládací prvek panelaplikace Outlook dynamicky přidává nebo odebere karty z displeje v závislosti na tom, kolik místa je k dispozici. Tato metoda se používá v rámci pomoci v tomto procesu.

## <a name="cmfcoutlookbartabctrlcreate"></a><a name="create"></a>CMFCOutlookBarTabctrl::Vytvořit

Vytvoří ovládací prvek panelové karty aplikace Outlook.

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[v] Určuje počáteční velikost a polohu v obrazových bodech.

*pParentWnd*<br/>
[v] Odkazuje na nadřazené okno. Nesmí být null.

*Nid*<br/>
[v] ID ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl ovládací prvek úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Ovládací prvky karty panelu aplikace Outlook jsou obvykle vytvořeny, když [třída CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md) řídí WM_CREATE zprávu procesu.

## <a name="cmfcoutlookbartabctrlenableanimation"></a><a name="enableanimation"></a>CMFCOutlookBarTabctrl::EnableAnimation

Určuje, zda je povolena animace, ke které dochází při přepínání mezi aktivními kartami.

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] Určuje, zda má být animace povolena nebo zakázána.

### <a name="remarks"></a>Poznámky

Volání této funkce pro povolení a zakázání animace. Když uživatel otevře stránku karty, titulek stránky se posune nahoru nebo dolů, pokud je animace povolena. Pokud je animace zakázána, stránka se okamžitě aktivuje.

Ve výchozím nastavení je animace povolena.

## <a name="cmfcoutlookbartabctrlenableinplaceedit"></a><a name="enableinplaceedit"></a>CMFCOutlookBartabctrl::EnableInplaceEdit

Určuje, zda může uživatel upravovat textové popisky na tlačítkách stránky karty na panelu aplikace Outlook.

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Pokud true, povolte na místě úpravy textového popisku. Pokud nepravda, zakažte úpravy na místě.

### <a name="remarks"></a>Poznámky

Voláním této funkce povolíte nebo zakážete úpravy textových štítků na tlačítkách stránky karty na místě. Ve výchozím nastavení je úpravy na místě zakázány.

## <a name="cmfcoutlookbartabctrlenablescrollbuttons"></a><a name="enablescrollbuttons"></a>CMFCOutlookBartabctrl::EnableScrollButtons

Volat rámci povolit posouvání úchyty, které umožňují uživateli procházet tlačítka v podokně panelu aplikace Outlook.

```cpp
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] Určuje, zda budou zobrazena posuvná tlačítka.

*bIsUp*<br/>
[v] Určuje, zda se zobrazí horní posuvník.

*bIsDown*<br/>
[v] Určuje, zda se zobrazí dolní posuvník.

### <a name="remarks"></a>Poznámky

Umožňuje zobrazení posuvných tlačítek. Tato metoda je volána rámci při změně aktivní kartu obnovit tlačítka posouvání.

## <a name="cmfcoutlookbartabctrlgetbordersize"></a><a name="getbordersize"></a>CMFCOutlookBartabctrl::GetborderSize

Vrátí velikost ohraničení ovládacího prvku karta Outlook.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost ohraničení v pixelech.

## <a name="cmfcoutlookbartabctrlgetvisiblepagebuttons"></a><a name="getvisiblepagebuttons"></a>CMFCOutlookBartabctrl::GetvisiblePageButtons

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcoutlookbartabctrlisanimation"></a><a name="isanimation"></a>CMFCOutlookBarTabctrl::isanimation

Určuje, zda je povolena animace, ke které dochází při přepínání mezi aktivními kartami.

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je animace povolena; jinak 0.

### <a name="remarks"></a>Poznámky

Volání [funkce CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation) pro povolení nebo zakázání animace.

## <a name="cmfcoutlookbartabctrlismode2003"></a><a name="ismode2003"></a>CMFCOutlookBarTabctrl::IsMode2003

Určuje, zda je ovládací prvek panelové karty aplikace Outlook v režimu, který emuluje aplikaci Microsoft Outlook 2003.

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je ovládací prvek panelové karty aplikace Outlook v režimu aplikace Outlook 2003; jinak NEPRAVDA;

### <a name="remarks"></a>Poznámky

Tato hodnota je nastavena [cmfcoutlookbar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003).

## <a name="cmfcoutlookbartabctrlonshowfewerpagebuttons"></a><a name="onshowfewerpagebuttons"></a>CMFCOutlookBarTabctrl::onshowFewerPageButtons

Volat rámci snížit počet tlačítek stránky karty, které jsou viditelné.

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>Poznámky

Tato metoda upraví počet viditelných tlačítek karty stránky při změní velikost ovládacího prvku.

## <a name="cmfcoutlookbartabctrlonshowmorepagebuttons"></a><a name="onshowmorepagebuttons"></a>CMFCOutlookBarTabctrl::onshowMorePageButtons

Volat rámci zvýšit počet tlačítek stránky karty, které jsou viditelné.

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>Poznámky

Tato metoda upravit počet tlačítek stránky karty, které jsou viditelné při velikosti ovládacího prvku.

## <a name="cmfcoutlookbartabctrlonshowoptions"></a><a name="onshowoptions"></a>CMFCOutlookBarTabctrl::onShowOptions

Zobrazí dialogové okno **Možnosti navigačního podokna.**

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>Poznámky

Dialogové okno **Možnosti navigačního podokna** umožňuje uživateli vybrat, která tlačítka stránky karty mají být zobrazena a v jakém pořadí se zobrazí.

Tato metoda je volána v rámci, když uživatel vybere položku nabídky **Možnosti navigačního podokna** z nabídky vlastního nastavení ovládacího prvku.

## <a name="cmfcoutlookbartabctrlsetactivetab"></a><a name="setactivetab"></a>CMFCOutlookBartabctrl::SetActiveTab

Nastaví aktivní kartu. Aktivní karta je ta, která je otevřená a její obsah je viditelný.

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>Parametry

*iTab*<br/>
[v] Nula na základě indexu kartu, která má být otevřena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla zadaná karta úspěšně otevřena; jinak 0.

### <a name="remarks"></a>Poznámky

Vizuální efekt nastavení aktivní karty závisí na tom, zda jste povolili animaci. Další informace naleznete v tématu [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation).

## <a name="cmfcoutlookbartabctrlsetbordersize"></a><a name="setbordersize"></a>CMFCOutlookBartabctrl::SetBorderSize

Nastaví velikost ohraničení ovládacího prvku karta Outlook.

```cpp
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>Parametry

*nBorderSize*<br/>
[v] Určuje novou velikost ohraničení v obrazových bodech.

### <a name="remarks"></a>Poznámky

Nastaví novou velikost ohraničení a přepočítá rozložení okna aplikace Outlook.

## <a name="cmfcoutlookbartabctrlsetpagebuttontextalign"></a><a name="setpagebuttontextalign"></a>CMFCOutlookBartabctrl::SetPageButtonTextAlign

Nastaví zarovnání textových popisků na tlačítkách karet na panelu aplikace Outlook.

```cpp
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*uiAlign*<br/>
[v] Určuje zarovnání textu.

*bPřekreslit*<br/>
[v] Pokud true, okno výhledu bude překreslena.

### <a name="remarks"></a>Poznámky

Tato funkce slouží ke změně zarovnání textu pro tlačítka stránky.

*uiAlign* může být jedna z následujících hodnot:

|Trvalé|Význam|
|--------------|-------------|
|TA_LEFT|Zarovnání vlevo|
|TA_CENTER|Zarovnání na střed|
|TA_RIGHT|Zarovnání vpravo|

Výchozí hodnota je TA_CENTER.

## <a name="cmfcoutlookbartabctrlsettoolbarimagelist"></a><a name="settoolbarimagelist"></a>CMFCOutlookBarTabCtrl::SetToolbarImageList

Nastaví bitmapu obsahující ikony zobrazené v dolní části panelu aplikace Outlook v režimu aplikace Outlook 2003.

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[v] Určuje ID prostředku obrazu, který má být načíst.

*Cx*<br/>
[v] Určuje šířku obrazu v seznamu obrázků v obrazových bodech.

*clrTransp*<br/>
[v] Hodnota RGB, která určuje průhlednou barvu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je úspěšná. v opačném případě vrátí hodnotu NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k připojení seznamu obrázků, jejichž obrázky budou zobrazeny na tlačítkách panelu nástrojů v režimu Sady Microsoft Office 2003. Indexy obrázků by měly odpovídat indexům stránek.

Tato metoda by neměla být volána, pokud není v režimu sady Microsoft Office 2003. Další informace naleznete v [tématu CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="cmfcoutlookbartabctrlsetvisiblepagebuttons"></a><a name="setvisiblepagebuttons"></a>CMFCOutlookBartabctrl::SetVisiblePageButtons

```cpp
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>Parametry

[v] *nVisiblePageButtons*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCBaseTabCtrl – třída](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarPane – třída](../../mfc/reference/cmfcoutlookbarpane-class.md)
