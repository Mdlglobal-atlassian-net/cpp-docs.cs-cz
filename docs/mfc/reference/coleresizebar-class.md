---
title: "Třída COleResizeBar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
dev_langs: C++
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3369ef30758b687c94c97e5fb0cf18bb7565ea83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="coleresizebar-class"></a>COleResizeBar – třída
Typ ovládacího prvku panel, který podporuje změnu velikosti na místě OLE – položky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleResizeBar : public CControlBar  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleResizeBar::COleResizeBar](#coleresizebar)|Vytvoří `COleResizeBar` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleResizeBar::Create](#create)|Vytvoří a inicializuje podřízeného okna Windows a přidruží ji k `COleResizeBar` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `COleResizeBar`objekty se zobrazí jako [crecttracker –](../../mfc/reference/crecttracker-class.md) s šrafované ohraničení a vnější změnit velikost obslužné rutiny.  
  
 `COleResizeBar`objekty jsou obvykle embedded členy odvozené z objektů oken s rámečkem [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) třídy.  
  
 Další informace najdete v článku [aktivace](../../mfc/activation-cpp.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Ccontrolbar –](../../mfc/reference/ccontrolbar-class.md)  
  
 `COleResizeBar`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="coleresizebar"></a>COleResizeBar::COleResizeBar  
 Vytvoří `COleResizeBar` objektu.  
  
```  
COleResizeBar();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání **vytvořit** k vytvoření objektu změny velikosti panelu.  
  
##  <a name="create"></a>COleResizeBar::Create  
 Vytvoří podřízeného okna a přidruží ji s `COleResizeBar` objektu.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,  
    UINT nID = AFX_IDW_RESIZE_BAR);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Ukazatel do nadřazeného okna změny velikosti panelu.  
  
 `dwStyle`  
 Určuje, [styl okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) atributy.  
  
 `nID`  
 ID změny velikosti panelu podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl vytvořen na změny velikosti panelu; jinak 0.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC SUPERPAD](../../visual-cpp-samples.md)   
 [Ccontrolbar – třída](../../mfc/reference/ccontrolbar-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleServerDoc – třída](../../mfc/reference/coleserverdoc-class.md)
