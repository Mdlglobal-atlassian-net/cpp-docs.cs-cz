---
title: "Třída COleLinksDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9b998cc18ac0c357b57bc841f6db13700b078063
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="colelinksdialog-class"></a>COleLinksDialog – třída
Používá se pro dialogové okno OLE upravit propojení.  
  
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
|[COleLinksDialog::DoModal](#domodal)|Zobrazí dialogové okno OLE upravit propojení.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleLinksDialog::m_el](#m_el)|Struktura typu **OLEUIEDITLINKS** , řídí chování dialogového okna.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvoření objektu třídy `COleLinksDialog` když chcete volat tohoto dialogového okna. Po `COleLinksDialog` objekt byl vytvořen, můžete použít [m_el](#m_el) struktura k chybě při inicializaci hodnoty nebo stavy, které ovládacích prvků v dialogovém okně. `m_el` Struktura je typu **OLEUIEDITLINKS**. Další informace o používání této třídy dialogového okna, najdete v článku [DoModal](#domodal) – členská funkce.  
  
> [!NOTE]
>  Kód aplikace generované v Průvodci kontejneru používá tuto třídu.  
  
 Další informace najdete v tématu [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) struktura ve Windows SDK.  
  
 Další informace týkající se konkrétní OLE dialogových oken, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleLinksDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxodlgs.h  
  
##  <a name="domodal"></a>COleLinksDialog::DoModal  
 Zobrazí dialogové okno OLE upravit propojení.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav dokončení pro dialogové okno. Jedna z následujících hodnot:  
  
- **IDOK** Pokud úspěšně zobrazí dialogové okno.  
  
- **IDCANCEL** Pokud uživatel zrušil dialogové okno.  
  
- **IDABORT** Pokud došlo k chybě. Pokud **IDABORT** se volání vrátí, `COleDialog::GetLastError` – členská funkce získat další informace o typu Chyba, že došlo k chybě. Seznam možné chyby, najdete v článku [OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) funkce ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k chybě při inicializaci různých dialogové okno Ovládací prvky nastavením členy [m_el](#m_el) struktura, měli byste tak provést před voláním `DoModal`, ale po objektu dialogového okna je vytvořený.  
  
##  <a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog  
 Vytvoří `COleLinksDialog` objektu.  
  
```  
COleLinksDialog (
    COleDocument* pDoc,  
    CView* pView,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDoc`  
 Body OLE dokumentu, který obsahuje odkazy k provádění úprav.  
  
 `pView`  
 Odkazuje na aktuální zobrazení na `pDoc`.  
  
 `dwFlags`  
 Vytvoření příznak, který obsahuje buď 0 nebo **ELF_SHOWHELP** k určení, zda na tlačítko Nápověda se zobrazí, když se zobrazí dialogové okno.  
  
 `pParentWnd`  
 Odkazuje na objekt okno nadřazené nebo vlastníka (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je **NULL**, nadřazeného okna dialogového okna nastavena na hlavní okno aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se vytvoří pouze `COleLinksDialog` objektu. Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal) funkce.  
  
##  <a name="m_el"></a>COleLinksDialog::m_el  
 Struktura typu **OLEUIEDITLINKS** používat k ovládání chování dialogové okno Upravit propojení.  
  
```  
OLEUIEDITLINKS m_el;  
```  
  
### <a name="remarks"></a>Poznámky  
 Členy této struktury lze změnit buď přímo nebo prostřednictvím členských funkcí.  
  
 Další informace najdete v tématu [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) struktura ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)
