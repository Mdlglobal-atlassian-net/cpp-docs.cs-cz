---
title: Třída CMFCRibbonCustomizeDialog | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e693a0e6a2353693f676ed0d63d7087d3e57455
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040896"
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog – třída
Zobrazí na pásu karet **přizpůsobit** stránky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|Vytvoří `CMFCRibbonCustomizeDialog` objektu.|  
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCRibbonCustomizeDialog::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
  
## <a name="remarks"></a>Poznámky  
 MFC vytvoří tato třída automaticky, pokud není zpracovat zprávu AFX_WM_ON_RIBBON_CUSTOMIZE, nebo pokud vrátíte 0 od obslužné rutiny zpráv.  
  
 Pokud chcete pomocí této třídy v aplikaci můžete zobrazit na pásu karet **přizpůsobit** dialogové okno pole, stačí vytvořit instanci a volání `DoModal` metoda.  
  
 Vzhledem k tomu, že tato třída je odvozený od [CMFCPropertySheet třída](../../mfc/reference/cmfcpropertysheet-class.md), můžete přidat vlastní stránky pomocí `CMFCPropertySheet` rozhraní API.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
 [CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribboncustomizedialog.h  
  
##  <a name="cmfcribboncustomizedialog"></a>  CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog  
 Vytvoří `CMFCRibbonCustomizeDialog` objektu.  
  
```  
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,  
    CMFCRibbonBar* pRibbon);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pWndParent*  
 Ukazatel do nadřazeného okna (obvykle hlavního rámce).  
  
 [v] *pRibbon*  
 Ukazatel `CMFCRibbonBar` , který má být přizpůsobit.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCRibbonCustomizeDialog` objektu.  
  
 [!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]  
  
### <a name="remarks"></a>Poznámky  
 V konstruktoru vytvoří [CMFCRibbonCustomizePropertyPage třída](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) objektu a přidá ji do kolekce stránky vlastností.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
