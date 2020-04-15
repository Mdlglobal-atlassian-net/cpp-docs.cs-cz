---
title: CCtrlView – třída
ms.date: 11/04/2016
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
ms.openlocfilehash: f77f1c265920bd160da790647ef754c55e6dbda3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369360"
---
# <a name="cctrlview-class"></a>CCtrlView – třída

Přizpůsobí architekturu zobrazení dokumentu běžným ovládacím prvkům podporovaným systémy Windows 98 a Windows NT verze 3.51 a novějšími.

## <a name="syntax"></a>Syntaxe

```
class CCtrlView : public CView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CCtrlView::CCtrlView](#cctrlview)|Vytvoří `CCtrlView` objekt.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CCtrlView::Ondraw](#ondraw)|Volat rámci k losování pomocí kontextu zadaného zařízení.|
|[CCtrlView::PreCreateWindow](#precreatewindow)|Volána před vytvořením okna systému `CCtrlView` Windows připojeného k tomuto objektu.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Obsahuje výchozí styl pro třídu zobrazení.|
|[CCtrlView::m_strClass](#m_strclass)|Obsahuje název třídy systému Windows pro třídu zobrazení.|

## <a name="remarks"></a>Poznámky

Třída `CCtrlView` a její derivace [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md)a [CRichEditView](../../mfc/reference/cricheditview-class.md), přizpůsobit architekturu zobrazení dokumentu nové běžné ovládací prvky podporované windows 95/98 a Windows NT verze 3.51 a novější. Další informace o architektuře zobrazení dokumentu naleznete v [tématu Document/View Architecture](../../mfc/document-view-architecture.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cctrlviewcctrlview"></a><a name="cctrlview"></a>CCtrlView::CCtrlView

Vytvoří `CCtrlView` objekt.

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*lpszClass*<br/>
Název třídy systému Windows třídy zobrazení.

*dwStyl*<br/>
Styl třídy zobrazení.

### <a name="remarks"></a>Poznámky

Rozhraní framework volá konstruktor při vytvoření nového okna rámce nebo rozdělení okna. Přepište [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) pro inicializaci zobrazení po připojení dokumentu. Volání [CWnd::Create](../../mfc/reference/cwnd-class.md#create) nebo [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) k vytvoření objektu systému Windows.

## <a name="cctrlviewm_strclass"></a><a name="m_strclass"></a>CCtrlView::m_strClass

Obsahuje název třídy systému Windows pro třídu zobrazení.

```
CString m_strClass;
```

## <a name="cctrlviewm_dwdefaultstyle"></a><a name="m_dwdefaultstyle"></a>CCtrlView::m_dwDefaultStyle

Obsahuje výchozí styl pro třídu zobrazení.

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>Poznámky

Tento styl se použije při vytvoření okna.

## <a name="cctrlviewondraw"></a><a name="ondraw"></a>CCtrlView::Ondraw

Volat rámci k nakreslení obsahu `CCtrlView` objektu pomocí kontextu zadaného zařízení.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext zařízení, ve kterém dochází k výkresu.

### <a name="remarks"></a>Poznámky

`OnDraw`je obvykle volána pro zobrazení na obrazovce, předávání kontextu obrazovky zařízení určené *ho pDC*.

## <a name="cctrlviewprecreatewindow"></a><a name="precreatewindow"></a>CCtrlView::PreCreateWindow

Volána před vytvořením okna systému `CWnd` Windows připojeného k tomuto objektu.

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parametry

*Cs*<br/>
Struktura [CREATESTRUCT.](/windows/win32/api/winuser/ns-winuser-createstructw)

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud by mělo pokračovat vytváření okna; 0 označuje selhání vytváření.

### <a name="remarks"></a>Poznámky

Nikdy nevolejte tuto funkci přímo.

Výchozí implementace této funkce zkontroluje název třídy okna NULL a nahradí příslušné výchozí nastavení. Přepište tuto členovou `CREATESTRUCT` funkci a upravte strukturu před vytvořením okna.

Každá třída odvozená z `CCtrlView` přidává své vlastní `PreCreateWindow`funkce k přepsání . Záměrné, tyto odvození `PreCreateWindow` nejsou zdokumentovány. Chcete-li určit styly vhodné pro každou třídu a vzájemné závislosti mezi styly, můžete prozkoumat zdrojový kód knihovny MFC pro základní třídu aplikace. Pokud se rozhodnete `PreCreateWindow`přepsat , můžete určit, zda styly použité v základní třídě aplikace poskytují požadované funkce pomocí informací shromážděných ze zdrojového kódu knihovny MFC.

Další informace o změně stylů oken naleznete v tématu [Změna stylů okna vytvořeného knihovnou MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Viz také

[Třída CView](../../mfc/reference/cview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CTreeView – třída](../../mfc/reference/ctreeview-class.md)<br/>
[CListView – třída](../../mfc/reference/clistview-class.md)<br/>
[CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
