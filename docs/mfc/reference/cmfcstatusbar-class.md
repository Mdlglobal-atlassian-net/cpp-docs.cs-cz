---
title: CMFCStatusBar – třída
ms.date: 11/19/2018
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
ms.openlocfilehash: c4891c6bb66fe5e4b737ca9b128a01bcedcf39e7
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176572"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar – třída

`CMFCStatusBar` Třída implementuje stavový řádek podobný `CStatusBar` třídy. Ale `CMFCStatusBar` třída obsahuje funkce, které nejsou nabízeny třídou `CStatusBar` třídy, jako je schopnost zobrazit obrázky, animace a indikátory; a schopnost reagovat na poklepání myši.

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Přepíše [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||
|[CMFCStatusBar::Create](#create)|Ovládací panel vytvoří a připojí ho k [cpane –](../../mfc/reference/cpane-class.md) objektu. (Přepíše [CPane::Create](../../mfc/reference/cpane-class.md#create).)|
|[CMFCStatusBar::CreateEx](#createex)|Ovládací panel vytvoří a připojí ho k [cpane –](../../mfc/reference/cpane-class.md) objektu. (Přepíše [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Určuje, zda jiný podokně můžete dynamicky vložen mezi toto podokno a nadřazeného rámce. (Přepíše [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Povolí nebo zakáže zpracování myši dvakrát klikne na stavovém řádku.|
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|V podokně zadané zobrazí indikátor průběhu.|
|[CMFCStatusBar::GetCount](#getcount)|Vrátí počet podokna na stavovém řádku.|
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar::GetItemID](#getitemid)||
|[CMFCStatusBar::GetItemRect](#getitemrect)||
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|Vrátí podokno style. (Přepíše [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|
|[CMFCStatusBar::GetPaneText](#getpanetext)||
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Vrátí šířku v pixelech, podokna zadané ve stavovém řádku.|
|[CMFCStatusBar::GetTipText](#gettiptext)|Vrátí text tipu nástroj pro zadané podokno ve stavovém řádku.|
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Zruší platnost zadané podokně a překreslí jeho obsah.|
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Volá se rozhraním před vytvořením okna Windows připojených k tomuto `CWnd` objektu. (Přepíše [CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar::SetIndicators](#setindicators)||
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|Přiřadí zadaný podokně animace.|
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|Nastaví barvu pozadí pro podokno zadané ve stavovém řádku.|
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Nastaví ikona indikátoru podokna zadané ve stavovém řádku.|
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|Nastaví aktuální průběh indikátoru průběhu pro zadaný podokno ve stavovém řádku.|
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|Nastaví styl podokna. (Přepíše [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|
|[CMFCStatusBar::SetPaneText](#setpanetext)||
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Nastaví barvu textu pro zadaný podokno ve stavovém řádku.|
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Nastavuje šířku v pixelech podokna zadané ve stavovém řádku.|
|[CMFCStatusBar::SetTipText](#settiptext)|Nastaví text popisu nástroje pro zadaný podokno ve stavovém řádku.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Volá se rozhraním, když ho překreslí podokně ve stavovém řádku.|

## <a name="remarks"></a>Poznámky

Následující diagram znázorňuje obrázek ve stavovém řádku z [stav panelu demonstrační ukázka](../../visual-cpp-samples.md) aplikace.

![Příklad CMFCStatusBar –](../../mfc/reference/media/cmfcstatusbar.png "CMFCStatusBar – příklad")

## <a name="example"></a>Příklad

Následující příklad ukazuje místní proměnné, které aplikace používá k volání různých metodách `CMFCStatusBar` třídy. Tyto proměnné jsou deklarovány v StatusBarDemoView.h. Hlavního rámce je deklarován v MainFrm.h, dokument je deklarován v StatusBarDemoDoc.h a zobrazení je deklarován v StatusBarDemoView.h. Tento fragment kódu je součástí [stav panelu demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak získat odkaz na `CMFCStatusBar` objekt zavedením `GetStatusBar` metoda MainFrm.h a následným voláním této metody z `GetStatusBar` metoda ve StatusBarDemoView.h. Tento fragment kódu je součástí [stav panelu demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob volání různých metodách `CMFCStatusBar` třídy v StatusBarDemoView.cpp. Konstanty jsou deklarovány v MainFrm.h. Tento příklad ukazuje, jak nastavit ikonu, nastaví text popisu tlačítka panelu stavového řádku stav, zobrazí indikátor průběhu na zadané podokně, přiřadit animace do podokna zadaný, nastavit text a šířku panelu stavového řádku stav a nastavit aktuální indikátoru průběhu progr panel upu pro podokno panelu Stav. Tento fragment kódu je součástí [stav panelu demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCStatusBar –](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxstatusbar.h

##  <a name="calcfixedlayout"></a>  CMFCStatusBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

[in] *bStretch*<br/>
[in] *bHorz*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="commandtoindex"></a>  CMFCStatusBar::CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

[in] *nIDFind*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="create"></a>  CMFCStatusBar::Create

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

[in] *pParentWnd*<br/>
[in] *dwStyle*<br/>
[in] *nID*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="createex"></a>  CMFCStatusBar::CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

[in] *pParentWnd*<br/>
[in] *dwCtrlStyle*<br/>
[in] *dwStyle*<br/>
[in] *nID*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="doesallowdyninsertbefore"></a>  CMFCStatusBar::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="enablepanedoubleclick"></a>  CMFCStatusBar::EnablePaneDoubleClick

Povolí nebo zakáže zpracování myši dvakrát klikne na stavovém řádku.

```
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] Pokud je hodnota TRUE, povolte zpracování dvojitým kliknutím myši. V opačném případě zakážete zpracování dvojitým kliknutím myši.

### <a name="remarks"></a>Poznámky

Pokud je stavový řádek je povoleno zpracování dvojité kliknutí, Windows odešle oznámení wm_command – spolu s ID prostředku vlastníkovi stavového řádku pokaždé, když uživatel dvakrát klikne na panelu stavového stav.

##  <a name="enablepaneprogressbar"></a>  CMFCStatusBar::EnablePaneProgressBar

V podokně zadané zobrazí indikátor průběhu.

```
void EnablePaneProgressBar(
    int nIndex,
    long nTotal=100,
    BOOL bDisplayText=FALSE,
    COLORREF clrBar=-1,
    COLORREF clrBarDest=-1,
    COLORREF clrProgressText=-1);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Určuje index podokna jehož indikátor průběhu povolit.

*ncelkový počet*<br/>
[in] Určuje maximální hodnotu indikátor průběhu.

*bDisplayText*<br/>
[in] Určuje, zda by měl indikátor průběhu zobrazit aktuální hodnotu průběh.

*clrBar*<br/>
[in] Určuje barvu pozadí indikátor průběhu.

*clrBarDest*<br/>
[in] Určuje sekundární barvu pozadí panelu průběh. Použít jinou hodnotu než *clrBar* tak, aby vyplnil pomocí barev prolnuty do přechodu.

*clrProgressText*<br/>
[in] Určuje barvu textu indikátor průběhu.

### <a name="remarks"></a>Poznámky

Pokud chcete zakázat volání panelu průběh `EnablePaneProgressBar` s *ncelkový počet* nastavena na hodnotu -1. Ve výchozím nastavení *ncelkový počet* je nastavena na hodnotu 100. Proto není nutné žádné další výpočty, chcete-li zobrazit průběh v procentech.

Je třeba předat různé hodnoty *clrBar* a *clrBarDest* tak, aby barvu pozadí indikátoru průběhu zobrazí barva prolnuty do přechodu. .

Chcete-li nastavit aktuální průběh, zavolejte [CMFCStatusBar::SetPaneProgress](#setpaneprogress) metody.

##  <a name="getcount"></a>  CMFCStatusBar::GetCount

Získá počet podokna ve stavovém řádku.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet podokna ve stavovém řádku.

##  <a name="getdrawextendedarea"></a>  CMFCStatusBar::GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getextendedarea"></a>  CMFCStatusBar::GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

[in] *rect*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getitemid"></a>  CMFCStatusBar::GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getitemrect"></a>  CMFCStatusBar::GetItemRect

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>
[in] *lprect –*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="getpaneinfo"></a>  CMFCStatusBar::GetPaneInfo

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>
[in] *nID*<br/>
[in] *nStyle*<br/>
[in] *cxWidth*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="getpaneprogress"></a>  CMFCStatusBar::GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getpanestyle"></a>  CMFCStatusBar::GetPaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getpanetext"></a>  CMFCStatusBar::GetPaneText

```
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>
[in] *s*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getpanewidth"></a>  CMFCStatusBar::GetPaneWidth

Načte šířku panelu stavového řádku.

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Určuje index panelu stavového řádku stav.

### <a name="return-value"></a>Návratová hodnota

Šířka panelu stavového stav, který *nIndex* určuje; v opačném případě nula, pokud neexistuje panelu stavového řádku.

##  <a name="gettiptext"></a>  CMFCStatusBar::GetTipText

Načtěte text popisku stavovém panelu.

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Určuje index v podokně pro kterou se má načíst text tipu nástroj.

### <a name="return-value"></a>Návratová hodnota

Text popisu tlačítka panelu stavového řádku, který *nIndex* určuje. V opačném případě prázdnému řetězci, pokud neexistuje panelu stavového řádku stavu pro zadaný *nIndex* nebo pokud jeho text popisu je prázdný.

##  <a name="invalidatepanecontent"></a>  CMFCStatusBar::InvalidatePaneContent

Zrušení platnosti panelu stavového řádku stav nebo ho překreslit jeho obsah.

```
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Určuje index v podokně, jejíž obsah má být zrušena a překreslení.

### <a name="remarks"></a>Poznámky

Když stavový řádek zneplatněna, označí se pro překreslení. Windows překreslí ho při `UpdateWindow` metoda odesílá zprávu WM_PAINT `OnPaint` metody.

##  <a name="ondrawpane"></a>  CMFCStatusBar::OnDrawPane

Ho překreslit podokně ve stavovém řádku.

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
[in] Ukazatel na kontext zařízení pro kreslení.

*pPane*<br/>
[in] Ukazatel `CMFCStatusBarPaneInfo` strukturu, která obsahuje informace o podokně tak, aby vyžadovaly překreslení.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `OnDrawPane` překreslí v podokně s použitím kontextu zařízení *primárního řadiče domény* podle stylu a obsah v podokně.

Potlačí tuto metodu v `CMFCStatusBar`-odvozené třídy pro přizpůsobení vzhledu podokno.

##  <a name="precreatewindow"></a>  CMFCStatusBar::PreCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parametry

[in] *cs*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="setdrawextendedarea"></a>  CMFCStatusBar::SetDrawExtendedArea

```
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *bSet*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setindicators"></a>  CMFCStatusBar::SetIndicators

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

[in] *lpIDArray*<br/>
[in] *nIDCount*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="setpaneanimation"></a>  CMFCStatusBar::SetPaneAnimation

Přiřadí zadaný podokně animace.

```
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Určuje index v podokně, ke kterému chcete přiřadit k ní animace.

*hImageList*<br/>
[in] Určuje popisovač pro seznam obrázků, která uchovává snímky animace.

*nFrameRate*<br/>
[in] Určuje frekvenci snímků v milisekundách pro animaci.

*bUpdate*<br/>
[in] Při hodnotě TRUE se aktualizace obsahu podokna okamžitě. V opačném případě se aktualizuje obsah podokně při jeho platnost.

### <a name="remarks"></a>Poznámky

Pokud chcete zakázat aktuální animace, zavolejte `SetPaneAnimation` s `hImageList` nastavena na hodnotu NULL.

##  <a name="setpanebackgroundcolor"></a>  CMFCStatusBar::SetPaneBackgroundColor

Nastaví barvu pozadí panelu stavového řádku stav.

```
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Určuje index v podokně pro kterou chcete nastavit novou barvou pozadí.

*clrBackground*<br/>
[in] Určuje novou barvou pozadí.

*bUpdate*<br/>
[in] Při hodnotě TRUE se aktualizace obsahu podokna okamžitě. Podokno obsahu v opačném případě neaktualizují, dokud podokně zneplatněna jinou metodou.

##  <a name="setpaneicon"></a>  CMFCStatusBar::SetPaneIcon

Nastavte ikonu panelu stavového řádku stav.

```
void SetPaneIcon(
    int nIndex,
    HICON hIcon,
    BOOL bUpdate=TRUE);

void SetPaneIcon(
    int nIndex,
    HBITMAP hBmp,
    COLORREF clrTransparent=RGB(255, 0, 255),
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Určuje index v podokně pro kterou chcete nastavit bitovou kopii.

*hIcon*<br/>
[in] Určuje popisovač ikona nastavit jako obrázek podokna.

*bUpdate*<br/>
[in] Určuje, zda pro aktualizaci obsahu podokna okamžitě.

*hBmp*<br/>
[in] Určuje popisovač rastrový obrázek, nastavit jako obrázek podokna.

*clrTransparent*<br/>
[in] Určuje průhlednou barvu rastrového obrázku, který *hBmp* označuje.

### <a name="remarks"></a>Poznámky

Můžete předat HICON nebo HBITMAP spolu s průhledná barva obrázku v podokně nastavení. Pokud nechcete zobrazit obrázek déle, předejte hodnotu NULL jako popisovač bitové kopie.

Pokud není k dispozici žádné běžící animace, která [CMFCStatusBar::SetPaneAnimation](#setpaneanimation) má nastavení, se zastaví animace.

##  <a name="setpaneinfo"></a>  CMFCStatusBar::SetPaneInfo

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>
[in] *nID*<br/>
[in] *nStyle*<br/>
[in] *cxWidth*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setpaneprogress"></a>  CMFCStatusBar::SetPaneProgress

Nastavte aktuální indikátoru průběhu indikátoru průběhu pro zadaný podokno.

```
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Určuje index v podokně, pro které chcete aktualizovat indikátor průběhu.

*nCurr*<br/>
[in] Určuje aktuální hodnotu indikátor průběhu.

*bUpdate*<br/>
[in] Určuje, zda by měl v podokně okamžitě aktualizovat.

### <a name="remarks"></a>Poznámky

Tuto metodu volejte, pokud chcete aktualizovat indikátoru průběhu pro indikátor průběhu v podokně zadané.

Chcete-li tuto funkci použít pro dané podokno, musíte volat [CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar) první.

##  <a name="setpanestyle"></a>  CMFCStatusBar::SetPaneStyle

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>
[in] *nStyle*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setpanetext"></a>  CMFCStatusBar::SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>
[in] *lpszNewText*<br/>
[in] *bUpdate*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="setpanetextcolor"></a>  CMFCStatusBar::SetPaneTextColor

Nastaví barvu textu zadaného podokna.

```
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Určuje index v podokně, ke kterému chcete přiřadit novou barvu textu.

*clrText*<br/>
[in] Určuje barvu textu.

*bUpdate*<br/>
[in] Při hodnotě TRUE se aktualizace obsahu podokna okamžitě. Podokno obsahu v opačném případě neaktualizují, dokud podokně zneplatněna jinou metodou.

##  <a name="setpanewidth"></a>  CMFCStatusBar::SetPaneWidth

Nastavte šířku panelu stavového řádku stav.

```
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Index podokno panelu Stav, pro kterou chcete nastavit novou šířku.

*CX*<br/>
[in] Novou šířku podokno panelu Stav, v pixelech.

##  <a name="settiptext"></a>  CMFCStatusBar::SetTipText

Nastavte text popisu tlačítka na panelu stavového řádku stav.

```
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Index v podokně, ke kterému chcete přiřadit přejede myší.

*pszTipText*<br/>
[in] Nový text popisku.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CPane – třída](../../mfc/reference/cpane-class.md)<br/>
[CStatusBar – třída](../../mfc/reference/cstatusbar-class.md)
