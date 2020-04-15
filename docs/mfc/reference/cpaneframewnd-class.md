---
title: Třída CPaneFrameWnd
ms.date: 11/04/2016
f1_keywords:
- CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd::AddPane
- AFXPANEFRAMEWND/CPaneFrameWnd::AddRemovePaneFromGlobalList
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustPaneFrames
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcBorderSize
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcExpectedDockedRect
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeAttached
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeDockedToPane
- AFXPANEFRAMEWND/CPaneFrameWnd::CheckGripperVisibility
- AFXPANEFRAMEWND/CPaneFrameWnd::ConvertToTabbedDocument
- AFXPANEFRAMEWND/CPaneFrameWnd::Create
- AFXPANEFRAMEWND/CPaneFrameWnd::CreateEx
- AFXPANEFRAMEWND/CPaneFrameWnd::DockPane
- AFXPANEFRAMEWND/CPaneFrameWnd::FindFloatingPaneByID
- AFXPANEFRAMEWND/CPaneFrameWnd::FrameFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionHeight
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionText
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingMode
- AFXPANEFRAMEWND/CPaneFrameWnd::GetFirstVisiblePane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::GetParent
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPinState
- AFXPANEFRAMEWND/CPaneFrameWnd::GetRecentFloatingRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetVisiblePaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::HitTest
- AFXPANEFRAMEWND/CPaneFrameWnd::IsCaptured
- AFXPANEFRAMEWND/CPaneFrameWnd::IsDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollDown
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollUp
- AFXPANEFRAMEWND/CPaneFrameWnd::KillDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::LoadState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnBeforeDock
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDockToRecentPos
- AFXPANEFRAMEWND/CPaneFrameWnd::OnKillRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnMovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::OnPaneRecalcLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::OnSetRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnShowPane
- AFXPANEFRAMEWND/CPaneFrameWnd::PaneFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::Pin
- AFXPANEFRAMEWND/CPaneFrameWnd::RedrawAll
- AFXPANEFRAMEWND/CPaneFrameWnd::RemoveNonValidPanes
- AFXPANEFRAMEWND/CPaneFrameWnd::RemovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::ReplacePane
- AFXPANEFRAMEWND/CPaneFrameWnd::SaveState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetCaptionButtons
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::SetPreDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SizeToContent
- AFXPANEFRAMEWND/CPaneFrameWnd::StartTearOff
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentDockSiteInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentTabRelatedInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::OnCheckRollState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDrawBorder
- AFXPANEFRAMEWND/CPaneFrameWnd::m_bUseSaveBits
helpviewer_keywords:
- CPaneFrameWnd [MFC], AddPane
- CPaneFrameWnd [MFC], AddRemovePaneFromGlobalList
- CPaneFrameWnd [MFC], AdjustLayout
- CPaneFrameWnd [MFC], AdjustPaneFrames
- CPaneFrameWnd [MFC], CalcBorderSize
- CPaneFrameWnd [MFC], CalcExpectedDockedRect
- CPaneFrameWnd [MFC], CanBeAttached
- CPaneFrameWnd [MFC], CanBeDockedToPane
- CPaneFrameWnd [MFC], CheckGripperVisibility
- CPaneFrameWnd [MFC], ConvertToTabbedDocument
- CPaneFrameWnd [MFC], Create
- CPaneFrameWnd [MFC], CreateEx
- CPaneFrameWnd [MFC], DockPane
- CPaneFrameWnd [MFC], FindFloatingPaneByID
- CPaneFrameWnd [MFC], FrameFromPoint
- CPaneFrameWnd [MFC], GetCaptionHeight
- CPaneFrameWnd [MFC], GetCaptionRect
- CPaneFrameWnd [MFC], GetCaptionText
- CPaneFrameWnd [MFC], GetDockingManager
- CPaneFrameWnd [MFC], GetDockingMode
- CPaneFrameWnd [MFC], GetFirstVisiblePane
- CPaneFrameWnd [MFC], GetHotPoint
- CPaneFrameWnd [MFC], GetPane
- CPaneFrameWnd [MFC], GetPaneCount
- CPaneFrameWnd [MFC], GetParent
- CPaneFrameWnd [MFC], GetPinState
- CPaneFrameWnd [MFC], GetRecentFloatingRect
- CPaneFrameWnd [MFC], GetVisiblePaneCount
- CPaneFrameWnd [MFC], HitTest
- CPaneFrameWnd [MFC], IsCaptured
- CPaneFrameWnd [MFC], IsDelayShow
- CPaneFrameWnd [MFC], IsRollDown
- CPaneFrameWnd [MFC], IsRollUp
- CPaneFrameWnd [MFC], KillDockingTimer
- CPaneFrameWnd [MFC], LoadState
- CPaneFrameWnd [MFC], OnBeforeDock
- CPaneFrameWnd [MFC], OnDockToRecentPos
- CPaneFrameWnd [MFC], OnKillRollUpTimer
- CPaneFrameWnd [MFC], OnMovePane
- CPaneFrameWnd [MFC], OnPaneRecalcLayout
- CPaneFrameWnd [MFC], OnSetRollUpTimer
- CPaneFrameWnd [MFC], OnShowPane
- CPaneFrameWnd [MFC], PaneFromPoint
- CPaneFrameWnd [MFC], Pin
- CPaneFrameWnd [MFC], RedrawAll
- CPaneFrameWnd [MFC], RemoveNonValidPanes
- CPaneFrameWnd [MFC], RemovePane
- CPaneFrameWnd [MFC], ReplacePane
- CPaneFrameWnd [MFC], SaveState
- CPaneFrameWnd [MFC], SetCaptionButtons
- CPaneFrameWnd [MFC], SetDelayShow
- CPaneFrameWnd [MFC], SetDockingManager
- CPaneFrameWnd [MFC], SetDockingTimer
- CPaneFrameWnd [MFC], SetDockState
- CPaneFrameWnd [MFC], SetHotPoint
- CPaneFrameWnd [MFC], SetPreDockState
- CPaneFrameWnd [MFC], SizeToContent
- CPaneFrameWnd [MFC], StartTearOff
- CPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
- CPaneFrameWnd [MFC], OnCheckRollState
- CPaneFrameWnd [MFC], OnDrawBorder
- CPaneFrameWnd [MFC], m_bUseSaveBits
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
ms.openlocfilehash: 02eee13928979a7d220ce03f9f61c789c6320b6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364101"
---
# <a name="cpaneframewnd-class"></a>Třída CPaneFrameWnd

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

Implementuje okno mini-frame, které obsahuje jedno podokno. Podokno vyplní klientskou oblast okna.

## <a name="syntax"></a>Syntaxe

```
class CPaneFrameWnd : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPaneFrameWnd::AddPane](#addpane)|Přidá podokno.|
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|Přidá nebo odebere podokno z globálního seznamu.|
|[CPaneFrameWnd::Upravit rozložení](#adjustlayout)|Upraví rozložení okna minirámečku.|
|[CPaneFrameWnd::Upravitpanframeframes](#adjustpaneframes)||
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|Vypočítá velikost ohraničení okna minirámečku.|
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Vypočítejte očekávaný obdélník ukotveného okna.|
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|Určuje, zda lze aktuální podokno ukotvit do jiného podokna nebo okna rámce.|
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Určuje, zda lze okno minirámečku ukotvit do podokna.|
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||
|[CPaneFrameWnd::Převést na tabbeddocument](#converttotabbeddocument)|Převede podokno na dokument s kartami.|
|[CPaneFrameWnd::Vytvořit](#create)|Vytvoří okno minirámečku a připojí `CPaneFrameWnd` ho k objektu.|
|[CPaneFrameWnd::CreateEx](#createex)|Vytvoří okno minirámečku a připojí `CPaneFrameWnd` ho k objektu.|
|[CPaneFrameWnd::DockPane](#dockpane)|Ukotví podokno.|
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|Vyhledá podokno se zadaným ID ovládacího prvku v globálním seznamu plovoucích podoken.|
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|Vyhledá okno minirámečku obsahující bod dodaný uživatelem.|
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|Vrátí výšku titulku okna minirámečku.|
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|Vypočítá ohraničovací obdélník titulku okna minirámečku.|
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|Vrátí text titulku.|
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|Vrátí režim ukotvení.|
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Vrátí první viditelné podokno, které je obsaženo v okně minirámečku.|
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||
|[CPaneFrameWnd::GetPane](#getpane)|Vrátí podokno, které je obsaženo v okně minirámečku.|
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|Vrátí počet podoken, které jsou obsaženy v okně minirámečku.|
|[CPaneFrameWnd::GetParent](#getparent)||
|[CPaneFrameWnd::GetPinState](#getpinstate)||
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Vrátí počet viditelných podoken, které jsou obsaženy v okně minirámečku.|
|[CPaneFrameWnd::HitTest](#hittest)|Určuje, která část okna minirámečku je v daném bodě.|
|[CPaneFrameWnd::IsCaptured](#iscaptured)||
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||
|[CPaneFrameWnd::IsRollDown](#isrolldown)|Určuje, zda má být okno minirámečku srolováno dolů.|
|[CPaneFrameWnd::IsRollUp](#isrollup)|Určuje, zda má být okno minirámečku shráno.|
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|Zastaví dokovací časovač.|
|[CPaneFrameWnd::Stav zatížení](#loadstate)|Načte stav podokna z registru.|
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|Určuje, zda je možné dokování.|
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Ukotví okno minirámečku v poslední poloze.|
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Zastaví souhrn časovače.|
|[CPaneFrameWnd::OnMovePane](#onmovepane)|Přesune okno minirámečku o zadaný posun.|
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Upraví rozložení obsaženého podokna.|
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Nastaví souhrnnou časovač.|
|[CPaneFrameWnd::OnShowPane](#onshowpane)|Volat rámci při podokně v okně mini-frame je skrytý nebo zobrazen.|
|[CPaneFrameWnd::PaneFromPoint](#panefrompoint)|Vrátí podokno, pokud obsahuje uživatelem dodaný bod uvnitř okna minirámce.|
|[CPaneFrameWnd::Pin](#pin)||
|`CPaneFrameWnd::PreTranslateMessage`|Používá třídy [CWinApp](../../mfc/reference/cwinapp-class.md) přeložit okno zprávy před jejich odesláním do [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows funkce.|
|[CPaneFrameWnd::PřekreslitVše](#redrawall)|Překreslí všechna okna s minirámečkem.|
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Volat rámci odebrat neplatná podokna.|
|[CPaneFrameWnd::RemovePane](#removepane)|Odebere podokno z okna minirámečku.|
|[CPaneFrameWnd::ReplacePane](#replacepane)|Nahradí jedno podokno jiným podoknem.|
|[CPaneFrameWnd::Uložitstav](#savestate)|Uloží stav podokna do registru.|
|`CPaneFrameWnd::Serialize`|Přečte nebo zapíše tento objekt z nebo do archivu.|
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|Nastaví tlačítka titulků.|
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|Nastaví dokovací časovač.|
|[CPaneFrameWnd::SetDockState](#setdockstate)|Nastaví stav ukotvení.|
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|Volat rámci nastavit stav předupokování.|
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|Upraví velikost okna minirámečku tak, aby bylo ekvivalentní velikosti s uzavřeným podoknem.|
|[CPaneFrameWnd::StartTearOff](#starttearoff)|Slzy z menu.|
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|Určuje, zda má být okno minirámečku srolováno nahoru nebo dolů.|
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|Nakreslí ohraničení okna minirámečku.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Určuje, zda má být třída okna evidována se stylem třídy CS_SAVEBITS.|

## <a name="remarks"></a>Poznámky

Rozhraní framework automaticky `CPaneFrameWnd` vytvoří objekt při přepnutí podokna z ukotveného stavu do plovoucího stavu.

Okno minirámečku lze přetáhnout s viditelným obsahem (okamžité ukotvení) nebo pomocí obdélníku přetahování (standardní ukotvení). Dokovací režim podokna kontejneru minirámečku určuje chování přetahování minirámečku. Další informace naleznete v tématu [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

Okno minirámečku zobrazuje tlačítka na titulku v souladu se stylem obsaženého podokna. Pokud lze podokno zavřít [(CBasePane::CanBeClosed),](../../mfc/reference/cbasepane-class.md#canbeclosed)zobrazí se tlačítko Zavřít. Pokud má podokno styl AFX_CBRS_AUTO_ROLLUP, zobrazí se špendlík.

Pokud odvodíte třídu z `CPaneFrameWnd`, musíte sdělit rámci, jak ji vytvořit. Buď vytvořte třídu přepsáním [CPane::CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe), nebo nastavte `CPane::m_pMiniFrameRTC` člen tak, aby směřovat k informacím o třídě runtime pro vaši třídu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxPaneFrameWnd.h

## <a name="cpaneframewndaddpane"></a><a name="addpane"></a>CPaneFrameWnd::AddPane

Přidá podokno.

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[v] Podokno, které chcete přidat.

## <a name="cpaneframewndaddremovepanefromgloballist"></a><a name="addremovepanefromgloballist"></a>CPaneFrameWnd::AddRemovePaneFromGlobalList

Přidá nebo odebere podokno z globálního seznamu.

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[v] Podokno, které chcete přidat nebo odebrat.

*bPřidat*<br/>
[v] Pokud je nenulová, přidejte podokno. Pokud 0, odeberte podokno.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla metoda úspěšná; jinak 0.

## <a name="cpaneframewndadjustlayout"></a><a name="adjustlayout"></a>CPaneFrameWnd::Upravit rozložení

Upraví rozložení okna minirámečku.

```
virtual void AdjustLayout();
```

## <a name="cpaneframewndadjustpaneframes"></a><a name="adjustpaneframes"></a>CPaneFrameWnd::Upravitpanframeframes

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndcalcbordersize"></a><a name="calcbordersize"></a>CPaneFrameWnd::CalcBorderSize

Vypočítá velikost ohraničení okna minirámečku.

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>Parametry

*rectBorderSize*<br/>
[out] Obsahuje velikost ohraničení okna minirámečku v obrazových bodech.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci pro výpočet velikosti hranice okna miniframe. Vrácená velikost závisí na tom, zda okno miniframe obsahuje panel nástrojů nebo [CDockablePane](../../mfc/reference/cdockablepane-class.md).

## <a name="cpaneframewndcalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CPaneFrameWnd::CalcExpectedDockedRect

Vypočítejte očekávaný obdélník ukotveného okna.

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Parametry

*pWndToDock*<br/>
[v] Ukazatel na okno do ukotvení.

*ptMouse*<br/>
[v] Umístění myši.

*rectVýsledek*<br/>
[out] Vypočítaný obdélník.

*bDrawTab*<br/>
[out] Pokud true, nakreslete kartu. Pokud false, nenakreslete kartu.

*ppCílový bar*<br/>
[out] Ukazatel na cílové podokno.

### <a name="remarks"></a>Poznámky

Tato metoda vypočítá obdélník, který by okno obsadit, pokud uživatel přetáhl okno do bodu určeného *ptMouse* a ukotvil ji tam.

## <a name="cpaneframewndcanbeattached"></a><a name="canbeattached"></a>CPaneFrameWnd::CanBeAttached

Určuje, zda lze aktuální podokno ukotvit do jiného podokna nebo okna rámce.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud lze podokno ukotvit do jiného okna podokna nebo rámce; jinak FALSE.

## <a name="cpaneframewndcanbedockedtopane"></a><a name="canbedockedtopane"></a>CPaneFrameWnd::CanBeDockedToPane

Určuje, zda lze okno minirámečku ukotvit do podokna.

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>Parametry

*pDockingBar*<br/>
[v] Tabule.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud může být mini-frame ukotven na *pDockingBar*; jinak 0.

## <a name="cpaneframewndcheckgrippervisibility"></a><a name="checkgrippervisibility"></a>CPaneFrameWnd::CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CPaneFrameWnd::Převést na tabbeddocument

Převede podokno na dokument s kartami.

```
virtual void ConvertToTabbedDocument();
```

## <a name="cpaneframewndcreate"></a><a name="create"></a>CPaneFrameWnd::Vytvořit

Vytvoří okno minirámečku a připojí ho k objektu [CPaneFrameWnd.](../../mfc/reference/cpaneframewnd-class.md)

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszNázev_okna*<br/>
[v] Určuje text, který se má zobrazit v okně minirámečku.

*dwStyl*<br/>
[v] Určuje styl okna. Další informace naleznete v [tématu Styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Rect*<br/>
[v] Určuje počáteční velikost a umístění okna minirámečku.

*pParentWnd*<br/>
[dovnitř, ven] Určuje nadřazený rámeček okna minirámečku. Tato hodnota nesmí být null.

*pKontext*<br/>
[dovnitř, ven] Určuje kontext definovaný uživatelem.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo okno úspěšně vytvořeno; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Okno minirámečku je vytvořeno ve dvou krocích. Nejprve rozhraní vytvoří `CPaneFrameWnd` objekt. Za druhé `Create` volá k vytvoření okna miniframe systému Windows a připojit jej k objektu. `CPaneFrameWnd`

## <a name="cpaneframewndcreateex"></a><a name="createex"></a>CPaneFrameWnd::CreateEx

Vytvoří okno minirámečku a připojí ho k objektu [CPaneFrameWnd.](../../mfc/reference/cpaneframewnd-class.md)

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Parametry

*dwStyleEx*<br/>
[v] Určuje styl rozšířeného okna. Další informace naleznete [v tématu Rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

*lpszNázev_okna*<br/>
[v] Určuje text, který se má zobrazit v okně minirámečku.

*dwStyl*<br/>
[v] Určuje styl okna. Další informace naleznete v [tématu Styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Rect*<br/>
[v] Určuje počáteční velikost a umístění okna minirámečku.

*pParentWnd*<br/>
[dovnitř, ven] Určuje nadřazený rámeček okna minirámečku. Tato hodnota nesmí být null.

*pKontext*<br/>
[dovnitř, ven] Určuje kontext definovaný uživatelem.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo okno úspěšně vytvořeno; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Okno minirámečku je vytvořeno ve dvou krocích. Nejprve rozhraní vytvoří `CPaneFrameWnd` objekt. Za druhé `Create` volá k vytvoření okna miniframe systému Windows a připojit jej k objektu. `CPaneFrameWnd`

## <a name="cpaneframewnddockpane"></a><a name="dockpane"></a>CPaneFrameWnd::DockPane

Ukotví podokno.

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>Parametry

*bWasDocked*<br/>
[out] PRAVDA, pokud podokno již bylo ukotveno; jinak FALSE.

### <a name="return-value"></a>Návratová hodnota

Pokud byla operace úspěšná, `CDockablePane` podokno, do kterého bylo podokno ukotveno; jinak NULL.

## <a name="cpaneframewndfindfloatingpanebyid"></a><a name="findfloatingpanebyid"></a>CPaneFrameWnd::FindFloatingPaneByID

Vyhledá podokno se zadaným ID ovládacího prvku v globálním seznamu plovoucích podoken.

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[v] Představuje ID ovládacího prvku podokna najít.

### <a name="return-value"></a>Návratová hodnota

Podokno se zadaným ID ovládacího prvku; v opačném případě null, pokud žádné podokno nemá zadané ID ovládacího prvku.

## <a name="cpaneframewndframefrompoint"></a><a name="framefrompoint"></a>CPaneFrameWnd::FrameFromPoint

Vyhledá okno minirámečku, které obsahuje zadaný bod.

```
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,
    int nSensitivity,
    CPaneFrameWnd* pFrameToExclude = NULL,
    BOOL bFloatMultiOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[v] Bod, na obrazovce souřadnice.

*nCitlivost*<br/>
[v] Zvětšete oblast hledání okna minirámečku o tuto velikost. Okno minirámečku splňuje kritéria vyhledávání, pokud daný bod spadá do zvětšené oblasti.

*pFrameToExclude*<br/>
[v] Určuje okno minirámečku, které má být z hledání vyloučeno.

*bFloatMultiOnly*<br/>
[v] Pokud true, prohledávejte pouze okna s minirámečky, která mají CBRS_FLOAT_MULTI styl. Pokud false, prohledejte všechna okna minirámečků.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno mini-frame, které obsahuje *pt*; jinak NULL.

## <a name="cpaneframewndgetcaptionheight"></a><a name="getcaptionheight"></a>CPaneFrameWnd::GetCaptionHeight

Vrátí výšku titulku okna minirámečku.

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Výška okna minirámečku v pixelech.

### <a name="remarks"></a>Poznámky

Volání této metody k určení výšky okna mini-frame. Ve výchozím nastavení je výška nastavena na SM_CYSMCAPTION. Další informace naleznete v tématu [GetSystemMetrics Function](/windows/win32/api/winuser/nf-winuser-getsystemmetrics).

## <a name="cpaneframewndgetcaptionrect"></a><a name="getcaptionrect"></a>CPaneFrameWnd::GetCaptionRect

Vypočítá ohraničovací obdélník titulku okna minirámečku.

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>Parametry

*rectCaption*<br/>
[out] Obsahuje velikost a umístění popisku okna mini-frame v souřadnicích obrazovky.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci pro výpočet ohraničující obdélník popisek okna mini-frame.

## <a name="cpaneframewndgetcaptiontext"></a><a name="getcaptiontext"></a>CPaneFrameWnd::GetCaptionText

Vrátí text titulku.

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>Návratová hodnota

Text titulku okna minirámečku.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci při zobrazení textu titulku.

## <a name="cpaneframewndgetdockingmanager"></a><a name="getdockingmanager"></a>CPaneFrameWnd::GetDockingManager

```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndgetdockingmode"></a><a name="getdockingmode"></a>CPaneFrameWnd::GetDockingMode

Vrátí režim ukotvení.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Dokovací režim. Jedna z následujících hodnot:

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

## <a name="cpaneframewndgetfirstvisiblepane"></a><a name="getfirstvisiblepane"></a>CPaneFrameWnd::GetFirstVisiblePane

Vrátí první viditelné podokno, které je obsaženo v okně minirámečku.

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>Návratová hodnota

První podokno v okně mini-frame nebo NULL, pokud okno mini-frame neobsahuje žádná podokna.

## <a name="cpaneframewndgethotpoint"></a><a name="gethotpoint"></a>CPaneFrameWnd::GetHotPoint

```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndgetpane"></a><a name="getpane"></a>CPaneFrameWnd::GetPane

Vrátí podokno, které je obsaženo v okně minirámečku.

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>Návratová hodnota

Podokno, které je obsaženo v mini-frame nebo NULL, pokud okno mini-frame neobsahuje žádná podokna.

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndgetpanecount"></a><a name="getpanecount"></a>CPaneFrameWnd::GetPaneCount

Vrátí počet podoken, které jsou obsaženy v okně minirámečku.

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet podoken v okně minirámečku. Tato hodnota může být nula.

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndgetparent"></a><a name="getparent"></a>CPaneFrameWnd::GetParent

```
CWnd* GetParent();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndgetpinstate"></a><a name="getpinstate"></a>CPaneFrameWnd::GetPinState

```
BOOL GetPinState() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndgetrecentfloatingrect"></a><a name="getrecentfloatingrect"></a>CPaneFrameWnd::GetRecentFloatingRect

```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndgetvisiblepanecount"></a><a name="getvisiblepanecount"></a>CPaneFrameWnd::GetVisiblePaneCount

Vrátí počet viditelných podoken, které jsou obsaženy v okně minirámečku.

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet viditelných podoken.

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndhittest"></a><a name="hittest"></a>CPaneFrameWnd::HitTest

Určuje, která část okna minirámečku je v daném bodě.

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
[v] Bod k testování.

*bDetectCaption*<br/>
[v] Pokud true, zkontrolujte bod proti titulek. Pokud nepravda, ignorujte titulek.

### <a name="return-value"></a>Návratová hodnota

Jedna z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|HTNOWHERE|Bod je mimo okno mini-frame.|
|HTCLIENT|Bod je v oblasti klienta.|
|HTCAPTION|Bod je na titulku.|
|HTTOP|Pointa je nahoře.|
|HTTOPLEFT|Bod je vlevo nahoře.|
|HTTOPRIGHT|Bod je vpravo nahoře.|
|HTLEFT|Bod je vlevo.|
|HTRIGHT|Bod je napravo.|
|HTBOTTOM|Bod je dole.|
|HTBOTTOMLEFT|Bod je vlevo dole.|
|HTBOTTOMV|Bod je vpravo dole.|

## <a name="cpaneframewndiscaptured"></a><a name="iscaptured"></a>CPaneFrameWnd::IsCaptured

```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndisdelayshow"></a><a name="isdelayshow"></a>CPaneFrameWnd::IsDelayShow

```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndisrolldown"></a><a name="isrolldown"></a>CPaneFrameWnd::IsRollDown

Určuje, zda má být okno minirámečku srolováno dolů.

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud musí být okno minirámečku srolováno dolů; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci k určení, zda by měl být srolován okno mini-frame. Funkce souhrnu/rozjezdu je povolena pro okno minirámečku, pokud obsahuje alespoň jedno podokno, které má příznak AFX_CBRS_AUTO_ROLLUP. Tento příznak je nastaven při vytvoření podokna. Další informace naleznete v tématu [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Ve výchozím nastavení framework zkontroluje, zda je ukazatel myši uvnitř obdélníku ohraničující okno mini-frame k určení, zda má být okno vráceno dolů. Toto chování můžete přepsat v odvozené třídě.

## <a name="cpaneframewndisrollup"></a><a name="isrollup"></a>CPaneFrameWnd::IsRollUp

Určuje, zda má být okno minirámečku shráno.

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud musí být okno minirámečku srolováno; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci k určení, zda by měl být srolován okno mini-frame. Funkce souhrnu/rozjezdu je povolena pro okno minirámečku, pokud obsahuje alespoň jedno podokno, které má příznak AFX_CBRS_AUTO_ROLLUP. Tento příznak je nastaven při vytvoření podokna. Další informace naleznete v tématu [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Ve výchozím nastavení framework zkontroluje, zda je ukazatel myši uvnitř obdélníku ohraničující okno mini-frame k určení, zda má být okno srolováno. Toto chování můžete přepsat v odvozené třídě.

## <a name="cpaneframewndkilldockingtimer"></a><a name="killdockingtimer"></a>CPaneFrameWnd::KillDockingTimer

Zastaví dokovací časovač.

```
void KillDockingTimer();
```

## <a name="cpaneframewndloadstate"></a><a name="loadstate"></a>CPaneFrameWnd::Stav zatížení

Načte stav podokna z registru.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Název profilu.

*uiID*<br/>
[v] ID podokna.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl stav podokna úspěšně načten; jinak FALSE.

## <a name="cpaneframewndm_busesavebits"></a><a name="m_busesavebits"></a>CPaneFrameWnd::m_bUseSaveBits

Určuje, zda má být registrace třídy okna, která má styl třídy CS_SAVEBITS.

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>Poznámky

Nastavte tento statický člen na HODNOTU TRUE pro registraci třídy okna mini-frame, která má CS_SAVEBITS styl. To může pomoci snížit blikání, když uživatel přetáhne okno mini-frame.

## <a name="cpaneframewndonbeforedock"></a><a name="onbeforedock"></a>CPaneFrameWnd::OnBeforeDock

Určuje, zda je možné dokování.

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je možné dokování; jinak NEPRAVDA.

## <a name="cpaneframewndoncheckrollstate"></a><a name="oncheckrollstate"></a>CPaneFrameWnd::OnCheckRollState

Určuje, zda má být okno minirámečku srolováno nahoru nebo dolů.

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci k určení, zda okno mini-frame by měla být srolována nahoru nebo dolů.

Ve výchozím nastavení framework volá [CPaneFrameWnd::IsRollUp](#isrollup) a [CPaneFrameWnd::IsRollDown](#isrolldown) a pouze roztáhne nebo obnoví okno mini-frame. Tuto metodu můžete přepsat v odvozené třídě a použít jiný vizuální efekt.

## <a name="cpaneframewndondocktorecentpos"></a><a name="ondocktorecentpos"></a>CPaneFrameWnd::OnDockToRecentPos

Ukotví okno minirámečku v poslední poloze.

```
virtual void OnDockToRecentPos();
```

## <a name="cpaneframewndondrawborder"></a><a name="ondrawborder"></a>CPaneFrameWnd::OnDrawBorder

Nakreslí ohraničení okna minirámečku.

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Kontext zařízení slouží k nakreslení ohraničení.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci k nakreslení hranice okna mini-frame.

## <a name="cpaneframewndonkillrolluptimer"></a><a name="onkillrolluptimer"></a>CPaneFrameWnd::OnKillRollUpTimer

Zastaví souhrn časovače.

```
virtual void OnKillRollUpTimer();
```

## <a name="cpaneframewndonmovepane"></a><a name="onmovepane"></a>CPaneFrameWnd::OnMovePane

Přesune okno minirámečku o zadaný posun.

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[v] Ukazatel na podokno (ignorováno).

*ptOffset*<br/>
[v] Posun, o který chcete přesunout podokno.

## <a name="cpaneframewndonpanerecalclayout"></a><a name="onpanerecalclayout"></a>CPaneFrameWnd::OnPaneRecalcLayout

Upraví rozložení podokna uvnitř okna minirámečku.

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto metodu, když musí upravit rozložení podokna uvnitř okna minirámce.

Ve výchozím nastavení je podokno umístěno tak, aby pokrývalo celou klientskou oblast okna minirámečku.

## <a name="cpaneframewndonsetrolluptimer"></a><a name="onsetrolluptimer"></a>CPaneFrameWnd::OnSetRollUpTimer

Nastaví souhrnnou časovač.

```
virtual void OnSetRollUpTimer();
```

## <a name="cpaneframewndonshowpane"></a><a name="onshowpane"></a>CPaneFrameWnd::OnShowPane

Volat rámci při podokně v okně mini-frame je skrytý nebo zobrazen.

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[v] Podokno, které je zobrazeno nebo skryto.

*bZobrazit*<br/>
[v] PRAVDA, pokud je podokno zobrazeno; Nepravda, pokud je podokno skryto.

### <a name="remarks"></a>Poznámky

Volat rámci při podokně v okně mini-frame je zobrazen nebo skrytý. Výchozí implementace neprovede žádné provádění.

## <a name="cpaneframewndpin"></a><a name="pin"></a>CPaneFrameWnd::Pin

```
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>Parametry

[v] *bPin*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndpanefrompoint"></a><a name="panefrompoint"></a>CPaneFrameWnd::PaneFromPoint

Vrátí podokno, pokud obsahuje uživatelem dodaný bod uvnitř okna minirámce.

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
[v] Bod, na který uživatel klepnul, na souřadnicích obrazovky.

*nCitlivost*<br/>
[v] Tento parametr se nepoužívá.

*bCheckVisibility*<br/>
[v] TRUE určit, že by měla být vrácena pouze viditelná podokna; jinak NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

Podokno, na které uživatel klepnul, nebo hodnota NULL, pokud v tomto umístění žádné podokno neexistuje.

### <a name="remarks"></a>Poznámky

Volání této metody získat podokno, které obsahuje daný bod.

## <a name="cpaneframewndredrawall"></a><a name="redrawall"></a>CPaneFrameWnd::PřekreslitVše

Překreslí všechna okna s minirámečkem.

```
static void RedrawAll();
```

### <a name="remarks"></a>Poznámky

Tato metoda aktualizuje všechna okna mini-frame voláním [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) pro každé okno.

## <a name="cpaneframewndremovenonvalidpanes"></a><a name="removenonvalidpanes"></a>CPaneFrameWnd::RemoveNonValidPanes

Volat rámci odebrat neplatná podokna.

```
virtual void RemoveNonValidPanes();
```

## <a name="cpaneframewndremovepane"></a><a name="removepane"></a>CPaneFrameWnd::RemovePane

Odebere podokno z okna minirámečku.

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[v] Ukazatel na podokno odebrat.

*bZničit*<br/>
[v] Určuje, co se stane s oknem minirámečku. Pokud *bDestroy* je PRAVDA, tato metoda zničí okno mini-frame okamžitě. Pokud je FALSE, tato metoda zničí okno mini-frame po určité prodlevě.

*bNoDelayedDestroy*<br/>
[v] Pokud je hodnota TRUE, je zakázáno zpožděné zničení. Pokud false, zpožděné zničení je povoleno.

### <a name="remarks"></a>Poznámky

Rámec může zničit okna mini-rámů okamžitě nebo po určité prodlevě. Pokud chcete zpoždění zničení oken mini-frame, předajte false v *parametru bNoDelayedDestroy.* Opožděné zničení dochází, když rozhraní framework zpracuje zprávu AFX_WM_CHECKEMPTYMINIFRAME.

## <a name="cpaneframewndreplacepane"></a><a name="replacepane"></a>CPaneFrameWnd::ReplacePane

Nahradí jedno podokno jiným podoknem.

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>Parametry

*pBarOrg*<br/>
[v] Ukazatel na původní podokno.

*pBarReplaceWith*<br/>
[v] Ukazatel na podokno, které nahrazuje původní podokno.

## <a name="cpaneframewndsavestate"></a><a name="savestate"></a>CPaneFrameWnd::Uložitstav

Uloží stav podokna do registru.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Název profilu.

*uiID*<br/>
[v] ID podokna.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl stav podokna úspěšně uložen; jinak FALSE.

## <a name="cpaneframewndsetcaptionbuttons"></a><a name="setcaptionbuttons"></a>CPaneFrameWnd::SetCaptionButtons

Nastaví tlačítka titulků.

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>Parametry

*dwTlačítka*<br/>
[v] Bitové nebo kombinace následujících hodnot:

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

## <a name="cpaneframewndsetdelayshow"></a><a name="setdelayshow"></a>CPaneFrameWnd::SetDelayShow

```
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>Parametry

[v] *bDelayZobrazit*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndsetdockingmanager"></a><a name="setdockingmanager"></a>CPaneFrameWnd::SetDockingManager

```
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>Parametry

[v] *pManažer*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndsetdockingtimer"></a><a name="setdockingtimer"></a>CPaneFrameWnd::SetDockingTimer

Nastaví dokovací časovač.

```
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>Parametry

*nTimeOut*<br/>
[v] Hodnota časového času v milisekundách.

## <a name="cpaneframewndsetdockstate"></a><a name="setdockstate"></a>CPaneFrameWnd::SetDockState

Nastaví stav ukotvení.

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>Parametry

*pDockManager*<br/>
[v] Ukazatel na správce ukotvení.

## <a name="cpaneframewndsethotpoint"></a><a name="sethotpoint"></a>CPaneFrameWnd::SetHotPoint

```
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>Parametry

[v] *ptNový*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndsetpredockstate"></a><a name="setpredockstate"></a>CPaneFrameWnd::SetPreDockState

Volat rámci nastavit stav předupokování.

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>Parametry

*preDockState*<br/>
[v] Možné hodnoty:

- PDS_NOTHING,

- PDS_DOCK_REGULAR,

- PDS_DOCK_TO_TAB

*pBarToDock*<br/>
[v] Ukazatel na podokno pro ukotvení.

*dockMethod*<br/>
[v] Dokovací metoda. (Tento parametr je ignorován.)

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je okno minirámečku odpojeno; False, pokud je ukotven.

## <a name="cpaneframewndsizetocontent"></a><a name="sizetocontent"></a>CPaneFrameWnd::SizeToContent

Upraví velikost okna minirámečku tak, aby bylo ekvivalentní uzavřenému podoknu.

```
virtual void SizeToContent();
```

### <a name="remarks"></a>Poznámky

Volání této metody upravit velikost okna mini-frame na velikost obsažené podokno.

## <a name="cpaneframewndstarttearoff"></a><a name="starttearoff"></a>CPaneFrameWnd::StartTearOff

Slzy z menu.

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>Parametry

*pNabídka*<br/>
[v] Ukazatel na nabídku.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; jinak NEPRAVDA.

## <a name="cpaneframewndstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>Parametry

[v] *pBar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpaneframewndstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CPaneFrameWnd::StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Parametry

[v] *pDockingBar*<br/>
[v] *pTabbedBar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)
