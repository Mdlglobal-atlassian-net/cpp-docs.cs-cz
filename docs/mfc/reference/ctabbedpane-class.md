---
title: Třída CTabbedPane
ms.date: 11/04/2016
f1_keywords:
- CTabbedPane
- AFXTABBEDPANE/CTabbedPane
- AFXTABBEDPANE/CTabbedPane::DetachPane
- AFXTABBEDPANE/CTabbedPane::EnableTabAutoColor
- AFXTABBEDPANE/CTabbedPane::FloatTab
- AFXTABBEDPANE/CTabbedPane::GetTabArea
- AFXTABBEDPANE/CTabbedPane::GetTabWnd
- AFXTABBEDPANE/CTabbedPane::HasAutoHideMode
- AFXTABBEDPANE/CTabbedPane::IsTabLocationBottom
- AFXTABBEDPANE/CTabbedPane::ResetTabs
- AFXTABBEDPANE/CTabbedPane::SetTabAutoColors
- AFXTABBEDPANE/CTabbedPane::m_bTabsAlwaysTop
- AFXTABBEDPANE/CTabbedPane::m_pTabWndRTC
helpviewer_keywords:
- CTabbedPane [MFC], DetachPane
- CTabbedPane [MFC], EnableTabAutoColor
- CTabbedPane [MFC], FloatTab
- CTabbedPane [MFC], GetTabArea
- CTabbedPane [MFC], GetTabWnd
- CTabbedPane [MFC], HasAutoHideMode
- CTabbedPane [MFC], IsTabLocationBottom
- CTabbedPane [MFC], ResetTabs
- CTabbedPane [MFC], SetTabAutoColors
- CTabbedPane [MFC], m_bTabsAlwaysTop
- CTabbedPane [MFC], m_pTabWndRTC
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
ms.openlocfilehash: 17351eaed585ec34117a2ef825964fd51bd0d86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365951"
---
# <a name="ctabbedpane-class"></a>Třída CTabbedPane

Implementuje funkce podokna s odnímatelnými kartami.

nebo podrobnější informace naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CTabbedPane : public CBaseTabbedPane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CTabbedPane::CTabbedPane`|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CTabbedPane::DetachPane](#detachpane)|(Přepíše [CBaseTabbedPane::DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Povolí nebo zakáže automatické barvení karet.|
|[CTabbedPane::FloatTab](#floattab)|Plovoucí podokno, ale pouze v případě, že podokno aktuálně umístěnna [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)odpojitelné karty.|
|[CTabbedPane::GetTabArea](#gettabarea)|Vrátí velikost a umístění oblasti tabulátoru v okně s kartami.|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Určuje, zda lze podokno s kartami přepnout do režimu automatického skrytí. (Přepíše [CBaseTabbedPane::HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Určuje, zda jsou karty umístěny v dolní části okna.|
|[CTabbedPane::Obnovit tabulátory](#resettabs)|Obnoví výchozí stav všech panelů s kartami.|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Nastaví seznam vlastních barev, které lze použít, když je povolena funkce automatické barvy.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|Výchozí umístění pro karty v aplikaci.|
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|Informace o třídě runtime pro vlastní `CMFCTabCtrl`odvozený objekt.|

## <a name="remarks"></a>Poznámky

Rozhraní framework automaticky vytvoří instanci této třídy, když uživatel připojí jedno podokno k jinému odkazem na titulek druhého podokna. Všechna podokna s kartami, které jsou vytvořeny v rámci mají ID -1.

Chcete-li místo karet stylu aplikace Outlook určit běžné karty, předajte styl AFX_CBRS_REGULAR_TABS metodě [CDockablePane::CreateEx.](../../mfc/reference/cdockablepane-class.md#createex)

Pokud vytvoříte podokno s kartami s odpojitelnými kartami, může být podokno automaticky zničeno rozhraním, takže byste neměli ukládat ukazatel. Chcete-li získat ukazatel na podokno `CBasePane::GetParentTabbedPane` s kartami, zavolejte metodu.

## <a name="example"></a>Příklad

V tomto příkladu `CTabbedPane` vytvoříme objekt. Dále použijeme [CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) připojit další karty.

```cpp
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);

if (!pTabbededBar->Create (_T(""),
    this,
    CRect (0,
    0,
    200,
    200),
    TRUE,
    (UINT) -1,
    WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |
    WS_CLIPCHILDREN | CBRS_LEFT |
    CBRS_FLOAT_MULTI))
{
    TRACE0("Failed to create Solution Explorer bar\n");

    return FALSE;      // fail to create
}

pTabbededBar->AddTab (&m_wndClassView);
pTabbededBar->AddTab (&m_wndResourceView);

pTabbededBar->AddTab (&m_wndFileView);
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);

DockPane(pTabbededBar);
```

## <a name="example"></a>Příklad

Dalším způsobem, jak vytvořit objekt ovládacího panelu s kartami, je použití [cdockablepane::AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). Metoda `AttachToTabWnd` dynamicky vytvoří objekt podokna s kartami pomocí informací o třídě runtime nastavených [cDockablePane::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc).

V tomto příkladu vytvoříme podokno s kartami dynamicky, připojíme dvě karty a druhou kartu vytvoříme neoddělitelnou.

```cpp
DockPane(&m_wndClassView);

CTabbedPane* pTabbedBar = NULL;
m_wndResourceView.AttachToTabWnd (&m_wndClassView,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

m_wndFileView.AttachToTabWnd (pTabbedBar,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1,
    FALSE);
```

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxTabbedPane.h

## <a name="ctabbedpanedetachpane"></a><a name="detachpane"></a>CTabbedPane::DetachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

[v] *pBar*<br/>

[v] *bSkrýt*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="ctabbedpaneenabletabautocolor"></a><a name="enabletabautocolor"></a>CTabbedPane::EnableTabAutoColor

Povolí nebo zakáže automatické barvení karet.

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE povolit automatické zbarvení karet; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tuto statickou metodu použijte k povolení nebo zakázání automatického barvení karet ve všech podoknech s kartami v aplikaci. Pokud je tato funkce povolena, každá karta je vyplněna vlastní barvou. Seznam barev, které se používají k barvení karet, najdete voláním metody [CMFCBaseTabCtrl::GetAutoColors.](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors)

Seznam barev, které budou použity pro tabulátory, můžete určit voláním [CTabbedPane::SetTabAutoColors](#settabautocolors).

Ve výchozím nastavení je tato možnost zakázána.

## <a name="ctabbedpanefloattab"></a><a name="floattab"></a>CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

[v] *pBar*<br/>
[v] *nTabID*<br/>
[v] *dockMethod*<br/>
[v] *bSkrýt*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="ctabbedpanegettabarea"></a><a name="gettabarea"></a>CTabbedPane::GetTabArea

Vrátí velikost a umístění oblasti tabulátoru v okně s kartami.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parametry

*rectTabAreaTop*<br/>
[out] Obsahuje velikost a umístění souřadnic obrazovky v oblasti horního tabulátoru.

*rectTabAreaBottom*<br/>
[out] Obsahuje velikost a umístění v souřadnicích obrazovky v oblasti dolní karty.

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto metodu k určení, jak ukotvit podokno, které uživatel přetahuje. Když uživatel přetáhne podokno přes oblast tabulátoru cílového podokna, rozhraní se pokusí přidat jako novou kartu cílového podokna. V opačném případě se pokusí ukotvit podokno na stranu cílového podokna, což zahrnuje vytvoření nového kontejneru podokna s oddělovačem podokna, který odděluje dvě podokna.

Přepsat tuto metodu `CTabbedPane`v -odvozené třídy změnit toto chování.

## <a name="ctabbedpanegettabwnd"></a><a name="gettabwnd"></a>CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="ctabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="ctabbedpaneistablocationbottom"></a><a name="istablocationbottom"></a>CTabbedPane::IsTabLocationBottom

Určuje, zda jsou karty umístěny v dolní části okna.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je oblast tabulátoru umístěna v dolní části okna s kartami; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="ctabbedpanem_btabsalwaystop"></a><a name="m_btabsalwaystop"></a>CTabbedPane::m_bTabsAlwaysTop

Výchozí umístění pro karty v aplikaci.

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>Poznámky

Nastavte tento statický člen na HODNOTU TRUE, aby se všechny karty v aplikaci zobrazily v horní části podokna s kartami.

Tuto hodnotu je nutné nastavit před vytvořením podokna s kartami.

Výchozí hodnota je FALSE.

## <a name="ctabbedpanem_ptabwndrtc"></a><a name="m_ptabwndrtc"></a>CTabbedPane::m_pTabWndRTC

Informace o třídě runtime pro vlastní `CMFCTabCtrl`odvozený objekt.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>Poznámky

Pokud používáte vlastní okno s kartami v `CMFCTabCtrl`podokně s kartami, nastavte tuto statickou člennou proměnnou na ukazatel na informace o třídě runtime odvozeného objektu.

## <a name="ctabbedpaneresettabs"></a><a name="resettabs"></a>CTabbedPane::Obnovit tabulátory

Obnoví výchozí stav všech panelů s kartami.

```
static void ResetTabs();
```

### <a name="remarks"></a>Poznámky

Volánítéto metody vrátit všechna podokna s kartami do výchozího stavu. Při volání tato metoda obnoví velikosti ohraničení a automatický stav barev všech panelů s kartami.

## <a name="ctabbedpanesettabautocolors"></a><a name="settabautocolors"></a>CTabbedPane::SetTabAutoColors

Nastaví seznam vlastních barev, které se používají, když je povolena funkce automatické barvy.

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parametry

*arBarvy*<br/>
[v] Obsahuje pole barev, které chcete nastavit.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete přizpůsobit seznam barev, které se používají, když je povolena funkce automatické barvy. Jedná se o statickou funkci, která ovlivňuje všechna podokna s kartami v aplikaci.

Pomocí [funkce CTabbedPane::EnableTabAutoColor](#enabletabautocolor) povolte nebo zakažte funkci automatické barvy.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CDockablePane](../../mfc/reference/cdockablepane-class.md)<br/>
[Třída CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)
