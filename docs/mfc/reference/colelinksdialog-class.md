---
title: Colelinksdialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
dev_langs:
- C++
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5dd17c0541b573cba40146c55b46d14143209c87
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853875"
---
# <a name="colelinksdialog-class"></a>Colelinksdialog – třída
Používá se pro dialogové okno úpravy odkazů OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleLinksDialog : public COleDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|Vytvoří `COleLinksDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleLinksDialog::DoModal](#domodal)|Zobrazí dialogové okno úpravy odkazů OLE.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleLinksDialog::m_el](#m_el)|Struktura typu OLEUIEDITLINKS, které ovládá chování dialogového okna.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvoření objektu třídy `COleLinksDialog` kdy chcete volat dialogovému oknu. Po `COleLinksDialog` objekt byl vytvořen, můžete použít [m_el](#m_el) struktury k inicializaci hodnoty nebo stavy ovládacích prvků v dialogovém okně. `m_el` Struktury je typu OLEUIEDITLINKS. Další informace o použití této třídy dialogového okna, najdete v článku [DoModal](#domodal) členskou funkci.  
  
> [!NOTE]
>  Generované průvodcem kontejneru kódu aplikace používá tuto třídu.  
  
 Další informace najdete v tématu [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) struktura v sadě Windows SDK.  
  
 Další informace o dialogových oken OLE konkrétní, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [Ccommondialog –](../../mfc/reference/ccommondialog-class.md)  
  
 [Coledialog –](../../mfc/reference/coledialog-class.md)  
  
 `COleLinksDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxodlgs.h  
  
##  <a name="domodal"></a>  COleLinksDialog::DoModal  
 Zobrazí dialogové okno úpravy odkazů OLE.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav dokončení pro dialogové okno. Jeden z následujících hodnot:  
  
- IDOK, pokud úspěšně zobrazí dialogové okno.  
  
- IDCANCEL, pokud uživatel zrušil dialogové okno.  
  
- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, zavolejte `COleDialog::GetLastError` členská funkce, chcete-li získat další informace o typu chyby, ke které došlo. Seznam možných chyb, najdete v článku [OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) funkce v sadě Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete inicializovat různé ovládací prvky dialogového okna pole tak, že nastavíte členy [m_el](#m_el) strukturu, proveďte to před voláním `DoModal`, ale po vytvoření objektu dialogového okna.  
  
##  <a name="colelinksdialog"></a>  COleLinksDialog::COleLinksDialog  
 Vytvoří `COleLinksDialog` objektu.  
  
```  
COleLinksDialog (
    COleDocument* pDoc,  
    CView* pView,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pDoc*  
 Ukazuje na dokument OLE, který obsahuje odkazy na Upravit.  
  
 *pView*  
 Odkazuje na aktuální zobrazení na *pDoc*.  
  
 *dwFlags*  
 Vytvoření příznak, který obsahuje 0 nebo ELF_SHOWHELP k určení, zda se zobrazí tlačítko Nápověda, když se zobrazí dialogové okno.  
  
 *pParentWnd*  
 Odkazuje na objekt okna nadřazené nebo vlastník (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je hodnota NULL, nadřazené okno dialogového okna je nastaveno na hlavního okna aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce vytvoří pouze `COleLinksDialog` objektu. Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal) funkce.  
  
##  <a name="m_el"></a>  COleLinksDialog::m_el  
 Struktura typu OLEUIEDITLINKS používat k ovládání chování dialogovém okně Upravit odkazy.  
  
```  
OLEUIEDITLINKS m_el;  
```  
  
### <a name="remarks"></a>Poznámky  
 Přímo nebo prostřednictvím členské funkce, lze upravit členy této struktury.  
  
 Další informace najdete v tématu [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) struktura v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Coledialog – třída](../../mfc/reference/coledialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)
