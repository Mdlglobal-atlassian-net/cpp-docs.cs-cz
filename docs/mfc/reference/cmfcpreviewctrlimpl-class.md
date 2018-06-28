---
title: Třída CMFCPreviewCtrlImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::Create
- AFXWIN/CMFCPreviewCtrlImpl::Destroy
- AFXWIN/CMFCPreviewCtrlImpl::Focus
- AFXWIN/CMFCPreviewCtrlImpl::GetDocument
- AFXWIN/CMFCPreviewCtrlImpl::Redraw
- AFXWIN/CMFCPreviewCtrlImpl::SetDocument
- AFXWIN/CMFCPreviewCtrlImpl::SetHost
- AFXWIN/CMFCPreviewCtrlImpl::SetPreviewVisuals
- AFXWIN/CMFCPreviewCtrlImpl::SetRect
- AFXWIN/CMFCPreviewCtrlImpl::DoPaint
- AFXWIN/CMFCPreviewCtrlImpl::m_clrBackColor
- AFXWIN/CMFCPreviewCtrlImpl::m_clrTextColor
- AFXWIN/CMFCPreviewCtrlImpl::m_font
- AFXWIN/CMFCPreviewCtrlImpl::m_pDocument
dev_langs:
- C++
helpviewer_keywords:
- CMFCPreviewCtrlImpl [MFC], CMFCPreviewCtrlImpl
- CMFCPreviewCtrlImpl [MFC], Create
- CMFCPreviewCtrlImpl [MFC], Destroy
- CMFCPreviewCtrlImpl [MFC], Focus
- CMFCPreviewCtrlImpl [MFC], GetDocument
- CMFCPreviewCtrlImpl [MFC], Redraw
- CMFCPreviewCtrlImpl [MFC], SetDocument
- CMFCPreviewCtrlImpl [MFC], SetHost
- CMFCPreviewCtrlImpl [MFC], SetPreviewVisuals
- CMFCPreviewCtrlImpl [MFC], SetRect
- CMFCPreviewCtrlImpl [MFC], DoPaint
- CMFCPreviewCtrlImpl [MFC], m_clrBackColor
- CMFCPreviewCtrlImpl [MFC], m_clrTextColor
- CMFCPreviewCtrlImpl [MFC], m_font
- CMFCPreviewCtrlImpl [MFC], m_pDocument
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a94ad813ff72eaed2642e9c78a098b999bf128fa
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040074"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl – třída
Tato třída implementuje okno, které je umístěn na hostitelské okno poskytuje prostředí pro verzi Preview formátováním.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCPreviewCtrlImpl : public CWnd;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl](#dtor)|Destructs objekt ovládacího prvku preview.|  
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|Vytvoří objekt ovládacího prvku preview.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::Create](#create)|Přetíženo. Volá obslužnou rutinou bohaté Preview vytvořit období systému Windows.|  
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|Voláno bohaté Preview obslužnou rutinou, pokud je chcete-li odstranit tento ovládací prvek.|  
|[CMFCPreviewCtrlImpl::Focus](#focus)|Nastaví vstupní zaměření tohoto ovládacího prvku.|  
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|Vrátí dokument připojený k tento ovládací prvek preview.|  
|[CMFCPreviewCtrlImpl::Redraw](#redraw)|Tento ovládací prvek pro ho překreslit informuje.|  
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|Volá obslužnou rutinou preview k vytvoření vztahu mezi implementace dokumentu a řízení preview.|  
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|Nastaví novou nadřazenou položku pro tento ovládací prvek.|  
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Volat bohaté Preview obslužnou rutinou, pokud je potřeba nastavit vizuální prvky bohaté Preview obsahu.|  
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|Nastaví nové ohraničující obdélník pro tento ovládací prvek.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|Voláno rámcem k vykreslení ve verzi preview.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|Barva pozadí z okna náhledu.|  
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|Barva textu z okna náhledu.|  
|[CMFCPreviewCtrlImpl::m_font](#m_font)|Písmo použité k zobrazení textu v podokně náhledu.|  
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|Ukazatel na dokument, jejichž obsah je zobrazen náhled v ovládacím prvku.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h    
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimpl"></a> CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
Vytvoří objekt ovládacího prvku preview.

### <a name="syntax"></a>Syntaxe
CMFCPreviewCtrlImpl();  

## <a name="create"></a> CMFCPreviewCtrlImpl::Create
Přetíženo. Volá obslužnou rutinou bohaté Preview vytvořit období systému Windows.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual BOOL Create(  
   HWND hWndParent,  
   const RECT* prc  
);  
virtual BOOL Create(  
   HWND hWndParent,  
   const RECT* prc,  
   CCreateContext* pContext  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *hWndParent*  
 Popisovač pro okno hostitele poskytl prostředí pro verzi Preview formátováním.  
  
 *ČLR*  
 Určuje počáteční velikost a umístění okna.  
  
 *pContext*  
 Ukazatel na vytvoření kontextu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se úspěšně vytvořila; v opačném případě `FALSE`.  
  
## <a name="destroy"></a> CMFCPreviewCtrlImpl::Destroy
Voláno bohaté Preview obslužnou rutinou, pokud je chcete-li odstranit tento ovládací prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void Destroy();  
```  
  
## <a name="dopaint"></a> CMFCPreviewCtrlImpl::DoPaint  
Voláno rámcem k vykreslení ve verzi preview.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void DoPaint(  
   CPaintDC* pDC  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *primárního řadiče domény*  
 Ukazatel na kontext zařízení pro malování.  


## <a name="focus"></a> CMFCPreviewCtrlImpl::Focus  
Nastaví vstupní zaměření tohoto ovládacího prvku.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void Focus();  
```  
## <a name="getdocument"></a> CMFCPreviewCtrlImpl::GetDocument
Vrátí dokument připojený k tento ovládací prvek preview.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ATL::IDocument* GetDocument();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na dokument, jejichž obsah je zobrazen náhled v ovládacím prvku.

## <a name="m_clrbackcolor"></a> CMFCPreviewCtrlImpl::m_clrBackColor  
Barva pozadí okna náhledu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
COLORREF m_clrBackColor;  
```  

## <a name="m_clrtextcolor"></a> CMFCPreviewCtrlImpl::m_clrTextColor
Barva textu z okna náhledu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
COLORREF m_clrTextColor;  
```  
## <a name="m_font"></a> CMFCPreviewCtrlImpl::m_font písmo použité k zobrazení textu v podokně náhledu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
CFont m_font;  
```  
## <a name="m_pdocument"></a> CMFCPreviewCtrlImpl::m_pDocument  
Ukazatel na dokument, jejichž obsah je zobrazen náhled v ovládacím prvku.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ATL::IDocument* m_pDocument;  
```  

## <a name="redraw"></a> CMFCPreviewCtrlImpl::Redraw  
Tento ovládací prvek pro ho překreslit informuje.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void Redraw();  
```  
## <a name="setdocument"></a> CMFCPreviewCtrlImpl::SetDocument 
Volá obslužnou rutinou preview k vytvoření vztahu mezi implementace dokumentu a řízení preview.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void SetDocument(  
   IDocument* pDocument  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDocument*  
 Ukazatel na implementaci dokumentu.  

## <a name="sethost"></a> CMFCPreviewCtrlImpl::SetHost  
Nastaví novou nadřazenou položku pro tento ovládací prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void SetHost(  
   HWND hWndParent  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *hWndParent*  
 Popisovač do nového nadřazeného okna.  

## <a name="setpreviewvisuals"></a> CMFCPreviewCtrlImpl::SetPreviewVisuals  
Volat bohaté Preview obslužnou rutinou, pokud je potřeba nastavit vizuální prvky bohaté Preview obsahu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void SetPreviewVisuals(  
   COLORREF clrBack,  
   COLORREF clrText,  
   const LOGFONTW *plf  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *clrBack*  
 Barva pozadí z okna náhledu.  
  
 *clrText*  
 Barva textu z okna náhledu.  
  
 *PLF*  
 Písmo použité k zobrazení textu v podokně náhledu. 

##  <a name="setrect"></a> CMFCPreviewCtrlImpl::SetRect  
Nastaví nové ohraničující obdélník pro tento ovládací prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual void SetRect(  
   const RECT* prc,  
   BOOL bRedraw  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *ČLR*  
 Určuje nové velikost a umístění ovládacího prvku preview.  
  
 *bRedraw*  
 Určuje, zda by měl být překreslen ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Nové ohraničující obdélník je obvykle nastavena při změně velikosti ovládacího prvku hostitele.  

## <a name="dtor"></a> CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl  
Destructs objekt ovládacího prvku preview.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual ~CMFCPreviewCtrlImpl();  
```  
  
