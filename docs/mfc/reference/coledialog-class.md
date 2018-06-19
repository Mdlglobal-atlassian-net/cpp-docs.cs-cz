---
title: Třída COleDialog | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
dev_langs:
- C++
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c13b5d0a3bb30e08eaaeb0250da7deef692a66d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368657"
---
# <a name="coledialog-class"></a>COleDialog – třída
Poskytuje funkce, které jsou společné pro dialogová okna pro OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDialog::GetLastError](#getlasterror)|Získá kód chyby vrácený dialogové okno.|  
  
## <a name="remarks"></a>Poznámky  
 Knihovny Microsoft Foundation Class poskytuje několik třídy odvozené od třídy `COleDialog`:  
  
- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)  
  
- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)  
  
- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)  
  
- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)  
  
- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)  
  
- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)  
  
- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)  
  
- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)  
  
 Další informace o dialogových oknech OLE specifické, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `COleDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxodlgs.h  
  
##  <a name="getlasterror"></a>  COleDialog::GetLastError  
 Volání `GetLastError` – členská funkce získat další informace o chybě při `DoModal` vrátí **IDABORT**.  
  
```  
UINT GetLastError() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kódů chyb vrácených nástrojem `GetLastError` závisí na konkrétní dialogu zobrazí.  
  
### <a name="remarks"></a>Poznámky  
 Najdete v článku `DoModal` – členská funkce v odvozených třídách informace o specifické chybové zprávy.  
  
## <a name="see-also"></a>Viz také  
 [CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



