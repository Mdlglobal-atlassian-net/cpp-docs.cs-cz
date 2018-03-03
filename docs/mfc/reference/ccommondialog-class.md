---
title: "Třída CCommonDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
dev_langs:
- C++
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a42acf9c4655868bcc078b3e40d3966587aeaaad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccommondialog-class"></a>CCommonDialog – třída
Základní třída pro třídy, které zapouzdřují funkce společná dialogová okna Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCommonDialog : public CDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CCommonDialog::CCommonDialog](#ccommondialog)|Vytvoří `CCommonDialog` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Následující třídy zapouzdřují funkce společná dialogová okna Windows:  
  
- [CFileDialog](../../mfc/reference/cfiledialog-class.md)  
  
- [CFontDialog](../../mfc/reference/cfontdialog-class.md)  
  
- [CColorDialog](../../mfc/reference/ccolordialog-class.md)  
  
- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)  
  
- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)  
  
- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)  
  
- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)  
  
- [COleDialog](../../mfc/reference/coledialog-class.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CCommonDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="ccommondialog"></a>CCommonDialog::CCommonDialog  
 Vytvoří `CCommonDialog` objektu.  
  
```  
explicit CCommonDialog(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Odkazuje na objekt okno nadřazené nebo vlastníka (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke které patří objektu dialogového okna. Pokud je **NULL**, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog) úplné informace.  
  
## <a name="see-also"></a>Viz také  
 [CDialog – třída](../../mfc/reference/cdialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CFileDialog – třída](../../mfc/reference/cfiledialog-class.md)   
 [CFontDialog – třída](../../mfc/reference/cfontdialog-class.md)   
 [CColorDialog – třída](../../mfc/reference/ccolordialog-class.md)   
 [CPageSetupDialog – třída](../../mfc/reference/cpagesetupdialog-class.md)   
 [CPrintDialog – třída](../../mfc/reference/cprintdialog-class.md)   
 [CFindReplaceDialog – třída](../../mfc/reference/cfindreplacedialog-class.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)
