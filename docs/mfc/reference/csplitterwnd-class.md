---
title: CSplitterWnd – třída
ms.date: 11/04/2016
f1_keywords:
- CSplitterWnd
- AFXEXT/CSplitterWnd
- AFXEXT/CSplitterWnd::CSplitterWnd
- AFXEXT/CSplitterWnd::ActivateNext
- AFXEXT/CSplitterWnd::CanActivateNext
- AFXEXT/CSplitterWnd::Create
- AFXEXT/CSplitterWnd::CreateScrollBarCtrl
- AFXEXT/CSplitterWnd::CreateStatic
- AFXEXT/CSplitterWnd::CreateView
- AFXEXT/CSplitterWnd::DeleteColumn
- AFXEXT/CSplitterWnd::DeleteRow
- AFXEXT/CSplitterWnd::DeleteView
- AFXEXT/CSplitterWnd::DoKeyboardSplit
- AFXEXT/CSplitterWnd::DoScroll
- AFXEXT/CSplitterWnd::DoScrollBy
- AFXEXT/CSplitterWnd::GetActivePane
- AFXEXT/CSplitterWnd::GetColumnCount
- AFXEXT/CSplitterWnd::GetColumnInfo
- AFXEXT/CSplitterWnd::GetPane
- AFXEXT/CSplitterWnd::GetRowCount
- AFXEXT/CSplitterWnd::GetRowInfo
- AFXEXT/CSplitterWnd::GetScrollStyle
- AFXEXT/CSplitterWnd::IdFromRowCol
- AFXEXT/CSplitterWnd::IsChildPane
- AFXEXT/CSplitterWnd::IsTracking
- AFXEXT/CSplitterWnd::RecalcLayout
- AFXEXT/CSplitterWnd::SetActivePane
- AFXEXT/CSplitterWnd::SetColumnInfo
- AFXEXT/CSplitterWnd::SetRowInfo
- AFXEXT/CSplitterWnd::SetScrollStyle
- AFXEXT/CSplitterWnd::SplitColumn
- AFXEXT/CSplitterWnd::SplitRow
- AFXEXT/CSplitterWnd::OnDraw
- AFXEXT/CSplitterWnd::OnDrawSplitter
- AFXEXT/CSplitterWnd::OnInvertTracker
helpviewer_keywords:
- CSplitterWnd [MFC], CSplitterWnd
- CSplitterWnd [MFC], ActivateNext
- CSplitterWnd [MFC], CanActivateNext
- CSplitterWnd [MFC], Create
- CSplitterWnd [MFC], CreateScrollBarCtrl
- CSplitterWnd [MFC], CreateStatic
- CSplitterWnd [MFC], CreateView
- CSplitterWnd [MFC], DeleteColumn
- CSplitterWnd [MFC], DeleteRow
- CSplitterWnd [MFC], DeleteView
- CSplitterWnd [MFC], DoKeyboardSplit
- CSplitterWnd [MFC], DoScroll
- CSplitterWnd [MFC], DoScrollBy
- CSplitterWnd [MFC], GetActivePane
- CSplitterWnd [MFC], GetColumnCount
- CSplitterWnd [MFC], GetColumnInfo
- CSplitterWnd [MFC], GetPane
- CSplitterWnd [MFC], GetRowCount
- CSplitterWnd [MFC], GetRowInfo
- CSplitterWnd [MFC], GetScrollStyle
- CSplitterWnd [MFC], IdFromRowCol
- CSplitterWnd [MFC], IsChildPane
- CSplitterWnd [MFC], IsTracking
- CSplitterWnd [MFC], RecalcLayout
- CSplitterWnd [MFC], SetActivePane
- CSplitterWnd [MFC], SetColumnInfo
- CSplitterWnd [MFC], SetRowInfo
- CSplitterWnd [MFC], SetScrollStyle
- CSplitterWnd [MFC], SplitColumn
- CSplitterWnd [MFC], SplitRow
- CSplitterWnd [MFC], OnDraw
- CSplitterWnd [MFC], OnDrawSplitter
- CSplitterWnd [MFC], OnInvertTracker
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
ms.openlocfilehash: 065735c13a3e763208142eb6bc989d3a496221f0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781442"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd – třída

Poskytuje funkce pro okno s rozdělovačem, což je okno, které obsahuje více podoken.

## <a name="syntax"></a>Syntaxe

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Volání k vytvoření `CSplitterWnd` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSplitterWnd::ActivateNext](#activatenext)|Provede příkaz Další podokno nebo předchozí podokno.|
|[CSplitterWnd::CanActivateNext](#canactivatenext)|Kontroluje, jestli je aktuálně možné příkaz Další podokno nebo předchozí podokno.|
|[CSplitterWnd::Create](#create)|K vytvoření dynamické okno s rozdělovačem a připojí k volání `CSplitterWnd` objektu.|
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|Vytvoří ovládací prvek posuvníku sdílené.|
|[CSplitterWnd::CreateStatic](#createstatic)|Volání statické rozdělovače oken a vytvořte tak, `CSplitterWnd` objektu.|
|[CSplitterWnd::CreateView](#createview)|Volání za účelem vytvoření podokno v okno s rozdělovačem.|
|[CSplitterWnd::DeleteColumn](#deletecolumn)|Odstraní sloupec z okna s rozdělovačem.|
|[CSplitterWnd::DeleteRow](#deleterow)|Odstraní řádek z okna s rozdělovačem.|
|[CSplitterWnd::DeleteView](#deleteview)|Odstraní zobrazení z okna s rozdělovačem.|
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|Provádí příkaz rozdělení klávesnice, obvykle "Window Split."|
|[CSplitterWnd::DoScroll](#doscroll)|Provádí synchronizované posouvání rozdělených oken.|
|[CSplitterWnd::DoScrollBy](#doscrollby)|Posouvání rozdělených oken o daný počet pixelů.|
|[CSplitterWnd::GetActivePane](#getactivepane)|Určuje aktivní podokno ze aktivní nebo aktivní zobrazení v rámci.|
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Vrátí aktuální počet sloupců podokně.|
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Vrací informace na sloupec.|
|[CSplitterWnd::GetPane](#getpane)|Vrátí podokno na zadaný řádek ve sloupci.|
|[CSplitterWnd::GetRowCount](#getrowcount)|Vrátí aktuální počet řádků podokně.|
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Vrací informace na zadaný řádek.|
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Vrací styl sdílené posuvníku.|
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Vrací podřízeného okna ID podokna na zadaný řádek ve sloupci.|
|[CSplitterWnd::IsChildPane](#ischildpane)|Volání k určení, zda je okno aktuálně podřízené podokno rozdělovač okna.|
|[CSplitterWnd::IsTracking](#istracking)|Určuje, pokud je aktuálně přesunutí příčky.|
|[CSplitterWnd::RecalcLayout](#recalclayout)|Volání k opětovnému zobrazení okna s rozdělovačem po úpravě řádku nebo sloupce.|
|[CSplitterWnd::SetActivePane](#setactivepane)|Nastaví podokno, které má být aktivní v rámci.|
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|Volání za účelem nastavení informací o zadaný sloupec.|
|[CSplitterWnd::SetRowInfo](#setrowinfo)|Volání za účelem nastavení informací o zadaný řádek.|
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Určuje, že podpora posuvníku sdílených nový styl posuvníku rozdělovač okna.|
|[CSplitterWnd::SplitColumn](#splitcolumn)|Určuje, kde se okno rámce rozdělí svisle.|
|[CSplitterWnd::SplitRow](#splitrow)|Určuje, kde se okno rámce rozdělí vodorovně.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CSplitterWnd::OnDraw](#ondraw)|Volá se rozhraním, chcete-li nakreslit okna s rozdělovačem.|
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Vykreslí obrázek rozděleného okna.|
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Vykreslí obraz rozděleného okna se stejnou velikost a tvar jako okno rámce.|

## <a name="remarks"></a>Poznámky

Podokno je obvykle odvozen od objektu specifické pro aplikaci [CView](../../mfc/reference/cview-class.md), ale může být kterýkoli [CWnd](../../mfc/reference/cwnd-class.md) objekt, který má ID odpovídající podřízené okno.

A `CSplitterWnd` objekt je obvykle vložený v nadřazeném prvku [CFrameWnd](../../mfc/reference/cframewnd-class.md) nebo [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objektu. Vytvoření `CSplitterWnd` pomocí následujících kroků:

1. Vložit `CSplitterWnd` členské proměnné v nadřazeného rámce.

2. Přepsat nadřazeného rámce [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) členskou funkci.

3. Z v rámci přepsané `OnCreateClient`, zavolejte [vytvořit](#create) nebo [CreateStatic](#createstatic) členskou funkci `CSplitterWnd`.

Volání `Create` členské funkci, která vytvoří dynamické okno s rozdělovačem. Dynamické okno s rozdělovačem se obvykle používá k vytvoření a posuňte číslo jednotlivá podokna nebo zobrazení stejného dokumentu. Rozhraní framework automaticky vytvoří počáteční podokno pro rozdělovač; rozhraní framework pak vytvoří, změní velikost a uvolní další podokna jako uživatel pracuje rozděleného okna ovládacích prvků.

Při volání `Create`, zadejte minimální řádek výšku a šířku sloupce, které určují, kdy jsou podokna příliš malá, který se zobrazí plně. Po zavolání `Create`, můžete upravit tyto minimálních voláním [SetColumnInfo](#setcolumninfo) a [SetRowInfo](#setrowinfo) členské funkce.

Použít také `SetColumnInfo` a `SetRowInfo` členské funkce pro nastavení "ideální" šířku sloupce a "ideální" výšku řádku. Když se zobrazí okno s rozdělovačem rozhraní, nejprve zobrazí nadřazeného rámce, pak okna s rozdělovačem. Rozhraní framework pak rozložen podokny sloupců a řádků podle jejich ideální dimenze práci v levém horním rohu do pravého dolního rohu okna s rozdělovačem od klientské oblasti.

Stejné třídy musí být všechny podokny dynamické okno s rozdělovačem. Známé aplikace, které podporují dynamické rozdělovače oken patří Microsoft Word a Microsoft Excelu.

Použití `CreateStatic` vytvořit okno rozdělovače pro statické členské funkce. Uživatel může změnit pouze velikost podokna ve statické rozdělovače oken, není jejich číslo nebo pořadí.

Konkrétně musíte vytvořit podokna všechny statické rozdělovače na při vytváření statický rozdělovač. Ujistěte se, že vytvoříte všechna podokna před nadřazeného rámce `OnCreateClient` členské funkce vrátí, nebo se framework není správně zobrazit okno.

`CreateStatic` Členskou funkci automaticky inicializuje statický rozdělovač s minimální řádek výšku a ve sloupci šířku na 0. Po zavolání `Create`, upravte tyto minimálních voláním [SetColumnInfo](#setcolumninfo) a [SetRowInfo](#setrowinfo) členské funkce. Použít také `SetColumnInfo` a `SetRowInfo` po zavolání `CreateStatic` k označení požadovaného ideální podokně dimenze.

Jednotlivá podokna statické rozdělovače často patří do různých tříd. Příklady statické rozdělovače oken najdete v grafickém editoru a Správce souborů Windows.

Okno s rozdělovačem podporuje speciální posuvníky (kromě posuvníků, které můžou mít podokna). Tyto posuvníky jsou podřízené `CSplitterWnd` objektu s nimi a podokna.

Můžete vytvořit tyto speciální posuvníky, při vytváření okna s rozdělovačem. Například `CSplitterWnd` , který má jeden řádek, dvěma sloupci a styl WS_VSCROLL se zobrazí svislý posuvník, jež jsou sdílena ve dvou podoken. Když se uživatel přesune na posuvník, WM_VSCROLL zprávy se posílají do obou podoken. Při podokna nastavení pozice posuvníku, je nastavit sdílený posuvníku.

Další informace o rozdělovače oken, naleznete v tématu [Technická poznámka 29](../../mfc/tn029-splitter-windows.md).

Další informace o tom, jak vytvořit dynamické rozdělovače oken, najdete tady:

- Ukázky knihovny MFC [Scribble](../../overview/visual-cpp-samples.md)

- Ukázky knihovny MFC [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget –](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

##  <a name="activatenext"></a>  CSplitterWnd::ActivateNext

Volá se rozhraním provést příkaz Další podokno nebo předchozí podokno.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parametry

*bPrev*<br/>
Označuje, které okno k aktivaci. **Hodnota TRUE** pro předchozí; **FALSE** pro další.

### <a name="remarks"></a>Poznámky

Tato členská funkce je základní příkaz, který je používán [CView](../../mfc/reference/cview-class.md) třídy delegovat `CSplitterWnd` implementace.

##  <a name="canactivatenext"></a>  CSplitterWnd::CanActivateNext

Volá se rozhraním, aby zkontrolujte, jestli je aktuálně možné příkaz Další podokno nebo předchozí podokno.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parametry

*bPrev*<br/>
Označuje, které okno k aktivaci. **Hodnota TRUE** pro předchozí; **FALSE** pro další.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je základní příkaz, který je používán [CView](../../mfc/reference/cview-class.md) třídy delegovat `CSplitterWnd` implementace.

##  <a name="create"></a>  CSplitterWnd::Create

Chcete-li vytvořit dynamické okno s rozdělovačem, zavolejte `Create` členskou funkci.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    int nMaxRows,
    int nMaxCols,
    SIZE sizeMin,
    CCreateContext* pContext,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_HSCROLL | WS_VSCROLL | SPLS_DYNAMIC_SPLIT,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Nadřazené okno rámce z okna s rozdělovačem.

*nMaxRows*<br/>
Maximální počet řádků v okna s rozdělovačem. Tato hodnota nesmí být delší než 2.

*nMaxCols*<br/>
Maximální počet sloupců v okna s rozdělovačem. Tato hodnota nesmí být delší než 2.

*sizeMin*<br/>
Určuje minimální velikost, ve kterém může se zobrazit podokno.

*pContext*<br/>
Ukazatel [ccreatecontext –](../../mfc/reference/ccreatecontext-structure.md) struktury. Ve většině případů to může být *pContext* předaný do nadřazeného okna rámce.

*dwStyle*<br/>
Určuje styl okna.

*nID*<br/>
Identifikátor podřízené okno okna. ID může být AFX_IDW_PANE_FIRST, dokud okna s rozdělovačem je vnořit do jiné okno s rozdělovačem.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vložit `CSplitterWnd` v nadřazeném prvku [CFrameWnd](../../mfc/reference/cframewnd-class.md) nebo [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objektu podle následujících kroků:

1. Vložit `CSplitterWnd` členské proměnné v nadřazeného rámce.

1. Přepsat nadřazeného rámce [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) členskou funkci.

1. Volání `Create` členské funkce v rámci přepsané `OnCreateClient`.

Při vytváření okno s rozdělovačem z v rámci nadřazené předat nadřazeného rámce *pContext* parametr do okna s rozdělovačem. V opačném případě tento parametr může mít hodnotu NULL.

Počáteční řádek minimální výšku a ve sloupci šířku dynamické okno s rozdělovačem určil institut NIST *sizeMin* parametru. Tyto minimálních hodnot, které určují, zda podokno je příliš malá v celém rozsahu, je možné měnit pomocí [SetRowInfo](#setrowinfo) a [SetColumnInfo](#setcolumninfo) členské funkce.

Další informace o dynamické rozdělovače oken, naleznete v tématu "Rozdělovač Windows" v článku [více typů dokumentů, zobrazení a rámečku Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technická poznámka 29](../../mfc/tn029-splitter-windows.md)a `CSplitterWnd` přehledu třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

##  <a name="createscrollbarctrl"></a>  CSplitterWnd::CreateScrollBarCtrl

Volá se rozhraním, chcete-li vytvořit ovládací prvek posuvníku sdílené.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl okna.

*nID*<br/>
Identifikátor podřízené okno okna. ID může být AFX_IDW_PANE_FIRST, dokud okna s rozdělovačem je vnořit do jiné okno s rozdělovačem.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Přepsat `CreateScrollBarCtrl` zahrnout další ovládací prvky vedle posuvníku. Výchozí chování je vytvořit ovládací prvky stavového řádku posuvníku normální Windows.

##  <a name="createstatic"></a>  CSplitterWnd::CreateStatic

Chcete-li vytvořit statické rozdělovače oken, zavolejte `CreateStatic` členskou funkci.

```
virtual BOOL CreateStatic(
    CWnd* pParentWnd,
    int nRows,
    int nCols,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Nadřazené okno rámce z okna s rozdělovačem.

*nRows*<br/>
Počet řádků. Tato hodnota nesmí být delší než 16.

*nCols*<br/>
Počet sloupců. Tato hodnota nesmí být delší než 16.

*dwStyle*<br/>
Určuje styl okna.

*nID*<br/>
Identifikátor podřízené okno okna. ID může být AFX_IDW_PANE_FIRST, dokud okna s rozdělovačem je vnořit do jiné okno s rozdělovačem.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

A `CSplitterWnd` je obvykle vložený v nadřazeném prvku `CFrameWnd` nebo [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objektu podle následujících kroků:

1. Vložit `CSplitterWnd` členské proměnné v nadřazeného rámce.

1. Přepsat nadřazeného rámce `OnCreateClient` členskou funkci.

1. Volání `CreateStatic` členské funkce v rámci přepsané [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).

Statický rozdělovač okna obsahuje číslo s pevným podoken, často z různých tříd.

Když vytvoříte statické rozdělovače oken, musíte ve stejnou dobu vytvořit jeho podoken. [CreateView](#createview) členská funkce se obvykle používá pro tento účel, ale můžete vytvořit další nonview třídy.

Počáteční řádek minimální výšku a ve sloupci šířka statický rozdělovač okna je 0. Tyto minimálních hodnot, které určují, kdy je příliš malá zobrazený v celém rozsahu na stavového řádku, je možné měnit pomocí [SetRowInfo](#setrowinfo) a [SetColumnInfo](#setcolumninfo) členské funkce.

Pokud chcete přidat do statické rozdělovače oken posuvníky, přidejte styly WS_HSCROLL a WS_VSCROLL *dwStyle*.

Viz "Rozdělovač Windows" v článku [více typů dokumentů, zobrazení a rámečku Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technická poznámka 29](../../mfc/tn029-splitter-windows.md)a `CSplitterWnd` přehledu třídy pro další informace o statické rozdělovače oken.

##  <a name="createview"></a>  CSplitterWnd::CreateView

Vytvoří podokna pro okno s rozdělovačem. statické.

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parametry

*Řádek*<br/>
Určuje řádku rozdělovač okna ve kterém je umístí nové zobrazení.

*sloupec*<br/>
Určuje sloupec rozdělovač okna, ve kterém k umístění nového zobrazení.

*pViewClass*<br/>
Určuje, [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) nového zobrazení.

*sizeInit*<br/>
Určuje počáteční velikost nové zobrazení.

*pContext*<br/>
Ukazatel na vytváření kontext použitý k vytvoření zobrazení (obvykle *pContext* předaná do nadřazeného rámce přepsané [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) členská funkce, ve kterém se okna s rozdělovačem Probíhá vytváření).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Všechna podokna statický rozdělovač okna musí být vytvořen před zobrazí rozhraní příčky.

Rozhraní volá také tato členská funkce k vytvoření nové podoken, když uživatel dynamické okno s rozdělovačem rozdělí podokně, řádek nebo sloupec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

##  <a name="csplitterwnd"></a>  CSplitterWnd::CSplitterWnd

Volání k vytvoření `CSplitterWnd` objektu.

```
CSplitterWnd();
```

### <a name="remarks"></a>Poznámky

Vytvoření `CSplitterWnd` objektu ve dvou krocích. Nejprve volat konstruktor, který vytvoří `CSplitterWnd` objekt a následně zavolat [vytvořit](#create) členskou funkci, která vytvoří okna s rozdělovačem a připojí ho k `CSplitterWnd` objektu.

##  <a name="deletecolumn"></a>  CSplitterWnd::DeleteColumn

Odstraní sloupec z okna s rozdělovačem.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Parametry

*colDelete*<br/>
Určuje sloupec, který se odstraní.

### <a name="remarks"></a>Poznámky

Tato členská funkce se volá se rozhraním implementovat logiku z okna s rozdělovačem dynamický (tj. Pokud okna s rozdělovačem má SPLS_DYNAMIC_SPLIT style). To je možné přizpůsobit, spolu s virtuální funkcí [CreateView](#createview), implementovat rozšířené dynamické příčky.

##  <a name="deleterow"></a>  CSplitterWnd::DeleteRow

Odstraní řádek z okna s rozdělovačem.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Parametry

*rowDelete*<br/>
Určuje řádku, který má být odstraněna.

### <a name="remarks"></a>Poznámky

Tato členská funkce se volá se rozhraním implementovat logiku z okna s rozdělovačem dynamický (tj. Pokud okna s rozdělovačem má SPLS_DYNAMIC_SPLIT style). To je možné přizpůsobit, spolu s virtuální funkcí [CreateView](#createview), implementovat rozšířené dynamické příčky.

##  <a name="deleteview"></a>  CSplitterWnd::DeleteView

Odstraní zobrazení z okna s rozdělovačem.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>Parametry

*Řádek*<br/>
Určuje řádku rozdělovač okna ve kterém se má odstranit zobrazení.

*sloupec*<br/>
Určuje sloupec rozdělovač okna na kterou chcete odstranit zobrazení.

### <a name="remarks"></a>Poznámky

Pokud se právě odstraňuje aktivní zobrazení, bude znovu aktivní další zobrazení. Výchozí implementace předpokládá zobrazení se automaticky odstranit [postncdestroy –](../../mfc/reference/cwnd-class.md#postncdestroy).

Tato členská funkce se volá se rozhraním implementovat logiku z okna s rozdělovačem dynamický (tj. Pokud okna s rozdělovačem má SPLS_DYNAMIC_SPLIT style). To je možné přizpůsobit, spolu s virtuální funkcí [CreateView](#createview), implementovat rozšířené dynamické příčky.

##  <a name="dokeyboardsplit"></a>  CSplitterWnd::DoKeyboardSplit

Provádí příkaz rozdělení klávesnice, obvykle "Window Split."

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je základní příkaz, který je používán [CView](../../mfc/reference/cview-class.md) třídy delegovat `CSplitterWnd` implementace.

##  <a name="doscroll"></a>  CSplitterWnd::DoScroll

Provádí synchronizované posouvání rozdělených oken.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewFrom*<br/>
Ukazatel na zobrazení, ze kterého pochází zpráva umožňující posouvání.

*nScrollCode*<br/>
Posuvníku kód, který označuje, že uživatel je posouvání požadavku. Tento parametr se skládá ze dvou částí: nejnižší bajt, který určuje typ vodorovně posuvný dochází, a implikovaný bajt, který určuje typ svisle posuvný výskytu:

    - Posune SB_BOTTOM dolů.

    - Posune SB_LINEDOWN jeden řádek dolů.

    - Posune SB_LINEUP jeden řádek nahoru.

    - Posune SB_PAGEDOWN jednu stránku dolů.

    - Posune SB_PAGEUP jednu stránku nahoru.

    - Posune SB_TOP nahoru.

*bDoScroll*<br/>
Určuje, zda dojde k posouvání zadanou akci. Pokud *bDoScroll* je hodnotu TRUE (tj. Pokud existuje podřízeného okna a mít rozsahu posouvání rozdělených oken), pak na zadanou akci posouvání může proběhnout; Pokud *bDoScroll* hodnotu FALSE (to znamená, pokud žádné podřízené okno existuje, nebo rozdělené zobrazení je k dispozici žádná oblast posouvání), pak posouvání nevyskytuje.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dojde k synchronizované posouvání; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce se volá se rozhraním provádět synchronizované posouvání rozdělených oken. při zobrazení přijme zprávu posuvníku. Přepsání nastavení za účelem před synchronizované posouvání může vyžadovat akci uživatele.

##  <a name="doscrollby"></a>  CSplitterWnd::DoScrollBy

Posouvání rozdělených oken o daný počet pixelů.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewFrom*<br/>
Ukazatel na zobrazení, ze kterého pochází zpráva umožňující posouvání.

*sizeScroll*<br/>
Počet pixelů k posouvat vodorovně a svisle.

*bDoScroll*<br/>
Určuje, zda dojde k posouvání zadanou akci. Pokud *bDoScroll* je hodnotu TRUE (tj. Pokud existuje podřízeného okna a mít rozsahu posouvání rozdělených oken), pak na zadanou akci posouvání může proběhnout; Pokud *bDoScroll* hodnotu FALSE (to znamená, pokud žádné podřízené okno existuje, nebo rozdělené zobrazení je k dispozici žádná oblast posouvání), pak posouvání nevyskytuje.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dojde k synchronizované posouvání; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce se volá se rozhraním v reakci na zprávu posuvníku, k provedení synchronizované posouvání rozdělených oken vzdálenost v pixelech, indikován *sizeScroll*. Kladné hodnoty udávají posun dolů a doprava; záporné hodnoty označují posouvání nahoru a doleva.

Přepsání nastavení za účelem vyžadovat zásah uživatele předtím, než posuvníku.

##  <a name="getactivepane"></a>  CSplitterWnd::GetActivePane

Určuje aktivní podokno ze aktivní nebo aktivní zobrazení v rámci.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Parametry

*pRow*<br/>
Ukazatel **int** načíst počet řádků aktivní podokno.

*pCol*<br/>
Ukazatel **int** načíst počet sloupců aktivní podokno.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktivní podokno. Hodnota NULL, pokud neexistuje žádná aktivní podokno.

### <a name="remarks"></a>Poznámky

Tato členská funkce se volá se rozhraním určit aktivní podokno v okno s rozdělovačem. Přepsání nastavení za účelem vyžadovat zásah uživatele před získáním aktivní podokno.

##  <a name="getcolumncount"></a>  CSplitterWnd::GetColumnCount

Vrátí aktuální počet sloupců podokně.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální počet sloupců v příčky. Pro statické rozdělovače bude také maximální počet sloupců.

##  <a name="getcolumninfo"></a>  CSplitterWnd::GetColumnInfo

Vrací informace na sloupec.

```
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>Parametry

*sloupec*<br/>
Určuje sloupec.

*cxCur*<br/>
Odkaz na **int** být nastavena na šířku sloupce.

*cxMin*<br/>
Odkaz na **int** být nastavena na aktuální minimální šířka sloupce.

##  <a name="getpane"></a>  CSplitterWnd::GetPane

Vrátí podokno na zadaný řádek ve sloupci.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parametry

*Řádek*<br/>
Určuje řádek.

*sloupec*<br/>
Určuje sloupec.

### <a name="return-value"></a>Návratová hodnota

Vrátí podokno na zadaný řádek ve sloupci. Vrácené podokno je obvykle [CView](../../mfc/reference/cview-class.md)-odvozené třídy.

##  <a name="getrowcount"></a>  CSplitterWnd::GetRowCount

Vrátí aktuální počet řádků podokně.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální počet řádků v okna s rozdělovačem. Statický rozdělovač okna bude také maximální počet řádků.

##  <a name="getrowinfo"></a>  CSplitterWnd::GetRowInfo

Vrací informace na zadaný řádek.

```
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>Parametry

*Řádek*<br/>
Určuje řádek.

*cyCur*<br/>
Odkaz na **int** být nastavena na aktuální výška řádku v pixelech.

*cyMin*<br/>
Odkaz na **int** být nastavena na aktuální minimální výška řádku v pixelech.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce k získání informací o zadaný řádek. *CyCur* parametr je vyplněna aktuální výška řádku zadané a *cyMin* je vyplněna minimální výška řádku.

##  <a name="getscrollstyle"></a>  CSplitterWnd::GetScrollStyle

Vrátí hodnotu sdíleného posuvník styl okna s rozdělovačem.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Jeden nebo více z následujících oken stylu příznaky, v případě úspěšného ověření:

    - WS_HSCROLL Pokud příčky aktuálně spravuje sdílené vodorovné posuvníky.

    - WS_VSCROLL Pokud příčky aktuálně spravuje sdílené svislé posuvníky.

Pokud je nula, okna s rozdělovačem aktuálně nespravuje žádné sdílené posuvníky.

##  <a name="idfromrowcol"></a>  CSplitterWnd::IdFromRowCol

Získá podřízené okno ID pro podokno na zadaný řádek ve sloupci.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parametry

*Řádek*<br/>
Určuje řádku rozdělovač okna.

*sloupec*<br/>
Určuje sloupec rozdělovač okna.

### <a name="return-value"></a>Návratová hodnota

ID podřízené okno podokna.

### <a name="remarks"></a>Poznámky

Tato členská funkce je vhodná k vytváření nonviews jako podokna a může být volána před podokně existuje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

##  <a name="ischildpane"></a>  CSplitterWnd::IsChildPane

Určuje, zda *pWnd* právě podřízené podokno rozdělovač okna.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objektu má být testována.

*pRow*<br/>
Ukazatel **int** ve které se má uložit číslo řádku.

*pCol*<br/>
Ukazatel **int** ve které se má uložit číslo sloupce.

### <a name="return-value"></a>Návratová hodnota

Pokud nenulovou hodnotu, *pWnd* právě podřízené podokno tento rozdělovač okna a *pRow* a *pCol* se vyplní pozici v podokně do okna s rozdělovačem. Pokud *pWnd* není podřízené podokno rozdělovač okna, vrátí se 0.

### <a name="remarks"></a>Poznámky

V jazyce Visual C++ verze starší než 6.0 tato funkce byla definována jako

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Tato verze je zastaralý a neměl by se používat.

##  <a name="istracking"></a>  CSplitterWnd::IsTracking

Voláním této členské funkce k určení, pokud je aktuálně přesunutí příčky v okně.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud operace rozdělovač probíhá; jinak 0.

##  <a name="ondrawsplitter"></a>  CSplitterWnd::OnDrawSplitter

Vykreslí obrázek rozděleného okna.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na kontext zařízení, ve kterém chcete-li nakreslit. Pokud *primárního řadiče domény* má hodnotu NULL, pak [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) nazývá a žádná rozdělení okna vykreslením.

*nType*<br/>
Hodnota `enum ESplitType`, což může být jeden z následujících akcí:

    - `splitBox` Přetáhněte pole rozdělovač.

    - `splitBar` Panel, který se zobrazí mezi dvěma rozdělených oken.

    - `splitIntersection` Je určena průsečíkem rozdělených oken. Tento prvek nebude volána, když běží na Windows 95/98.

    - `splitBorder` Rozdělit okno ohraničení.

*rect*<br/>
Odkaz na [crect –](../../atl-mfc-shared/reference/crect-class.md) určující velikost a tvar rozdělených oken.

### <a name="remarks"></a>Poznámky

Tato členská funkce se volá se rozhraním, kreslit a určit přesné vlastnosti okno s rozdělovačem. Přepsat `OnDrawSplitter` pro vlastní obrázek pro různé součásti grafické okno s rozdělovačem. Výchozí obrázek je podobný rozdělovač v aplikaci Microsoft Works pro Windows nebo Microsoft Windows 95/98, průnikům pruhy rozdělovač jsou prolnuty společně.

Další informace o dynamické rozdělovače oken, naleznete v tématu "Rozdělovač Windows" v článku [více typů dokumentů, zobrazení a rámečku Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technická poznámka 29](../../mfc/tn029-splitter-windows.md)a `CSplitterWnd` přehledu třídy.

##  <a name="oninverttracker"></a>  CSplitterWnd::OnInvertTracker

Vykreslí obraz rozděleného okna se stejnou velikost a tvar jako okno rámce.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Parametry

*rect*<br/>
Odkaz `CRect` určující sledování obdélník.

### <a name="remarks"></a>Poznámky

Tato členská funkce je voláno rozhraním během změny velikosti příčky. Přepsat `OnInvertTracker` pro vlastní obrázek okna s rozdělovačem. Výchozí obrázek je podobný rozdělovač v aplikaci Microsoft Works pro Windows nebo Microsoft Windows 95/98, průnikům pruhy rozdělovač jsou prolnuty společně.

Další informace o dynamické rozdělovače oken, naleznete v tématu "Rozdělovač Windows" v článku [více typů dokumentů, zobrazení a rámečku Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technická poznámka 29](../../mfc/tn029-splitter-windows.md)a `CSplitterWnd` přehledu třídy.

##  <a name="recalclayout"></a>  CSplitterWnd::RecalcLayout

Volání k opětovnému zobrazení okna s rozdělovačem po úpravě řádku nebo sloupce.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Poznámky

Voláním této členské funkce až po úpravě velikosti řádků a sloupců s správně znovu zobrazit okna s rozdělovačem [SetRowInfo](#setrowinfo) a [SetColumnInfo](#setcolumninfo) členské funkce. Pokud změníte velikost řádků a sloupců jako součást procesu vytváření před okna s rozdělovačem je viditelná, není nutné zavolat tuto členskou funkci.

Rozhraní volá tuto funkci člena pokaždé, když uživatel změní velikost okna s rozdělovačem nebo přesune rozdělení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CSplitterWnd::SetColumnInfo](#setcolumninfo).

##  <a name="setactivepane"></a>  CSplitterWnd::SetActivePane

Nastaví podokno, které má být aktivní v rámci.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Řádek*<br/>
Pokud *pWnd* má hodnotu NULL, určuje řádku v podokně, které bude aktivní.

*sloupec*<br/>
Pokud *pWnd* má hodnotu NULL, určuje sloupec v podokně, které bude aktivní.

*pWnd*<br/>
Ukazatel `CWnd` objektu. Pokud má hodnotu NULL, v podokně určené *řádek* a *sloupec* je nastavit aktivní. Pokud není NULL, určuje podokno, které se nastavit aktivní.

### <a name="remarks"></a>Poznámky

Tato členská funkce se volá se rozhraním nastavit podokno jako aktivní, když uživatel změní fokus do podokna okna rámce. Můžete explicitně volat `SetActivePane` změnit fokus na určené zobrazení.

Zadejte podokně poskytnutím řádků a sloupců, **nebo** poskytnutím *pWnd*.

##  <a name="setcolumninfo"></a>  CSplitterWnd::SetColumnInfo

Volání za účelem nastavení informací o zadaný sloupec.

```
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>Parametry

*sloupec*<br/>
Určuje sloupec rozdělovač okna.

*cxIdeal*<br/>
Určuje ideální šířku sloupce rozdělovač okna v pixelech.

*cxMin*<br/>
Určuje minimální šířku sloupce rozdělovač okna v pixelech.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce nastavte nový minimální šířku a ideální šířku sloupce. Minimální hodnota sloupce určuje, kdy bude sloupec příliš malá, který se zobrazí plně.

Když se zobrazí rozhraní okna s rozdělovačem, rozložen podokny sloupců a řádků podle jejich ideální dimenze práci v levém horním rohu do pravého dolního rohu okna s rozdělovačem od klientské oblasti.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

##  <a name="setrowinfo"></a>  CSplitterWnd::SetRowInfo

Volání za účelem nastavení informací o zadaný řádek.

```
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>Parametry

*Řádek*<br/>
Určuje řádek rozdělovač okna.

*cyIdeal*<br/>
Ideální výška řádku okno rozdělovače určuje v pixelech.

*cyMin*<br/>
Určuje minimální výška řádku rozdělovač okna v pixelech.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce, chcete-li nastavit nový minimální výšku a ideální výšku řádku. Minimální hodnota řádku určuje, kdy bude příliš malá, který se má zobrazit plně řádku.

Když se zobrazí rozhraní okna s rozdělovačem, rozložen podokny sloupců a řádků podle jejich ideální dimenze práci v levém horním rohu do pravého dolního rohu okna s rozdělovačem od klientské oblasti.

##  <a name="setscrollstyle"></a>  CSplitterWnd::SetScrollStyle

Určuje, že podpora posuvníku sdílených nový styl posouvání rozdělovač okna.

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Nový styl posouvání pro okna s rozdělovačem na sdílené podporu posuvníku, která může být jedna z následujících hodnot:

- WS_HSCROLL Create/zobrazit sdílené vodorovným posuvníkům.

- WS_VSCROLL Create/zobrazit svislé sdílené posuvníky.

### <a name="remarks"></a>Poznámky

Po vytvoření posuvníku nebude zničení i v případě `SetScrollStyle` je volána bez styl; místo toho jsou skryté tyto posuvníky. To umožňuje posuvníky zachovat jejich stavu, i když jsou skryté. Po volání `SetScrollStyle` je potřeba volat [recalclayout –](#recalclayout) pro všechny změny se projeví.

##  <a name="splitcolumn"></a>  CSplitterWnd::SplitColumn

Určuje, kde se okno rámce rozdělí svisle.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Parametry

*cxBefore*<br/>
Pozice v pixelech, u nichž dojde k rozdělení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána, když se vytvoří okno svislé příčky. `SplitColumn` Určuje výchozí umístění, kde dochází k rozdělení.

`SplitColumn` je voláno rozhraním implementovat logiku z okna s rozdělovačem dynamický (tj. Pokud okna s rozdělovačem má SPLS_DYNAMIC_SPLIT style). To je možné přizpůsobit, spolu s virtuální funkcí [CreateView](#createview), implementovat rozšířené dynamické příčky.

##  <a name="splitrow"></a>  CSplitterWnd::SplitRow

Určuje, kde se okno rámce rozdělí vodorovně.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Parametry

*cyBefore*<br/>
Pozice v pixelech, u nichž dojde k rozdělení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána, když se vytvoří okno vodorovné příčky. `SplitRow` Určuje výchozí umístění, kde dochází k rozdělení.

`SplitRow` je voláno rozhraním implementovat logiku z okna s rozdělovačem dynamický (tj. Pokud okna s rozdělovačem má SPLS_DYNAMIC_SPLIT style). To je možné přizpůsobit, spolu s virtuální funkcí [CreateView](#createview), implementovat rozšířené dynamické příčky.

##  <a name="ondraw"></a>  CSplitterWnd::OnDraw

Volá se rozhraním, chcete-li nakreslit okna s rozdělovačem.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na kontext zařízení.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[Třída CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[Třída CWnd](../../mfc/reference/cwnd-class.md)
