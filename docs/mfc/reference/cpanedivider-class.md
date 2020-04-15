---
title: CPaneDivider – třída
ms.date: 11/04/2016
f1_keywords:
- CPaneDivider
- AFXPANEDIVIDER/CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::AddPaneContainer
- AFXPANEDIVIDER/CPaneDivider::AddPane
- AFXPANEDIVIDER/CPaneDivider::AddRecentPane
- AFXPANEDIVIDER/CPaneDivider::CalcExpectedDockedRect
- AFXPANEDIVIDER/CPaneDivider::CalcFixedLayout
- AFXPANEDIVIDER/CPaneDivider::CheckVisibility
- AFXPANEDIVIDER/CPaneDivider::CreateEx
- AFXPANEDIVIDER/CPaneDivider::DoesAllowDynInsertBefore
- AFXPANEDIVIDER/CPaneDivider::DoesContainFloatingPane
- AFXPANEDIVIDER/CPaneDivider::FindPaneContainer
- AFXPANEDIVIDER/CPaneDivider::FindTabbedPane
- AFXPANEDIVIDER/CPaneDivider::GetDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::GetFirstPane
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividerStyle
- AFXPANEDIVIDER/CPaneDivider::GetRootContainerRect
- AFXPANEDIVIDER/CPaneDivider::GetWidth
- AFXPANEDIVIDER/CPaneDivider::Init
- AFXPANEDIVIDER/CPaneDivider::InsertPane
- AFXPANEDIVIDER/CPaneDivider::IsAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::IsDefault
- AFXPANEDIVIDER/CPaneDivider::IsHorizontal
- AFXPANEDIVIDER/CPaneDivider::Move
- AFXPANEDIVIDER/CPaneDivider::NotifyAboutRelease
- AFXPANEDIVIDER/CPaneDivider::OnShowPane
- AFXPANEDIVIDER/CPaneDivider::ReleaseEmptyPaneContainers
- AFXPANEDIVIDER/CPaneDivider::RemovePane
- AFXPANEDIVIDER/CPaneDivider::ReplacePane
- AFXPANEDIVIDER/CPaneDivider::RepositionPanes
- AFXPANEDIVIDER/CPaneDivider::Serialize
- AFXPANEDIVIDER/CPaneDivider::SetAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::SetPaneContainerManager
- AFXPANEDIVIDER/CPaneDivider::ShowWindow
- AFXPANEDIVIDER/CPaneDivider::StoreRecentDockSiteInfo
- AFXPANEDIVIDER/CPaneDivider::StoreRecentTabRelatedInfo
- AFXPANEDIVIDER/CPaneDivider::GetPanes
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividers
- AFXPANEDIVIDER/CPaneDivider::m_nDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::m_pSliderRTC
helpviewer_keywords:
- CPaneDivider [MFC], CPaneDivider
- CPaneDivider [MFC], AddPaneContainer
- CPaneDivider [MFC], AddPane
- CPaneDivider [MFC], AddRecentPane
- CPaneDivider [MFC], CalcExpectedDockedRect
- CPaneDivider [MFC], CalcFixedLayout
- CPaneDivider [MFC], CheckVisibility
- CPaneDivider [MFC], CreateEx
- CPaneDivider [MFC], DoesAllowDynInsertBefore
- CPaneDivider [MFC], DoesContainFloatingPane
- CPaneDivider [MFC], FindPaneContainer
- CPaneDivider [MFC], FindTabbedPane
- CPaneDivider [MFC], GetDefaultWidth
- CPaneDivider [MFC], GetFirstPane
- CPaneDivider [MFC], GetPaneDividerStyle
- CPaneDivider [MFC], GetRootContainerRect
- CPaneDivider [MFC], GetWidth
- CPaneDivider [MFC], Init
- CPaneDivider [MFC], InsertPane
- CPaneDivider [MFC], IsAutoHideMode
- CPaneDivider [MFC], IsDefault
- CPaneDivider [MFC], IsHorizontal
- CPaneDivider [MFC], Move
- CPaneDivider [MFC], NotifyAboutRelease
- CPaneDivider [MFC], OnShowPane
- CPaneDivider [MFC], ReleaseEmptyPaneContainers
- CPaneDivider [MFC], RemovePane
- CPaneDivider [MFC], ReplacePane
- CPaneDivider [MFC], RepositionPanes
- CPaneDivider [MFC], Serialize
- CPaneDivider [MFC], SetAutoHideMode
- CPaneDivider [MFC], SetPaneContainerManager
- CPaneDivider [MFC], ShowWindow
- CPaneDivider [MFC], StoreRecentDockSiteInfo
- CPaneDivider [MFC], StoreRecentTabRelatedInfo
- CPaneDivider [MFC], GetPanes
- CPaneDivider [MFC], GetPaneDividers
- CPaneDivider [MFC], m_nDefaultWidth
- CPaneDivider [MFC], m_pSliderRTC
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
ms.openlocfilehash: 41fa3204712749a3b1123a20d31b01ba8b5fbaa4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364117"
---
# <a name="cpanedivider-class"></a>CPaneDivider – třída

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

Třída `CPaneDivider` rozdělí dvě podokna, rozdělí dvě skupiny podoken nebo oddělí skupinu podoken od klientské oblasti okna hlavního rámce.

## <a name="syntax"></a>Syntaxe

```
class CPaneDivider : public CBasePane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CPaneDivider::CPaneDivider](#cpanedivider)||

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPaneDivider::AddPaneContainer](#addpanecontainer)||
|[CPaneDivider::AddPane](#addpane)||
|[CPaneDivider::AddRecentPane](#addrecentpane)||
|[CPaneDivider::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CPaneDivider::CalcFixedLayout](#calcfixedlayout)|(Přepíše [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CPaneDivider::CheckVisibility](#checkvisibility)||
|[CPaneDivider::CreateEx](#createex)|(Přepíše [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CPaneDivider::DoesAllowDynInsertPřed](#doesallowdyninsertbefore)|(Přepíše [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CPaneDivider::DoesContainFloatingPane](#doescontainfloatingpane)||
|[CPaneDivider::FindPaneContainer](#findpanecontainer)||
|[CPaneDivider::FindTabbedPane](#findtabbedpane)||
|[CPaneDivider::GetDefaultWidth](#getdefaultwidth)||
|[CPaneDivider::GetFirstPane](#getfirstpane)||
|[CPaneDivider::GetPaneDividerStyle](#getpanedividerstyle)||
|[CPaneDivider::GetRootContainerRect](#getrootcontainerrect)||
|[CPaneDivider::GetWidth](#getwidth)||
|[CPaneDivider::Init](#init)||
|[CPaneDivider::InsertPane](#insertpane)||
|[CPaneDivider::Režim isautohidemode](#isautohidemode)|(Přepíše [CBasePane::IsAutoHideMode](../../mfc/reference/cbasepane-class.md#isautohidemode).)|
|[CPaneDivider::IsDefault](#isdefault)||
|[CPaneDivider::Je vodorovný](#ishorizontal)|(Přepíše [CBasePane::IsHorizontal](../../mfc/reference/cbasepane-class.md#ishorizontal).)|
|[CPaneDivider::Přesunout](#move)||
|[CPaneDivider::NotifyAboutRelease](#notifyaboutrelease)||
|[CPaneDivider::OnShowPane](#onshowpane)||
|[CPaneDivider::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)||
|[CPaneDivider::RemovePane](#removepane)||
|[CPaneDivider::ReplacePane](#replacepane)||
|[CPaneDivider::Přemístitpodokna](#repositionpanes)||
|[CPaneDivider::Serializovat](#serialize)|(Přepíše `CBasePane::Serialize`.)|
|[CPaneDivider::SetAutoHideMode](#setautohidemode)||
|[CPaneDivider::SetPaneContainerManager](#setpanecontainermanager)||
|[CPaneDivider::Zobrazitokno](#showwindow)||
|[CPaneDivider::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneDivider::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPaneDivider::GetPanes](#getpanes)|Vrátí seznam podoken, které jsou umístěny ve [třídě CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Tato metoda by měla být volána pouze pro výchozí oddělovače podokna.|
|[CPaneDivider::GetPaneDividers](#getpanedividers)|Vrátí seznam oddělovačů panelů, které jsou umístěny ve [třídě CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Tato metoda by měla být volána pouze pro výchozí oddělovače podokna.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CPaneDivider::m_nDefaultWidth](#m_ndefaultwidth)|Určuje výchozí šířku všech oddělovačů panelů v aplikaci v obrazových bodech.|
|[CPaneDivider::m_pSliderRTC](#m_psliderrtc)|Obsahuje ukazatel na informace o třídě `CPaneDivider`runtime o odvozeném objektu.|

## <a name="remarks"></a>Poznámky

Rozhraní framework `CPaneDivider` vytvoří objekty automaticky při ukotvení podokna.

Existují dva typy oddělovačů panelů:

- Výchozí oddělovač podokna je vytvořen, když je skupina podoken ukotvena na stranu okna hlavního rámce. Výchozí oddělovač podokna obsahuje ukazatel na [třídu CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md) a přesměruje většinu operací ve skupině podoken (například změna velikosti podokna nebo ukotvení jiného podokna nebo kontejneru) na správce kontejnerů. Každé dokovací podokno udržuje ukazatel na výchozí oddělovač podokna.

- Oddělovač běžných panelů pouze rozdělí dvě podokna v kontejneru. Další informace naleznete v [tématu CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CPaneDivider` získat objekt `CWorkspaceBar` z objektu. Tento fragment kódu je součástí [ukázky ukázky ukázky karty MDI](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)\
啦&nbsp;[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;啦&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;啦&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;啦&nbsp;[CPaneDivider](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxPaneDivider.h

## <a name="cpanedividersetautohidemode"></a><a name="setautohidemode"></a>CPaneDivider::SetAutoHideMode

```
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>Parametry

[v] *bRežim*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpanedividersetpanecontainermanager"></a><a name="setpanecontainermanager"></a>CPaneDivider::SetPaneContainerManager

```
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>Parametry

[v] *p*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpanedivideraddpane"></a><a name="addpane"></a>CPaneDivider::AddPane

```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

[v] *pBar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpanedivideraddpanecontainer"></a><a name="addpanecontainer"></a>CPaneDivider::AddPaneContainer

```
virtual BOOL AddPaneContainer(
    CPaneContainerManager& barContainerManager,
    BOOL bOuterEdge);

virtual BOOL AddPaneContainer(
    CDockablePane* pTargetBar,
    CPaneContainerManager& barContainerManager,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

[v] *barContainerManager*<br/>
[v] *bOuterEdge*<br/>
[v] *pCílový panel*<br/>
[v] *dwAlignment*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedivideraddrecentpane"></a><a name="addrecentpane"></a>CPaneDivider::AddRecentPane

```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

[v] *pBar*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CPaneDivider::CalcExpectedDockedRect

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Parametry

[v] *pWndToDock*<br/>
[v] *ptMouse*<br/>
[v] *rectVýsledek*<br/>
[v] *bDrawTab*<br/>
[v] *ppCílový bar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpanedividercalcfixedlayout"></a><a name="calcfixedlayout"></a>CPaneDivider::CalcFixedLayout

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

## <a name="cpanedividercheckvisibility"></a><a name="checkvisibility"></a>CPaneDivider::CheckVisibility

```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividercpanedivider"></a><a name="cpanedivider"></a>CPaneDivider::CPaneDivider

```
CPaneDivider();

CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Parametry

[v] *bVýchozíJezdec*<br/>
[v] *pParent*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividercreateex"></a><a name="createex"></a>CPaneDivider::CreateEx

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parametry

[v] *dwStyleEx*<br/>
[v] *dwStyl*<br/>
[v] *rect*<br/>
[v] *pParentWnd*<br/>
[v] *nID*<br/>
[v] *pKontext*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerdoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CPaneDivider::DoesAllowDynInsertPřed

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerdoescontainfloatingpane"></a><a name="doescontainfloatingpane"></a>CPaneDivider::DoesContainFloatingPane

```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerfindpanecontainer"></a><a name="findpanecontainer"></a>CPaneDivider::FindPaneContainer

```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>Parametry

[v] *pBar*<br/>
[v] *bLevý pruh*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerfindtabbedpane"></a><a name="findtabbedpane"></a>CPaneDivider::FindTabbedPane

```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>Parametry

[v] *nID*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividergetdefaultwidth"></a><a name="getdefaultwidth"></a>CPaneDivider::GetDefaultWidth

```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividergetfirstpane"></a><a name="getfirstpane"></a>CPaneDivider::GetFirstPane

```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividergetpanedividers"></a><a name="getpanedividers"></a>CPaneDivider::GetPaneDividers

Vrátí seznam oddělovačů panelů, které jsou umístěny ve [třídě CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Tato metoda by měla být volána pouze pro výchozí oddělovače podokna.

```
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>Parametry

*lstSliders*<br/>
[out] Obsahuje seznam oddělovačů panelů, které jsou umístěny v kontejneru podokna.

### <a name="remarks"></a>Poznámky

Tato metoda by měla být volána pouze pro výchozí oddělovače podokna. Výchozí oddělovač podokna je oddělovač, který změní velikost celého kontejneru podokna.

## <a name="cpanedividergetpanedividerstyle"></a><a name="getpanedividerstyle"></a>CPaneDivider::GetPaneDividerStyle

```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividergetpanes"></a><a name="getpanes"></a>CPaneDivider::GetPanes

Vrátí seznam podoken, které jsou umístěny ve [třídě CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Tato metoda by měla být volána pouze k načtení výchozích oddělovačů podokna.

```
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>Parametry

*LstBary*<br/>
[out] Obsahuje seznam podoken, které jsou umístěny v kontejneru podokna.

### <a name="remarks"></a>Poznámky

Tato metoda by měla být volána pouze pro výchozí oddělovače podokna. Výchozí oddělovač podokna je oddělovač, který změní velikost celého kontejneru podokna.

## <a name="cpanedividergetrootcontainerrect"></a><a name="getrootcontainerrect"></a>CPaneDivider::GetRootContainerRect

```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividergetwidth"></a><a name="getwidth"></a>CPaneDivider::GetWidth

```
int GetWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerinit"></a><a name="init"></a>CPaneDivider::Init

```
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Parametry

[v] *bVýchozíJezdec*<br/>
[v] *pParent*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerinsertpane"></a><a name="insertpane"></a>CPaneDivider::InsertPane

```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

[v] *pBarToInsert*<br/>
[v] *pCílový panel*<br/>
[v] *dwAlignment*<br/>
[v] *lpRect*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerisautohidemode"></a><a name="isautohidemode"></a>CPaneDivider::Režim isautohidemode

```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerisdefault"></a><a name="isdefault"></a>CPaneDivider::IsDefault

```
BOOL IsDefault() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerishorizontal"></a><a name="ishorizontal"></a>CPaneDivider::Je vodorovný

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerm_ndefaultwidth"></a><a name="m_ndefaultwidth"></a>CPaneDivider::m_nDefaultWidth

Určuje výchozí šířku všech oddělovačů panelů v aplikaci v obrazových bodech.

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

## <a name="cpanedividermove"></a><a name="move"></a>CPaneDivider::Přesunout

```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parametry

[v] *ptOffset*<br/>
[v] *bAdjustLayout*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerm_psliderrtc"></a><a name="m_psliderrtc"></a>CPaneDivider::m_pSliderRTC

Obsahuje ukazatel pro informace o `CPaneDivider`třídě runtime o odvozeném objektu.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>Poznámky

Pokud vytvoříte vlastní oddělovač podokna, nastavte tuto členovou proměnnou. To umožňuje rozhraní vytvořit oddělovač podokna při vykreslování podokna.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `m_pSliderRTC` nastavit proměnnou člena:

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

## <a name="cpanedividernotifyaboutrelease"></a><a name="notifyaboutrelease"></a>CPaneDivider::NotifyAboutRelease

```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>Poznámky

## <a name="cpanedivideronshowpane"></a><a name="onshowpane"></a>CPaneDivider::OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

[v] *pBar*<br/>
[v] *bZobrazit*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a>CPaneDivider::ReleaseEmptyPaneContainers

```
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerremovepane"></a><a name="removepane"></a>CPaneDivider::RemovePane

```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

[v] *pBar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerreplacepane"></a><a name="replacepane"></a>CPaneDivider::ReplacePane

```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>Parametry

[v] *pBarChcete-li nahradit*<br/>
[v] *pBarTonahradit*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerrepositionpanes"></a><a name="repositionpanes"></a>CPaneDivider::Přemístitpodokna

```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>Parametry

[v] *rectNew*<br/>
[v] *hdwp*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerserialize"></a><a name="serialize"></a>CPaneDivider::Serializovat

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

[v] *ar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpanedividershowwindow"></a><a name="showwindow"></a>CPaneDivider::Zobrazitokno

```
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parametry

[v] *nCmdZobrazit*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CPaneDivider::StoreRecentDockSiteInfo

```
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

[v] *pBar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cpanedividerstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CPaneDivider::StoreRecentTabRelatedInfo

```
void StoreRecentTabRelatedInfo(
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
[Třída CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[Třída CPaneContainer](../../mfc/reference/cpanecontainer-class.md)<br/>
[Třída CDockingManager](../../mfc/reference/cdockingmanager-class.md)<br/>
[CBasePane – třída](../../mfc/reference/cbasepane-class.md)
