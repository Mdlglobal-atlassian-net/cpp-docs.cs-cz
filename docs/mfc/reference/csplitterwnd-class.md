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
ms.openlocfilehash: a872854af1695b8b2b347b21d73165d259b3a986
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753061"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd – třída

Poskytuje funkce okna rozdělovače, což je okno, které obsahuje více podoken.

## <a name="syntax"></a>Syntaxe

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Volání k `CSplitterWnd` vytvoření objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSplitterWnd::AktivovatDalší](#activatenext)|Provede příkaz Další podokno nebo Předchozí podokno.|
|[CSplitterWnd::CanActivateNext](#canactivatenext)|Zkontroluje, zda je aktuálně možný příkaz Další podokno nebo Předchozí podokno.|
|[CSplitterWnd::Vytvořit](#create)|Volání vytvořit dynamické okno rozdělovač a `CSplitterWnd` připojit k objektu.|
|[CSplitterWnd::VytvořitScrollBarCtrl](#createscrollbarctrl)|Vytvoří sdílený ovládací prvek posuvníku.|
|[CSplitterWnd::Vytvořitstatickou](#createstatic)|Volání vytvořit statické okno rozdělovač a `CSplitterWnd` připojit k objektu.|
|[CSplitterWnd::CreateView](#createview)|Volání k vytvoření podokna v okně rozdělovače.|
|[CSplitterWnd::DeleteSloupec](#deletecolumn)|Odstraní sloupec z okna rozdělovače.|
|[CSplitterWnd::DeleteRow](#deleterow)|Odstraní řádek z okna rozdělovače.|
|[CSplitterWnd::DeleteView](#deleteview)|Odstraní pohled z okna rozdělovače.|
|[CSplitterWnd::DoKlávesniceSplit](#dokeyboardsplit)|Provede příkaz rozdělení klávesnice, obvykle "Rozdělení okna".|
|[CSplitterWnd::DoScroll](#doscroll)|Provádí synchronizované posouvání rozdělených oken.|
|[CSplitterWnd::DoScrollBy](#doscrollby)|Posouvá rozdělená okna o daný počet pixelů.|
|[CSplitterWnd::GetActivePane](#getactivepane)|Určuje aktivní podokno z fokusu nebo aktivního pohledu v rámečku.|
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Vrátí počet aktuálních sloupců podokna.|
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Vrátí informace v zadaném sloupci.|
|[CSplitterWnd::GetPane](#getpane)|Vrátí podokno na zadaném řádku a sloupci.|
|[CSplitterWnd::GetRowCount](#getrowcount)|Vrátí počet řádků aktuálního podokna.|
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Vrátí informace na zadaném řádku.|
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Vrátí styl sdíleného posuvníku.|
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Vrátí ID podřízeného okna podokna v zadaném řádku a sloupci.|
|[CSplitterWnd::IsChildPane](#ischildpane)|Volání k určení, zda okno je aktuálně podřízené podokno tohoto okna rozdělovače.|
|[CSplitterWnd::Sledování](#istracking)|Určuje, zda je panel rozdělovače právě přesouván.|
|[CSplitterWnd::Rozložení](#recalclayout)|Volání znovu zobrazit okno rozdělovače po úpravě řádku nebo velikosti sloupce.|
|[CSplitterWnd::SetActivePane](#setactivepane)|Nastaví podokno jako aktivní podokno v rámečku.|
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|Volání nastavení informací o zadaném sloupci.|
|[CSplitterWnd::SetRowInfo](#setrowinfo)|Volání pro nastavení informací o zadaném řádku.|
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Určuje nový styl posuvníku pro podporu sdíleného posuvníku v okně rozdělovače.|
|[CSplitterWnd::SplitColumn](#splitcolumn)|Označuje, kde se okno rámce rozdělí svisle.|
|[CSplitterWnd::SplitRow](#splitrow)|Označuje, kde se okno rámce rozdělí vodorovně.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CSplitterWnd::OnDraw](#ondraw)|Volat rámci k nakreslení okno rozdělovače.|
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Vykreslí obrázek rozděleného okna.|
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Vykreslí obraz rozděleného okna na stejnou velikost a tvar jako okno rámce.|

## <a name="remarks"></a>Poznámky

Podokno je obvykle objekt specifický pro aplikaci odvozený z [CView](../../mfc/reference/cview-class.md), ale může být libovolný [cwnd](../../mfc/reference/cwnd-class.md) objekt, který má příslušné podřízené okno ID.

Objekt `CSplitterWnd` je obvykle vložen do nadřazeného objektu [CFrameWnd](../../mfc/reference/cframewnd-class.md) nebo [CMDIChildWnd.](../../mfc/reference/cmdichildwnd-class.md) Vytvořte `CSplitterWnd` objekt pomocí následujících kroků:

1. Vloží člennou `CSplitterWnd` proměnnou do nadřazeného rámečku.

2. Přepište nadřazený rám [je CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) členská funkce.

3. Z v rámci `OnCreateClient`přepsána volejte [vytvořit](#create) nebo `CSplitterWnd` [VytvořitStatic](#createstatic) členská funkce .

Volání `Create` členské funkce k vytvoření dynamického okna rozdělovače. Dynamické okno rozdělovače se obvykle používá k vytvoření a posouvání několika jednotlivých podoken nebo zobrazení stejného dokumentu. Rozhraní automaticky vytvoří počáteční podokno pro rozdělovač; pak rozhraní vytvoří, změní velikost a nakládá s dalšími podokny, protože uživatel pracuje s ovládacími prvky okna rozdělovače.

Při volání `Create`zadáte minimální výšku řádku a šířku sloupce, které určují, kdy jsou podokna příliš malá na to, aby byla plně zobrazena. Po volání `Create`můžete upravit tato minima voláním členských funkcí [SetColumnInfo](#setcolumninfo) a [SetRowInfo.](#setrowinfo)

Také použijte `SetColumnInfo` `SetRowInfo` a členské funkce pro nastavení "ideální" šířky pro sloupec a "ideální" výšky pro řádek. Když rozhraní zobrazí okno rozdělovače, nejprve zobrazí nadřazený rámec, potom okno rozdělovače. Rámec pak rozdělí podokna ve sloupcích a řádcích podle jejich ideálních rozměrů a pracuje od levého horního rohu do pravého dolního rohu klientské oblasti okna rozdělovače.

Všechna podokna v okně dynamického rozdělovače musí být stejné třídy. Mezi známé aplikace, které podporují dynamická okna rozdělovače, patří aplikace Microsoft Word a Microsoft Excel.

Pomocí `CreateStatic` členské funkce vytvořte statické okno rozdělovače. Uživatel může změnit pouze velikost podoken ve statickém okně rozdělovače, nikoli jejich číslo nebo pořadí.

Při vytváření statického rozdělovače je nutné vytvořit konkrétně všechna podokna statického rozdělovače. Ujistěte se, že vytvoříte všechna podokna před členské funkce nadřazeného `OnCreateClient` rámce vrátí nebo rozhraní nezobrazí okno správně.

Členská `CreateStatic` funkce automaticky inicializuje statický rozdělovač s minimální výškou řádku a šířkou sloupce 0. Po volání `Create`upravte tato minima voláním členských funkcí [SetColumnInfo](#setcolumninfo) a [SetRowInfo.](#setrowinfo) Používejte `SetColumnInfo` také `SetRowInfo` a `CreateStatic` po volání označte požadované ideální rozměry podokna.

Jednotlivá podokna statického rozdělovače často patří do různých tříd. Příklady statických dělicích oken naleznete v grafickém editoru a ve Správci souborů systému Windows.

Okno rozdělovače podporuje speciální posuvníky (kromě posuvníků, které mohou mít podokna). Tyto posuvníky `CSplitterWnd` jsou podřízené objektu a jsou sdíleny s podokny.

Tyto speciální posuvníky vytvoříte při vytváření okna rozdělovače. Například, `CSplitterWnd` který má jeden řádek, dva sloupce a styl WS_VSCROLL zobrazí svislý posuvník, který je sdílen dvěma podokny. Když uživatel přesune posuvník, WM_VSCROLL zprávy jsou odesílány do obou podoken. Když podokna nastaví polohu posuvníku, nastaví se sdílený posuvník.

Další informace o rozbočovači jsou nadále [viz technická poznámka 29](../../mfc/tn029-splitter-windows.md).

Další informace o vytváření dynamických dělicích oken naleznete v tématu:

- [Klikyháky](../../overview/visual-cpp-samples.md) vzorku knihovny MFC

- Vzorek MFC [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="csplitterwndactivatenext"></a><a name="activatenext"></a>CSplitterWnd::AktivovatDalší

Volat rámci k provedení příkazu Další podokno nebo Předchozí podokno.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parametry

*bPrev*<br/>
Označuje, které okno se má aktivovat. **TRUE** pro předchozí; **FALSE** pro další.

### <a name="remarks"></a>Poznámky

Tato členská funkce je příkaz vysoké úrovně, který používá `CSplitterWnd` třída [CView](../../mfc/reference/cview-class.md) k delegování implementace.

## <a name="csplitterwndcanactivatenext"></a><a name="canactivatenext"></a>CSplitterWnd::CanActivateNext

Volat v rámci zkontrolovat, zda další podokno nebo předchozí podokno příkaz je aktuálně možné.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parametry

*bPrev*<br/>
Označuje, které okno se má aktivovat. **TRUE** pro předchozí; **FALSE** pro další.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je příkaz vysoké úrovně, který používá `CSplitterWnd` třída [CView](../../mfc/reference/cview-class.md) k delegování implementace.

## <a name="csplitterwndcreate"></a><a name="create"></a>CSplitterWnd::Vytvořit

Chcete-li vytvořit dynamické okno `Create` rozdělovače, zavolejte členní funkci.

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
Nadřazené okno rámce okna rozdělovače.

*nMaxRows*<br/>
Maximální počet řádků v okně rozdělovače. Tato hodnota nesmí překročit 2.

*nMaxCols*<br/>
Maximální počet sloupců v okně rozdělovače. Tato hodnota nesmí překročit 2.

*sizeMin*<br/>
Určuje minimální velikost, při které může být podokno zobrazeno.

*pKontext*<br/>
Ukazatel na [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Ve většině případů to může být *pContext* předán a nadřazené okno rámce.

*dwStyl*<br/>
Určuje styl okna.

*Nid*<br/>
ID podřízeného okna. ID lze AFX_IDW_PANE_FIRST, pokud je okno rozdělovače vnořené do jiného okna rozdělovače.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

A můžete vložit `CSplitterWnd` do nadřazeného objektu [CFrameWnd](../../mfc/reference/cframewnd-class.md) nebo [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) následujícím postupem:

1. Vloží člennou `CSplitterWnd` proměnnou do nadřazeného rámečku.

1. Přepište nadřazený rám [je CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) členská funkce.

1. Volání `Create` členské funkce z v `OnCreateClient`rámci přepsaného .

Když vytvoříte okno rozdělovače z v rámci nadřazeného rámce, předajte parametr *pContext* nadřazeného rámce do okna rozdělovače. V opačném případě může být tento parametr null.

Počáteční minimální výška řádku a šířka sloupce dynamického okna rozdělovače jsou nastaveny parametrem *sizeMin.* Tato minima, která určují, zda je podokno příliš malé na to, aby se zobrazilo v plném rozsahu, lze změnit pomocí členských funkcí [SetRowInfo](#setrowinfo) a [SetColumnInfo.](#setcolumninfo)

Další informace o dynamických oknech rozdělovače naleznete v článku [Více typů dokumentů, zobrazení a rámového systému](../../mfc/multiple-document-types-views-and-frame-windows.md) `CSplitterWnd` Windows , [technická poznámka 29](../../mfc/tn029-splitter-windows.md)a přehled třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

## <a name="csplitterwndcreatescrollbarctrl"></a><a name="createscrollbarctrl"></a>CSplitterWnd::VytvořitScrollBarCtrl

Volat rámci vytvořit sdílený ovládací prvek posuvníku.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl okna.

*Nid*<br/>
ID podřízeného okna. ID lze AFX_IDW_PANE_FIRST, pokud je okno rozdělovače vnořené do jiného okna rozdělovače.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Přepsáním `CreateScrollBarCtrl` chcete-li vedle posuvníku zahrnout další ovládací prvky. Výchozím chováním je vytvoření běžných ovládacích prvků posuvníku systému Windows.

## <a name="csplitterwndcreatestatic"></a><a name="createstatic"></a>CSplitterWnd::Vytvořitstatickou

Chcete-li vytvořit statické okno `CreateStatic` rozdělovače, zavolejte členní funkci.

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
Nadřazené okno rámce okna rozdělovače.

*nŘádky*<br/>
Počet řádků Tato hodnota nesmí překročit 16.

*nKolky*<br/>
Počet sloupců Tato hodnota nesmí překročit 16.

*dwStyl*<br/>
Určuje styl okna.

*Nid*<br/>
ID podřízeného okna. ID lze AFX_IDW_PANE_FIRST, pokud je okno rozdělovače vnořené do jiného okna rozdělovače.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

A `CSplitterWnd` je obvykle vložena `CFrameWnd` do nadřazeného objektu nebo [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) provedením následujících kroků:

1. Vloží člennou `CSplitterWnd` proměnnou do nadřazeného rámečku.

1. Přepište člennou funkci `OnCreateClient` nadřazeného rámce.

1. Volání `CreateStatic` členské funkce z přepsaného [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).

Statické okno rozdělovače obsahuje pevný počet podoken, často z různých tříd.

Při vytváření statického rozdělovače okna, musíte současně vytvořit všechny jeho podokna. Členská funkce [CreateView](#createview) se obvykle používá pro tento účel, ale můžete také vytvořit jiné třídy bez zobrazení.

Počáteční minimální výška řádku a šířka sloupce pro statické okno rozdělovače je 0. Tato minima, která určují, kdy je podokno příliš malé, aby se zobrazilo v plném rozsahu, lze změnit pomocí členských funkcí [SetRowInfo](#setrowinfo) a [SetColumnInfo.](#setcolumninfo)

Chcete-li přidat posuvníky do statického okna rozdělovače, přidejte styly WS_HSCROLL a WS_VSCROLL do *stylu dwStyle*.

Další informace o statických oknech rozdělovače naleznete v článku "Splitter Windows" v článku [Více typů dokumentů, zobrazení a rámového systému Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [technická poznámka 29](../../mfc/tn029-splitter-windows.md)a přehled `CSplitterWnd` tříd.

## <a name="csplitterwndcreateview"></a><a name="createview"></a>CSplitterWnd::CreateView

Vytvoří podokna pro statické okno rozdělovače.

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parametry

*Řádku*<br/>
Určuje řádek okna rozdělovače, do kterého se má umístit nové zobrazení.

*Col*<br/>
Určuje sloupec okna rozdělovače, do kterého se má umístit nové zobrazení.

*pViewClass*<br/>
Určuje [cruntimedclass](../../mfc/reference/cruntimeclass-structure.md) nového zobrazení.

*sizeInit*<br/>
Určuje počáteční velikost nového zobrazení.

*pKontext*<br/>
Ukazatel na kontext vytvoření použitého k vytvoření zobrazení (obvykle *pContext* předaný do přepsané funkce CFrameWnd nadřazeného [rámce::OnCreateClient,](../../mfc/reference/cframewnd-class.md#oncreateclient) ve kterém se vytváří okno rozdělovače).

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Všechny podokna statického okna rozdělovače musí být vytvořeny před rozhraní mj.

Rozhraní Framework také volá tuto členská funkci k vytvoření nových podoken, když uživatel dynamického okna rozdělovače rozdělí podokno, řádek nebo sloupec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

## <a name="csplitterwndcsplitterwnd"></a><a name="csplitterwnd"></a>CSplitterWnd::CSplitterWnd

Volání k `CSplitterWnd` vytvoření objektu.

```
CSplitterWnd();
```

### <a name="remarks"></a>Poznámky

Vytvořte `CSplitterWnd` objekt ve dvou krocích. Nejprve zavolejte konstruktor, `CSplitterWnd` který vytvoří objekt, a potom volání [vytvořit](#create) členovou funkci, která `CSplitterWnd` vytvoří okno rozdělovače a připojí jej k objektu.

## <a name="csplitterwnddeletecolumn"></a><a name="deletecolumn"></a>CSplitterWnd::DeleteSloupec

Odstraní sloupec z okna rozdělovače.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Parametry

*colDelete*<br/>
Určuje sloupec, který má být odstraněn.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním pro implementaci logiky dynamického okna rozdělovače (to znamená, pokud má okno rozdělovače SPLS_DYNAMIC_SPLIT stylu). To může být přizpůsoben, spolu s virtuální funkcí [CreateView](#createview), implementovat pokročilejší dynamické rozdělovače.

## <a name="csplitterwnddeleterow"></a><a name="deleterow"></a>CSplitterWnd::DeleteRow

Odstraní řádek z okna rozdělovače.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Parametry

*řádekOdstranit*<br/>
Určuje řádek, který má být odstraněn.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním pro implementaci logiky dynamického okna rozdělovače (to znamená, pokud má okno rozdělovače SPLS_DYNAMIC_SPLIT stylu). To může být přizpůsoben, spolu s virtuální funkcí [CreateView](#createview), implementovat pokročilejší dynamické rozdělovače.

## <a name="csplitterwnddeleteview"></a><a name="deleteview"></a>CSplitterWnd::DeleteView

Odstraní pohled z okna rozdělovače.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>Parametry

*Řádku*<br/>
Určuje řádek okna rozdělovače, na kterém má být zobrazení odstraněno.

*Col*<br/>
Určuje sloupec okna rozdělovače, ve kterém má být zobrazení odstraněno.

### <a name="remarks"></a>Poznámky

Pokud je aktivní zobrazení odstraněno, bude aktivní další zobrazení. Výchozí implementace předpokládá, že zobrazení bude automaticky odstranit v [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).

Tato členská funkce je volána rozhraním pro implementaci logiky dynamického okna rozdělovače (to znamená, pokud má okno rozdělovače SPLS_DYNAMIC_SPLIT stylu). To může být přizpůsoben, spolu s virtuální funkcí [CreateView](#createview), implementovat pokročilejší dynamické rozdělovače.

## <a name="csplitterwnddokeyboardsplit"></a><a name="dokeyboardsplit"></a>CSplitterWnd::DoKlávesniceSplit

Provede příkaz rozdělení klávesnice, obvykle "Rozdělení okna".

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je příkaz vysoké úrovně, který používá `CSplitterWnd` třída [CView](../../mfc/reference/cview-class.md) k delegování implementace.

## <a name="csplitterwnddoscroll"></a><a name="doscroll"></a>CSplitterWnd::DoScroll

Provádí synchronizované posouvání rozdělených oken.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewFrom*<br/>
Ukazatel na zobrazení, ze kterého pochází rolovací zpráva.

*nScrollCode*<br/>
Posuvník ový kód, který označuje požadavek uživatele na posouvání. Tento parametr se skládá ze dvou částí: bajtu nízkého řádu, který určuje typ posouvání, ke kterému dochází vodorovně, a bajt vysokého řádu, který určuje typ posouvání, ke kterému dochází svisle:

- SB_BOTTOM posune dolů.

- SB_LINEDOWN posune o řádek dolů.

- SB_LINEUP Posune o řádek nahoru.

- SB_PAGEDOWN posune o jednu stránku dolů.

- SB_PAGEUP Posune o jednu stránku nahoru.

- SB_TOP posouvá nahoru.

*bDoScroll*<br/>
Určuje, zda dojde k zadané akci posouvání. Pokud *bDoScroll* je TRUE (to znamená, pokud existuje podřízené okno a rozdělená okna mají rozsah posouvání), pak může dojít k zadané akci posouvání; Pokud *bDoScroll* je FALSE (to znamená, pokud neexistuje žádné podřízené okno nebo rozdělená zobrazení nemají rozsah posouvání), pak posouvání nedojde.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud dojde k synchronizované rolování; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním k provedení synchronizovaného posouvání rozdělených oken, když zobrazení obdrží posuvnou zprávu. Přepište, chcete-li vyžadovat akci uživatele před synchronizované posouvání je povoleno.

## <a name="csplitterwnddoscrollby"></a><a name="doscrollby"></a>CSplitterWnd::DoScrollBy

Posouvá rozdělená okna o daný počet pixelů.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewFrom*<br/>
Ukazatel na zobrazení, ze kterého pochází rolovací zpráva.

*sizeScroll*<br/>
Počet obrazových bodů, které mají být posunuty vodorovně a svisle.

*bDoScroll*<br/>
Určuje, zda dojde k zadané akci posouvání. Pokud *bDoScroll* je TRUE (to znamená, pokud existuje podřízené okno a rozdělená okna mají rozsah posouvání), pak může dojít k zadané akci posouvání; Pokud *bDoScroll* je FALSE (to znamená, pokud neexistuje žádné podřízené okno nebo rozdělená zobrazení nemají rozsah posouvání), pak posouvání nedojde.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud dojde k synchronizované rolování; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rámci v reakci na zprávu scroll, provádět synchronizované posouvání rozdělených oken o množství v pixelech, označené *sizeScroll*. Kladné hodnoty označují posouvání dolů a doprava; záporné hodnoty označují posouvání nahoru a doleva.

Přepište, chcete-li vyžadovat akci uživatele před povolením posouvání.

## <a name="csplitterwndgetactivepane"></a><a name="getactivepane"></a>CSplitterWnd::GetActivePane

Určuje aktivní podokno z fokusu nebo aktivního pohledu v rámečku.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Parametry

*pŘádek*<br/>
Ukazatel na **int** načíst číslo řádku aktivní podokno.

*pCol*<br/>
Ukazatel na **int** načíst číslo sloupce aktivní podokno.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktivní podokno. Null, pokud neexistuje žádné aktivní podokno.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním k určení aktivnípodokno v okně rozdělovače. Přepsáním budete před získáním aktivního podokna vyžadovat akci uživatele.

## <a name="csplitterwndgetcolumncount"></a><a name="getcolumncount"></a>CSplitterWnd::GetColumnCount

Vrátí počet aktuálních sloupců podokna.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální počet sloupců v rozdělovači. Pro statický rozdělovač to bude také maximální počet sloupců.

## <a name="csplitterwndgetcolumninfo"></a><a name="getcolumninfo"></a>CSplitterWnd::GetColumnInfo

Vrátí informace v zadaném sloupci.

```cpp
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>Parametry

*Col*<br/>
Určuje sloupec.

*cxCur*<br/>
Odkaz na **int** nastavit aktuální šířku sloupce.

*cxMin*<br/>
Odkaz na **int,** které mají být nastaveny na aktuální minimální šířku sloupce.

## <a name="csplitterwndgetpane"></a><a name="getpane"></a>CSplitterWnd::GetPane

Vrátí podokno na zadaném řádku a sloupci.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parametry

*Řádku*<br/>
Určuje řádek.

*Col*<br/>
Určuje sloupec.

### <a name="return-value"></a>Návratová hodnota

Vrátí podokno na zadaném řádku a sloupci. Vrácené podokno je obvykle [CView](../../mfc/reference/cview-class.md)-odvozené třídy.

## <a name="csplitterwndgetrowcount"></a><a name="getrowcount"></a>CSplitterWnd::GetRowCount

Vrátí počet řádků aktuálního podokna.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální počet řádků v okně rozdělovače. Pro statické okno rozdělovače to bude také maximální počet řádků.

## <a name="csplitterwndgetrowinfo"></a><a name="getrowinfo"></a>CSplitterWnd::GetRowInfo

Vrátí informace na zadaném řádku.

```cpp
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>Parametry

*Řádku*<br/>
Určuje řádek.

*cyCur*<br/>
Odkaz **na int,** který má být nastaven na aktuální výšku řádku v pixelech.

*cyMin*<br/>
Odkaz **na int,** který má být nastaven na aktuální minimální výšku řádku v pixelech.

### <a name="remarks"></a>Poznámky

Volání této členské funkce získat informace o zadaném řádku. Parametr *cyCur* je vyplněn aktuální výškou zadaného řádku a *cyMin* je vyplněn minimální výškou řádku.

## <a name="csplitterwndgetscrollstyle"></a><a name="getscrollstyle"></a>CSplitterWnd::GetScrollStyle

Vrátí styl sdíleného posuvníku pro okno rozdělovače.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Jeden nebo více z následujících příznaků stylu systému Windows, pokud je úspěšná:

- WS_HSCROLL Pokud rozdělovač aktuálně spravuje sdílené vodorovné posuvníky.

- WS_VSCROLL Pokud rozdělovač aktuálně spravuje sdílené svislé posuvníky.

Pokud nula, okno rozdělovače aktuálně nespravuje žádné sdílené posuvníky.

## <a name="csplitterwndidfromrowcol"></a><a name="idfromrowcol"></a>CSplitterWnd::IdFromRowCol

Získá ID podřízeného okna pro podokno na zadaném řádku a sloupci.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parametry

*Řádku*<br/>
Určuje řádek okna rozdělovače.

*Col*<br/>
Určuje sloupec okna rozdělovače.

### <a name="return-value"></a>Návratová hodnota

ID podřízeného okna podokna.

### <a name="remarks"></a>Poznámky

Tato členská funkce se používá k vytváření nezobrazení jako podoken a může být volána před existencí podokna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

## <a name="csplitterwndischildpane"></a><a name="ischildpane"></a>CSplitterWnd::IsChildPane

Určuje, zda *pWnd* je aktuálně podřízený mašlí tohoto okna rozdělovače.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na [cWnd](../../mfc/reference/cwnd-class.md) objekt, který má být testován.

*pŘádek*<br/>
Ukazatel na **int,** ve kterém chcete uložit číslo řádku.

*pCol*<br/>
Ukazatel na **int,** do kterého chcete uložit číslo sloupce.

### <a name="return-value"></a>Návratová hodnota

Pokud nenulová, *pWnd* je aktuálně podřízený malíček tohoto okna rozdělovače a *pRow* a *pCol* jsou vyplněny s umístěním podokna v okně rozdělovače. Pokud *pWnd* není podřízený mašlový panel tohoto okna rozdělovače, 0 je vrácena.

### <a name="remarks"></a>Poznámky

Ve verzích Visual C++ před verzí 6.0 byla tato funkce definována jako

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Tato verze je nyní zastaralá a neměla by být používána.

## <a name="csplitterwndistracking"></a><a name="istracking"></a>CSplitterWnd::Sledování

Volání této členské funkce k určení, zda je nyní přesouván rozdělovač v okně.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud probíhá operace rozdělovače; jinak 0.

## <a name="csplitterwndondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWnd::OnDrawSplitter

Vykreslí obrázek rozděleného okna.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext zařízení, ve kterém chcete kreslit. Pokud *pDC* je NULL, pak [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) je volána rámci a žádné rozdělené okno je nakreslena.

*nTyp*<br/>
Hodnota `enum ESplitType`, která může být jedna z následujících:

- `splitBox`Rozdělovač přetahovací rámeček.

- `splitBar`Pruh, který se zobrazí mezi dvěma rozdělenými okny.

- `splitIntersection`Průsečík rozdělených oken. Tento prvek nebude volán při spuštění v systému Windows 95/98.

- `splitBorder`Rozdělení ohraničení okna.

*Rect*<br/>
Odkaz na [cRect](../../atl-mfc-shared/reference/crect-class.md) objekt určující velikost a tvar rozdělených oken.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rámci k nakreslení a určení přesné charakteristiky okna rozdělovače. Přepsat `OnDrawSplitter` pro pokročilé přizpůsobení snímků pro různé grafické součásti okna rozdělovače. Výchozí snímky jsou podobné rozdělovači v aplikaci Microsoft Works pro systém Windows nebo Microsoft Windows 95/98 v tom, že průsečíky pruhů rozdělovače jsou prolnuty dohromady.

Další informace o dynamických oknech rozdělovače naleznete v článku [Více typů dokumentů, zobrazení a rámového systému](../../mfc/multiple-document-types-views-and-frame-windows.md) `CSplitterWnd` Windows , [technická poznámka 29](../../mfc/tn029-splitter-windows.md)a přehled třídy.

## <a name="csplitterwndoninverttracker"></a><a name="oninverttracker"></a>CSplitterWnd::OnInvertTracker

Vykreslí obraz rozděleného okna na stejnou velikost a tvar jako okno rámce.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Odkaz na `CRect` objekt určující sledovací obdélník.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rámci při změna velikosti rozdělovače. Přepsat `OnInvertTracker` pro pokročilé přizpůsobení snímků okna rozdělovače. Výchozí snímky jsou podobné rozdělovači v aplikaci Microsoft Works pro systém Windows nebo Microsoft Windows 95/98 v tom, že průsečíky pruhů rozdělovače jsou prolnuty dohromady.

Další informace o dynamických oknech rozdělovače naleznete v článku [Více typů dokumentů, zobrazení a rámového systému](../../mfc/multiple-document-types-views-and-frame-windows.md) `CSplitterWnd` Windows , [technická poznámka 29](../../mfc/tn029-splitter-windows.md)a přehled třídy.

## <a name="csplitterwndrecalclayout"></a><a name="recalclayout"></a>CSplitterWnd::Rozložení

Volání znovu zobrazit okno rozdělovače po úpravě řádku nebo velikosti sloupce.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Poznámky

Volání této členské funkce správně znovu zobrazit okno rozdělovač po úpravě velikosti řádků a sloupců s [SetRowInfo](#setrowinfo) a [SetColumnInfo](#setcolumninfo) členské funkce. Pokud změníte velikost řádků a sloupců jako součást procesu vytváření před okno rozdělovače je viditelný, není nutné volat tuto člennou funkci.

Rozhraní Framework volá tuto členská funkci vždy, když uživatel změní velikost okna rozdělovače nebo přesune rozdělení.

### <a name="example"></a>Příklad

  Viz příklad pro [CSplitterWnd::SetColumnInfo](#setcolumninfo).

## <a name="csplitterwndsetactivepane"></a><a name="setactivepane"></a>CSplitterWnd::SetActivePane

Nastaví podokno jako aktivní podokno v rámečku.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Řádku*<br/>
Pokud *pWnd* je NULL, určuje řádek v podokně, které bude aktivní.

*Col*<br/>
Pokud *pWnd* je NULL, určuje sloupec v podokně, který bude aktivní.

*pWnd*<br/>
Ukazatel na `CWnd` objekt. Pokud null, podokno určené *řádek* a *col* je nastavena aktivní. Pokud ne null, určuje podokno, které je nastaveno aktivní.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána v rámci nastavit podokno jako aktivní, když uživatel změní fokus na podokno v okně rámce. Můžete explicitně `SetActivePane` volat a změnit fokus na zadané zobrazení.

Určete podokno zadáním řádku a sloupce **nebo** zadáním *pWnd*.

## <a name="csplitterwndsetcolumninfo"></a><a name="setcolumninfo"></a>CSplitterWnd::SetColumnInfo

Volání nastavení informací o zadaném sloupci.

```cpp
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>Parametry

*Col*<br/>
Určuje sloupec okna rozdělovače.

*cxIdeální*<br/>
Určuje ideální šířku pro sloupec rozdělovače oken v obrazových bodech.

*cxMin*<br/>
Určuje minimální šířku sloupce okna rozdělovače v obrazových bodech.

### <a name="remarks"></a>Poznámky

Volání této členské funkce nastavit novou minimální šířku a ideální šířku pro sloupec. Minimální hodnota sloupce určuje, kdy bude sloupec příliš malý na to, aby byl plně zobrazen.

Když rozhraní zobrazí okno rozdělovače, rozkládá podokna ve sloupcích a řádcích podle jejich ideálních rozměrů a pracuje od levého horního rohu do pravého dolního rohu klientské oblasti okna rozdělovače.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

## <a name="csplitterwndsetrowinfo"></a><a name="setrowinfo"></a>CSplitterWnd::SetRowInfo

Volání pro nastavení informací o zadaném řádku.

```cpp
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>Parametry

*Řádku*<br/>
Určuje řádek okna rozdělovače.

*cyIdeální*<br/>
Určuje ideální výšku pro řádek okna rozdělovače v obrazových bodech.

*cyMin*<br/>
Určuje minimální výšku pro řádek okna rozdělovače v obrazových bodech.

### <a name="remarks"></a>Poznámky

Volání této členské funkce nastavit novou minimální výšku a ideální výšku pro řádek. Minimální hodnota řádku určuje, kdy bude řádek příliš malý, aby byl plně zobrazen.

Když rozhraní zobrazí okno rozdělovače, rozkládá podokna ve sloupcích a řádcích podle jejich ideálních rozměrů a pracuje od levého horního rohu do pravého dolního rohu klientské oblasti okna rozdělovače.

## <a name="csplitterwndsetscrollstyle"></a><a name="setscrollstyle"></a>CSplitterWnd::SetScrollStyle

Určuje nový styl posouvání pro podporu sdíleného posuvníku v okně rozdělovače.

```cpp
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Nový styl posouvání pro podporu sdíleného posuvníku v okně rozdělovače, což může být jedna z následujících hodnot:

- WS_HSCROLL Vytvořit/zobrazit vodorovné sdílené posuvníky.

- WS_VSCROLL Vytvořit/zobrazit svislé sdílené posuvníky.

### <a name="remarks"></a>Poznámky

Po vytvoření posuvníku nebude zničen, `SetScrollStyle` i když se nazývá bez tohoto stylu; místo toho jsou tyto posuvníky skryté. To umožňuje posuvníky zachovat jejich stav, i když jsou skryté. Po `SetScrollStyle` volání je nutné volat [RecalcLayout](#recalclayout) pro všechny změny se projeví.

## <a name="csplitterwndsplitcolumn"></a><a name="splitcolumn"></a>CSplitterWnd::SplitColumn

Označuje, kde se okno rámce rozdělí svisle.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Parametry

*cxPřed*<br/>
Pozice v pixelech, před kterou dojde k rozdělení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána při vytvoření okna svislého rozdělovače. `SplitColumn`označuje výchozí umístění, kde dojde k rozdělení.

`SplitColumn`je volána rámci implementovat logiku dynamického okna rozdělovače (to znamená, pokud okno rozdělovač má SPLS_DYNAMIC_SPLIT styl). To může být přizpůsoben, spolu s virtuální funkcí [CreateView](#createview), implementovat pokročilejší dynamické rozdělovače.

## <a name="csplitterwndsplitrow"></a><a name="splitrow"></a>CSplitterWnd::SplitRow

Označuje, kde se okno rámce rozdělí vodorovně.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Parametry

*cyPřed*<br/>
Pozice v pixelech, před kterou dojde k rozdělení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána při vytvoření vodorovného okna rozdělovače. `SplitRow`označuje výchozí umístění, kde dojde k rozdělení.

`SplitRow`je volána rámci implementovat logiku dynamického okna rozdělovače (to znamená, pokud okno rozdělovač má SPLS_DYNAMIC_SPLIT styl). To může být přizpůsoben, spolu s virtuální funkcí [CreateView](#createview), implementovat pokročilejší dynamické rozdělovače.

## <a name="csplitterwndondraw"></a><a name="ondraw"></a>CSplitterWnd::OnDraw

Volat rámci k nakreslení okno rozdělovače.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext zařízení.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CView](../../mfc/reference/cview-class.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)
