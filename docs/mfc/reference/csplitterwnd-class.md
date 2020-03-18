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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421455"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd – třída

Poskytuje funkce okna s rozdělovačem, což je okno, které obsahuje více podoken.

## <a name="syntax"></a>Syntaxe

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSplitterWnd:: CSplitterWnd](#csplitterwnd)|Zavolejte k vytvoření objektu `CSplitterWnd`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSplitterWnd:: ActivateNext](#activatenext)|Provede příkaz další podokno nebo předchozí podokno.|
|[CSplitterWnd:: CanActivateNext](#canactivatenext)|Zkontroluje, jestli je v tuto chvíli možné použít příkaz další podokno nebo předchozí podokno.|
|[CSplitterWnd:: Create](#create)|Zavolejte na vytvořit dynamické okno s rozdělovačem a připojte ho k objektu `CSplitterWnd`.|
|[CSplitterWnd:: CreateScrollBarCtrl](#createscrollbarctrl)|Vytvoří sdílený ovládací prvek posuvníku.|
|[CSplitterWnd:: CreateStatic](#createstatic)|Zavolejte k vytvoření statického rozdělovačového okna a připojte ho k objektu `CSplitterWnd`.|
|[CSplitterWnd:: CreateView](#createview)|Voláním vytvoříte podokno v okně s rozdělovačem.|
|[CSplitterWnd::D eleteColumn](#deletecolumn)|Odstraní sloupec z okna s rozdělovačem.|
|[CSplitterWnd::D eleteRow](#deleterow)|Odstraní řádek z okna s rozdělovačem.|
|[CSplitterWnd::D eleteView](#deleteview)|Odstraní zobrazení z okna s rozdělovačem.|
|[CSplitterWnd::D oKeyboardSplit](#dokeyboardsplit)|Provede příkaz rozdělení klávesnice, obvykle "Window Split".|
|[CSplitterWnd::D oScroll](#doscroll)|Provádí synchronizované posouvání rozdělených oken.|
|[CSplitterWnd::D oScrollBy](#doscrollby)|Posouvá rozdělená okna o daný počet pixelů.|
|[CSplitterWnd:: GetActivePane](#getactivepane)|Určuje aktivní podokno z fokusu nebo aktivního zobrazení v rámci rámce.|
|[CSplitterWnd:: getpočet sloupců](#getcolumncount)|Vrátí počet sloupců aktuálního podokna.|
|[CSplitterWnd:: GetColumnInfo](#getcolumninfo)|Vrátí informace o zadaném sloupci.|
|[CSplitterWnd:: getpodokno](#getpane)|Vrátí podokno na zadaném řádku a sloupci.|
|[CSplitterWnd:: GetRowCount](#getrowcount)|Vrátí počet řádků aktuálního podokna.|
|[CSplitterWnd:: GetRowInfo](#getrowinfo)|Vrátí informace o zadaném řádku.|
|[CSplitterWnd:: GetScrollStyle](#getscrollstyle)|Vrátí sdílený styl posuvníku.|
|[CSplitterWnd:: IdFromRowCol](#idfromrowcol)|Vrátí ID podřízeného okna podokna na zadaném řádku a sloupci.|
|[CSplitterWnd:: IsChildPane](#ischildpane)|Zavolejte k určení, zda je okno aktuálně podřízené podokno tohoto okna s rozdělovačem.|
|[CSplitterWnd:: detracking](#istracking)|Určuje, zda se právě přesouvá Příčkový panel.|
|[CSplitterWnd:: RecalcLayout](#recalclayout)|Po nastavení velikosti řádku nebo sloupce zavolejte k zobrazení okna s rozdělovačem.|
|[CSplitterWnd:: SetActivePane](#setactivepane)|Nastaví podokno jako aktivní v rámci tohoto rámce.|
|[CSplitterWnd:: SetColumnInfo](#setcolumninfo)|Voláním metody nastavte zadané informace o sloupci.|
|[CSplitterWnd:: SetRowInfo](#setrowinfo)|Zavolejte k nastavení informací o zadaných řádcích.|
|[CSplitterWnd:: SetScrollStyle](#setscrollstyle)|Určuje nový styl posuvníku pro sdílenou posuvníkovou podporu pro okno s rozdělovačem.|
|[CSplitterWnd:: SplitColumn](#splitcolumn)|Indikuje, kde se okno rámce rozdělí svisle.|
|[CSplitterWnd:: SplitRow](#splitrow)|Indikuje, kde se okno rámce rozdělí vodorovně.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CSplitterWnd:: Draw](#ondraw)|Volá se rozhraním, aby se nakreslilo okno s rozdělovačem.|
|[CSplitterWnd:: OnDrawSplitter](#ondrawsplitter)|Vykreslí obrázek rozděleného okna.|
|[CSplitterWnd:: OnInvertTracker](#oninverttracker)|Vykreslí obraz rozděleného okna se stejnou velikostí a tvarem jako okno rámce.|

## <a name="remarks"></a>Poznámky

Podokno je obvykle objekt specifický pro aplikaci odvozený od programu [CView](../../mfc/reference/cview-class.md), ale může to být libovolný objekt [CWnd](../../mfc/reference/cwnd-class.md) , který má příslušné ID podřízeného okna.

Objekt `CSplitterWnd` je obvykle vložen do nadřazeného objektu [CFrameWnd](../../mfc/reference/cframewnd-class.md) nebo [CMDIChildWnd –](../../mfc/reference/cmdichildwnd-class.md) . Vytvořte objekt `CSplitterWnd` pomocí následujících kroků:

1. Vložte `CSplitterWnd` členskou proměnnou do nadřazeného rámce.

2. Přepište členskou funkci [CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) nadřazeného rámce.

3. V rámci přepsaného `OnCreateClient`Zavolejte členskou funkci [Create](#create) nebo [CreateStatic](#createstatic) `CSplitterWnd`.

Chcete-li vytvořit dynamické okno s rozdělovačem, zavolejte členskou funkci `Create`. Dynamické okno s rozdělovačem obvykle slouží k vytvoření a posunutí počtu jednotlivých podoken nebo zobrazení stejného dokumentu. Rozhraní automaticky vytvoří počáteční podokno pro rozdělovač; pak rozhraní vytvoří, změní velikost a uvolní další podokna, když uživatel pracuje s ovládacími prvky rozdělovače.

Při volání `Create`zadáte minimální výšku řádku a šířku sloupce, které určují, kdy jsou podokna příliš malá, aby bylo možné je plně zobrazit. Po volání `Create`můžete tyto minima upravit voláním členských funkcí [SetColumnInfo](#setcolumninfo) a [SetRowInfo](#setrowinfo) .

K nastavení "ideální" šířky sloupce a "ideální" výšky řádku můžete také použít členské funkce `SetColumnInfo` a `SetRowInfo`. Když rozhraní zobrazí okno s rozdělovačem, nejprve zobrazí nadřazený rámec a pak okno s rozdělovačem. Rozhraní potom rozloží podokna ve sloupcích a řádcích podle jejich ideálních rozměrů, které pracují vlevo v pravém dolním rohu klientské oblasti.

Všechna podokna v dynamickém rozdělovacím okně musí být stejné třídy. Mezi známé aplikace podporující dynamické rozdělovače Windows patří Microsoft Word a Microsoft Excel.

Pomocí členské funkce `CreateStatic` vytvořte statické okno s rozdělovačem. Uživatel může změnit pouze velikost podoken ve statickém rozdělovacím okně, nikoli jejich číslo nebo pořadí.

Při vytváření statického rozdělovače musíte specificky vytvořit všechna podokna statického rozdělovače. Ujistěte se, že jste vytvořili všechna podokna předtím, než se vrátí členská funkce `OnCreateClient` nadřazeného rámce, nebo v rozhraní se okno nezobrazí správně.

Členská funkce `CreateStatic` automaticky inicializuje statický rozdělovač s minimální výškou řádku a šířkou sloupce 0. Po volání `Create`upravte tyto minimum voláním členských funkcí [SetColumnInfo](#setcolumninfo) a [SetRowInfo](#setrowinfo) . Také `SetColumnInfo` a `SetRowInfo` použít po volání `CreateStatic` k označení požadovaných ideálních dimenzí podokna.

Jednotlivá podokna statického rozdělovače často patří do různých tříd. Příklady statických rozdělovačových oken naleznete v editoru grafiky a ve Správci souborů systému Windows.

Okno rozdělovače podporuje speciální posuvníky (vedle posuvníků, které mohou mít podokna). Tyto posuvníky jsou podřízené objekty objektu `CSplitterWnd` a jsou sdíleny s podokny.

Tyto speciální posuvníky vytvoříte při vytváření okna s rozdělovačem. Například `CSplitterWnd`, který má jeden řádek, dva sloupce a styl WS_VSCROLL zobrazí svislý posuvník, který je sdílen dvěma podokny. Když uživatel přesune posuvník, WM_VSCROLL zprávy budou odesílány do obou podoken. Když se v podoknech nastaví pozice posuvníku, je nastaven sdílený posuvník.

Další informace o rozdělovacích oknech najdete v části [technická Poznámka 29](../../mfc/tn029-splitter-windows.md).

Další informace o tom, jak vytvořit dynamické rozdělovače, najdete v tématech:

- Ukázka prostředí MFC – [Klikyháky](../../overview/visual-cpp-samples.md)

- [VIEWEX](../../overview/visual-cpp-samples.md)Sample MFC.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext. h

##  <a name="activatenext"></a>CSplitterWnd:: ActivateNext

Volá se rozhraním, aby se provedl příkaz další podokno nebo předchozí podokno.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parametry

*bPrev*<br/>
Určuje, které okno se má aktivovat. **True** pro předchozí; **Hodnota false** pro další.

### <a name="remarks"></a>Poznámky

Tato členská funkce je příkaz vysoké úrovně, který je používán třídou [CView](../../mfc/reference/cview-class.md) k delegování na `CSplitterWnd` implementaci.

##  <a name="canactivatenext"></a>CSplitterWnd:: CanActivateNext

Volá se rozhraním, aby se zkontrolovalo, jestli je v současné době možné použít další podokno nebo předchozí podokno.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parametry

*bPrev*<br/>
Určuje, které okno se má aktivovat. **True** pro předchozí; **Hodnota false** pro další.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je příkaz vysoké úrovně, který je používán třídou [CView](../../mfc/reference/cview-class.md) k delegování na `CSplitterWnd` implementaci.

##  <a name="create"></a>CSplitterWnd:: Create

Chcete-li vytvořit dynamické okno s rozdělovačem, zavolejte členskou funkci `Create`.

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
Nadřazené okno rámce okna s rozdělovačem

*nMaxRows*<br/>
Maximální počet řádků v okně s oddělovači. Tato hodnota nesmí překročit 2.

*nMaxCols*<br/>
Maximální počet sloupců v okně s oddělovači. Tato hodnota nesmí překročit 2.

*sizeMin*<br/>
Určuje minimální velikost, při které se může zobrazit podokno.

*pContext*<br/>
Ukazatel na strukturu [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Ve většině případů to může být *pContext* předaný do okna nadřazeného rámce.

*dwStyle*<br/>
Určuje styl okna.

*nID*<br/>
ID podřízeného okna okna ID může být AFX_IDW_PANE_FIRST, pokud rozdělovací okno není vnořené uvnitř jiného okna s rozdělovačem.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`CSplitterWnd` můžete vložit do nadřazeného objektu [CFrameWnd](../../mfc/reference/cframewnd-class.md) nebo [CMDIChildWnd –](../../mfc/reference/cmdichildwnd-class.md) , a to provedením následujících kroků:

1. Vložte `CSplitterWnd` členskou proměnnou do nadřazeného rámce.

1. Přepište členskou funkci [CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) nadřazeného rámce.

1. Volání členské funkce `Create` v rámci přepsané `OnCreateClient`.

Při vytváření rozdělovače v rámci nadřazeného rámce předejte parametr *pContext* nadřazeného rámce do okna s rozdělovačem. V opačném případě může mít tento parametr hodnotu NULL.

Počáteční minimální výška řádku a šířka sloupce dynamického rozdělovače se nastaví pomocí parametru *sizeMin* . Tyto minimální možnosti, které určují, zda je podokno příliš malé, aby se zobrazilo v celém rozsahu, lze změnit pomocí členských funkcí [SetRowInfo](#setrowinfo) a [SetColumnInfo](#setcolumninfo) .

Další informace o dynamických rozdělovacích oknech naleznete v části "příčky Windows" v článku [více typů dokumentů, zobrazení a oken s rámečkem](../../mfc/multiple-document-types-views-and-frame-windows.md), [technická Poznámka 29](../../mfc/tn029-splitter-windows.md)a přehled `CSplitterWnd` třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

##  <a name="createscrollbarctrl"></a>CSplitterWnd:: CreateScrollBarCtrl

Volá se rozhraním, aby se vytvořil sdílený ovládací prvek posuvníku.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl okna.

*nID*<br/>
ID podřízeného okna okna ID může být AFX_IDW_PANE_FIRST, pokud rozdělovací okno není vnořené uvnitř jiného okna s rozdělovačem.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Přepište `CreateScrollBarCtrl` pro zahrnutí dalších ovládacích prvků vedle posuvníku. Výchozím chováním je vytváření normálních ovládacích prvků posuvníku Windows.

##  <a name="createstatic"></a>CSplitterWnd:: CreateStatic

Chcete-li vytvořit statické okno s rozdělovačem, zavolejte členskou funkci `CreateStatic`.

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
Nadřazené okno rámce okna s rozdělovačem

*Hodnota nRows*<br/>
Počet řádků Tato hodnota nesmí přesáhnout 16.

*nCols*<br/>
Počet sloupců Tato hodnota nesmí přesáhnout 16.

*dwStyle*<br/>
Určuje styl okna.

*nID*<br/>
ID podřízeného okna okna ID může být AFX_IDW_PANE_FIRST, pokud rozdělovací okno není vnořené uvnitř jiného okna s rozdělovačem.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`CSplitterWnd` se obvykle vloží do nadřazeného objektu `CFrameWnd` nebo [CMDIChildWnd –](../../mfc/reference/cmdichildwnd-class.md) , a to provedením následujících kroků:

1. Vložte `CSplitterWnd` členskou proměnnou do nadřazeného rámce.

1. Přepište členskou funkci `OnCreateClient` nadřazeného rámce.

1. Volání členské funkce `CreateStatic` v rámci přepsaného [CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).

Statické okno s rozdělovačem obsahuje pevný počet podoken, často z různých tříd.

Při vytváření statického rozdělovačového okna musíte současně vytvořit všechna jeho podokna. Členská funkce [CreateView](#createview) se obvykle používá k tomuto účelu, ale můžete také vytvořit jiné nezobrazeníelné třídy.

Počáteční minimální výška řádku a šířka sloupce pro statické dělicí okno je 0. Tyto minimum, které určují, kdy je podokno příliš malé, aby se zobrazilo v celém rozsahu, lze změnit pomocí členských funkcí [SetRowInfo](#setrowinfo) a [SetColumnInfo](#setcolumninfo) .

Chcete-li přidat posuvníky do statického rozdělovačového okna, přidejte WS_HSCROLL a styly WS_VSCROLL do *dwStyle*.

Další informace o statických oknech s rozdělovačem naleznete v části "příčky Windows" v článku [více typů dokumentů, zobrazení a oken s rámečkem](../../mfc/multiple-document-types-views-and-frame-windows.md), [technická Poznámka 29](../../mfc/tn029-splitter-windows.md)a přehled `CSplitterWnd` třídy.

##  <a name="createview"></a>CSplitterWnd:: CreateView

Vytvoří podokna pro statické okno s rozdělovačem.

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parametry

*řadě*<br/>
Určuje řádek okna s rozdělovačem, do kterého se má nové zobrazení umístit.

*vyloučit*<br/>
Určuje sloupec rozdělovače, do kterého se má nové zobrazení umístit.

*pViewClass*<br/>
Určuje [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) nového zobrazení.

*sizeInit*<br/>
Určuje počáteční velikost nového zobrazení.

*pContext*<br/>
Ukazatel na kontext vytvoření použitý k vytvoření zobrazení (obvykle *pContext* předaný do přepsané členské funkce [CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) , ve které se vytváří rozdělovač).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Před zobrazením příčky je nutné vytvořit všechna podokna statického rozdělovačového okna.

Rozhraní také volá tuto členskou funkci pro vytváření nových podoken, když uživatel dynamického rozdělovače rozdělí podokno, řádek nebo sloupec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

##  <a name="csplitterwnd"></a>CSplitterWnd:: CSplitterWnd

Zavolejte k vytvoření objektu `CSplitterWnd`.

```
CSplitterWnd();
```

### <a name="remarks"></a>Poznámky

Vytvořte objekt `CSplitterWnd` ve dvou krocích. Nejprve volejte konstruktor, který vytvoří objekt `CSplitterWnd` a poté zavolejte funkci [Create](#create) member, která vytvoří rozdělovač a připojí ho k objektu `CSplitterWnd`.

##  <a name="deletecolumn"></a>CSplitterWnd::D eleteColumn

Odstraní sloupec z okna s rozdělovačem.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Parametry

*colDelete*<br/>
Určuje sloupec, který se má odstranit.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním pro implementaci logiky dynamického rozdělovačového okna (to znamená, pokud má okno oddělovače SPLS_DYNAMIC_SPLIT styl). Dá se přizpůsobit společně s virtuální funkcí [CreateView](#createview)k implementaci pokročilejších dynamických rozdělovačů.

##  <a name="deleterow"></a>CSplitterWnd::D eleteRow

Odstraní řádek z okna s rozdělovačem.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Parametry

*rowDelete*<br/>
Určuje řádek, který se má odstranit.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním pro implementaci logiky dynamického rozdělovačového okna (to znamená, pokud má okno oddělovače SPLS_DYNAMIC_SPLIT styl). Dá se přizpůsobit společně s virtuální funkcí [CreateView](#createview)k implementaci pokročilejších dynamických rozdělovačů.

##  <a name="deleteview"></a>CSplitterWnd::D eleteView

Odstraní zobrazení z okna s rozdělovačem.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>Parametry

*řadě*<br/>
Určuje řádek okna s oddělovači, na kterém se má zobrazení odstranit.

*vyloučit*<br/>
Určuje sloupec rozdělovacího okna, pro které se má zobrazení odstranit.

### <a name="remarks"></a>Poznámky

Pokud se aktivní zobrazení odstraňuje, stane se další zobrazení aktivní. Výchozí implementace předpokládá, že zobrazení se automaticky odstraní v [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).

Tato členská funkce je volána rozhraním pro implementaci logiky dynamického rozdělovačového okna (to znamená, pokud má okno oddělovače SPLS_DYNAMIC_SPLIT styl). Dá se přizpůsobit společně s virtuální funkcí [CreateView](#createview)k implementaci pokročilejších dynamických rozdělovačů.

##  <a name="dokeyboardsplit"></a>CSplitterWnd::D oKeyboardSplit

Provede příkaz rozdělení klávesnice, obvykle "Window Split".

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je příkaz vysoké úrovně, který je používán třídou [CView](../../mfc/reference/cview-class.md) k delegování na `CSplitterWnd` implementaci.

##  <a name="doscroll"></a>CSplitterWnd::D oScroll

Provádí synchronizované posouvání rozdělených oken.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewFrom*<br/>
Ukazatel na zobrazení, ze kterého zpráva o posunu vznikla.

*nScrollCode*<br/>
Kód posuvníku, který označuje požadavek na posunutí uživatele. Tento parametr se skládá ze dvou částí: bajt nízkého řádu, který určuje typ posouvání, ke kterému dochází vodorovně, a horní bajt, který určuje typ posouvání, ke kterému dochází vertikálně:

    - SB_BOTTOM posouvá se dolů.

    - SB_LINEDOWN posouvá jeden řádek dolů.

    - SB_LINEUP posouvá o jeden řádek nahoru.

    - SB_PAGEDOWN posouvá jednu stránku dolů.

    - SB_PAGEUP posouvá o jednu stránku nahoru.

    - SB_TOP posouvá na začátek.

*bDoScroll*<br/>
Určuje, zda dojde k zadané akci posunutí. Pokud má *bDoScroll* hodnotu true (to znamená, pokud existuje podřízené okno, a pokud má rozdělená okna rozsah posunu), může dojít k zadané akci posouvání. Pokud má *bDoScroll* hodnotu false (tj. Pokud žádné podřízené okno neexistuje nebo pokud rozdělená zobrazení nemají žádný rozsah posunu), není k dispozici posouvání.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dojde k synchronizovanému posouvání; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním, aby prováděla synchronizované posouvání rozdělených oken, když zobrazení obdrží zprávu s posuvníkem. Před tím, než je povoleno synchronizované posouvání, je nutné přepsat tak, aby uživatel vyžadoval akci.

##  <a name="doscrollby"></a>CSplitterWnd::D oScrollBy

Posouvá rozdělená okna o daný počet pixelů.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewFrom*<br/>
Ukazatel na zobrazení, ze kterého zpráva o posunu vznikla.

*sizeScroll*<br/>
Počet pixelů, které mají být posunuty vodorovně a svisle.

*bDoScroll*<br/>
Určuje, zda dojde k zadané akci posunutí. Pokud má *bDoScroll* hodnotu true (to znamená, pokud existuje podřízené okno, a pokud má rozdělená okna rozsah posunu), může dojít k zadané akci posouvání. Pokud má *bDoScroll* hodnotu false (tj. Pokud žádné podřízené okno neexistuje nebo pokud rozdělená zobrazení nemají žádný rozsah posunu), není k dispozici posouvání.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dojde k synchronizovanému posouvání; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním v reakci na posouvaných zpráv, aby bylo možné provést synchronizované posouvání rozdělených oken podle množství v pixelech, které jsou označeny *sizeScroll*. Kladné hodnoty označují posun dolů a doprava; záporné hodnoty označují posun nahoru a doleva.

Před povolením posouvání popište, aby uživatel vyžadoval akci.

##  <a name="getactivepane"></a>CSplitterWnd:: GetActivePane

Určuje aktivní podokno z fokusu nebo aktivního zobrazení v rámci rámce.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Parametry

*pRow*<br/>
Ukazatel na **int** , který načte číslo řádku aktivního podokna.

*pCol*<br/>
Ukazatel na **int** , který načte číslo sloupce aktivního podokna.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktivní podokno. Hodnota NULL, pokud neexistuje žádné aktivní podokno.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním pro určení aktivního podokna v okně s rozdělovačem. Před tím, než se zobrazí aktivní podokno, přepište, aby uživatel vyžadoval akci.

##  <a name="getcolumncount"></a>CSplitterWnd:: getpočet sloupců

Vrátí počet sloupců aktuálního podokna.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální počet sloupců v rozdělovači. U statického rozdělovače bude to také maximální počet sloupců.

##  <a name="getcolumninfo"></a>CSplitterWnd:: GetColumnInfo

Vrátí informace o zadaném sloupci.

```
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>Parametry

*vyloučit*<br/>
Určuje sloupec.

*cxCur*<br/>
Odkaz na typ **int** , který má být nastaven na aktuální šířku sloupce.

*cxMin*<br/>
Odkaz na typ **int** , který má být nastaven na aktuální minimální šířku sloupce.

##  <a name="getpane"></a>CSplitterWnd:: getpodokno

Vrátí podokno na zadaném řádku a sloupci.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parametry

*řadě*<br/>
Určuje řádek.

*vyloučit*<br/>
Určuje sloupec.

### <a name="return-value"></a>Návratová hodnota

Vrátí podokno na zadaném řádku a sloupci. Vrácené podokno je obvykle třída odvozená od typu [CView](../../mfc/reference/cview-class.md).

##  <a name="getrowcount"></a>CSplitterWnd:: GetRowCount

Vrátí počet řádků aktuálního podokna.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální počet řádků v okně s oddělovači. Pro statické okno s rozdělovačem bude to také maximální počet řádků.

##  <a name="getrowinfo"></a>CSplitterWnd:: GetRowInfo

Vrátí informace o zadaném řádku.

```
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>Parametry

*řadě*<br/>
Určuje řádek.

*cyCur*<br/>
Odkaz na **int** , který se nastaví na aktuální výšku řádku v pixelech

*cyMin*<br/>
Odkaz na **int** , který se nastaví na aktuální minimální výšku řádku v pixelech

### <a name="remarks"></a>Poznámky

Chcete-li získat informace o zadaném řádku, zavolejte tuto členskou funkci. Parametr *cyCur* je vyplněn aktuální výškou zadaného řádku a *cyMin* je vyplněn minimální výškou řádku.

##  <a name="getscrollstyle"></a>CSplitterWnd:: GetScrollStyle

Vrátí sdílený styl posuvníku pro okno s rozdělovačem.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Jeden nebo více následujících příznaků stylu Windows, pokud jsou úspěšné:

    - WS_HSCROLL, zda rozdělovač aktuálně spravuje sdílené vodorovné posuvníky.

    - WS_VSCROLL, zda rozdělovač aktuálně spravuje sdílené svislé posuvníky.

Pokud je nula, okno s rozdělovačem aktuálně nespravuje žádné sdílené posuvníky.

##  <a name="idfromrowcol"></a>CSplitterWnd:: IdFromRowCol

Získá ID podřízeného okna pro podokno na zadaném řádku a sloupci.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parametry

*řadě*<br/>
Určuje řádek okna s rozdělovačem.

*vyloučit*<br/>
Určuje sloupec rozdělovacího okna.

### <a name="return-value"></a>Návratová hodnota

ID podřízeného okna pro podokno

### <a name="remarks"></a>Poznámky

Tato členská funkce se používá pro vytváření nezobrazení jako podoken a může být volána před tím, než podokno existuje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

##  <a name="ischildpane"></a>CSplitterWnd:: IsChildPane

Určuje, zda je *pWnd* aktuálně podřízeným podoknem tohoto okna s rozdělovačem.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který má být testován.

*pRow*<br/>
Ukazatel na **int** , v němž má být uloženo číslo řádku.

*pCol*<br/>
Ukazatel na **int** , do kterého se uloží číslo sloupce.

### <a name="return-value"></a>Návratová hodnota

Pokud je nenulová, *pWnd* je aktuálně podřízené podokno tohoto okna s rozdělovačem a *pRow* a *pCol* jsou vyplněny umístěním podokna v okně s rozdělovačem. Pokud *pWnd* není podřízené podokno tohoto okna s rozdělovačem, vrátí se 0.

### <a name="remarks"></a>Poznámky

V jazyce C++ Visual ve verzích starších než 6,0 byla tato funkce definována jako

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Tato verze je teď zastaralá a neměla by se používat.

##  <a name="istracking"></a>CSplitterWnd:: detracking

Voláním této členské funkce určíte, zda je dělicí příčka v okně právě přesunuta.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud probíhá operace rozdělovače; v opačném případě 0.

##  <a name="ondrawsplitter"></a>CSplitterWnd:: OnDrawSplitter

Vykreslí obrázek rozděleného okna.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Ukazatel na kontext zařízení, ve kterém se má kreslit. Pokud má *primární řadič domény* hodnotu null, pak se rozhraní [CWnd:: RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) volá rozhraním a nevykresluje se žádné rozdělené okno.

*Noznámení*<br/>
Hodnota `enum ESplitType`, což může být jedna z následujících:

    - `splitBox` příčky přetáhněte pole.

    - `splitBar` pruh, který se zobrazí mezi dvěma rozdělenými okny.

    - `splitIntersection` průsečík rozdělených oken. Tento prvek nebude volán při spuštění v systému Windows 95/98.

    - `splitBorder` ohraničení rozděleného okna.

*OBD*<br/>
Odkaz na objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) určující velikost a tvar rozdělených oken.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním, aby vykreslila a určovala přesné charakteristiky okna s rozdělovačem. Přepište `OnDrawSplitter` pro pokročilé přizpůsobení různých grafických prvků okna s rozdělovačem. Výchozí obrázek je podobný rozdělovači v Microsoft Works pro Windows nebo Microsoft Windows 95/98, v tom, že průniky příčky jsou společně kombinovány.

Další informace o dynamických rozdělovacích oknech naleznete v části "příčky Windows" v článku [více typů dokumentů, zobrazení a oken s rámečkem](../../mfc/multiple-document-types-views-and-frame-windows.md), [technická Poznámka 29](../../mfc/tn029-splitter-windows.md)a přehled `CSplitterWnd` třídy.

##  <a name="oninverttracker"></a>CSplitterWnd:: OnInvertTracker

Vykreslí obraz rozděleného okna se stejnou velikostí a tvarem jako okno rámce.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
Odkaz na objekt `CRect` určující obdélník sledování.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním během změny velikosti rozdělovačů. Přepsat `OnInvertTracker` pro pokročilou úpravu obrázků okna s rozdělovačem Výchozí obrázek je podobný rozdělovači v Microsoft Works pro Windows nebo Microsoft Windows 95/98, v tom, že průniky příčky jsou společně kombinovány.

Další informace o dynamických rozdělovacích oknech naleznete v části "příčky Windows" v článku [více typů dokumentů, zobrazení a oken s rámečkem](../../mfc/multiple-document-types-views-and-frame-windows.md), [technická Poznámka 29](../../mfc/tn029-splitter-windows.md)a přehled `CSplitterWnd` třídy.

##  <a name="recalclayout"></a>CSplitterWnd:: RecalcLayout

Po nastavení velikosti řádku nebo sloupce zavolejte k zobrazení okna s rozdělovačem.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Poznámky

Zavolejte tuto členskou funkci pro správné opětovné zobrazení rozdělovače poté, co jste upravili velikosti řádků a sloupců pomocí členských funkcí [SetRowInfo](#setrowinfo) a [SetColumnInfo](#setcolumninfo) . Pokud změníte velikosti řádků a sloupců v rámci procesu vytváření před zobrazením okna s rozdělovačem, není nutné volat tuto členskou funkci.

Rozhraní volá tuto členskou funkci pokaždé, když uživatel změní velikost okna rozdělovače nebo přesune rozdělení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CSplitterWnd:: SetColumnInfo](#setcolumninfo).

##  <a name="setactivepane"></a>CSplitterWnd:: SetActivePane

Nastaví podokno jako aktivní v rámci tohoto rámce.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Parametry

*řadě*<br/>
Pokud má *pWnd* hodnotu null, Určuje řádek v podokně, které bude aktivní.

*vyloučit*<br/>
Pokud má *pWnd* hodnotu null, určuje sloupec v podokně, které bude aktivní.

*pWnd*<br/>
Ukazatel na objekt `CWnd`. Pokud má hodnotu NULL, je podokno určené jako *řádek* a *sloupec* nastavené na aktivní. Pokud hodnota není NULL, určuje podokno, které je nastavené jako aktivní.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním, aby bylo možné nastavit podokno jako aktivní, když uživatel změní fokus na podokno v rámci okna rámce. Můžete explicitně volat `SetActivePane` pro změnu fokusu na zadané zobrazení.

Určete podokno zadáním řádku a sloupce **nebo** zadáním *pWnd*.

##  <a name="setcolumninfo"></a>CSplitterWnd:: SetColumnInfo

Voláním metody nastavte zadané informace o sloupci.

```
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>Parametry

*vyloučit*<br/>
Určuje sloupec rozdělovacího okna.

*cxIdeal*<br/>
Určuje ideální šířku sloupce rozdělovacího okna v pixelech.

*cxMin*<br/>
Určuje minimální šířku sloupce rozdělovacího okna v pixelech.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce nastavte novou minimální šířku a ideální šířku sloupce. Minimální hodnota sloupce určuje, kdy bude sloupec příliš malý, aby se plně zobrazil.

Když rozhraní zobrazí rozdělovač, rozloží podokna ve sloupcích a řádcích podle jejich ideálních rozměrů, a to v pravém horním rohu klientské oblasti okna s rozdělovačem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

##  <a name="setrowinfo"></a>CSplitterWnd:: SetRowInfo

Zavolejte k nastavení informací o zadaných řádcích.

```
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>Parametry

*řadě*<br/>
Určuje řádek okna s rozdělovačem.

*cyIdeal*<br/>
Určuje ideální výšku řádku okna s oddělovači v pixelech.

*cyMin*<br/>
Určuje minimální výšku řádku okna s oddělovači v pixelech.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce můžete nastavit novou minimální výšku a ideální výšku řádku. Minimální hodnota řádku určuje, kdy bude řádek příliš malý, aby se plně zobrazil.

Když rozhraní zobrazí rozdělovač, rozloží podokna ve sloupcích a řádcích podle jejich ideálních rozměrů, a to v pravém horním rohu klientské oblasti okna s rozdělovačem.

##  <a name="setscrollstyle"></a>CSplitterWnd:: SetScrollStyle

Určuje nový styl posouvání pro sdílenou posuvníkovou podporu pro okno s rozdělovačem.

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Nový styl posouvání pro sdílenou posuvnou příčku okna, což může být jedna z následujících hodnot:

- WS_HSCROLL vytvořit nebo zobrazit vodorovně sdílené posuvníky.

- Umožňuje WS_VSCROLL vytvořit nebo zobrazit svislé posuvníky.

### <a name="remarks"></a>Poznámky

Po vytvoření posuvníku nebude zničen, i když je zavolána `SetScrollStyle` bez tohoto stylu; místo toho se tyto posuvníky skryjí. To umožňuje posuvníkům zachovat svůj stav, i když jsou skryté. Po volání `SetScrollStyle` je nutné volat [RecalcLayout](#recalclayout) , aby se změny projevily.

##  <a name="splitcolumn"></a>CSplitterWnd:: SplitColumn

Indikuje, kde se okno rámce rozdělí svisle.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Parametry

*cxBefore*<br/>
Pozice (v pixelech), před kterou dojde k rozdělení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce se volá, když se vytvoří svislé okno s rozdělovačem. `SplitColumn` označuje výchozí umístění, kde dojde k rozdělení.

`SplitColumn` je volána rozhraním pro implementaci logiky dynamického rozdělovačového okna (to znamená, pokud příčka má SPLS_DYNAMIC_SPLIT styl). Dá se přizpůsobit společně s virtuální funkcí [CreateView](#createview)k implementaci pokročilejších dynamických rozdělovačů.

##  <a name="splitrow"></a>CSplitterWnd:: SplitRow

Indikuje, kde se okno rámce rozdělí vodorovně.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Parametry

*cyBefore*<br/>
Pozice (v pixelech), před kterou dojde k rozdělení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce se volá při vytvoření vodorovného rozdělovačového okna. `SplitRow` označuje výchozí umístění, kde dojde k rozdělení.

`SplitRow` je volána rozhraním pro implementaci logiky dynamického rozdělovačového okna (to znamená, pokud příčka má SPLS_DYNAMIC_SPLIT styl). Dá se přizpůsobit společně s virtuální funkcí [CreateView](#createview)k implementaci pokročilejších dynamických rozdělovačů.

##  <a name="ondraw"></a>CSplitterWnd:: Draw

Volá se rozhraním, aby se nakreslilo okno s rozdělovačem.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Ukazatel na kontext zařízení.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[VIEWEX Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)
