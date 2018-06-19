---
title: CDataExchange – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDataExchange
- AFXWIN/CDataExchange
- AFXWIN/CDataExchange::CDataExchange
- AFXWIN/CDataExchange::Fail
- AFXWIN/CDataExchange::PrepareCtrl
- AFXWIN/CDataExchange::PrepareEditCtrl
- AFXWIN/CDataExchange::PrepareOleCtrl
- AFXWIN/CDataExchange::m_bSaveAndValidate
- AFXWIN/CDataExchange::m_pDlgWnd
dev_langs:
- C++
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03d68359d075efd72a1bf1907daa71e74110fa28
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368934"
---
# <a name="cdataexchange-class"></a>CDataExchange – třída
Podporuje výměna dialogových dat (DDX) a používá třídy Microsoft Foundation rutiny ověření (DDV) dat dialogového okna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDataExchange  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDataExchange::CDataExchange](#cdataexchange)|Vytvoří `CDataExchange` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDataExchange::Fail](#fail)|Voláno, když se ověřování nezdaří. Obnoví fokus na předchozí ovládacího prvku a vyvolá výjimku.|  
|[CDataExchange::PrepareCtrl](#preparectrl)|Připraví daný ovládací prvek pro data systému exchange nebo ověření. Použití pro ovládací prvky nonedit.|  
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|Připraví zadané textové pole pro data systému exchange nebo ověření.|  
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|Připravuje daný ovládací prvek OLE výměny dat nebo ověření. Použití pro ovládací prvky nonedit.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|Příznak směru DDX a DDV.|  
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|Dialogové okno nebo okno, kde data exchange probíhá.|  
  
## <a name="remarks"></a>Poznámky  
 `CDataExchange` nemá základní třídu.  
  
 Tuto třídu použít, pokud píšete rutiny výměny dat pro vlastní datové typy nebo ovládací prvky, nebo pokud píšete vlastní rutiny ověřování dat. Další informace o psaní vlastní rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [dialogová okna](../../mfc/dialog-boxes.md).  
  
 A `CDataExchange` objekt poskytuje informace o kontextu, které jsou potřebné pro DDX a DDV přijmout umístit. Příznak `m_bSaveAndValidate` je **FALSE** při DDX slouží k vyplnění počáteční hodnoty ovládací prvky dialogového okna z datových členů. Příznak `m_bSaveAndValidate` je **TRUE** při DDX používá k nastavení aktuální hodnoty ovládací prvky dialogového okna do datových členů a když DDV slouží k ověření datových hodnot. Pokud DDV ověření selže, bude postup DDV zobrazit okno se zprávou vysvětlením vstupních chyb. Postup DDV pak zavolá **nezdaří** obnovit fokus do ovládacího prvku problematické a způsobí výjimku zastavit proces ověření.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CDataExchange`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cdataexchange"></a>  CDataExchange::CDataExchange  
 Volání této funkce člen k vytvoření `CDataExchange` objektu.  
  
```  
CDataExchange(
    CWnd* pDlgWnd,  
    BOOL bSaveAndValidate);
```  
  
### <a name="parameters"></a>Parametry  
 *pDlgWnd*  
 Ukazatel do nadřazeného okna, který obsahuje ovládací prvek. To je obvykle [CDialog](../../mfc/reference/cdialog-class.md)-odvozené objektu.  
  
 `bSaveAndValidate`  
 Pokud **TRUE**, tento objekt ověří data a pak zapíše data z ovládacích prvků do členů. Pokud **FALSE**, tento objekt se přesun dat z členy do ovládacích prvků.  
  
### <a name="remarks"></a>Poznámky  
 Vytvořit `CDataExchange` objekt sami k uložení doplňující informace v objektu dat systému exchange mají být předána do vaší okno [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]  
  
##  <a name="fail"></a>  CDataExchange::Fail  
 Rozhraní framework volá funkci tento člen, pokud selže ověření (DDV) operace dat dialogové okno.  
  
```  
void Fail();
```  
  
### <a name="remarks"></a>Poznámky  
 **Selhání** obnoví fokus a výběr do ovládacího prvku, jejichž ověření se nezdařilo (Pokud je ovládací prvek obnovit). **Selhání** poté vyvolá výjimku typu [CUserException](../../mfc/reference/cuserexception-class.md) zastavit proces ověření. Výjimka způsobí, že se zprávou vysvětlením zobrazí chyba. Po ověření DDV nezdaří, uživatel může znovu zadat dat v ovládacím prvku problematické.  
  
 Můžete volat implementors vlastní rutiny DDV **nezdaří** z jejich rutiny, když se ověřování nezdaří.  
  
 Další informace o psaní vlastní rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [dialogové okno pole témata](../../mfc/dialog-boxes.md).  
  
##  <a name="m_bsaveandvalidate"></a>  CDataExchange::m_bSaveAndValidate  
 Tento příznak určuje směr operace dialogové okno dat systému exchange (DDX).  
  
```  
BOOL m_bSaveAndValidate;  
```  
  
### <a name="remarks"></a>Poznámky  
 Příznak je nenulové hodnoty v Pokud `CDataExchange` objektu je používána pro přesun dat z ovládací prvky dialogového okna pro členy třídy dialogového okna dat po uživatel upravuje ovládacích prvků. Příznak je nula. Pokud se používá objekt se inicializovat ovládací prvky dialogového okna z datové členy třídy dialogového okna.  
  
 Příznak je také nenulové hodnoty při ověřování dat dialogového okna (DDV).  
  
 Další informace o psaní vlastní rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [dialogové okno pole témata](../../mfc/dialog-boxes.md).  
  
##  <a name="m_pdlgwnd"></a>  CDataExchange::m_pDlgWnd  
 Obsahuje odkazy [CWnd](../../mfc/reference/cwnd-class.md) objekt, pro které dialogové okno ověření (DDV) nebo výměna dat (DDX) probíhá.  
  
```  
CWnd* m_pDlgWnd;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento objekt je obvykle [CDialog](../../mfc/reference/cdialog-class.md) objektu. Implementors vlastní rutiny DDX a DDV vám pomůže získat přístup k dialogového okna, který obsahuje ovládací prvky jsou provozu na tento ukazatel.  
  
 Další informace o psaní vlastní rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [dialogové okno pole témata](../../mfc/dialog-boxes.md).  
  
##  <a name="preparectrl"></a>  CDataExchange::PrepareCtrl  
 Rozhraní framework volá tuto funkci člen Příprava daný ovládací prvek pro výměna dialogových dat (DDX) a ověřování (DDV).  
  
```  
HWND PrepareCtrl(int nIDC);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDC`  
 ID ovládacího prvku připravit pro DDX a DDV.  
  
### <a name="return-value"></a>Návratová hodnota  
 `HWND` Připraveném pro DDX a DDV ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Použít [PrepareEditCtrl](#prepareeditctrl) místo pro ovládacích prvcích pro úpravy; tuto funkci můžete používat člena pro všechny ostatní ovládací prvky.  
  
 Příprava se skládá z ukládání ovládacího prvku `HWND` v `CDataExchange` třídy. Rozhraní používá k obnovení zaměřená na dříve cílených ovládací prvek v případě selhání DDX a DDV tento popisovač.  
  
 Implementors vlastní rutiny DDX a DDV by měly volat `PrepareCtrl` pro všechny ovládací prvky bez úprav, pro které jsou výměna dat prostřednictvím DDX nebo ověřování dat prostřednictvím DDV.  
  
 Další informace o psaní vlastní rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [dialogové okno pole témata](../../mfc/dialog-boxes.md).  
  
##  <a name="prepareeditctrl"></a>  CDataExchange::PrepareEditCtrl  
 Rozhraní framework volá tuto funkci člen Příprava zadané textové pole pro výměna dialogových dat (DDX) a ověřování (DDV).  
  
```  
HWND PrepareEditCtrl(int nIDC);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDC`  
 ID ovládacích prvků pro úpravy být připraveny DDX a DDV.  
  
### <a name="return-value"></a>Návratová hodnota  
 `HWND` Ovládacích prvků pro úpravy připraveném pro DDX a DDV.  
  
### <a name="remarks"></a>Poznámky  
 Použití [PrepareCtrl](#preparectrl) místo pro všechny ovládací prvky bez úprav.  
  
 Příprava se skládá ze dvou akcí. První, `PrepareEditCtrl` ukládá ovládacího prvku `HWND` v `CDataExchange` třídy. Rozhraní používá k obnovení zaměřená na dříve cílených ovládací prvek v případě selhání DDX a DDV tento popisovač. Druhý, `PrepareEditCtrl` nastaví příznak `CDataExchange` třída, která označuje, že ovládací prvek, jejichž data se vyměňují nebo ověřit je ovládací prvek upravit.  
  
 Implementors vlastní rutiny DDX a DDV by měly volat `PrepareEditCtrl` pro všechny ovládací prvky, pro které jsou výměna dat prostřednictvím DDX nebo ověřování dat prostřednictvím DDV úprav.  
  
 Další informace o psaní vlastní rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [dialogové okno pole témata](../../mfc/dialog-boxes.md).  
  
##  <a name="prepareolectrl"></a>  CDataExchange::PrepareOleCtrl  
 Rozhraní framework volá tuto funkci člen připravte daný ovládací prvek OLE výměna dialogových dat (DDX) a ověřování (DDV).  
  
```  
COleControlSite* PrepareOleCtrl(int nIDC);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDC`  
 ID ovládacího prvku OLE připravit pro DDX a DDV.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na ovládací prvek webu OLE.  
  
### <a name="remarks"></a>Poznámky  
 Použití [PrepareEditCtrl](#prepareeditctrl) místo pro ovládacích prvcích pro úpravy nebo [PrepareCtrl](#preparectrl) pro všechny ostatní ovládací prvky jiných než OLE.  
  
 Implementors vlastní rutiny DDX a DDV by měly volat `PrepareOleCtrl` pro všechny ovládací prvky OLE, pro které jsou výměna dat prostřednictvím DDX nebo ověřování dat prostřednictvím DDV.  
  
 Další informace o psaní vlastní rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [dialogové okno pole témata](../../mfc/dialog-boxes.md).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC VIEWEX](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)   
 [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)

