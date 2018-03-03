---
title: "Třída CCtrlView | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
dev_langs:
- C++
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 484abaf5344400e03b53038d2c137497c202345f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cctrlview-class"></a>CCtrlView – třída
Přizpůsobení zobrazení dokumentu architekturu pro běžné ovládací prvky, které podporuje verze Windows 98 a systému Windows NT 3.51 a novější.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCtrlView : public CView  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CCtrlView::CCtrlView](#cctrlview)|Vytvoří `CCtrlView` objektu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CCtrlView::OnDraw](#ondraw)|Voláno rámcem kreslení pomocí kontextu zadané zařízení.|  
|[CCtrlView::PreCreateWindow](#precreatewindow)|Volá se před vytvořením okna Windows připojených k tomuto `CCtrlView` objektu.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Obsahuje výchozí styl pro třídu zobrazení.|  
|[CCtrlView::m_strClass](#m_strclass)|Obsahuje název třídy Windows pro třídu zobrazení.|  
  
## <a name="remarks"></a>Poznámky  
 Třída `CCtrlView` a odvozené, [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md), a [cricheditview –](../../mfc/reference/cricheditview-class.md), přizpůsobit zobrazení dokumentu architekturu pro nové běžné ovládací prvky podporuje systém Windows 95/98 a systému Windows NT 3.51 a novější verze. Další informace o architektuře dokument zobrazení najdete v tématu [Document/View – architektura](../../mfc/document-view-architecture.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CCtrlView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cctrlview"></a>CCtrlView::CCtrlView  
 Vytvoří `CCtrlView` objektu.  
  
```  
CCtrlView(
    LPCTSTR lpszClass,  
    DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszClass`  
 Název třídy Windows třídy zobrazení  
  
 `dwStyle`  
 Styl zobrazení třídy.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá konstruktor při vytvoření nové okně s rámečkem nebo je rozdělit okno. Přepsání [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) k inicializaci zobrazení po je dokument připojen. Volání [CWnd::Create](../../mfc/reference/cwnd-class.md#create) nebo [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) k vytvoření objektu Windows.  
  
##  <a name="m_strclass"></a>CCtrlView::m_strClass  
 Obsahuje název třídy Windows pro třídu zobrazení.  
  
```  
CString m_strClass;  
```  
  
##  <a name="m_dwdefaultstyle"></a>CCtrlView::m_dwDefaultStyle  
 Obsahuje výchozí styl pro třídu zobrazení.  
  
```  
DWORD m_dwDefaultStyle;  
```  
  
### <a name="remarks"></a>Poznámky  
 Toto je použit, když se vytvoří okno.  
  
##  <a name="ondraw"></a>CCtrlView::OnDraw  
 Voláno rámcem k vykreslení obsahu `CCtrlView` objektu v kontextu zadané zařízení.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel na zařízení kontext, ve kterém dojde k kreslení.  
  
### <a name="remarks"></a>Poznámky  
 `OnDraw`pro zobrazení na obrazovce, předávání určeného kontextu zařízení obrazovky obvykle nazývá `pDC`.  
  
##  <a name="precreatewindow"></a>CCtrlView::PreCreateWindow  
 Volá se před vytvořením okna Windows připojených k tomuto `CWnd` objektu.  
  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>Parametry  
 *cs*  
 A [createstruct –](http://msdn.microsoft.com/library/windows/desktop/ms632603) struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud by měly pokračovat ve vytváření oken; 0 k označení vytvoření se nezdařilo.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nikdy volat přímo.  
  
 Výchozí implementace této funkce zkontroluje **NULL** název třídy okna a nahradí odpovídající výchozí. Člen funkci k úpravě přepsat `CREATESTRUCT` struktury před vytvořením okna.  
  
 Jednotlivé třídy odvozené od `CCtrlView` přidá svůj vlastní funkce k jeho přepsání `PreCreateWindow`. Návrh tyto odvození z `PreCreateWindow` nejsou popsané. Pokud chcete určit vhodné pro každou třídu a vzájemné závislosti mezi stylů styly, můžete zkontrolovat MFC zdrojový kód pro základní třídu vaší aplikace. Pokud se rozhodnete přepsat `PreCreateWindow`, můžete určit, zda styly využívané v základní třídě vaší aplikace poskytují funkce, je nutné pomocí informace získané z MFC zdrojového kódu.  
  
 Další informace o změně styly oken, najdete v článku [změna stylů okna vytvořeného rozhraním MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [CView – třída](../../mfc/reference/cview-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CTreeView – třída](../../mfc/reference/ctreeview-class.md)   
 [CListView – třída](../../mfc/reference/clistview-class.md)   
 [CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
