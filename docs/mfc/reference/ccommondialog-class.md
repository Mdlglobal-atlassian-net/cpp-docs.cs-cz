---
title: Ccommondialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6821b7a33339b2a143778172caa7a4a22cb101e
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335912"
---
# <a name="ccommondialog-class"></a>Ccommondialog – třída
Základní třída pro třídy, které zapouzdřují funkce běžných dialogových oken Windows.  
  
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
 Následující třídy zapouzdřují funkce běžných dialogových oken Windows:  
  
- [CFileDialog](../../mfc/reference/cfiledialog-class.md)  
  
- [Cfontdialog –](../../mfc/reference/cfontdialog-class.md)  
  
- [Ccolordialog –](../../mfc/reference/ccolordialog-class.md)  
  
- [Cpagesetupdialog –](../../mfc/reference/cpagesetupdialog-class.md)  
  
- [Cprintdialog –](../../mfc/reference/cprintdialog-class.md)  
  
- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)  
  
- [CFindReplaceDialog.](../../mfc/reference/cfindreplacedialog-class.md)  
  
- [Coledialog –](../../mfc/reference/coledialog-class.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CCommonDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="ccommondialog"></a>  CCommonDialog::CCommonDialog  
 Vytvoří `CCommonDialog` objektu.  
  
```  
explicit CCommonDialog(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Odkazuje na objekt okna nadřazené nebo vlastník (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke které patří objektu dialogového okna. Pokud je hodnota NULL, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog) podrobnější informace.  
  
## <a name="see-also"></a>Viz také  
 [CDialog – třída](../../mfc/reference/cdialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Cfiledialog – třída](../../mfc/reference/cfiledialog-class.md)   
 [Cfontdialog – třída](../../mfc/reference/cfontdialog-class.md)   
 [Ccolordialog – třída](../../mfc/reference/ccolordialog-class.md)   
 [Cpagesetupdialog – třída](../../mfc/reference/cpagesetupdialog-class.md)   
 [Cprintdialog – třída](../../mfc/reference/cprintdialog-class.md)   
 [Cfindreplacedialog – třída](../../mfc/reference/cfindreplacedialog-class.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)
