---
title: Třída CHtmlEditView | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10f474ce860bf5d9071a93f17654123f4777efa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367341"
---
# <a name="chtmleditview-class"></a>CHtmlEditView – třída
Poskytuje funkci platformou WebBrowser úpravy v kontextu na MFC document/view – architektura.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|Vytvoří `CHtmlEditView` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CHtmlEditView::Create](#create)|Vytvoří nový objekt okno.|  
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|Vrátí **IHTMLDocument2** rozhraní na aktuálním dokumentu.|  
|[CHtmlEditView::GetStartDocument](#getstartdocument)|Načte název výchozího dokumentu pro toto zobrazení.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [Třídy CFormView](../../mfc/reference/cformview-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CHtmlView](../../mfc/reference/chtmlview-class.md)  
  
 `CHtmlEditView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxhtml.h  
  
##  <a name="chtmleditview"></a>  CHtmlEditView::CHtmlEditView  
 Vytvoří `CHtmlEditView` objektu.  
  
```  
CHtmlEditView();
```  
  
##  <a name="create"></a>  CHtmlEditView::Create  
 Vytvoří nový objekt okno.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszClassName`  
 Bodů na řetězec znaků ukončené hodnotou null, který názvy třídy Windows. Název třídy může být jakýkoli název zaregistrována [afxregisterwndclass –](application-information-and-management.md#afxregisterwndclass) globální funkce nebo **RegisterClass** funkce systému Windows. Pokud **NULL**, používá předdefinovanou výchozí [CFrameWnd](../../mfc/reference/cframewnd-class.md) atributy.  
  
 `lpszWindowName`  
 Odkazuje na řetězec znaků ukončené hodnotou null, který představuje název okna.  
  
 `dwStyle`  
 Určuje styl atributů okna. Ve výchozím nastavení **ws_visible –** a **ws_child –** styly Windows jsou nastavené.  
  
 `rect`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura velikost a umístění okna. `rectDefault` Systému Windows zadejte velikost a umístění nového okna umožní hodnotu.  
  
 `pParentWnd`  
 Ukazatel do nadřazeného okna ovládacího prvku.  
  
 `nID`  
 Číslo ID zobrazení. Ve výchozím nastavení **AFX_IDW_PANE_FIRST**.  
  
 `pContext`  
 Ukazatel [CCreateContext](../../mfc/reference/ccreatecontext-structure.md). **NULL** ve výchozím nastavení.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyžaduje také obsahují WebBrowser **přejděte** metoda načíst výchozí dokument (viz [CHtmlEditView::GetStartDocument](#getstartdocument)).  
  
##  <a name="getdhtmldocument"></a>  CHtmlEditView::GetDHtmlDocument  
 Vrátí **IHTMLDocument2** rozhraní na aktuálním dokumentu.  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `ppDocument`  
 [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) rozhraní.  
  
##  <a name="getstartdocument"></a>  CHtmlEditView::GetStartDocument  
 Načte název výchozího dokumentu pro toto zobrazení.  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>Viz také  
 [Ukázka HTMLEdit](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)


