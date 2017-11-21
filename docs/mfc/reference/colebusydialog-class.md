---
title: "Třída COleBusyDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
dev_langs: C++
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 968c8cefb9dd9be853ceeb8bd98d631e884ad1c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="colebusydialog-class"></a>COleBusyDialog – třída
Použít pro dialogových oken OLE serveru neodpovídá nebo zaneprázdněný Server.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleBusyDialog : public COleDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|Vytvoří `COleBusyDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleBusyDialog::DoModal](#domodal)|Zobrazí dialogové okno OLE Server zaneprázdněn.|  
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Určuje volby provedené v dialogovém okně.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleBusyDialog::m_bz](#m_bz)|Struktura typu **OLEUIBUSY** , řídí chování dialogového okna.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvoření objektu třídy `COleBusyDialog` když chcete volat tyto dialogy. Po `COleBusyDialog` objekt byl vytvořen, můžete použít [m_bz](#m_bz) struktura k chybě při inicializaci hodnoty nebo stavy, které ovládacích prvků v dialogovém okně. `m_bz` Struktura je typu **OLEUIBUSY**. Další informace o používání této třídy dialogového okna, najdete v článku [DoModal](#domodal) – členská funkce.  
  
> [!NOTE]
>  Kód aplikace generované v Průvodci kontejneru používá tuto třídu.  
  
 Další informace najdete v tématu [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) struktura ve Windows SDK.  
  
 Další informace o dialogových oknech OLE specifické, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleBusyDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxodlgs.h  
  
##  <a name="colebusydialog"></a>COleBusyDialog::COleBusyDialog  
 Tato funkce pouze vytvoří `COleBusyDialog` objektu.  
  
```  
explicit COleBusyDialog(
    HTASK htaskBusy,  
    BOOL bNotResponding = FALSE,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *htaskBusy*  
 Zpracování úlohy serveru, který je zaneprázdněn.  
  
 *bNotResponding*  
 Pokud **TRUE**, volání dialogové okno neodpovídá místo dialogové okno Server zaneprázdněn. Pomocí jiné volby slov v dialogovém okně neodpovídá se poněkud liší od slov v dialogovém okně zaneprázdněný Server a je zakázáno na tlačítko Storno.  
  
 `dwFlags`  
 Vytvoření příznak. Může obsahovat nula nebo více z následujících hodnot v kombinaci s operátorem bitový operátor OR:  
  
- **BZ_DISABLECANCELBUTTON** zakázat tlačítko Zrušit při volání metody dialogové okno.  
  
- **BZ_DISABLESWITCHTOBUTTON** zakázat tlačítko přepínače při volání metody dialogové okno.  
  
- **BZ_DISABLERETRYBUTTON** zakázat tlačítko Opakovat při volání metody dialogové okno.  
  
 `pParentWnd`  
 Odkazuje na objekt okno nadřazené nebo vlastníka (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je **NULL**, okno nadřazeného objektu dialogové okno bude nastaveno na hlavní okno aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zobrazit dialogové okno, volejte [DoModal](#domodal).  
  
 Další informace najdete v tématu [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) struktura ve Windows SDK.  
  
##  <a name="domodal"></a>COleBusyDialog::DoModal  
 Volání této funkce můžete zobrazit dialogové okno OLE Server zaneprázdněn nebo Server neodpovídá.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav dokončení pro dialogové okno. Jedna z následujících hodnot:  
  
- **IDOK** Pokud úspěšně zobrazí dialogové okno.  
  
- **IDCANCEL** Pokud uživatel zrušil dialogové okno.  
  
- **IDABORT** Pokud došlo k chybě. Pokud **IDABORT** se volání vrátí, `COleDialog::GetLastError` – členská funkce získat další informace o typu Chyba, že došlo k chybě. Seznam možné chyby, najdete v článku [OleUIBusy](http://msdn.microsoft.com/library/windows/desktop/ms680125) funkce ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k chybě při inicializaci různých dialogové okno Ovládací prvky nastavením členy [m_bz](#m_bz) struktura, bude třeba provést před voláním `DoModal`, ale po objektu dialogového okna je vytvořený.  
  
 Pokud `DoModal` vrátí **IDOK**, můžete volat jiné členské funkce načíst nastavení nebo informace, které se vstup uživatelem na dialogové okno.  
  
##  <a name="getselectiontype"></a>COleBusyDialog::GetSelectionType  
 Volání této funkce se získat typ výběr volená uživatelem v dialogovém okně Server zaneprázdněn.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Typ provedeného výběru.  
  
### <a name="remarks"></a>Poznámky  
 Návratový typ hodnoty jsou určené **výběr** typ výčtu deklarované v `COleBusyDialog` – třída.  
  
```  
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```  
  
 Postupujte podle stručný popis těchto hodnot:  
  
- **COleBusyDialog::switchTo** klepnutí na přepínač na tlačítko.  
  
- **COleBusyDialog::retry** klepnutí na tlačítko Opakovat.  
  
- **COleBusyDialog::callUnblocked** volání k aktivaci serveru je nyní odblokování.  
  
##  <a name="m_bz"></a>COleBusyDialog::m_bz  
 Struktura typu **OLEUIBUSY** používat k ovládání chování serveru zaneprázdněn dialogových oken.  
  
```  
OLEUIBUSY m_bz;  
```  
  
### <a name="remarks"></a>Poznámky  
 Členové této struktury se dá změnit přímo nebo prostřednictvím členských funkcí.  
  
 Další informace najdete v tématu [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) struktura ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)
