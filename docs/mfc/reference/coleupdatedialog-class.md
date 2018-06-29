---
title: Třída COleUpdateDialog | Microsoft Docs
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
ms.openlocfilehash: c0208a24b69c1884d72c0ae525ce95b3d3258271
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079971"
---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog – třída
Použít pro ve speciálním případě dialogových oken OLE upravit propojení, která se má použít, když potřebujete aktualizovat pouze existující propojené nebo vložené objekty v dokumentu.  
  
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
|[COleUpdateDialog::DoModal](#domodal)|Zobrazí **upravit propojení** dialogové okno v režimu aktualizace.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace týkající se konkrétní OLE dialogových oken, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
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
 Odkazuje na dokument obsahující odkazy, které mohou vyžadovat aktualizaci.  
  
 *bUpdateLinks*  
 Příznak, který určuje, jestli propojené objekty se mají aktualizovat.  
  
 *bUpdateEmbeddings*  
 Příznak, který určuje, jestli vložené objekty se mají aktualizovat.  
  
 *pParentWnd*  
 Odkazuje na objekt okno nadřazené nebo vlastníka (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je **NULL**, nadřazeného okna dialogového okna bude nastavena pro hlavní okno aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se vytvoří pouze `COleUpdateDialog` objektu. Chcete-li zobrazit dialogové okno, volejte [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Tato třída slouží místo `COleLinksDialog` Pokud chcete aktualizovat existující pouze propojené nebo vložené položky.  
  
##  <a name="domodal"></a>  COleUpdateDialog::DoModal  
 Zobrazí dialogové okno Upravit propojení pole v aktualizaci režimu.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav dokončení pro dialogové okno. Jedna z následujících hodnot:  
  
- **IDOK** úspěšně vrácen dialogové okno.  
  
- **IDCANCEL** Pokud žádná z propojené nebo vložené položky v aktuálním dokumentu vyžadovat aktualizaci.  
  
- **IDABORT** Pokud došlo k chybě. Pokud **IDABORT** se volání vrátí, [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) – členská funkce získat další informace o typu Chyba, že došlo k chybě. Seznam možné chyby, najdete v článku [OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) funkce ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud uživatel vybere na tlačítko Storno, jsou aktualizovány všechny odkazy nebo vložené části.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC OCLIENT](../../visual-cpp-samples.md)   
 [COleLinksDialog – třída](../../mfc/reference/colelinksdialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleLinksDialog – třída](../../mfc/reference/colelinksdialog-class.md)
