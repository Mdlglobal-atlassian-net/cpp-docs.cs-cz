---
title: Cmfcoutlookbartabctrl – třída
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
ms.openlocfilehash: e858d5a481add0f3c6e61175a96a5b27133bf125
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559715"
---
# <a name="cmfcoutlookbartabctrl-class"></a>Cmfcoutlookbartabctrl – třída

Ovládací prvek karty, která má vzhled **navigačním podokně** v aplikaci Microsoft Outlook.
Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.
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
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|Přidá ovládací prvek Windows jako novou kartu na panelu aplikace Outlook.|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Volá se rozhraním, k určení velikosti pole pro úpravy, které se zobrazí, když se uživatel přejmenuje na kartě. (Přepíše `CMFCBaseTabCtrl::CalcRectEdit`.)|
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|Volá se rozhraním, během operací změny velikosti k určení, zda je možné zobrazit méně tlačítka stránky kartu panel aplikace Outlook, než je aktuálně viditelné.|
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|Volá se rozhraním, během operací změny velikosti k určení, zda je možné zobrazit další tlačítka stránky kartu panel aplikace Outlook, než je aktuálně viditelné.|
|[CMFCOutlookBarTabCtrl::Create](#create)|Vytvoří ovládací prvek karty panelu aplikace Outlook.|
|`CMFCOutlookBarTabCtrl::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|Určuje, zda je povoleno animace, který nastává při přepínání mezi aktivní karty.|
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|Určuje, zda uživatel může změnit textové popisky tlačítek kartu panelu aplikace Outlook. (Přepíše [CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|Volá se rozhraním, aby tlačítka, která umožní uživateli procházení tlačítka na podokno panelu aplikace Outlook.|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|Určuje panel, který obsahuje zadaný bod. (Přepíše [CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|Vrátí velikost ohraničení ovládacího prvku Karta aplikace Outlook.|
|`CMFCOutlookBarTabCtrl::GetTabArea`|Načte velikost a umístění od oblasti karet ovládacího prvku karta. (Přepíše [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|
|`CMFCOutlookBarTabCtrl::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|Určuje, zda je povoleno animace, který nastává při přepínání mezi aktivní karty.|
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|Určuje, zda ovládací prvek karty panelu aplikace Outlook je v režimu, který emuluje aplikace Microsoft Outlook 2003.|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Určuje, zda bod uvnitř oblasti karet. (Přepíše [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Určuje, zda je na kartě odpojitelných. (Přepíše [CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable).)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Volá se rozhraním, když na kartě Vložení nebo jejich odebrání. (Přepíše `CMFCBaseTabCtrl::OnChangeTabs`.)|
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|Volá se rozhraním, snižte počet tlačítek stránce kartu, která jsou viditelné.|
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|Volá se rozhraním, zvyšte počet tlačítek stránky kartu, která jsou viditelné.|
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|Zobrazí **Možnosti navigačního podokna** dialogového okna.|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Přepočítá rozložení vnitřní ovládací prvek karty. (Přepíše [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|Nastaví na aktivní kartě. (Přepíše [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|Nastaví velikost ohraničení ovládacího prvku Karta aplikace Outlook.|
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|Nastaví zarovnání textu popisků na kartě tlačítka panelu aplikace Outlook.|
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|Nastavuje rastrový obrázek, který obsahuje ikony, které jsou zobrazeny v dolní části panelu aplikace Outlook v aplikaci Outlook 2003 režimu (viz [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)).|
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>Poznámky

Chcete-li vytvořit panel aplikace Outlook s podporou ukotvení, použijte `CMFCOutlookBar` objektu k hostování aplikace Outlook panelu ovládacího prvku karta. Další informace najdete v tématu [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak inicializovat `CMFCOutlookBarTabCtrl` objektu a použít různé metody v `CMFCOutlookBarTabCtrl` třídy. Tento příklad ukazuje, jak povolit místní úpravy textu popisku na kartu stránky tlačítka panelu aplikace Outlook, povolení animace a povolit posouvání popisovačů, které uživateli umožňuje procházet tlačítka na podokno panelu aplikace Outlook, nastavit velikost ohraničení pokračování kartu aplikace Outlook Rol a nastavte zarovnání popisků text na tlačítkách kartu panelu aplikace Outlook. Tento fragment kódu je součástí [Outlook demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[Cmfcbasetabctrl –](../../mfc/reference/cmfcbasetabctrl-class.md)

[Cmfcoutlookbartabctrl –](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxoutlookbartabctrl.h

##  <a name="addcontrol"></a>  CMFCOutlookBarTabCtrl::AddControl

Přidá ovládací prvek Windows jako novou kartu na panelu aplikace Outlook.

```
void AddControl(
    CWnd* pWndCtrl,
    LPCTSTR lpszName,
    int nImageID=-1,
    BOOL bDetachable=TRUE,
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```

### <a name="parameters"></a>Parametry

*pWndCtrl*<br/>
[in] Ukazatel na ovládací prvek pro přidání.

*lpszName*<br/>
[in] Určuje název karty.

*bDetachable*<br/>
[in] Při hodnotě TRUE se na stránce se vytvoří na jako odpojitelných.

*nImageID*<br/>
[in] Index obrázku v seznamu interní image pro image, který se má zobrazit v nové záložce.

*dwControlBarStyle*<br/>
[in] Určuje styl AFX_ CBRS_ * zabalené ukotvitelných podoken.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte k přidání ovládacího prvku na novou stránku panel aplikace outlook.

Tato funkce volá interně v [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab).

Pokud nastavíte *bDetachable* na hodnotu TRUE, `AddControl` interně vytvoří `CDockablePaneAdapter` objektu a zabalí přidání ovládacího prvku. Automaticky nastaví runtime třídy okna s kartami na třídy modulu runtime `CMFCOutlookBar` a modulu runtime třídy s plovoucí desetinnou čárkou rámečku `CMultiPaneFrameWnd`.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `AddControl` metodu `CMFCOutlookBarTabCtrl` třídy. Tento fragment kódu je součástí [Outlook demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

##  <a name="canshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowFewerPageButtons

Volá se rozhraním, během operace k určení, zda lze zobrazit méně tlačítka stránky kartu panel aplikace Outlook, než je aktuálně viditelné změny velikosti.

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud existuje více než jedno tlačítko; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Ovládací prvek karty panelu aplikace Outlook dynamicky přidá nebo odebere karty ze zobrazení v závislosti na tom, kolik místa je k dispozici. Tato metoda se používá rozhraním, které pomáhají při tomto procesu.

##  <a name="canshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowMorePageButtons

Volá se rozhraním, během operace k určení, zda lze zobrazit další tlačítka stránky kartu panel aplikace Outlook, než je aktuálně viditelné změny velikosti.

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud jsou tlačítka, která nejsou aktuálně viditelné; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Ovládací prvek karty panelu aplikace Outlook dynamicky přidá nebo odebere karty ze zobrazení, v závislosti na tom, kolik místa je k dispozici. Tato metoda se používá rozhraním, které pomáhají při tomto procesu.

##  <a name="create"></a>  CMFCOutlookBarTabCtrl::Create

Vytvoří ovládací prvek karty panelu aplikace Outlook.

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Určuje počáteční velikost a umístění v pixelech.

*pParentWnd*<br/>
[in] Body do nadřazeného okna. Nesmí mít hodnotu NULL.

*nID*<br/>
[in] ID ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud ovládací prvek se úspěšně vytvořila; jinak 0.

### <a name="remarks"></a>Poznámky

Obvykle, ovládací prvky karet panelu aplikace outlook se vytvoří, pokud [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md) řídí zpráva WM_CREATE procesu.

##  <a name="enableanimation"></a>  CMFCOutlookBarTabCtrl::EnableAnimation

Určuje, zda je povoleno animace, který nastává při přepínání mezi aktivní karty.

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] Určuje, zda by měl být animace povoleno nebo zakázáno.

### <a name="remarks"></a>Poznámky

Voláním této funkce můžete povolit nebo zakázat animace. Když uživatel otevře kartu, snímky popisek na stránku nahoru nebo dolů Pokud je povolené animace. Pokud je animace je zakázané, na stránce aktivují okamžitě.

Ve výchozím nastavení je povoleno animace.

##  <a name="enableinplaceedit"></a>  CMFCOutlookBarTabCtrl::EnableInPlaceEdit

Určuje, zda uživatel může změnit textové popisky tlačítek stránky karty panelu aplikace Outlook.

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Pokud je hodnota TRUE, povolte místní úpravy textu popisku. Pokud má hodnotu FALSE, zakažte místní úpravy.

### <a name="remarks"></a>Poznámky

Voláním této funkce můžete povolit nebo zakázat místní úpravy textu popisků na kartě stránky tlačítka. Ve výchozím nastavení je zakázané místní úpravy.

##  <a name="enablescrollbuttons"></a>  CMFCOutlookBarTabCtrl::EnableScrollButtons

Volá se rozhraním umožňující posouvání popisovačů, které uživateli umožňují procházet tlačítka na podokno panelu aplikace Outlook.

```
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] Určuje, zda jsou zobrazena tlačítka pro posunutí.

*bIsUp*<br/>
[in] Určuje, zda je zobrazen posuvník nejvyšší.

*bIsDown*<br/>
[in] Určuje, zda je zobrazen posuvník dolní části.

### <a name="remarks"></a>Poznámky

Umožňuje zobrazovat tlačítka pro posunutí. Tato metoda je volána rozhraním, když se změní na aktivní kartě obnovení tlačítka pro posunutí.

##  <a name="getbordersize"></a>  CMFCOutlookBarTabCtrl::GetBorderSize

Vrátí velikost ohraničení ovládacího prvku Karta aplikace Outlook.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost ohraničení v pixelech.

##  <a name="getvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::GetVisiblePageButtons

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="isanimation"></a>  CMFCOutlookBarTabCtrl::IsAnimation

Určuje, zda je povoleno animace, který nastává při přepínání mezi aktivní karty.

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je povoleno animace; jinak 0.

### <a name="remarks"></a>Poznámky

Volání [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation) funkce k povolení nebo zakázání animace.

##  <a name="ismode2003"></a>  CMFCOutlookBarTabCtrl::IsMode2003

Určuje, zda ovládací prvek karty panelu aplikace Outlook je v režimu, který emuluje aplikace Microsoft Outlook 2003.

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud aplikace Outlook panelu ovládacího prvku karta je v režimu Outlook 2003. v opačném případě FALSE;

### <a name="remarks"></a>Poznámky

Tato hodnota nastavena [CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003).

##  <a name="onshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowFewerPageButtons

Volá se rozhraním, snižte počet tlačítek stránce kartu, která jsou viditelné.

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>Poznámky

Tato metoda přizpůsobí počet tlačítka viditelné stránky karty při změně velikosti ovládacího prvku.

##  <a name="onshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowMorePageButtons

Volá se rozhraním, zvyšte počet tlačítek stránky kartu, která jsou viditelné.

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>Poznámky

Tato metoda upravte počet tlačítek stránce kartu, která jsou viditelné při změně velikosti ovládacího prvku.

##  <a name="onshowoptions"></a>  CMFCOutlookBarTabCtrl::OnShowOptions

Zobrazí **Možnosti navigačního podokna** dialogové okno.

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>Poznámky

**Možnosti navigačního podokna** dialogové okno umožňuje uživateli vyberte požadovanou kartu stránky tlačítka se mají zobrazit a pořadí, ve kterém jsou zobrazeny.

Tato metoda je volána rozhraním, když uživatel vybere **Možnosti navigačního podokna** položky nabídky v nabídce přizpůsobení ovládacího prvku.

##  <a name="setactivetab"></a>  CMFCOutlookBarTabCtrl::SetActiveTab

Nastaví na aktivní kartě. Aktivní karta je ten, který je otevřen v jeho obsahu viditelné.

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>Parametry

*iTab*<br/>
[in] Index založený na nule kartě Otevřít.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zadaný kartu se otevřelo úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Vizuální efekt nastavení na aktivní kartě závisí na tom, jestli jste povolili animace. Další informace najdete v tématu [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation).

##  <a name="setbordersize"></a>  CMFCOutlookBarTabCtrl::SetBorderSize

Nastaví velikost ohraničení ovládacího prvku Karta aplikace Outlook.

```
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>Parametry

*nBorderSize*<br/>
[in] Určuje novou velikost ohraničení v pixelech.

### <a name="remarks"></a>Poznámky

Nastaví novou velikost ohraničení a přepočítá rozložení okna aplikace outlook.

##  <a name="setpagebuttontextalign"></a>  CMFCOutlookBarTabCtrl::SetPageButtonTextAlign

Nastaví zarovnání textu popisků na kartě tlačítka panelu aplikace Outlook.

```
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*uiAlign*<br/>
[in] Určuje zarovnání textu.

*bRedraw*<br/>
[in] Pokud je hodnota TRUE, bude se měl překreslit okno aplikace outlook.

### <a name="remarks"></a>Poznámky

Pomocí této funkce můžete změnit zarovnání textu pro stránky, tlačítka.

*uiAlign* může být jedna z následujících hodnot:

|Konstanta|Význam|
|--------------|-------------|
|TA_LEFT|Zarovnání doleva|
|TA_CENTER|Zarovnání na střed|
|TA_RIGHT|Zarovnání doprava|

Výchozí hodnota je TA_CENTER.

##  <a name="settoolbarimagelist"></a>  CMFCOutlookBarTabCtrl::SetToolbarImageList

Nastavuje rastrový obrázek, který obsahuje ikony, které jsou zobrazeny v dolní části panelu aplikace Outlook v režimu Outlook 2003.

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[in] Určuje ID prostředku bitové kopie k načtení.

*CX*<br/>
[in] Určuje šířku obrázku v seznamu obrázku v pixelech.

*clrTransp*<br/>
[in] Hodnota RGB, která určuje průhlednou barvu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; v opačném případě vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k připojení seznamu obrázků jehož Image se zobrazí na tlačítka na panelu nástrojů v režimu Microsoft Office 2003. Indexy Image musí odpovídat stránky indexy.

Pokud není v režimu Microsoft Office 2003 by neměl volat tuto metodu. Další informace najdete v tématu [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md).

##  <a name="setvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::SetVisiblePageButtons

```
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>Parametry

[in] *nVisiblePageButtons*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCBaseTabCtrl – třída](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarPane – třída](../../mfc/reference/cmfcoutlookbarpane-class.md)
