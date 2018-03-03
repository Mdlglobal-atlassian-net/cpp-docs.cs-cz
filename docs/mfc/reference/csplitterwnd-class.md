---
title: "Třída CSplitterWnd | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 706425dd8d729937d310da9cc2f09eac8ec1ad57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="csplitterwnd-class"></a>CSplitterWnd – třída
Poskytuje funkci rozděleném okně, které je okno, které obsahuje více podokna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSplitterWnd : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Volání k vytvoření `CSplitterWnd` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSplitterWnd::ActivateNext](#activatenext)|Provedení příkazu podokně Další nebo předchozí.|  
|[CSplitterWnd::CanActivateNext](#canactivatenext)|Kontroluje, zda příkaz Další podokno nebo předchozí podokno je nyní možné.|  
|[CSplitterWnd::Create](#create)|Volání vytvoření okna dynamické rozdělovače a připojte ji k `CSplitterWnd` objektu.|  
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|Vytvoří ovládací prvek sdílené posuvníku.|  
|[CSplitterWnd::CreateStatic](#createstatic)|Volání vytvoření statické rozdělovače okna a jeho k připojení `CSplitterWnd` objektu.|  
|[CSplitterWnd::CreateView](#createview)|Volání za účelem vytvoření podokno v rozděleném okně.|  
|[CSplitterWnd::DeleteColumn](#deletecolumn)|Z okna rozdělovače odstraní sloupec.|  
|[CSplitterWnd::DeleteRow](#deleterow)|Odstranění řádku z okna rozdělovače.|  
|[CSplitterWnd::DeleteView](#deleteview)|Odstraní z okna rozdělovače zobrazení.|  
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|Provede klávesnice split příkazu, obvykle "rozdělení na okna".|  
|[CSplitterWnd::DoScroll](#doscroll)|Provede synchronizované posouvání rozdělení windows.|  
|[CSplitterWnd::DoScrollBy](#doscrollby)|Posouvá rozdělit windows zadaný počet pixelů.|  
|[CSplitterWnd::GetActivePane](#getactivepane)|Určuje podokně active z fokus nebo aktivní zobrazení v rámečku.|  
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Vrátí aktuální počet sloupců podokně.|  
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Vrátí informace na zadaný sloupec.|  
|[CSplitterWnd::GetPane](#getpane)|Vrátí panelu v zadané řádků a sloupců.|  
|[CSplitterWnd::GetRowCount](#getrowcount)|Vrátí aktuální počet řádků podokně.|  
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Vrátí informace na zadaný řádek.|  
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Vrátí styl sdílené posuvníku.|  
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Vrací podřízeného okna ID panelu v zadané řádků a sloupců.|  
|[CSplitterWnd::IsChildPane](#ischildpane)|Chcete-li určit, zda okno je aktuálně podřízený podokně tohoto okna rozdělovače volání.|  
|[CSplitterWnd::IsTracking](#istracking)|Určuje, pokud rozdělovač právě přesouvá.|  
|[CSplitterWnd::RecalcLayout](#recalclayout)|Volání k opětovnému zobrazení okna rozdělovače po nastavení velikosti sloupce či řádku.|  
|[CSplitterWnd::SetActivePane](#setactivepane)|Nastaví podokně být aktivní v rámečku.|  
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|Volání nastavení informací o zadaný sloupec.|  
|[CSplitterWnd::SetRowInfo](#setrowinfo)|Volání se nastavit informace o zadané řádek.|  
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Určuje, že nový styl posuvníku pro okno rozdělovače posuvníku podpora sdílených.|  
|[CSplitterWnd::SplitColumn](#splitcolumn)|Určuje, kde okně s rámečkem rozdělí svisle.|  
|[CSplitterWnd::SplitRow](#splitrow)|Určuje, kde okně s rámečkem rozdělí vodorovně.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSplitterWnd::OnDraw](#ondraw)|Voláno rámcem k vykreslení rozdělovače oken.|  
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Vykreslí obrázek rozděleném okně.|  
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Vykreslí bitové kopie rozděleném okně stejnou velikost a tvar jako rámce okna.|  
  
## <a name="remarks"></a>Poznámky  
 Podokno je obvykle objekt specifické pro aplikace získané z [CView](../../mfc/reference/cview-class.md), ale může být libovolná [CWnd](../../mfc/reference/cwnd-class.md) objekt, který má odpovídající podřízené okno ID.  
  
 A `CSplitterWnd` objekt obvykle vložený v nadřazeném prvku [CFrameWnd](../../mfc/reference/cframewnd-class.md) nebo [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objektu. Vytvoření `CSplitterWnd` objektu pomocí následujících kroků:  
  
1.  Vložení `CSplitterWnd` členské proměnné v rámci nadřazené.  
  
2.  Přepsání nadřazeného rámce [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) – členská funkce.  
  
3.  Z v rámci přepsané `OnCreateClient`, volání [vytvořit](#create) nebo [CreateStatic](#createstatic) členské funkce `CSplitterWnd`.  
  
 Volání **vytvořit** – členská funkce vytvořit dynamické rozdělovače okno. Dynamické rozdělovače oken se obvykle používá k vytvoření a posuňte se počet jednotlivých podokna nebo zobrazení, stejného dokumentu. Rozhraní framework automaticky vytvoří počáteční podokně aplikace pro rozdělovače; rozhraní framework pak vytvoří, změní a uvolní další podokna jako uživatel okno rozdělovač – ovládací prvky.  
  
 Při volání **vytvořit**, můžete zadat minimální řádek výšky a ve sloupci šířku určující, kdy jsou příliš malá, který se má zobrazit plně podokna. Po zavolání metody **vytvořit**, můžete upravit tyto minimálních voláním [SetColumnInfo](#setcolumninfo) a [SetRowInfo](#setrowinfo) členské funkce.  
  
 Také použít `SetColumnInfo` a `SetRowInfo` členské funkce nastavit pro sloupec "ideální" šířku a výšku "ideální" pro řádek. Pokud rozhraní zobrazí okno rozdělovače, nejprve zobrazí nadřazené rámečku, pak rozdělovače oken. Rozhraní framework pak rozložen podokna ve sloupci a řádky podle jejich ideální dimenze práce z levého horního do pravém dolním rohu okna rozdělovače klientské oblasti.  
  
 Všechny podokna v okně dynamické rozdělovače musí být stejné. Známé aplikace, které podporují dynamické rozdělovače oken zahrnují Microsoft Word a Excel.  
  
 Použití `CreateStatic` – členská funkce vytvoření statické rozdělovače okna. Uživatel může změnit pouze velikost podokna v statické rozdělovače oken, není jejich číslo nebo pořadí.  
  
 Konkrétně je nutné vytvořit všechny statické rozdělovače na podokna při vytváření statické rozdělovače. Zajistěte, aby vytvoříte všechny podokna před nadřazeného rámce `OnCreateClient` členské funkce vrátí, nebo bude framework není správně zobrazení okna.  
  
 `CreateStatic` – Členská funkce automaticky inicializuje statické rozdělovače s minimální řádku výšky a ve sloupci šířku 0. Po zavolání metody **vytvořit**, upravte tyto minimálních voláním [SetColumnInfo](#setcolumninfo) a [SetRowInfo](#setrowinfo) členské funkce. Použít také `SetColumnInfo` a `SetRowInfo` po zavolání metody `CreateStatic` znamenat požadovaných ideální podokně dimenzí.  
  
 Jednotlivé podoken programu statické rozdělovače často patří do různých tříd. Příklady statické rozdělovače oken najdete v editoru grafiky a Správce souborů systému Windows.  
  
 Rozdělovače oken podporuje speciální posuvníky (kromě posuvníky, které mohou mít podokna). Tyto posuvníky jsou podřízené objekty `CSplitterWnd` objektu a jsou sdíleny s podokna.  
  
 Při vytváření okna rozdělovače vytvoříte tyto speciální posuvníky. Například `CSplitterWnd` který má jeden řádek, dva sloupce a **ws_vscroll –** styl zobrazí svislý posuvník, který sdílí dvě podokna. Když se uživatel přesune posuvníku, `WM_VSCROLL` jsou zprávy odesílány do obou podokna. Když podokna nastavení posuvníku pozice, se nastaví sdílené posuvníku.  
  
 Další informace o rozdělovače oken viz:  
  
- [Technická poznámka 29](../../mfc/tn029-splitter-windows.md)  
  
-   Článek znalostní báze Knowledge Base Q262024: postupy: použití cpropertysheet – jako podřízené CSplitterWnd  
  
 Další informace o tom, jak vytvořit dynamické rozdělovače oken najdete v tématu:  
  
-   Ukázka MFC [Klikyháky](../../visual-cpp-samples.md)  
  
-   Ukázka MFC [VIEWEX](../../visual-cpp-samples.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSplitterWnd`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="activatenext"></a>CSplitterWnd::ActivateNext  
 Voláno rámcem provést další podokně nebo předchozí příkaz.  
  
```  
virtual void ActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bPrev`  
 Určuje, které okno aktivovat. **Hodnota TRUE,** pro předchozí; **FALSE** pro další.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen je nejvyšší úrovni příkaz, který je používán [CView](../../mfc/reference/cview-class.md) třída delegovat `CSplitterWnd` implementace.  
  
##  <a name="canactivatenext"></a>CSplitterWnd::CanActivateNext  
 Voláno rámcem k zkontrolujte, zda příkaz Další podokno nebo předchozí podokno je nyní možné.  
  
```  
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bPrev`  
 Určuje, které okno aktivovat. **Hodnota TRUE,** pro předchozí; **FALSE** pro další.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen je nejvyšší úrovni příkaz, který je používán [CView](../../mfc/reference/cview-class.md) třída delegovat `CSplitterWnd` implementace.  
  
##  <a name="create"></a>CSplitterWnd::Create  
 Chcete-li vytvořit dynamické rozdělovače oken, zavolejte **vytvořit** – členská funkce.  
  
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
 `pParentWnd`  
 Nadřazené okno rámce okna rozdělovače.  
  
 *nMaxRows*  
 Maximální počet řádků v rozděleném okně. Tato hodnota nesmí být větší než 2.  
  
 *nMaxCols*  
 Maximální počet sloupců v rozděleném okně. Tato hodnota nesmí být větší než 2.  
  
 `sizeMin`  
 Určuje minimální velikost, kdy se může zobrazit podokno.  
  
 `pContext`  
 Ukazatel [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Ve většině případů to může být `pContext` předaný nadřazeného rámce okna.  
  
 `dwStyle`  
 Určuje styl okna.  
  
 `nID`  
 ID okno podřízeného okna. ID může být **AFX_IDW_PANE_FIRST** Pokud je okno rozdělovače vnořit další okno rozdělovače.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vložit `CSplitterWnd` v nadřazené [CFrameWnd](../../mfc/reference/cframewnd-class.md) nebo [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objekt provedením následujících kroků:  
  
1.  Vložení `CSplitterWnd` členské proměnné v rámci nadřazené.  
  
2.  Přepsání nadřazeného rámce [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) – členská funkce.  
  
3.  Volání **vytvořit** – členská funkce z v rámci přepsané `OnCreateClient`.  
  
 Při vytváření okna rozdělovače z v rámci nadřazené předat nadřazeného rámce `pContext` parametr do okna rozdělovače. Jinak, tento parametr může být **NULL**.  
  
 Počáteční řádek minimální výška a ve sloupci šířku dynamické rozdělovače oken nastavené `sizeMin` parametr. Tyto minimálních, které určují, zda je příliš malá, která se má zobrazit v celé jeho šíři podokno, můžete změnit pomocí [SetRowInfo](#setrowinfo) a [SetColumnInfo](#setcolumninfo) členské funkce.  
  
 Další informace o dynamické rozdělovače oken, najdete v části "Rozdělovače Windows" v článku [více typů dokumentů, zobrazení a oken s rámečkem](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technická poznámka 29](../../mfc/tn029-splitter-windows.md)a `CSplitterWnd` přehledu třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]  
  
##  <a name="createscrollbarctrl"></a>CSplitterWnd::CreateScrollBarCtrl  
 Voláno rámcem vytvořit ovládací prvek sdílené posuvníku.  
  
```  
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl okna.  
  
 `nID`  
 ID okno podřízeného okna. ID může být **AFX_IDW_PANE_FIRST** Pokud je okno rozdělovače vnořit další okno rozdělovače.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání `CreateScrollBarCtrl` zahrnout další ovládací prvky vedle posuvníku. Výchozí chování je vytvoření ovládací prvky panelu přejděte normální Windows.  
  
##  <a name="createstatic"></a>CSplitterWnd::CreateStatic  
 Chcete-li vytvořit statické rozdělovače oken, zavolejte `CreateStatic` – členská funkce.  
  
```  
virtual BOOL CreateStatic(
    CWnd* pParentWnd,  
    int nRows,  
    int nCols,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Nadřazené okno rámce okna rozdělovače.  
  
 `nRows`  
 Počet řádků. Tato hodnota nesmí být delší než 16.  
  
 *nCols*  
 Počet sloupců. Tato hodnota nesmí být delší než 16.  
  
 `dwStyle`  
 Určuje styl okna.  
  
 `nID`  
 ID okno podřízeného okna. ID může být **AFX_IDW_PANE_FIRST** Pokud je okno rozdělovače vnořit další okno rozdělovače.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 A `CSplitterWnd` je obvykle vložený v nadřazeném prvku `CFrameWnd` nebo [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objekt provedením následujících kroků:  
  
1.  Vložení `CSplitterWnd` členské proměnné v rámci nadřazené.  
  
2.  Přepsání nadřazeného rámce `OnCreateClient` – členská funkce.  
  
3.  Volání `CreateStatic` – členská funkce z v rámci přepsané [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).  
  
 Statické rozdělovače oken obsahuje pevný počet podokna často z různých tříd.  
  
 Když vytvoříte statické rozdělovače oken, musíte ve stejnou dobu vytvořit všechny jeho podokna. [Objektu CreateView](#createview) – členská funkce se obvykle používá pro tento účel, ale můžete vytvořit další nonview třídy.  
  
 Počáteční řádek minimální výška a ve sloupci šířka statické rozdělovače oken je 0. Tyto minimálních, které určují, kdy je příliš malá, která se má zobrazit v celé jeho šíři podokno, můžete změnit pomocí [SetRowInfo](#setrowinfo) a [SetColumnInfo](#setcolumninfo) členské funkce.  
  
 Chcete-li přidat posuvníky statické rozdělovače oken, přidejte **ws_hscroll –** a **ws_vscroll –** styly k `dwStyle`.  
  
 Najdete v části "Rozdělovače Windows" v článku [více typů dokumentů, zobrazení a oken s rámečkem](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technická poznámka 29](../../mfc/tn029-splitter-windows.md)a `CSplitterWnd` přehledu třídy pro další informace o statické rozdělovače oken.  
  
##  <a name="createview"></a>CSplitterWnd::CreateView  
 Vytvoří podokna pro statické rozdělovače oken.  
  
```  
virtual BOOL CreateView(
    int row,  
    int col,  
    CRuntimeClass* pViewClass,  
    SIZE sizeInit,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Určuje řádek okno rozdělovače do níž umístíte nové zobrazení.  
  
 `col`  
 Určuje sloupec rozdělovače oken, ve kterém umístit nové zobrazení.  
  
 `pViewClass`  
 Určuje, [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) nového zobrazení.  
  
 *sizeInit*  
 Určuje počáteční velikost nového zobrazení.  
  
 `pContext`  
 Ukazatel na vytvoření kontextu použít k vytvoření zobrazení (obvykle `pContext` předaný do nadřazeného rámce přepsaného [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) – členská funkce, ve kterém se vytváří rozděleném okně).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Všechny podokna statické rozdělovače oken musí být vytvořeny, než rozdělovače zobrazí rozhraní.  
  
 Rozhraní framework také volá tuto funkci člen k vytvoření nové podokna, když uživatel dynamické rozdělovače oken rozdělí podokně, sloupce či řádku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]  
  
##  <a name="csplitterwnd"></a>CSplitterWnd::CSplitterWnd  
 Volání k vytvoření `CSplitterWnd` objektu.  
  
```  
CSplitterWnd();
```  
  
### <a name="remarks"></a>Poznámky  
 Vytvořit `CSplitterWnd` objektu ve dvou krocích. Nejprve volání konstruktoru, který vytvoří `CSplitterWnd` objektu a pak zavolají [vytvořit](#create) členská funkce, který vytvoří okno rozdělovače a připojí jej k `CSplitterWnd` objektu.  
  
##  <a name="deletecolumn"></a>CSplitterWnd::DeleteColumn  
 Z okna rozdělovače odstraní sloupec.  
  
```  
virtual void DeleteColumn(int colDelete);
```  
  
### <a name="parameters"></a>Parametry  
 *colDelete*  
 Určuje sloupec, který má být odstraněn.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen je voláno rámcem implementovat logiku okna dynamické rozdělovače (tj. Pokud má rozdělovače oken **SPLS_DYNAMIC_SPLIT** styl). Lze jej upravit, společně s virtuální funkcí [objektu CreateView](#createview), implementovat pokročilejší dynamické příčky.  
  
##  <a name="deleterow"></a>CSplitterWnd::DeleteRow  
 Odstranění řádku z okna rozdělovače.  
  
```  
virtual void DeleteRow(int rowDelete);
```  
  
### <a name="parameters"></a>Parametry  
 *rowDelete*  
 Určuje řádku, který má být odstraněna.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen je voláno rámcem implementovat logiku okna dynamické rozdělovače (tj. Pokud má rozdělovače oken **SPLS_DYNAMIC_SPLIT** styl). Lze jej upravit, společně s virtuální funkcí [objektu CreateView](#createview), implementovat pokročilejší dynamické příčky.  
  
##  <a name="deleteview"></a>CSplitterWnd::DeleteView  
 Odstraní z okna rozdělovače zobrazení.  
  
```  
virtual void DeleteView(
    int row,  
    int col);
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Určuje řádek rozdělovače oken, pro kterou chcete odstranit zobrazení.  
  
 `col`  
 Určuje sloupec rozdělovače oken, pro kterou chcete odstranit zobrazení.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se odstraňuje aktivní zobrazení, další zobrazení je aktivní. Výchozí implementace předpokládá zobrazení automaticky odstranit v [postncdestroy –](../../mfc/reference/cwnd-class.md#postncdestroy).  
  
 Tato funkce člen je voláno rámcem implementovat logiku okna dynamické rozdělovače (tj. Pokud má rozdělovače oken **SPLS_DYNAMIC_SPLIT** styl). Lze jej upravit, společně s virtuální funkcí [objektu CreateView](#createview), implementovat pokročilejší dynamické příčky.  
  
##  <a name="dokeyboardsplit"></a>CSplitterWnd::DoKeyboardSplit  
 Provede klávesnice split příkazu, obvykle "rozdělení na okna".  
  
```  
virtual BOOL DoKeyboardSplit();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen je nejvyšší úrovni příkaz, který je používán [CView](../../mfc/reference/cview-class.md) třída delegovat `CSplitterWnd` implementace.  
  
##  <a name="doscroll"></a>CSplitterWnd::DoScroll  
 Provede synchronizované posouvání rozdělení windows.  
  
```  
virtual BOOL DoScroll(
    CView* pViewFrom,  
    UINT nScrollCode,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pViewFrom`  
 Ukazatel na zobrazení, z něhož pochází posouvání zprávy.  
  
 `nScrollCode`  
 Posuvníku kód, který označuje uživatele je posouvání požadavku. Tento parametr se skládá ze dvou částí: nejnižší bajtů, která určuje typ posouvání výskytu vodorovně, a horní bajtů, která určuje typ posouvání výskytu svisle:  
  
- **SB_BOTTOM** posouvá dolů.  
  
- **SB_LINEDOWN** jeden řádek posune stránku dolů.  
  
- **SB_LINEUP** posune jeden řádek nahoru.  
  
- **SB_PAGEDOWN** jednu stránku posune stránku dolů.  
  
- **SB_PAGEUP** posune jednu stránku nahoru.  
  
- **SB_TOP** posune nahoru.  
  
 `bDoScroll`  
 Určuje, zda dochází k posouvání zadanou akci. Pokud `bDoScroll` je **TRUE** (tj. Pokud existuje podřízeného okna a rozdělení windows mít rozsah scroll), pak na zadanou akci posouvání můžete provést místní; v případě `bDoScroll` je **FALSE** (tj. Pokud neexistuje žádné podřízeného okna, nebo zobrazení rozdělení je k dispozici žádné scroll rozsah), pak posouvání nedojde.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě synchronizované posouvání; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je volána rámcem provést synchronizované posouvání rozdělení windows, když zobrazení přijme zprávu o scroll. Přepsání nastavení za účelem vyžadovat akci uživatele předtím, než je povoleno posouvání synchronizované.  
  
##  <a name="doscrollby"></a>CSplitterWnd::DoScrollBy  
 Posouvá rozdělit windows zadaný počet pixelů.  
  
```  
virtual BOOL DoScrollBy(
    CView* pViewFrom,  
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pViewFrom`  
 Ukazatel na zobrazení, z něhož pochází posouvání zprávy.  
  
 `sizeScroll`  
 Počet pixelů k posouvat vodorovně a svisle.  
  
 bDoScroll  
 Určuje, zda dochází k posouvání zadanou akci. Pokud `bDoScroll` je **TRUE** (tj. Pokud existuje podřízeného okna a rozdělení windows mít rozsah scroll), pak na zadanou akci posouvání můžete provést místní; v případě `bDoScroll` je **FALSE** (tj. Pokud neexistuje žádné podřízeného okna, nebo zobrazení rozdělení je k dispozici žádné scroll rozsah), pak posouvání nedojde.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě synchronizované posouvání; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci člen je voláno rámcem v odpovědi na zprávu přejděte, k provedení synchronizované posouvání Windows dělené velikostí v pixelech indikován `sizeScroll`. Kladné hodnoty stanovují posouvání dolů a doprava; záporné hodnoty znamenat posouvání nahoru a doleva.  
  
 Přepsání nastavení za účelem vyžadovat zásah uživatele před povolením scroll.  
  
##  <a name="getactivepane"></a>CSplitterWnd::GetActivePane  
 Určuje podokně active z fokus nebo aktivní zobrazení v rámečku.  
  
```  
virtual CWnd* GetActivePane(
    int* pRow = NULL,  
    int* pCol = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pRow`  
 Ukazatel na **int** načíst řádek počet podokně aktivní.  
  
 `pCol`  
 Ukazatel na **int** načíst číslo sloupce active podokna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na podokně aktivní. **NULL** Pokud neexistuje žádné aktivní podokně.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen je voláno rámcem k určení podokně aktivní v rozděleném okně. Přepsání nastavení za účelem vyžadovat zásah uživatele před získáním podokně aktivní.  
  
##  <a name="getcolumncount"></a>CSplitterWnd::GetColumnCount  
 Vrátí aktuální počet sloupců podokně.  
  
```  
int GetColumnCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktuální počet sloupců rozdělovače. U statické rozdělovače to bude také maximální počet sloupců.  
  
##  <a name="getcolumninfo"></a>CSplitterWnd::GetColumnInfo  
 Vrátí informace na zadaný sloupec.  
  
```  
void GetColumnInfo(
    int col,  
    int& cxCur,  
    int& cxMin) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `col`  
 Určuje sloupec.  
  
 *cxCur*  
 Odkaz na `int` být nastavena na aktuální šířka sloupce.  
  
 `cxMin`  
 Odkaz na `int` být nastavena na aktuální minimální šířka sloupce.  
  
##  <a name="getpane"></a>CSplitterWnd::GetPane  
 Vrátí panelu v zadané řádků a sloupců.  
  
```  
CWnd* GetPane(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Určuje řádek.  
  
 `col`  
 Určuje sloupec.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí panelu v zadané řádků a sloupců. Vrácený podokno je obvykle [CView](../../mfc/reference/cview-class.md)-odvozené třídy.  
  
##  <a name="getrowcount"></a>CSplitterWnd::GetRowCount  
 Vrátí aktuální počet řádků podokně.  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktuální počet řádků v rozděleném okně. Statické rozdělovače období to také bude maximální počet řádků.  
  
##  <a name="getrowinfo"></a>CSplitterWnd::GetRowInfo  
 Vrátí informace na zadaný řádek.  
  
```  
void GetRowInfo(
    int row,  
    int& cyCur,  
    int& cyMin) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Určuje řádek.  
  
 `cyCur`  
 Odkaz na `int` být nastavena na aktuální výšku řádku v pixelech.  
  
 `cyMin`  
 Odkaz na `int` být nastavena na aktuální minimální výška řádku v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen získat informace o zadané řádku. `cyCur` Parametr je vyplněn aktuální výšku řádku zadaný a `cyMin` je vyplněn minimální výška řádku.  
  
##  <a name="getscrollstyle"></a>CSplitterWnd::GetScrollStyle  
 Vrátí styl sdílené posuvníku pro okno rozdělovače.  
  
```  
DWORD GetScrollStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden nebo více následujících windows styl příznaky, pokud bylo úspěšné:  
  
- **Ws_hscroll –** Pokud rozdělovače aktuálně spravuje sdílené vodorovné posuvníky.  
  
- **Ws_vscroll –** Pokud rozdělovače aktuálně spravuje sdílené svislé posuvníky.  
  
 Pokud nula, okno rozdělovače aktuálně nespravuje žádné sdílené posuvníky.  
  
##  <a name="idfromrowcol"></a>CSplitterWnd::IdFromRowCol  
 Získá podřízená okna ID pro panelu v zadané řádků a sloupců.  
  
```  
int IdFromRowCol(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Určuje řádek rozdělovače oken.  
  
 `col`  
 Určuje sloupec rozdělovače oken.  
  
### <a name="return-value"></a>Návratová hodnota  
 ID podřízené okno podokně.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen se používá k vytváření nonviews jako podokna a může být volána před podokně existuje.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]  
  
##  <a name="ischildpane"></a>CSplitterWnd::IsChildPane  
 Určuje, zda `pWnd` je aktuálně podřízený podokně tohoto okna rozdělovače.  
  
```  
BOOL IsChildPane(
    CWnd* pWnd,  
    int* pRow,  
    int* pCol);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který má být testována.  
  
 `pRow`  
 Ukazatel na `int` pro uložení číslo řádku.  
  
 `pCol`  
 Ukazatel na `int` pro uložení počet sloupců.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je nenulový, `pWnd` je aktuálně podřízený podokně tohoto okna rozdělovače a `pRow` a `pCol` jsou vyplněny pozice v podokně v rozděleném okně. Pokud `pWnd` není podřízené podokně okna rozdělovače, je vrácena 0.  
  
### <a name="remarks"></a>Poznámky  
 Ve Visual C++ verze starší než 6.0 tato funkce byla definována jako  
  
 `BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`  
  
 Tato verze je zastaralá a by se neměla používat.  
  
##  <a name="istracking"></a>CSplitterWnd::IsTracking  
 Volání této funkce člen k určení, pokud tento panel v okně právě přesouvá.  
  
```  
BOOL IsTracking();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud operace rozdělovače probíhá; jinak 0.  
  
##  <a name="ondrawsplitter"></a>CSplitterWnd::OnDrawSplitter  
 Vykreslí obrázek rozděleném okně.  
  
```  
virtual void OnDrawSplitter(
    CDC* pDC,  
    ESplitType nType,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel na zařízení kontextu, ve kterém k vykreslení. Pokud `pDC` je **NULL**, pak [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) nazývá rozhraní a žádné rozdělení okna vykreslením.  
  
 `nType`  
 Hodnota **výčtu ESplitType**, který může být jedna z následujících akcí:  
  
- **splitBox** rozdělovače přetáhněte pole.  
  
- `splitBar`Panel, který se zobrazí mezi dvěma rozdělení windows.  
  
- **splitIntersection** průnik rozdělení windows. Tento element nebude volána, když se používá systém Windows 95/98.  
  
- **splitBorder** ohraničení rozdělení oken.  
  
 `rect`  
 Odkaz na [CRect](../../atl-mfc-shared/reference/crect-class.md) určující velikost a tvar rozdělení Windows.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen je voláno rámcem kreslení a určete přesnou charakteristika rozděleném okně. Přepsání `OnDrawSplitter` pro vlastní nastavení dokumentů pro různé součásti grafické rozděleném okně. Výchozí obrazů je podobná rozdělovače v aplikaci Microsoft Works pro Windows nebo Microsoft Windows 95/98, v tom, že jsou průniků řádky rozdělovače smíšení společně.  
  
 Další informace o dynamické rozdělovače oken, najdete v části "Rozdělovače Windows" v článku [více typů dokumentů, zobrazení a oken s rámečkem](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technická poznámka 29](../../mfc/tn029-splitter-windows.md)a `CSplitterWnd` přehledu třídy.  
  
##  <a name="oninverttracker"></a>CSplitterWnd::OnInvertTracker  
 Vykreslí bitové kopie rozděleném okně stejnou velikost a tvar jako rámce okna.  
  
```  
virtual void OnInvertTracker(const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Odkaz na `CRect` určující rámeček sledování.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen je voláno rámcem během změnu velikosti příčky. Přepsání `OnInvertTracker` pro vlastní nastavení obrazů okna rozdělovače. Výchozí obrazů je podobná rozdělovače v aplikaci Microsoft Works pro Windows nebo Microsoft Windows 95/98, v tom, že jsou průniků řádky rozdělovače smíšení společně.  
  
 Další informace o dynamické rozdělovače oken, najdete v části "Rozdělovače Windows" v článku [více typů dokumentů, zobrazení a oken s rámečkem](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technická poznámka 29](../../mfc/tn029-splitter-windows.md)a `CSplitterWnd` přehledu třídy.  
  
##  <a name="recalclayout"></a>CSplitterWnd::RecalcLayout  
 Volání k opětovnému zobrazení okna rozdělovače po nastavení velikosti sloupce či řádku.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen správně znovu zobrazit okno rozdělovače po po úpravě velikosti řádků a sloupců se [SetRowInfo](#setrowinfo) a [SetColumnInfo](#setcolumninfo) členské funkce. Pokud změníte velikosti řádků a sloupců jako součást procesu vytváření před okno rozdělovače je viditelné, není nutné volání této funkce člen.  
  
 Tento člen funkce volá framework pokaždé, když uživatel změní velikost okna rozdělovače nebo přesune rozdělení.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CSplitterWnd::SetColumnInfo](#setcolumninfo).  
  
##  <a name="setactivepane"></a>CSplitterWnd::SetActivePane  
 Nastaví podokně být aktivní v rámečku.  
  
```  
virtual void SetActivePane(
    int row,  
    int col,  
    CWnd* pWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Pokud `pWnd` je **NULL**, určuje řádek v podokně, které se bude aktivní.  
  
 `col`  
 Pokud `pWnd` je **NULL**, určuje sloupec, v podokně, které se bude aktivní.  
  
 `pWnd`  
 Ukazatel na `CWnd` objektu. Pokud **NULL**, v podokně určeného `row` a `col` je nastaveno jako aktivní. Není-li **NULL**, určuje, v podokně, který je nastavený active.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen je voláno rámcem a nastavte podokno jako aktivní, když uživatel změní fokus do podokna v okně s rámečkem. Můžete explicitně volat `SetActivePane` změnit zaměřuje na zadané zobrazení.  
  
 Zadejte podokně tím, že poskytuje řádků a sloupců, **nebo** tím, že poskytuje `pWnd`.  
  
##  <a name="setcolumninfo"></a>CSplitterWnd::SetColumnInfo  
 Volání nastavení informací o zadaný sloupec.  
  
```  
void SetColumnInfo(
    int col,  
    int cxIdeal,  
    int cxMin);
```  
  
### <a name="parameters"></a>Parametry  
 `col`  
 Určuje sloupec rozdělovače oken.  
  
 *cxIdeal*  
 Určuje pro sloupec okno rozdělovače ideální šířku v pixelech.  
  
 `cxMin`  
 Určuje minimální šířka sloupce rozdělovače oken v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen nastavit novou minimální šířku a šířka ideální pro sloupec. Minimální hodnota sloupce určuje, kdy budou příliš malá, aby plně zobrazit sloupce.  
  
 Pokud rozhraní zobrazí okno rozdělovače, rozložen podokna ve sloupci a řádky podle jejich ideální dimenze práce z levého horního do pravém dolním rohu okna rozdělovače klientské oblasti.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]  
  
##  <a name="setrowinfo"></a>CSplitterWnd::SetRowInfo  
 Volání se nastavit informace o zadané řádek.  
  
```  
void SetRowInfo(
    int row,  
    int cyIdeal,  
    int cyMin);
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Určuje řádek rozdělovače oken.  
  
 *cyIdeal*  
 Určuje ideální výšku řádku rozdělovače oken v pixelech.  
  
 `cyMin`  
 Určuje minimální výška řádku rozdělovače oken v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen nastavit nové minimální výška a ideální výšku řádku. Minimální hodnota řádek určuje, kdy budou řádek příliš malá, aby plně nezobrazí.  
  
 Pokud rozhraní zobrazí okno rozdělovače, rozložen podokna ve sloupci a řádky podle jejich ideální dimenze práce z levého horního do pravém dolním rohu okna rozdělovače klientské oblasti.  
  
##  <a name="setscrollstyle"></a>CSplitterWnd::SetScrollStyle  
 Určuje, že nový styl posunutí pro okno rozdělovače posuvníku podpora sdílených.  
  
```  
void SetScrollStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Nový styl posunutí pro okno rozdělovače sdílené posuvníku podpora, což může mít jednu z následujících hodnot:  
  
- **Ws_hscroll –** vodorovných vytvořit/zobrazit sdílené posuvníky.  
  
- **Ws_vscroll –** vertical vytvořit/zobrazit sdílené posuvníky.  
  
### <a name="remarks"></a>Poznámky  
 Po vytvoření posuvníku nebude zničen i v případě `SetScrollStyle` je volána bez této styl; místo toho jsou tyto posuvníky skryté. To umožňuje posuvníky zachování jejich stavu, i když jejich skrytí. Po volání `SetScrollStyle` je nutné volat [recalclayout –](#recalclayout) pro všechny změny se projeví.  
  
##  <a name="splitcolumn"></a>CSplitterWnd::SplitColumn  
 Určuje, kde okně s rámečkem rozdělí svisle.  
  
```  
virtual BOOL SplitColumn(int cxBefore);
```  
  
### <a name="parameters"></a>Parametry  
 *cxBefore*  
 Pozice v pixelech, které, než dojde k rozdělení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je volána při vytvoření svislé rozděleném okně. `SplitColumn`Určuje výchozí umístění, kde dojde k rozdělení.  
  
 `SplitColumn`je voláno rámcem implementovat logiku okna dynamické rozdělovače (tj. Pokud má rozdělovače oken **SPLS_DYNAMIC_SPLIT** styl). Lze jej upravit, společně s virtuální funkcí [objektu CreateView](#createview), implementovat pokročilejší dynamické příčky.  
  
##  <a name="splitrow"></a>CSplitterWnd::SplitRow  
 Určuje, kde okně s rámečkem rozdělí vodorovně.  
  
```  
virtual BOOL SplitRow(int cyBefore);
```  
  
### <a name="parameters"></a>Parametry  
 *cyBefore*  
 Pozice v pixelech, které, než dojde k rozdělení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je volána, když se vytvoří okno vodorovný rozdělovač. `SplitRow`Určuje výchozí umístění, kde dojde k rozdělení.  
  
 `SplitRow`je voláno rámcem implementovat logiku okna dynamické rozdělovače (tj. Pokud má rozdělovače oken **SPLS_DYNAMIC_SPLIT** styl). Lze jej upravit, společně s virtuální funkcí [objektu CreateView](#createview), implementovat pokročilejší dynamické příčky.  
  
##  <a name="ondraw"></a>CSplitterWnd::OnDraw  
 Voláno rámcem k vykreslení rozdělovače oken.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel na kontextu zařízení.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC VIEWEX](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CView – třída](../../mfc/reference/cview-class.md)   
 [CWnd – třída](../../mfc/reference/cwnd-class.md)
