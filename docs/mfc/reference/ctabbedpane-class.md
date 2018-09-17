---
title: Ctabbedpane – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a73d5bb3ef67469ad1cc12b2a2c2757cf1ce137
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712828"
---
# <a name="ctabbedpane-class"></a>Ctabbedpane – třída

Implementuje funkce podokna s odnímatelnými kartami.

nebo další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CTabbedPane : public CBaseTabbedPane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CTabbedPane::CTabbedPane`|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTabbedPane::DetachPane](#detachpane)|(Přepíše [CBaseTabbedPane::DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Povolí nebo zakáže automatické barvy karet.|
|[CTabbedPane::FloatTab](#floattab)|Podokno, ale pouze čísel s plovoucí čárkou, pokud se v podokně se aktuálně nachází odpojitelných kartě. (Přepíše [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CTabbedPane::GetTabArea](#gettabarea)|Vrátí velikost a umístění od oblasti karet v rámci okna s kartami.|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Určuje, zda podokno s kartami můžete přepnout do režimu automaticky skrývat. (Přepíše [CBaseTabbedPane::HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Určuje, zda karty jsou umístěné v dolní části okna.|
|[CTabbedPane::ResetTabs](#resettabs)|Všechna podokna s kartami obnoví do výchozího stavu.|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Nastaví seznam vlastních barev, které lze použít, pokud je povolena funkce barva automaticky.|

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|Výchozí umístění pro karty v aplikaci.|
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|Informace o třídě modulu runtime pro vlastní `CMFCTabCtrl`-odvozenému objektu.|

## <a name="remarks"></a>Poznámky

Rozhraní framework automaticky vytvoří instanci této třídy, když uživatel připojí jedno podokno do jiného najetím myší na titulek druhé části okna. Všechny podokna s kartami, které jsou vytvořeny v rámci rozhraní mají ID-1.

K určení běžné karty namísto tabulátorů stylu Outlook, předejte AFX_CBRS_REGULAR_TABS styl, který má [CDockablePane::CreateEx](../../mfc/reference/cdockablepane-class.md#createex) metody.

Pokud vytvoříte podokna s kartami s odnímatelnými kartami, v podokně může zničí automaticky rozhraním, proto neměli ukládat ukazatel. Chcete-li získat ukazatel do podokna s kartami, zavolejte `CBasePane::GetParentTabbedPane` metody.

## <a name="example"></a>Příklad

V tomto příkladu vytvoříme `CTabbedPane` objektu. V dalším kroku použijeme [CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) připojit další záložky.

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

Dalším způsobem, jak vytvořit objekt ovládacího prvku na kartách panelu je použití [CDockablePane::AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). `AttachToTabWnd` Metoda dynamicky vytvoří objekt podokna s kartami pomocí informací o třídě modulu runtime nastavil [CDockablePane::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc).

V tomto příkladu vytvoříme dynamicky podokna s kartami připojte dvě karty a ujistěte se, druhá karta bez odpojitelných.

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

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[Cbasetabbedpane –](../../mfc/reference/cbasetabbedpane-class.md)

[Ctabbedpane –](../../mfc/reference/ctabbedpane-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxTabbedPane.h

##  <a name="detachpane"></a>  CTabbedPane::DetachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

[in] *pBar*  

[in] *bHide*  

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="enabletabautocolor"></a>  CTabbedPane::EnableTabAutoColor

Povolí nebo zakáže automatické barvy karet.

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] TRUE pro povolení automatického barvy karet; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato statická metoda použijte k povolení nebo zakázání automatického barvy karet v všechna podokna s kartami v aplikaci. Pokud je tato funkce povolena, každá karta sestavil svou vlastní barvy. Můžete najít seznam barev, které se používají k voláním barev karty [CMFCBaseTabCtrl::GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) metody.

Můžete zadat seznam barev, které se použijí u tabulátorů voláním [CTabbedPane::SetTabAutoColors](#settabautocolors).

Ve výchozím nastavení je tato možnost zakázaná.

##  <a name="floattab"></a>  CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] [in] *nTabID*  
*dockMethod*<br/>
[in] [in] *bHide*  

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="gettabarea"></a>  CTabbedPane::GetTabArea

Vrátí velikost a umístění oblast karty v okně s kartami.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parametry

*rectTabAreaTop*<br/>
[out] Obsahuje velikost a umístění, v souřadnicovém systému obrazovky, oblasti horní kartě.

*rectTabAreaBottom*<br/>
[out] Obsahuje velikost a umístění, v souřadnicovém systému obrazovky, od oblasti karet dole.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu za účelem určení, jak podokno, které uživatel přetahuje ukotvení. Když uživatel přetáhne podokno přes oblast karty podokna cíl, se pokusí ho přidat jako na nové kartě v podokně cílové rozhraní framework. V opačném případě se pokusí ukotvit na straně podokna target, která zahrnuje vytvoření nového kontejneru podokno s podokně oddělovač, který odděluje podokna.

Potlačí tuto metodu v `CTabbedPane`-odvozené třídy ke změně tohoto chování.

##  <a name="gettabwnd"></a>  CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="hasautohidemode"></a>  CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="istablocationbottom"></a>  CTabbedPane::IsTabLocationBottom

Určuje, zda karty jsou umístěné v dolní části okna.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud oblast karty se nachází v dolní části okna s kartami. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="m_btabsalwaystop"></a>  CTabbedPane::m_bTabsAlwaysTop

Výchozí umístění pro karty v aplikaci.

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>Poznámky

Nastavte tento statický člen na hodnotu PRAVDA, platnost všechny karty v aplikaci, který se má zobrazit v horní části podokna s kartami.

Tato hodnota je nutné nastavit před podokna s kartami se vytvořil.

Výchozí hodnota je FALSE.

##  <a name="m_ptabwndrtc"></a>  CTabbedPane::m_pTabWndRTC
Informace o třídě modulu runtime pro vlastní `CMFCTabCtrl`-odvozenému objektu.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>Poznámky

Tuto proměnnou statického člena na ukazatel na informace o modulu runtime třídy z nastavit `CMFCTabCtrl`-odvozenému objektu, pokud používáte vlastní okno s kartami uvnitř podokna s kartami.

##  <a name="resettabs"></a>  CTabbedPane::ResetTabs

Všechna podokna s kartami obnoví do výchozího stavu.

```
static void ResetTabs();
```

### <a name="remarks"></a>Poznámky

Volání této metody vrátit zpět všechny podokna s kartami do výchozího stavu. Při volání této metody obnoví ohraničení velikosti a barvy stav automaticky všechna podokna s kartami.

##  <a name="settabautocolors"></a>  CTabbedPane::SetTabAutoColors

Nastaví seznam vlastních barev, které se používají, když je povolena funkce barva automaticky.

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parametry

*arColors*<br/>
[in] Obsahuje pole barev k nastavení.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k přizpůsobení seznamu barev, které se používají, když je povolena funkce barva automaticky. Toto je statické funkce a má vliv na všech kartách podokna ve vaší aplikaci.

Použití [CTabbedPane::EnableTabAutoColor](#enabletabautocolor) povolit nebo zakázat funkci Automatické barvu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)  
[Třídy](../../mfc/reference/mfc-classes.md)  
[CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)  
[CBaseTabbedPane – třída](../../mfc/reference/cbasetabbedpane-class.md)  
[CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)  
