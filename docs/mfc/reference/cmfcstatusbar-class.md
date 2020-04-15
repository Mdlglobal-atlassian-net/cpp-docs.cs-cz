---
title: Třída CMFCStatusBar
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
ms.openlocfilehash: 8f262d0139b6dffe54e16748ffda4938ba43fc08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366056"
---
# <a name="cmfcstatusbar-class"></a>Třída CMFCStatusBar

Třída `CMFCStatusBar` implementuje stavový řádek `CStatusBar` podobný třídě. `CMFCStatusBar` Třída však má funkce, které `CStatusBar` tato třída nenabízí, například možnost zobrazení obrázků, animací a indikátorů průběhu; a schopnost reagovat na poklepání myší.

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCStavový bar::CalcFixedLayout](#calcfixedlayout)|(Přepíše [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCStavový řádek::Příkaztoindex](#commandtoindex)||
|[CMFCStavový řádek::Vytvořit](#create)|Vytvoří ovládací panel a připojí jej k objektu [CPane.](../../mfc/reference/cpane-class.md) (Přepíše [CPane::Create](../../mfc/reference/cpane-class.md#create).)|
|[CMFCStavový řádek::CreateEx](#createex)|Vytvoří ovládací panel a připojí jej k objektu [CPane.](../../mfc/reference/cpane-class.md) (Přepíše [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|
|[CMFCStatusBar::DoesAllowDynInsertPřed](#doesallowdyninsertbefore)|Určuje, zda lze mezi toto podokno a nadřazený rámec dynamicky vložit jiné podokno. (Přepíše [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Povolí nebo zakáže zpracování poklepání myší na stavovém řádku.|
|[CMFCStavový řádek::EnablePaneProgressBar](#enablepaneprogressbar)|Zobrazí indikátor průběhu v zadaném podokně.|
|[CMFCStavový řádek::GetCount](#getcount)|Vrátí počet podoken na stavovém řádku.|
|[CMFCStavový řádek::GetdrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCStavový řádek::GetItemID](#getitemid)||
|[CMFCStavový bar::GetItemRect](#getitemrect)||
|[CMFCStavový řádek::GetPaneInfo](#getpaneinfo)||
|[CMFCStavový řádek::GetpaneProgress](#getpaneprogress)||
|[CMFCStavový řádek::GetpaneStyle](#getpanestyle)|Vrátí styl podokna. (Přepíše [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|
|[CMFCStavový řádek::GetpaneText](#getpanetext)||
|[CMFCStavový pruh::GetpaneWidth](#getpanewidth)|Vrátí šířku zadaného podokna stavového řádku v obrazových bodech.|
|[CMFCStavový řádek::GetTipText](#gettiptext)|Vrátí text tipu nástroje pro zadané podokno stavového řádku.|
|[CMFCStatusBar::Zneplatnitpanecontent](#invalidatepanecontent)|Zruší platnost zadaného podokna a překreslí jeho obsah.|
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Volat rámci před vytvořením okna systému Windows `CWnd` připojené k tomuto objektu. (Přepíše [CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|
|[CMFCStavový řádek::SetdrawExtendedArea](#setdrawextendedarea)||
|[CMFCStavový řádek:SetIndicators](#setindicators)||
|[CMFCStavový řádek:Setpaneanimation](#setpaneanimation)|Přiřadí animaci zadanému podoknu.|
|[CMFCStavový řádek::SetpaneBackgroundColor](#setpanebackgroundcolor)|Nastaví barvu pozadí pro zadané podokno stavového řádku.|
|[CMFCStavový řádek::SetpaneIcon](#setpaneicon)|Nastaví ikonu indikátoru pro zadané podokno stavového řádku.|
|[CMFCStavový řádek::SetpaneInfo](#setpaneinfo)||
|[CMFCStavový řádek::SetpaneProgress](#setpaneprogress)|Nastaví aktuální průběh indikátoru průběhu pro zadané podokno stavového řádku.|
|[CMFCStavový řádek::SetpaneStyle](#setpanestyle)|Nastaví styl podokna. (Přepíše [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|
|[CMFCStavový řádek::SetpaneText](#setpanetext)||
|[CMFCStavový řádek::SetpanetextColor](#setpanetextcolor)|Nastaví barvu textu pro zadané podokno stavového řádku.|
|[CMFCStavový řádek:SetpaneWidth](#setpanewidth)|Nastaví šířku v obrazových bodech zadaného podokna stavového řádku.|
|[CMFCStavový řádek:SetTipText](#settiptext)|Nastaví text tipu nástroje pro zadané podokno stavového řádku.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCStavový řádek::OnDrawPane](#ondrawpane)|Volat rámci při překreslí podokno stavového řádku.|

## <a name="remarks"></a>Poznámky

Následující diagram znázorňuje obrázek stavového řádku z ukázkové aplikace [stavového řádku.](../../overview/visual-cpp-samples.md)

![Příklad cmfcstatusbaru](../../mfc/reference/media/cmfcstatusbar.png "Příklad cmfcstatusbaru")

## <a name="example"></a>Příklad

Následující příklad ukazuje místní proměnné, které aplikace používá k `CMFCStatusBar` volání různých metod ve třídě. Tyto proměnné jsou deklarovány v StatusBarDemoView.h. Hlavní rámec je deklarován v MainFrm.h, dokument je deklarován v StatusBarDemoDoc.h a zobrazení je deklarováno v StatusBarDemoView.h. Tento fragment kódu je součástí [ukázky ukázky ukázky panelu stavu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak získat `CMFCStatusBar` odkaz na `GetStatusBar` objekt zavedením metody v MainFrm.h `GetStatusBar` a voláním této metody z metody v StatusBarDemoView.h. Tento fragment kódu je součástí [ukázky ukázky ukázky panelu stavu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak volat různé `CMFCStatusBar` metody ve třídě v StatusBarDemoView.cpp. Konstanty jsou deklarovány v MainFrm.h. Příklad ukazuje, jak nastavit ikonu, nastavit text popisku podokna stavového řádku, zobrazit indikátor průběhu v zadaném podokně, přiřadit animaci určenému podoknu, nastavit text a šířku podokna stavového řádku a nastavit indikátor aktuálního průběhu indikátoru průběhu panelu stavového řádku. Tento fragment kódu je součástí [ukázky ukázky ukázky panelu stavu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CmFCStavový pruh](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxstatusbar.h

## <a name="cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCStavový bar::CalcFixedLayout

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

## <a name="cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CMFCStavový řádek::Příkaztoindex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

[v] *nIDNajít*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbarcreate"></a><a name="create"></a>CMFCStavový řádek::Vytvořit

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

[v] *pParentWnd*<br/>
[v] *dwStyl*<br/>
[v] *nID*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbarcreateex"></a><a name="createex"></a>CMFCStavový řádek::CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

[v] *pParentWnd*<br/>
[v] *dwCtrlStyl*<br/>
[v] *dwStyl*<br/>
[v] *nID*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCStatusBar::DoesAllowDynInsertPřed

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a>CMFCStatusBar::EnablePaneDoubleClick

Povolí nebo zakáže zpracování poklepání myší na stavovém řádku.

```
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] Pokud true, povolit zpracování myši poklepáním. V opačném případě zakažte zpracování myši poklepáním.

### <a name="remarks"></a>Poznámky

Pokud je na stavovém řádku povoleno zpracování poklepání, odešle systém Windows oznámení o WM_COMMAND spolu s ID prostředku vlastníkovi stavového řádku pokaždé, když uživatel dvakrát klikne na podokno stavového řádku.

## <a name="cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a>CMFCStavový řádek::EnablePaneProgressBar

Zobrazí indikátor průběhu v zadaném podokně.

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
[v] Určuje index podokna, jehož indikátor průběhu chcete povolit.

*nCelkem*<br/>
[v] Určuje maximální hodnotu indikátoru průběhu.

*bDisplayText*<br/>
[v] Určuje, zda má indikátor průběhu zobrazovat aktuální hodnotu průběhu.

*clrBar*<br/>
[v] Určuje barvu pozadí indikátoru průběhu.

*clrBarDest*<br/>
[v] Určuje sekundární barvu pozadí indikátoru průběhu. Použijte jinou hodnotu než *clrBar* k vyplnění barvou prolnutou do přechodu.

*clrProgressText*<br/>
[v] Určuje barvu textu indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Pokud chcete zakázat volání `EnablePaneProgressBar` indikátoru průběhu s *nTotal* nastaveno na -1. Ve výchozím nastavení je *nTotal* nastaven na 100. Proto nepotřebujete žádné další výpočty k zobrazení průběhu v procentech.

Měli byste předat různé hodnoty pro *clrBar* a *clrBarDest* tak, aby barva pozadí indikátoru průběhu zobrazí barvu prolnutou do přechodu. .

Chcete-li nastavit aktuální průběh, zavolejte metodu [CMFCStatusBar::SetPaneProgress.](#setpaneprogress)

## <a name="cmfcstatusbargetcount"></a><a name="getcount"></a>CMFCStavový řádek::GetCount

Načte počet podoken ve stavovém řádku.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet podoken na stavovém řádku.

## <a name="cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a>CMFCStavový řádek::GetdrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFCStatusBar::GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

[v] *rect*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbargetitemid"></a><a name="getitemid"></a>CMFCStavový řádek::GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[v] *nIndex*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbargetitemrect"></a><a name="getitemrect"></a>CMFCStavový bar::GetItemRect

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

[v] *nIndex*<br/>
[v] *lpRect*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CMFCStavový řádek::GetPaneInfo

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parametry

[v] *nIndex*<br/>
[v] *nID*<br/>
[v] *nStyl*<br/>
[v] *cxWidth*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a>CMFCStavový řádek::GetpaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[v] *nIndex*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a>CMFCStavový řádek::GetpaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[v] *nIndex*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbargetpanetext"></a><a name="getpanetext"></a>CMFCStavový řádek::GetpaneText

```
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[v] *nIndex*<br/>
[v] *s*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a>CMFCStavový pruh::GetpaneWidth

Načte šířku podokna stavového řádku.

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[v] Určuje index podokna stavového řádku.

### <a name="return-value"></a>Návratová hodnota

Šířka podokna stavového řádku, kterou *určuje nIndex;* jinak nula, pokud podokno stavového řádku neexistuje.

## <a name="cmfcstatusbargettiptext"></a><a name="gettiptext"></a>CMFCStavový řádek::GetTipText

Načte text popisku podokna stavového řádku.

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[v] Určuje index podokna, pro které chcete načíst text tipu nástroje.

### <a name="return-value"></a>Návratová hodnota

Text popisku podokna stavového řádku, který *určuje nIndex.* V opačném případě prázdný řetězec, pokud podokno stavového řádku neexistuje pro zadaný *nIndex* nebo pokud je jeho text popisku prázdný.

## <a name="cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a>CMFCStatusBar::Zneplatnitpanecontent

Zneplatnit podokno stavového řádku a překreslit jeho obsah.

```
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[v] Určuje index podokna, jehož obsah má být zneplatněn a překreslen.

### <a name="remarks"></a>Poznámky

Pokud je stavový řádek zrušen, je označen pro překreslení. Systém Windows překreslí, když `UpdateWindow` metoda odešle WM_PAINT zprávu k metodě. `OnPaint`

## <a name="cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a>CMFCStavový řádek::OnDrawPane

Překreslování podokna stavového řádku.

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení pro kreslení.

*pPane*<br/>
[v] Ukazatel na `CMFCStatusBarPaneInfo` strukturu, která obsahuje informace o podokně, které má být překresleno.

### <a name="remarks"></a>Poznámky

Ve výchozím `OnDrawPane` nastavení překreslí podokno pomocí *pDC* kontextu zařízení podle stylu a obsahu podokna.

Přepsat tuto metodu `CMFCStatusBar`v odvozené třídě přizpůsobit vzhled podokna.

## <a name="cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a>CMFCStatusBar::PreCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parametry

[v] *cs*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a>CMFCStavový řádek::SetdrawExtendedArea

```
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

[v] *bSet*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbarsetindicators"></a><a name="setindicators"></a>CMFCStavový řádek:SetIndicators

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

[v] *pole lpIDArray*<br/>
[v] *nIDCount*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a>CMFCStavový řádek:Setpaneanimation

Přiřadí animaci zadanému podoknu.

```
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[v] Určuje index podokna, ke kterému chcete přiřadit animaci.

*hSeznam obrázků*<br/>
[v] Určuje úchyt do seznamu obrázků, který obsahuje snímky animace.

*nFrameRate*<br/>
[v] Určuje kmitočet snímků v milisekundách pro animaci.

*bAktualizovat*<br/>
[v] Pokud true, aktualizovat obsah podokna okamžitě. V opačném případě je obsah podokna aktualizován, pokud je zneplatněn.

### <a name="remarks"></a>Poznámky

Pokud chcete zakázat aktuální animaci, volání `SetPaneAnimation` s `hImageList` nastavenou na hodnotu NULL.

## <a name="cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a>CMFCStavový řádek::SetpaneBackgroundColor

Nastaví barvu pozadí podokna stavového řádku.

```
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[v] Určuje index podokna, pro který chcete nastavit novou barvu pozadí.

*clrPozadí*<br/>
[v] Určuje novou barvu pozadí.

*bAktualizovat*<br/>
[v] Pokud true, aktualizovat obsah podokna okamžitě. V opačném případě neaktualizujte obsah podokna, dokud nebude podokno zneplatněno jinou metodou.

## <a name="cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a>CMFCStavový řádek::SetpaneIcon

Nastavte ikonu podokna stavového řádku.

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
[v] Určuje index podokna, pro které chcete obrázek nastavit.

*hIkona*<br/>
[v] Určuje táhlo na ikonu, která má být nastavena jako obrázek podokna.

*bAktualizovat*<br/>
[v] Určuje, zda má být obsah podokna aktualizován okamžitě.

*hBmp*<br/>
[v] Určuje úchyt pro bitmapu, která má být nastavena jako obraz podokna.

*clrTransparent*<br/>
[v] Určuje průhlednou barvu bitmapy, kterou *hBmp* označuje.

### <a name="remarks"></a>Poznámky

Můžete předat buď HICON nebo HBITMAP spolu s průhlednou barvou pro nastavení obrazu podokna. Pokud již nechcete zobrazit obraz, předejte hodnotu NULL jako popisovač obrázku.

Pokud je spuštěna animace, která [CMFCStatusBar::SetPaneAnimation](#setpaneanimation) má nastavena, animace bude zastavena.

## <a name="cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CMFCStavový řádek::SetpaneInfo

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

[v] *nIndex*<br/>
[v] *nID*<br/>
[v] *nStyl*<br/>
[v] *cxWidth*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a>CMFCStavový řádek::SetpaneProgress

Nastavte indikátor aktuálního průběhu indikátoru průběhu pro zadané podokno.

```
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[v] Určuje index podokna, pro které má být indikátor průběhu aktualizován.

*nCurr*<br/>
[v] Určuje aktuální hodnotu indikátoru průběhu.

*bAktualizovat*<br/>
[v] Určuje, zda má být podokno aktualizováno okamžitě.

### <a name="remarks"></a>Poznámky

Tuto metodu zavolejte, pokud chcete aktualizovat indikátor průběhu indikátoru průběhu v zadaném podokně.

Chcete-li tuto funkci použít pro dané podokno, musíte nejprve zavolat [CMFCStatusBar::EnablePaneProgressBar.](#enablepaneprogressbar)

## <a name="cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CMFCStavový řádek::SetpaneStyle

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

[v] *nIndex*<br/>
[v] *nStyl*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a>CMFCStavový řádek::SetpaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parametry

[v] *nIndex*<br/>
[v] *lpszNewText*<br/>
[v] *bAktualizovat*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a>CMFCStavový řádek::SetpanetextColor

Nastaví barvu textu zadaného podokna.

```
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[v] Určuje index podokna, ke kterému chcete přiřadit novou barvu textu.

*clrText*<br/>
[v] Určuje barvu textu.

*bAktualizovat*<br/>
[v] Pokud true, aktualizovat obsah podokna okamžitě. V opačném případě neaktualizujte obsah podokna, dokud nebude podokno zneplatněno jinou metodou.

## <a name="cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a>CMFCStavový řádek:SetpaneWidth

Nastavte šířku podokna stavového řádku.

```
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[v] Index podokna stavového řádku, pro který chcete nastavit novou šířku.

*Cx*<br/>
[v] Nová šířka podokna stavového řádku v obrazových bodech.

## <a name="cmfcstatusbarsettiptext"></a><a name="settiptext"></a>CMFCStavový řádek:SetTipText

Nastavte text popisku podokna stavového řádku.

```
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[v] Index podokna, ke kterému chcete přiřadit text popisu.

*pszTipText*<br/>
[v] Nový text popisku.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CPane – třída](../../mfc/reference/cpane-class.md)<br/>
[CStatusBar – třída](../../mfc/reference/cstatusbar-class.md)
