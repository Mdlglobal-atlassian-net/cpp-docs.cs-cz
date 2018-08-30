---
title: Cctrlview – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fdcec255c7d2398e1bb0efa7f86a31fc5dd938e4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210200"
---
# <a name="cctrlview-class"></a>Cctrlview – třída
Přizpůsobí architekturu document / view pro běžné ovládací prvky, které podporuje Windows 98 a Windows NT verze 3.51 a vyšší.  
  
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
|[CCtrlView::OnDraw](#ondraw)|Volá se rozhraním, chcete-li nakreslit v kontextu zadané zařízení.|  
|[CCtrlView::PreCreateWindow](#precreatewindow)|Volá se před vytvořením okna Windows připojených k tomuto `CCtrlView` objektu.|  
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Obsahuje výchozí styl pro danou třídu zobrazení.|  
|[CCtrlView::m_strClass](#m_strclass)|Obsahuje název třídy Windows pro danou třídu zobrazení.|  
  
## <a name="remarks"></a>Poznámky  
 Třída `CCtrlView` a odvozené, [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md), a [cricheditview –](../../mfc/reference/cricheditview-class.md), přizpůsobit architektuře document / view do nové běžné ovládací prvky, nepodporuje Windows 95/98 a Windows NT verze 3.51 a vyšší. Další informace o architektuře document / view najdete v tématu [architekturu Document/View](../../mfc/document-view-architecture.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CCtrlView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cctrlview"></a>  CCtrlView::CCtrlView  
 Vytvoří `CCtrlView` objektu.  
  
```  
CCtrlView(
    LPCTSTR lpszClass,  
    DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszClass*  
 Název třídy Windows třídy zobrazení.  
  
 *dwStyle*  
 Styl zobrazení třídy.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní volá konstruktor, když se vytvoří nový objekt okna rámce nebo je rozdělit okno. Přepsat [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) k inicializaci zobrazení po dokumentu. Volání [CWnd::Create](../../mfc/reference/cwnd-class.md#create) nebo [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) k vytvoření objektu Windows.  
  
##  <a name="m_strclass"></a>  CCtrlView::m_strClass  
 Obsahuje název třídy Windows pro danou třídu zobrazení.  
  
```  
CString m_strClass;  
```  
  
##  <a name="m_dwdefaultstyle"></a>  CCtrlView::m_dwDefaultStyle  
 Obsahuje výchozí styl pro danou třídu zobrazení.  
  
```  
DWORD m_dwDefaultStyle;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento styl se použije, když se vytvoří okno.  
  
##  <a name="ondraw"></a>  CCtrlView::OnDraw  
 Volá se rozhraním, chcete-li nakreslit obsah `CCtrlView` objektu v kontextu zadané zařízení.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 *primární řadič domény*  
 Ukazatel na kontext zařízení, ve kterém dochází výkresu.  
  
### <a name="remarks"></a>Poznámky  
 `OnDraw` je obvykle volána pro obrazovku, předávání určeného kontextu zařízení obrazovky *primárního řadiče domény*.  
  
##  <a name="precreatewindow"></a>  CCtrlView::PreCreateWindow  
 Volá se před vytvořením okna Windows připojených k tomuto `CWnd` objektu.  
  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>Parametry  
 *cs*  
 A [soubor CREATESTRUCT](https://msdn.microsoft.com/library/windows/desktop/ms632603) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud by měly pokračovat ve vytváření oken; 0 označující selhání.  
  
### <a name="remarks"></a>Poznámky  
 Nikdy přímo volat tuto funkci.  
  
 Výchozí implementace této funkce kontroluje název třídy okna NULL a nahradí vhodné výchozí nastavení. Přepsání této členské funkce lze upravit `CREATESTRUCT` strukturu před vytvořením okna.  
  
 Každá třída odvozena z `CCtrlView` přidá vlastní funkce k jeho přepsání `PreCreateWindow`. Standardně tyto odvození z `PreCreateWindow` nejsou uvedené. K určení styly, které jsou vhodné pro každou třídu a vzájemné závislosti mezi styly, můžete zkontrolovat zdrojový kód knihovny MFC pro základní třídu vaší aplikace. Pokud budete chtít přepsat `PreCreateWindow`, můžete určit, zda stylů použitých v základní třídě vaší aplikace poskytují funkce, je nutné pomocí informace získané z zdrojového kódu knihovny MFC.  
  
 Další informace o změně styly oken, najdete v článku [změna stylů okna vytvořeného rozhraním MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [CView – třída](../../mfc/reference/cview-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CTreeView – třída](../../mfc/reference/ctreeview-class.md)   
 [CListView – třída](../../mfc/reference/clistview-class.md)   
 [CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
