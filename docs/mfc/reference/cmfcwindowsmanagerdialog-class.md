---
title: Třída CMFCWindowsManagerDialog | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b5ae46280a537577ae3e3ab0fbdf73f2e449e58
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042094"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog – třída
`CMFCWindowsManagerDialog` Objektu umožňuje uživatelům spravovat podřízených oken MDI v aplikaci MDI.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCWindowsManagerDialog : public CDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|Vytvoří `CMFCWindowsManagerDialog` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCWindowsManagerDialog` Obsahuje seznam podřízených oken MDI, které jsou právě otevřeny v aplikaci. Uživatele můžete ručně řídit stav podřízených oken MDI pomocí tohoto dialogového okna.  
  
 `CMFCWindowsManagerDialog` je vložena do [CMDIFrameWndEx Class](../../mfc/reference/cmdiframewndex-class.md). `CMFCWindowsManagerDialog` Není třídu, která byste měli vytvořit ručně. Místo toho zavolejte funkci [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), a vytvoří a zobrazí `CMFCWindowsManagerDialog` objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCWindowsManagerDialog` objekt voláním `CMDIFrameWndEx::ShowWindowsDialog`. Tento fragment kódu je součástí [Visual Studio Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxWindowsManagerDialog.h  
  
##  <a name="cmfcwindowsmanagerdialog"></a>  CMFCWindowsManagerDialog::CMFCWindowsManagerDialog  
 Vytvoří [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) objektu.  
  
```  
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,  
    BOOL bHelpButton = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pMDIFrame*  
 Ukazatel na okno nadřazené nebo vlastníka.  
  
 [v] *bHelpButton*  
 Parametr typu Boolean, která určuje, zda se má zobrazit rozhraní **pomoci** tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o správcích visual najdete v tématu [správce vizualizace](../../mfc/visualization-manager.md).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWndEx – třída](../../mfc/reference/cmdiframewndex-class.md)
