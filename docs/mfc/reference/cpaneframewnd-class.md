---
title: CPaneFrameWnd – třída
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
ms.openlocfilehash: 37ab241219f28336e73ea459a4e32ff413de8964
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502978"
---
# <a name="cpaneframewnd-class"></a>CPaneFrameWnd – třída

Další podrobnosti najdete ve zdrojovém kódu ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.

Implementuje okno se zkráceným rámcem, které obsahuje jedno podokno. Podokno vyplní klientské oblasti okna.

## <a name="syntax"></a>Syntaxe

```
class CPaneFrameWnd : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPaneFrameWnd::AddPane](#addpane)|Přidá podokno.|
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|Přidá nebo odebere podokno z globálního seznamu.|
|[CPaneFrameWnd::AdjustLayout](#adjustlayout)|Upraví rozložení okna se zkrácenými rámečky.|
|[CPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)||
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|Vypočítá velikost ohraničení okna se zkrácenými rámečky.|
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Vypočítá očekávaný obdélník ukotveného okna.|
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|Určuje, zda je možné aktuální podokno ukotvit do jiného podokna nebo okna rámce.|
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Určuje, zda může být okno se zkráceným rámcem ukotveno do podokna.|
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|Převede podokno na dokument s kartami.|
|[CPaneFrameWnd:: Create](#create)|Vytvoří okno se zkráceným rámcem a připojí ho k `CPaneFrameWnd` objektu.|
|[CPaneFrameWnd::CreateEx](#createex)|Vytvoří okno se zkráceným rámcem a připojí ho k `CPaneFrameWnd` objektu.|
|[CPaneFrameWnd::DockPane](#dockpane)|Ukotví podokno.|
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|Najde podokno se zadaným ID ovládacího prvku v globálním seznamu plovoucích podoken.|
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|Najde okno se zkráceným rámcem obsahující uživatelem zadaný bod.|
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|Vrátí výšku nadpisu okna se zkráceným rámcem.|
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|Vypočítá ohraničující rámeček nadpisu okna se zkráceným orámováním.|
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|Vrátí text titulku.|
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|Vrátí režim ukotvení.|
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Vrátí první viditelné podokno, které je obsaženo v okně s minimálním rámcem.|
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||
|[CPaneFrameWnd:: getpodokno](#getpane)|Vrátí podokno, které je obsaženo v okně s minimálním rámcem.|
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|Vrátí počet podoken, která jsou obsažena v okně s minimálním rámcem.|
|[CPaneFrameWnd:: GetParent](#getparent)||
|[CPaneFrameWnd::GetPinState](#getpinstate)||
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Vrátí počet viditelných podoken, které jsou obsaženy v okně s minimálním rámcem.|
|[CPaneFrameWnd::HitTest](#hittest)|Určuje, která část okna se zkráceným rámcem je v daném okamžiku.|
|[CPaneFrameWnd::IsCaptured](#iscaptured)||
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||
|[CPaneFrameWnd::IsRollDown](#isrolldown)|Určuje, zda má být zahrnuto okno se zkráceným snímkem.|
|[CPaneFrameWnd::IsRollUp](#isrollup)|Určuje, zda má být zahrnuto okno se zkráceným snímkem.|
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|Zastaví časovač dokování.|
|[CPaneFrameWnd:: LoadState](#loadstate)|Načte stav podokna z registru.|
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|Určuje, zda je možné ukotvit.|
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Ukotví okno s minimálním rámcem na nejnovější pozici.|
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Zastaví kumulativní časovač.|
|[CPaneFrameWnd::OnMovePane](#onmovepane)|Přesune okno s minimálním rámcem podle zadaného posunu.|
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Upraví rozložení obsaženého podokna.|
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Nastaví časovač souhrnu.|
|[CPaneFrameWnd::OnShowPane](#onshowpane)|Volá se rozhraním, když je podokno v okně s minimálním rámcem skryté nebo zobrazené.|
|[CPaneFrameWnd::P aneFromPoint](#panefrompoint)|Vrátí podokno, pokud obsahuje uživatelem zadaný bod uvnitř okna se zkráceným rámcem.|
|[CPaneFrameWnd::Pin](#pin)||
|`CPaneFrameWnd::PreTranslateMessage`|Používá se třídou [CWinApp](../../mfc/reference/cwinapp-class.md) k překladu zpráv oken před odesláním do funkcí Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) .|
|[CPaneFrameWnd::RedrawAll](#redrawall)|Překreslí všechna okna se zkrácenými rámečky.|
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Volá se rozhraním, aby se odebraly neplatná podokna.|
|[CPaneFrameWnd::RemovePane](#removepane)|Odebere podokno z okna se zkráceným snímkem.|
|[CPaneFrameWnd::ReplacePane](#replacepane)|Nahradí jedno podokno jiným.|
|[CPaneFrameWnd:: SaveState](#savestate)|Uloží stav podokna do registru.|
|`CPaneFrameWnd::Serialize`|Přečte nebo zapisuje tento objekt z nebo do archivu.|
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|Nastaví tlačítka titulků.|
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|Nastaví časovač dokování.|
|[CPaneFrameWnd::SetDockState](#setdockstate)|Nastaví stav ukotvení.|
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|Volá se rozhraním, aby se nastavil stav předvysunutí.|
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|Upraví velikost okna se zkráceným rámcem tak, aby byla stejná jako velikost v seznamu obsažených.|
|[CPaneFrameWnd::StartTearOff](#starttearoff)|Trhlina z nabídky|
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|Určuje, zda má být zahrnuto nebo nižší okno se zkráceným snímkem.|
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|Vykreslí ohraničení okna se zkráceným rámcem.|

### <a name="data-members"></a>Datové členy

|Name|Popis|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Určuje, zda se má zaregistrovat Třída okna se stylem třídy CS_SAVEBITS.|

## <a name="remarks"></a>Poznámky

Rozhraní automaticky vytvoří `CPaneFrameWnd` objekt, když je podokno přepnuto z ukotveného stavu do plovoucího stavu.

Okno s malým rámcem lze přetáhnout se zobrazeným obsahem (bezprostřední ukotvení) nebo pomocí obdélníku přetažení (standardní ukotvení). Režim ukotvení podokna kontejneru pro minimální snímek určuje chování při přetahování na Mini snímek. Další informace najdete v tématu [CBasePane:: GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

Okno se zkráceným rámcem zobrazuje tlačítka na popisku v souladu se stylem obsaženým v podokně. Pokud je podokno možné zavřít ( [CBasePane:: CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), zobrazí se tlačítko Zavřít. Pokud má podokno styl AFX_CBRS_AUTO_ROLLUP, zobrazí se kód PIN.

Pokud třídu Odvozujete z `CPaneFrameWnd`, je nutné sdělit rozhraní Framework, jak ho vytvořit. Buď vytvořte třídu přepsáním [CPane:: CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe), nebo nastavte `CPane::m_pMiniFrameRTC` člena tak, aby odkazoval na informace třídy modulu runtime pro vaši třídu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxPaneFrameWnd. h

##  <a name="addpane"></a>CPaneFrameWnd::AddPane

Přidá podokno.

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Podokno, které se má přidat

##  <a name="addremovepanefromgloballist"></a>CPaneFrameWnd::AddRemovePaneFromGlobalList

Přidá nebo odebere podokno z globálního seznamu.

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Podokno, které se má přidat nebo odebrat

*bAdd*<br/>
pro Pokud není nula, přidejte podokno. Pokud je 0, odeberte podokno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla metoda úspěšná; v opačném případě 0.

##  <a name="adjustlayout"></a>CPaneFrameWnd::AdjustLayout

Upraví rozložení okna se zkrácenými rámečky.

```
virtual void AdjustLayout();
```

##  <a name="adjustpaneframes"></a>CPaneFrameWnd::AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Poznámky

##  <a name="calcbordersize"></a>CPaneFrameWnd::CalcBorderSize

Vypočítá velikost ohraničení okna miniframe.

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>Parametry

*rectBorderSize*<br/>
mimo Obsahuje velikost ohraničení okna miniframe v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním pro výpočet velikosti ohraničení okna miniframe. Vrácená velikost závisí na tom, zda okno miniframe obsahuje panel nástrojů nebo [CDockablePane](../../mfc/reference/cdockablepane-class.md).

##  <a name="calcexpecteddockedrect"></a>CPaneFrameWnd::CalcExpectedDockedRect

Vypočítá očekávaný obdélník ukotveného okna.

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
pro Ukazatel na ukotvení okna.

*ptMouse*<br/>
pro Umístění myši.

*rectResult*<br/>
mimo Počítaný obdélník.

*bDrawTab*<br/>
mimo Pokud má hodnotu TRUE, nakreslete kartu. Pokud je hodnota FALSE, Nekreslete kartu.

*ppTargetBar*<br/>
mimo Ukazatel na cílové podokno.

### <a name="remarks"></a>Poznámky

Tato metoda vypočítá obdélník, který by okno zabíralo, pokud uživatel přetáhl okno do bodu určeného parametrem *ptMouse* a jeho ukotvený tam.

##  <a name="canbeattached"></a>CPaneFrameWnd::CanBeAttached

Určuje, zda je možné aktuální podokno ukotvit do jiného podokna nebo okna rámce.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je podokno možné ukotvit do jiného podokna nebo okna rámce; v opačném případě FALSE.

##  <a name="canbedockedtopane"></a>CPaneFrameWnd::CanBeDockedToPane

Určuje, zda může být okno se zkráceným rámcem ukotveno do podokna.

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>Parametry

*pDockingBar*<br/>
pro Podokno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je mini rámec možné ukotvit na *pDockingBar*; v opačném případě 0.

##  <a name="checkgrippervisibility"></a>CPaneFrameWnd::CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>Poznámky

##  <a name="converttotabbeddocument"></a>CPaneFrameWnd::ConvertToTabbedDocument

Převede podokno na dokument s kartami.

```
virtual void ConvertToTabbedDocument();
```

##  <a name="create"></a>CPaneFrameWnd:: Create

Vytvoří okno miniframe a připojí ho k objektu [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) .

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszWindowName*<br/>
pro Určuje text, který se má zobrazit v okně miniframe.

*dwStyle*<br/>
pro Určuje styl okna. Další informace naleznete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*OBD*<br/>
pro Určuje počáteční velikost a polohu okna miniframe.

*pParentWnd*<br/>
[in, out] Určuje nadřazený rámec okna miniframe. Tato hodnota nesmí být NULL.

*pContext*<br/>
[in, out] Určuje uživatelsky definovaný kontext.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud bylo okno úspěšně vytvořeno; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Okno miniframe se vytvoří ve dvou krocích. Nejprve rozhraní vytvoří `CPaneFrameWnd` objekt. Za druhé volá `Create` , aby se vytvořilo okno Windows miniframe a připojilo se `CPaneFrameWnd` k objektu.

##  <a name="createex"></a>CPaneFrameWnd::CreateEx

Vytvoří okno miniframe a připojí ho k objektu [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) .

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
pro Určuje rozšířený styl okna. Další informace najdete v tématu [Rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) .

*lpszWindowName*<br/>
pro Určuje text, který se má zobrazit v okně miniframe.

*dwStyle*<br/>
pro Určuje styl okna. Další informace naleznete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*OBD*<br/>
pro Určuje počáteční velikost a polohu okna miniframe.

*pParentWnd*<br/>
[in, out] Určuje nadřazený rámec okna miniframe. Tato hodnota nesmí být NULL.

*pContext*<br/>
[in, out] Určuje uživatelsky definovaný kontext.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud bylo okno úspěšně vytvořeno; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Okno miniframe se vytvoří ve dvou krocích. Nejprve rozhraní vytvoří `CPaneFrameWnd` objekt. Za druhé volá `Create` , aby se vytvořilo okno Windows miniframe a připojilo se `CPaneFrameWnd` k objektu.

##  <a name="dockpane"></a>CPaneFrameWnd::D ockPane

Ukotví podokno.

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>Parametry

*bWasDocked*<br/>
mimo TRUE, pokud je podokno již ukotveno; v opačném případě FALSE.

### <a name="return-value"></a>Návratová hodnota

Pokud byla operace úspěšná, `CDockablePane` bylo ukotveno podokno, na kterém bylo ukotveno. v opačném případě hodnota null.

##  <a name="findfloatingpanebyid"></a>CPaneFrameWnd::FindFloatingPaneByID

Najde podokno se zadaným ID ovládacího prvku v globálním seznamu plovoucích podoken.

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
pro Představuje ID ovládacího prvku podokna, které se má najít.

### <a name="return-value"></a>Návratová hodnota

Podokno se zadaným ID ovládacího prvku; v opačném případě NULL, pokud žádné podokno nemá zadané ID ovládacího prvku.

##  <a name="framefrompoint"></a>CPaneFrameWnd::FrameFromPoint

Najde okno se zkráceným rámcem, které obsahuje zadaný bod.

```
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,
    int nSensitivity,
    CPaneFrameWnd* pFrameToExclude = NULL,
    BOOL bFloatMultiOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*bodů*<br/>
pro Bod v souřadnicích obrazovky.

*nSensitivity*<br/>
pro Zvětšete oblast hledání okna s minimálním rámcem podle této velikosti. Okno s minimálním snímkem splňuje kritéria hledání, pokud daný bod spadá do zvýšené oblasti.

*pFrameToExclude*<br/>
pro Určuje okno se zkráceným rámcem, které se má vyloučit z hledání.

*bFloatMultiOnly*<br/>
pro Je-li nastavena hodnota TRUE, prohledejte pouze okna se zkrácenými rámečky, která mají styl CBRS_FLOAT_MULTI. Pokud je hodnota FALSE, prohledejte všechna okna se zkrácenými rámečky.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno se zkrácenými rámečky, které obsahuje *PT*; jinak NULL.

##  <a name="getcaptionheight"></a>CPaneFrameWnd::GetCaptionHeight

Vrátí výšku nadpisu okna se zkráceným rámcem.

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Výška okna se zkráceným rámcem v pixelech.

### <a name="remarks"></a>Poznámky

Voláním této metody určíte výšku okna se zkrácenými rámečky. Ve výchozím nastavení je výška nastavená na SM_CYSMCAPTION. Další informace najdete v tématu [funkce GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics).

##  <a name="getcaptionrect"></a>CPaneFrameWnd::GetCaptionRect

Vypočítá ohraničující rámeček nadpisu okna se zkráceným orámováním.

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>Parametry

*rectCaption*<br/>
mimo Obsahuje velikost a polohu nadpisu okna se zkráceným rámečkem, v souřadnicích obrazovky.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním pro výpočet ohraničujícího obdélníku nadpisu okna se zkráceným orámováním.

##  <a name="getcaptiontext"></a>CPaneFrameWnd::GetCaptionText

Vrátí text titulku.

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>Návratová hodnota

Text titulku okna s minimálním rámcem

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, když zobrazuje text titulku.

##  <a name="getdockingmanager"></a>CPaneFrameWnd::GetDockingManager

```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getdockingmode"></a>CPaneFrameWnd::GetDockingMode

Vrátí režim ukotvení.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Režim ukotvení. Jedna z následujících hodnot:

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

##  <a name="getfirstvisiblepane"></a>CPaneFrameWnd::GetFirstVisiblePane

Vrátí první viditelné podokno, které je obsaženo v okně s minimálním rámcem.

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>Návratová hodnota

První podokno v okně s minimálním rámcem nebo hodnotu NULL, pokud okno se zkráceným rámcem neobsahuje žádná podokna.

##  <a name="gethotpoint"></a>CPaneFrameWnd::GetHotPoint

```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getpane"></a>CPaneFrameWnd:: getpodokno

Vrátí podokno, které je obsaženo v okně s minimálním rámcem.

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>Návratová hodnota

Podokno, které je obsaženo ve zkráceném snímku, nebo hodnotu NULL, pokud okno se zkráceným rámcem neobsahuje žádná podokna.

### <a name="remarks"></a>Poznámky

##  <a name="getpanecount"></a>CPaneFrameWnd::GetPaneCount

Vrátí počet podoken, která jsou obsažena v okně s minimálním rámcem.

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet podoken v okně s minimálním rámcem Tato hodnota může být nulová.

### <a name="remarks"></a>Poznámky

##  <a name="getparent"></a>CPaneFrameWnd:: GetParent

```
CWnd* GetParent();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getpinstate"></a>CPaneFrameWnd::GetPinState

```
BOOL GetPinState() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getrecentfloatingrect"></a>CPaneFrameWnd::GetRecentFloatingRect

```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getvisiblepanecount"></a>CPaneFrameWnd::GetVisiblePaneCount

Vrátí počet viditelných podoken, které jsou obsaženy v okně s minimálním rámcem.

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet viditelných podoken.

### <a name="remarks"></a>Poznámky

##  <a name="hittest"></a>CPaneFrameWnd::HitTest

Určuje, která část okna se zkráceným rámcem je v daném okamžiku.

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
pro Bod, který chcete otestovat.

*bDetectCaption*<br/>
pro Je-li nastavena hodnota TRUE, obraťte se na titulek k tomuto titulku. Pokud je hodnota FALSE, ignorujte titulek.

### <a name="return-value"></a>Návratová hodnota

Jedna z následujících hodnot:

|Value|Význam|
|-----------|-------------|
|HTNOWHERE|Bod je mimo okno se zkráceným rámcem.|
|HTCLIENT|Bod je v oblasti klienta.|
|HTCAPTION|Bod je na popisku.|
|HTTOP|Bod je v horní části.|
|HTTOPLEFT|Bod je v levém horním rohu.|
|HTTOPRIGHT|Bod je v pravém horním rohu.|
|HTLEFT|Bod je vlevo.|
|HTRIGHT|Bod je napravo.|
|HTBOTTOM|Bod je v dolní části.|
|HTBOTTOMLEFT|Bod je v levém dolním rohu.|
|HTBOTTOMRIGHT|Bod je v pravém dolním rohu.|

##  <a name="iscaptured"></a>CPaneFrameWnd::-Captured

```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="isdelayshow"></a>CPaneFrameWnd::IsDelayShow

```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="isrolldown"></a>CPaneFrameWnd::IsRollDown

Určuje, zda má být zahrnuto okno se zkráceným snímkem.

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je nutné rozčlenit okno se zkráceným snímkem; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, aby bylo možné určit, zda by mělo být rozděleno okno se zkrácenými snímky. Funkce Rollup/rolldown je povolená pro okno se zkráceným rámcem, pokud obsahuje aspoň jedno podokno s příznakem AFX_CBRS_AUTO_ROLLUP. Tento příznak je nastaven při vytvoření podokna. Další informace najdete v tématu [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Ve výchozím nastavení Framework kontroluje, zda je ukazatel myši uvnitř ohraničujícího rámečku okna s minimálním rámcem, aby bylo možné zjistit, zda je okno nutné rozčlenit. Toto chování můžete přepsat v odvozené třídě.

##  <a name="isrollup"></a>CPaneFrameWnd::-RollUp

Určuje, zda má být zahrnuto okno se zkráceným snímkem.

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud musí být zahrnuto okno se zkráceným snímkem; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, aby bylo možné určit, zda má být zahrnuto okno se zkráceným snímkem. Funkce Rollup/rolldown je povolená pro okno se zkráceným rámcem, pokud obsahuje aspoň jedno podokno s příznakem AFX_CBRS_AUTO_ROLLUP. Tento příznak je nastaven při vytvoření podokna. Další informace najdete v tématu [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Ve výchozím nastavení Framework kontroluje, zda je ukazatel myši uvnitř ohraničujícího obdélníkového okna, aby bylo možné určit, zda má být okno zahrnuto. Toto chování můžete přepsat v odvozené třídě.

##  <a name="killdockingtimer"></a>CPaneFrameWnd::KillDockingTimer

Zastaví časovač dokování.

```
void KillDockingTimer();
```

##  <a name="loadstate"></a>CPaneFrameWnd:: LoadState

Načte stav podokna z registru.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
pro Název profilu.

*uiID*<br/>
pro ID podokna

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byl stav podokna úspěšně načten; v opačném případě FALSE.

##  <a name="m_busesavebits"></a>CPaneFrameWnd::m_bUseSaveBits

Určuje, zda má být registrována třída okna, která má styl třídy CS_SAVEBITS.

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>Poznámky

Nastavte tohoto statického člena na hodnotu TRUE, chcete-li zaregistrovat třídu okna se zkrácenými rámečky, která má styl CS_SAVEBITS. To může přispět k omezení blikání, když uživatel přetáhne okno se zkrácenými snímky.

##  <a name="onbeforedock"></a>CPaneFrameWnd::OnBeforeDock

Určuje, zda je možné ukotvit.

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je možné docking; v opačném případě FALSE.

##  <a name="oncheckrollstate"></a>CPaneFrameWnd::OnCheckRollState

Určuje, zda má být zahrnuto nebo nižší okno se zkráceným snímkem.

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, aby bylo možné určit, zda má být zahrnuto nebo dolů okno se zkrácenými snímky.

Ve výchozím nastavení rozhraní volá [CPaneFrameWnd::-Rollup](#isrollup) a [CPaneFrameWnd:: IsRollDown](#isrolldown) a právě roztáhne nebo obnoví okno s minimálním snímkem. Tuto metodu můžete přepsat v odvozené třídě, aby používala jiný vizuální efekt.

##  <a name="ondocktorecentpos"></a>  CPaneFrameWnd::OnDockToRecentPos

Ukotví okno s minimálním rámcem na nejnovější pozici.

```
virtual void OnDockToRecentPos();
```

##  <a name="ondrawborder"></a>CPaneFrameWnd::OnDrawBorder

Vykreslí ohraničení okna se zkráceným rámcem.

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Kontext zařízení použitý k vykreslení ohraničení.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, aby vykreslila ohraničení okna se zkráceným rámcem.

##  <a name="onkillrolluptimer"></a>CPaneFrameWnd::OnKillRollUpTimer

Zastaví kumulativní časovač.

```
virtual void OnKillRollUpTimer();
```

##  <a name="onmovepane"></a>CPaneFrameWnd::OnMovePane

Přesune okno s minimálním rámcem podle zadaného posunu.

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
pro Ukazatel na podokno (ignorováno).

*ptOffset*<br/>
pro Posun, kterým má být podokno přesunuto.

##  <a name="onpanerecalclayout"></a>CPaneFrameWnd::OnPaneRecalcLayout

Upraví rozložení podokna uvnitř okna se zkráceným rámcem.

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když musí upravit rozložení podokna uvnitř okna se zkrácenými snímky.

Ve výchozím nastavení je podokno umístěno tak, aby pokrylo celou klientskou oblast okna s minimálním rámcem.

##  <a name="onsetrolluptimer"></a>CPaneFrameWnd::OnSetRollUpTimer

Nastaví časovač souhrnu.

```
virtual void OnSetRollUpTimer();
```

##  <a name="onshowpane"></a>CPaneFrameWnd::OnShowPane

Volá se rozhraním, když je podokno v okně s minimálním rámcem skryté nebo zobrazené.

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
pro Podokno, které se zobrazuje nebo je skryto.

*bShow*<br/>
pro TRUE, pokud se zobrazuje podokno; FALSE, pokud je podokno skryto.

### <a name="remarks"></a>Poznámky

Volá se rozhraním, když se zobrazí nebo skryje podokno v okně s minimálním rámcem. Výchozí implementace neprovádí žádnou akci.

##  <a name="pin"></a>CPaneFrameWnd::P v

```
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>Parametry

pro *bPin*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="panefrompoint"></a>CPaneFrameWnd::P aneFromPoint

Vrátí podokno, pokud obsahuje uživatelem zadaný bod uvnitř okna se zkráceným rámcem.

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
pro Bod, na který uživatel kliknul, v souřadnicích obrazovky.

*nSensitivity*<br/>
pro Tento parametr se nepoužívá.

*bCheckVisibility*<br/>
pro TRUE, pokud chcete určit, že se mají vracet jenom viditelná podokna; v opačném případě FALSE.

### <a name="return-value"></a>Návratová hodnota

Podokno, na které uživatel kliknul, nebo hodnotu NULL, pokud v daném umístění neexistuje žádné podokno.

### <a name="remarks"></a>Poznámky

Voláním této metody získáte podokno, které obsahuje daný bod.

##  <a name="redrawall"></a>CPaneFrameWnd::RedrawAll

Překreslí všechna okna se zkrácenými rámečky.

```
static void RedrawAll();
```

### <a name="remarks"></a>Poznámky

Tato metoda aktualizuje všechna okna se zkráceným rámcem voláním [CWnd:: RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) pro každé okno.

##  <a name="removenonvalidpanes"></a>CPaneFrameWnd::RemoveNonValidPanes

Volá se rozhraním, aby se odebraly neplatná podokna.

```
virtual void RemoveNonValidPanes();
```

##  <a name="removepane"></a>CPaneFrameWnd::RemovePane

Odebere podokno z okna se zkráceným snímkem.

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Ukazatel na podokno, které se má odebrat

*bDestroy*<br/>
pro Určuje, co se stane s oknem se zkráceným snímkem. Pokud má *bDestroy* hodnotu true, tato metoda okamžitě odstraní okno se zkráceným rámcem. Pokud je hodnota FALSE, tato metoda po určité prodlevě odstraní okno se zkráceným rámcem.

*bNoDelayedDestroy*<br/>
pro Při hodnotě TRUE je zpoždění zničení zakázané. Je-li nastaveno na hodnotu FALSE, je povoleno zpožděné zničení.

### <a name="remarks"></a>Poznámky

Rozhraní dokáže zničit okna se zkrácenými snímky hned nebo po určité prodlevě. Pokud chcete zpozdit zničení oken se zkrácenými rámečky, předejte hodnotu FALSE do parametru *bNoDelayedDestroy* . Ke zpoždění zničení dojde, když rozhraní zpracovává zprávu AFX_WM_CHECKEMPTYMINIFRAME.

##  <a name="replacepane"></a>CPaneFrameWnd::ReplacePane

Nahradí jedno podokno jiným.

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>Parametry

*pBarOrg*<br/>
pro Ukazatel na původní podokno.

*pBarReplaceWith*<br/>
pro Ukazatel na podokno, které nahrazuje původní podokno.

##  <a name="savestate"></a>CPaneFrameWnd:: SaveState

Uloží stav podokna do registru.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
pro Název profilu.

*uiID*<br/>
pro ID podokna

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byl stav podokna úspěšně uložen; v opačném případě FALSE.

##  <a name="setcaptionbuttons"></a>CPaneFrameWnd::SetCaptionButtons

Nastaví tlačítka titulků.

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>Parametry

*dwButtons*<br/>
pro Bitový nebo kombinaci následujících hodnot:

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

##  <a name="setdelayshow"></a>CPaneFrameWnd::SetDelayShow

```
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>Parametry

pro *bDelayShow*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setdockingmanager"></a>CPaneFrameWnd::SetDockingManager

```
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>Parametry

[in] *pManager*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setdockingtimer"></a>CPaneFrameWnd::SetDockingTimer

Nastaví časovač dokování.

```
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>Parametry

*nTimeOut*<br/>
pro Hodnota časového limitu v milisekundách

##  <a name="setdockstate"></a>CPaneFrameWnd::SetDockState

Nastaví stav ukotvení.

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>Parametry

*pDockManager*<br/>
pro Ukazatel na správce Docker.

##  <a name="sethotpoint"></a>CPaneFrameWnd::SetHotPoint

```
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>Parametry

[in] *ptNew*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setpredockstate"></a>CPaneFrameWnd::SetPreDockState

Volá se rozhraním, aby se nastavil stav předvysunutí.

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>Parametry

*preDockState*<br/>
pro Možné hodnoty:

- PDS_NOTHING,

- PDS_DOCK_REGULAR,

- PDS_DOCK_TO_TAB

*pBarToDock*<br/>
pro Ukazatel na ukotvení podokna.

*dockMethod*<br/>
pro Metoda docking. (Tento parametr je ignorován.)

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je okno se zkráceným snímkem neukotveno; FALSE, pokud je ukotveno.

##  <a name="sizetocontent"></a>CPaneFrameWnd::SizeToContent

Upraví velikost okna s minimálním snímkem tak, aby byla ekvivalentní k obsaženému podoknu.

```
virtual void SizeToContent();
```

### <a name="remarks"></a>Poznámky

Voláním této metody upravíte velikost okna se zkráceným rámcem na velikost obsaženého podokna.

##  <a name="starttearoff"></a>CPaneFrameWnd::StartTearOff

Trhlina z nabídky

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>Parametry

*pMenu*<br/>
pro Ukazatel na nabídku.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; v opačném případě FALSE.

##  <a name="storerecentdocksiteinfo"></a>CPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>Parametry

pro *pBar*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="storerecenttabrelatedinfo"></a>CPaneFrameWnd::StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Parametry

pro *pDockingBar*<br/>
pro *pTabbedBar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)
