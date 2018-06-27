---
title: Třída CFolderPickerDialog | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
dev_langs:
- C++
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ded586e6d8ad5252d73e0972424915d174b8b1f3
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956516"
---
# <a name="cfolderpickerdialog-class"></a>CFolderPickerDialog – třída
Třída CFolderPickerDialog implementuje CFileDialog v režimu výběr složky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFolderPickerDialog : public CFileDialog;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFolderPickerDialog:: ~ CFolderPickerDialog](#cfolderpickerdialog__~cfolderpickerdialog)|Destruktor.|  
|[CFolderPickerDialog::CFolderPickerDialog](#cfolderpickerdialog)|Konstruktor|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [CFileDialog](../../mfc/reference/cfiledialog-class.md)  
  
 `CFolderPickerDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="cfolderpickerdialog"></a>  CFolderPickerDialog::CFolderPickerDialog  
 Konstruktor  
  
```  
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL,  
    DWORD dwSize = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszFolder*  
 Počáteční složka.  
  
 *dwFlags*  
 Kombinace jeden nebo více příznaky, které vám umožní přizpůsobit dialogové okno.  
  
 *pParentWnd*  
 Ukazatel na okno nadřazené nebo vlastníka objektu pole dialogového okna.  
  
 *dwSize*  
 Velikost strukturu název otevřeného souboru.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="_dtorcfolderpickerdialog"></a>  CFolderPickerDialog:: ~ CFolderPickerDialog  
 Destruktor.  
  
```  
virtual ~CFolderPickerDialog();
```  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
