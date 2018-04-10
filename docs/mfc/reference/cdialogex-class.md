---
title: Třída CDialogEx | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
dev_langs:
- C++
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c22e258c8306eab1f55fa94f875dde5b68256c71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdialogex-class"></a>CDialogEx – třída
`CDialogEx` Třída určuje barvu pozadí a obrázku pozadí dialogového okna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDialogEx : public CDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDialogEx::CDialogEx](#cdialogex)|Vytvoří `CDialogEx` objektu.|  
|`CDialogEx::~CDialogEx`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|Nastaví barvu pozadí dialogového okna.|  
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|Nastaví obrázek na pozadí dialogové okno.|  
  
## <a name="remarks"></a>Poznámky  
 Použít `CDialogEx` třídy, odvození třídy z vaší dialogového okna `CDialogEx` místo `CDialog` třídy.  
  
 Dialogové okno pole Image jsou uložené v souboru prostředků. Rozhraní framework automaticky odstraní žádný obrázek, který je načten ze zdrojového souboru. Chcete-li odstranit prostřednictvím kódu programu aktuální obrázku pozadí, volejte [CDialogEx::SetBackgroundImage](#setbackgroundimage) metoda nebo implementace `OnDestroy` obslužné rutiny události. Při volání [CDialogEx::SetBackgroundImage](#setbackgroundimage) metoda, předejte jí `HBITMAP` parametr jako popisovač bitové kopie. `CDialogEx` Objektu bude převzít vlastnictví bitové kopie a odstranit, jestliže `m_bAutoDestroyBmp` je příznak `TRUE`.  
  
 A `CDialogEx` objekt může být nadřazené položky [CMFCPopupMenu třída](../../mfc/reference/cmfcpopupmenu-class.md) objektu. [CMFCPopupMenu – třída](../../mfc/reference/cmfcpopupmenu-class.md) objektu volání `CDialogEx::SetActiveMenu` metoda při [CMFCPopupMenu třída](../../mfc/reference/cmfcpopupmenu-class.md) objektu se otevře. Potom `CDialogEx` objekt zpracovává událost žádné nabídky, dokud [CMFCPopupMenu třída](../../mfc/reference/cmfcpopupmenu-class.md) objekt je zavřený.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdialogex.h  
  
##  <a name="cdialogex"></a>CDialogEx::CDialogEx  
 Vytvoří `CDialogEx` objektu.  
  
```  
CDialogEx(
    UINT nIDTemplate,  
    CWnd* pParent=NULL);

 
CDialogEx(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nIDTemplate`  
 ID prostředku šablony pole dialogového okna.  
  
 [v]`lpszTemplateName`  
 Název prostředku šablony pole dialogového okna.  
  
 [v]`pParent`  
 Ukazatel do nadřazeného okna. Výchozí hodnota je `NULL`.  
  
 [v]`pParentWnd`  
 Ukazatel do nadřazeného okna. Výchozí hodnota je `NULL`.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setbackgroundcolor"></a>CDialogEx::SetBackgroundColor  
 Nastaví barvu pozadí dialogového okna.  
  
```  
void SetBackgroundColor(
    COLORREF color,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`color`  
 Hodnotu barva RGB.  
  
 [v]`bRepaint`  
 `TRUE`Chcete-li okamžitě aktualizovat na obrazovce; v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setbackgroundimage"></a>CDialogEx::SetBackgroundImage  
 Nastaví obrázek na pozadí dialogové okno.  
  
```  
void SetBackgroundImage(
    HBITMAP hBitmap,  
    BackgroundLocation location=BACKGR_TILE,  
    BOOL bAutoDestroy=TRUE,  
    BOOL bRepaint=TRUE);

 
BOOL SetBackgroundImage(
    UINT uiBmpResId,  
    BackgroundLocation location=BACKGR_TILE,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hBitmap`  
 Popisovač pro obrázek pozadí.  
  
 [v]`uiBmpResId`  
 ID prostředku obrázku pozadí.  
  
 [v]`location`  
 Jeden z `CDialogEx::BackgroundLocation` hodnoty, které určují umístění bitové kopie. Platné hodnoty patří BACKGR_TILE, BACKGR_TOPLEFT, BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT a BACKGR_BOTTOMRIGHT. Výchozí hodnota je BACKGR_TILE.  
  
 [v]`bAutoDestroy`  
 `TRUE`Chcete-li automaticky odstranit obrázku pozadí; v opačném `FALSE`.  
  
 [v]`bRepaint`  
 `TRUE`okamžitě ho překreslit dialogové okno. v opačném `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 V druhé metody přetížení syntaxe, `TRUE` Pokud metoda úspěšná, jinak hodnota `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Obrázek, který zadáte není roztažen tak, aby vyhovovaly oblast klienta dialogového okna.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu – třída](../../mfc/reference/cmfcpopupmenu-class.md)   
 [CContextMenuManager – třída](../../mfc/reference/ccontextmenumanager-class.md)
