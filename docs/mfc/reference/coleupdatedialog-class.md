---
title: Coleupdatedialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f522635c170af784b5bd9f2bb7011fd51e345b3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211605"
---
# <a name="coleupdatedialog-class"></a>Coleupdatedialog – třída
Používá pro zvláštní případ dialogového okna upravení odkazů OLE, která se má použít, když potřebujete aktualizovat pouze existující propojené nebo vložené objekty v dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleUpdateDialog : public COleLinksDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|Vytvoří `COleUpdateDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleUpdateDialog::DoModal](#domodal)|Zobrazí **upravit odkazy** dialogové okno v režimu aktualizace.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o dialogových oken OLE konkrétní, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [Ccommondialog –](../../mfc/reference/ccommondialog-class.md)  
  
 [Coledialog –](../../mfc/reference/coledialog-class.md)  
  
 [Colelinksdialog –](../../mfc/reference/colelinksdialog-class.md)  
  
 `COleUpdateDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxodlgs.h  
  
##  <a name="coleupdatedialog"></a>  COleUpdateDialog::COleUpdateDialog  
 Vytvoří `COleUpdateDialog` objektu.  
  
```  
explicit COleUpdateDialog(
    COleDocument* pDoc,  
    BOOL bUpdateLinks = TRUE,  
    BOOL bUpdateEmbeddings = FALSE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pDoc*  
 Ukazuje na dokument obsahující odkazy, které mohou vyžadovat aktualizaci.  
  
 *bUpdateLinks*  
 Příznak, který určuje, zda má být aktualizován jsou propojené objekty.  
  
 *bUpdateEmbeddings*  
 Příznak, který určuje, zda má být aktualizován jsou vložené objekty.  
  
 *pParentWnd*  
 Odkazuje na objekt okna nadřazené nebo vlastník (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je hodnota NULL, nastaví se nadřazené okno dialogového okna do hlavního okna aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce vytvoří pouze `COleUpdateDialog` objektu. Chcete-li zobrazit dialogové okno, zavolejte [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Tato třída by měla být použita místo `COleLinksDialog` kdy budete chtít aktualizovat pouze existující propojené nebo vložené položky.  
  
##  <a name="domodal"></a>  COleUpdateDialog::DoModal  
 Zobrazí dialogové okno Upravit odkazy pole v aktualizaci režimu.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav dokončení pro dialogové okno. Jeden z následujících hodnot:  
  
- IDOK, pokud bylo úspěšně vráceno dialogových oken.  
  
- IDCANCEL Pokud žádná z položek propojené nebo vložené v aktuálním dokumentu je třeba aktualizovat.  
  
- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, zavolejte [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) členská funkce, chcete-li získat další informace o typu chyby, ke které došlo. Seznam možných chyb, najdete v článku [OleUIEditLinks](/windows/desktop/api/oledlg/nf-oledlg-oleuieditlinksa) funkce v sadě Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud uživatel vybere tlačítko Storno, se aktualizují všechny odkazy a/nebo vložené části.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky knihovny MFC OCLIENT](../../visual-cpp-samples.md)   
 [Colelinksdialog – třída](../../mfc/reference/colelinksdialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleLinksDialog – třída](../../mfc/reference/colelinksdialog-class.md)
