---
title: Cdialogex – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d941b112047dc8f90a8cdc4686e422f028b6d7e
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335955"
---
# <a name="cdialogex-class"></a>Cdialogex – třída
`CDialogEx` Třída určuje barvu pozadí a obrázek pozadí dialogového okna.  
  
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
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|Nastaví obrázek pozadí dialogového okna.|  
  
## <a name="remarks"></a>Poznámky  
 Použít `CDialogEx` třídy, odvoďte vlastní třídy dialogového okna pole z `CDialogEx` místo na třídě `CDialog` třídy.  
  
 Dialogové okno pole Image se ukládají do souboru prostředků. Rozhraní automaticky odstraní všechny image, která jsou načtená ze souboru prostředků. Chcete-li programově odstranit aktuální obrázek na pozadí, zavolejte [CDialogEx::SetBackgroundImage](#setbackgroundimage) metody nebo implementovat `OnDestroy` obslužné rutiny události. Při volání [CDialogEx::SetBackgroundImage](#setbackgroundimage) metoda, předejte `HBITMAP` parametr jako popisovač bitové kopie. `CDialogEx` Objekt převzít vlastnictví na obrázku, který se odstranit, pokud `m_bAutoDestroyBmp` příznak je `TRUE`.  
  
 A `CDialogEx` objekt může být nadřazená [cmfcpopupmenu – třída](../../mfc/reference/cmfcpopupmenu-class.md) objektu. [Cmfcpopupmenu – třída](../../mfc/reference/cmfcpopupmenu-class.md) objektu volání `CDialogEx::SetActiveMenu` metoda při [cmfcpopupmenu – třída](../../mfc/reference/cmfcpopupmenu-class.md) objektu se otevře. Následně `CDialogEx` objekt zpracovává událost všechny nabídky do [cmfcpopupmenu – třída](../../mfc/reference/cmfcpopupmenu-class.md) objekt je zavřený.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [Cdialogex –](../../mfc/reference/cdialogex-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdialogex.h  
  
##  <a name="cdialogex"></a>  CDialogEx::CDialogEx  
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
 [in] *nIDTemplate*  
 ID prostředku šablony dialogového okna.  
  
 [in] *lpszTemplateName*  
 Název prostředku šablony dialogového okna.  
  
 [in] *pParent*  
 Ukazatel do nadřazeného okna. Výchozí hodnota je NULL.  
  
 [in] *pParentWnd*  
 Ukazatel do nadřazeného okna. Výchozí hodnota je NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setbackgroundcolor"></a>  CDialogEx::SetBackgroundColor  
 Nastaví barvu pozadí dialogového okna.  
  
```  
void SetBackgroundColor(
    COLORREF color,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *barva*  
 Hodnota barvy RGB.  
  
 [in] *bRepaint*  
 TRUE, pokud chcete okamžitě aktualizovat obrazovce. v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setbackgroundimage"></a>  CDialogEx::SetBackgroundImage  
 Nastaví obrázek pozadí dialogového okna.  
  
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
 [in] *hBitmap*  
 Popisovač pro obrázek na pozadí.  
  
 [in] *uiBmpResId*  
 ID prostředku obrázku pozadí.  
  
 [in] *umístění*  
 Jeden z `CDialogEx::BackgroundLocation` hodnoty, které určují umístění bitové kopie. Platné hodnoty jsou BACKGR_TILE BACKGR_TOPLEFT, BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT a BACKGR_BOTTOMRIGHT. Výchozí hodnota je BACKGR_TILE.  
  
 [in] *bAutoDestroy*  
 TRUE, pokud chcete automaticky odstranit obrázek pozadí; v opačném případě hodnota FALSE.  
  
 [in] *bRepaint*  
 TRUE, pokud chcete okamžitě ho překreslit dialogové okno. v opačném případě hodnota FALSE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ve druhé metodě přetížení syntaxe, hodnotu TRUE Pokud je metoda úspěšná. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Klientskou oblast dialogového okna není roztažení obrázku, který zadáte.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Cmfcpopupmenu – třída](../../mfc/reference/cmfcpopupmenu-class.md)   
 [CContextMenuManager – třída](../../mfc/reference/ccontextmenumanager-class.md)
