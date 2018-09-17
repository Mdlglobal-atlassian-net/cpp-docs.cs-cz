---
title: Cmfcwindowsmanagerdialog – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 71c85d3061da7cf4c87abef9549542900e962f64
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707002"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>Cmfcwindowsmanagerdialog – třída
`CMFCWindowsManagerDialog` Objektu umožňuje uživateli spravovat podřízená okna MDI v aplikaci MDI.  
  
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
 `CMFCWindowsManagerDialog` Obsahuje seznam podřízených oken MDI, které jsou právě otevřeny v aplikaci. Uživatele můžete ručně řídit stav podřízených oken MDI pomocí dialogovému oknu.  
  
 `CMFCWindowsManagerDialog` je vložena do [CMDIFrameWndEx – třída](../../mfc/reference/cmdiframewndex-class.md). `CMFCWindowsManagerDialog` Se nejedná o třídu, která byste měli vytvořit ručně. Místo toho zavolejte funkci [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), potom vytvoří a zobrazí `CMFCWindowsManagerDialog` objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCWindowsManagerDialog` objektu voláním `CMDIFrameWndEx::ShowWindowsDialog`. Tento fragment kódu je součástí [Visual Studio demonstrační ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [Cmfcwindowsmanagerdialog –](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxWindowsManagerDialog.h  
  
##  <a name="cmfcwindowsmanagerdialog"></a>  CMFCWindowsManagerDialog::CMFCWindowsManagerDialog  
 Vytvoří [cmfcwindowsmanagerdialog –](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) objektu.  
  
```  
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,  
    BOOL bHelpButton = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
*pMDIFrame*<br/>
[in] Ukazatel na okno nadřazené nebo vlastníka.  
  
*bHelpButton*<br/>
[in] Parametr logické hodnoty, která určuje, zda se zobrazí rozhraní framework **pomáhají** tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o vzhledu najdete v tématu [správce vizualizace](../../mfc/visualization-manager.md).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWndEx – třída](../../mfc/reference/cmdiframewndex-class.md)
