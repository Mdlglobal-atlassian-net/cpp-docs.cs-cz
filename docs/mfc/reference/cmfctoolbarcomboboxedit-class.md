---
title: Cmfctoolbarcomboboxedit – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarComboBoxEdit [MFC], CMFCToolBarComboBoxEdit
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35fa804c7cdcff8a2005a3c91176209e8cc96219
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680171"
---
# <a name="cmfctoolbarcomboboxedit-class"></a>Cmfctoolbarcomboboxedit – třída
Rozhraní používá `CMFCToolBarComboBoxEdit` třídy za účelem vytvoření tlačítka panelu nástrojů, který se chová jako ovládací prvek upravovat pole se seznamem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarComboBoxEdit : public CEdit  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit](#cmfctoolbarcomboboxedit)|Vytvoří `CMFCToolBarComboBoxEdit` objektu.|  
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|Přeloží okno zprávy před odesláním do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkce Windows. (Přepíše [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
  
### <a name="remarks"></a>Poznámky  
 Odvodit třídu z `CMFCToolBarComboBoxEdit` třídy přizpůsobit jeho operace úpravy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cedit –](../../mfc/reference/cedit-class.md)  
  
 [Cmfctoolbarcomboboxedit –](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbarcomboboxbutton.h  
  
##  <a name="cmfctoolbarcomboboxedit"></a>  CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit  
 Vytvoří `CMFCToolBarComboBoxEdit` objektu.  
  
```  
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *– pole se seznamem*  
 Odkaz na [cmfctoolbarcomboboxbutton –](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objekt, který je tlačítko panelu nástrojů obsahující ovládací prvek pole se seznamem.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCToolBarComboBoxEdit` třídy. Tento fragment kódu je součástí [IE demonstrační ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo#5](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarComboBoxButton – třída](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)
