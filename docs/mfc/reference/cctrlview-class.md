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
ms.openlocfilehash: 334f139b81afeb06d57cbd128abe9e413b1fd0e7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507149"
---
# <a name="cctrlview-class"></a>CCtrlView – třída

Přizpůsobí architekturu zobrazení dokumentu na běžné ovládací prvky podporované systémy Windows 98 a Windows NT verze 3,51 a novější.

## <a name="syntax"></a>Syntaxe

```
class CCtrlView : public CView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CCtrlView::CCtrlView](#cctrlview)|`CCtrlView` Vytvoří objekt.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CCtrlView::OnDraw](#ondraw)|Volá se rozhraním, aby se vykreslilo pomocí určeného kontextu zařízení.|
|[CCtrlView::PreCreateWindow](#precreatewindow)|Volá se před vytvořením okna Windows připojeného k tomuto `CCtrlView` objektu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Obsahuje výchozí styl pro třídu zobrazení.|
|[CCtrlView::m_strClass](#m_strclass)|Obsahuje název třídy systému Windows pro třídu zobrazení.|

## <a name="remarks"></a>Poznámky

Třída `CCtrlView` a její deriváty, [CEditView](../../mfc/reference/ceditview-class.md), [CListView –](../../mfc/reference/clistview-class.md), [CTreeView –](../../mfc/reference/ctreeview-class.md)a [CRichEditView –](../../mfc/reference/cricheditview-class.md), přizpůsobuje architekturu zobrazení dokumentu na nové běžné ovládací prvky podporované systémy Windows 95/98 a Windows NT verze 3,51 a novější. Další informace o architektuře dokumentů a zobrazení najdete v tématu [Architektura Document/View](../../mfc/document-view-architecture.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cctrlview"></a>CCtrlView::CCtrlView

`CCtrlView` Vytvoří objekt.

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*lpszClass*<br/>
Název třídy zobrazení třídy pro Windows

*dwStyle*<br/>
Styl třídy zobrazení

### <a name="remarks"></a>Poznámky

Rozhraní volá konstruktor při vytvoření nového okna rámce nebo rozdělení okna. Přepište [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) pro inicializaci zobrazení po připojení dokumentu. Chcete-li vytvořit objekt Windows, zavolejte na adresu [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) nebo [CWnd:: CreateEx](../../mfc/reference/cwnd-class.md#createex) .

##  <a name="m_strclass"></a>CCtrlView::m_strClass

Obsahuje název třídy systému Windows pro třídu zobrazení.

```
CString m_strClass;
```

##  <a name="m_dwdefaultstyle"></a>CCtrlView::m_dwDefaultStyle

Obsahuje výchozí styl pro třídu zobrazení.

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>Poznámky

Tento styl je použit při vytvoření okna.

##  <a name="ondraw"></a>CCtrlView:: Draw

Volá se rozhraním, aby se nakreslil obsah `CCtrlView` objektu pomocí zadaného kontextu zařízení.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na kontext zařízení, ve kterém probíhá vykreslování.

### <a name="remarks"></a>Poznámky

`OnDraw`je obvykle volána pro zobrazení obrazovky, při předávání kontextu zařízení obrazovky určeného *řadičem domény*.

##  <a name="precreatewindow"></a>CCtrlView::P recreatewindow

Volá se před vytvořením okna Windows připojeného k tomuto `CWnd` objektu.

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parametry

*cs*<br/>
Struktura [CREATESTRUCT –](/windows/win32/api/winuser/ns-winuser-createstructw)

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud by mělo vytvoření okna pokračovat; 0 pro indikaci selhání vytvoření.

### <a name="remarks"></a>Poznámky

Tuto funkci nikdy Nevolejte přímo.

Výchozí implementace této funkce kontroluje název třídy okna s hodnotou NULL a nahradí vhodnou výchozí hodnotu. Přepište tuto členskou funkci pro úpravu `CREATESTRUCT` struktury před vytvořením okna.

Každá třída odvozená `CCtrlView` od přidává vlastní funkce k `PreCreateWindow`přepsání. V takovém případě tyto odvozené `PreCreateWindow` označení nejsou dokumentovány. Chcete-li určit styly vhodné pro jednotlivé třídy a vzájemné závislosti mezi styly, můžete prostudovat zdrojový kód MFC pro základní třídu vaší aplikace. Pokud se rozhodnete přepsat `PreCreateWindow`, můžete určit, zda styly použité v základní třídě vaší aplikace poskytují funkcionalitu, kterou potřebujete, pomocí informací shromážděných ze zdrojového kódu knihovny MFC.

Další informace o změně stylů oken naleznete v tématu [Změna stylů okna vytvořeného pomocí knihovny MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Viz také:

[CView – třída](../../mfc/reference/cview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CTreeView – třída](../../mfc/reference/ctreeview-class.md)<br/>
[CListView – třída](../../mfc/reference/clistview-class.md)<br/>
[CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
