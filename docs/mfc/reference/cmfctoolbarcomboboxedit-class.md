---
title: Třída CMFCToolBarComboBoxEdit | Microsoft Docs
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
ms.openlocfilehash: d541702d73befedab72ad7b130b56a125a5817aa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376303"
---
# <a name="cmfctoolbarcomboboxedit-class"></a>CMFCToolBarComboBoxEdit – třída
Rozhraní používá `CMFCToolBarComboBoxEdit` třídy za účelem vytvoření tlačítka panelu nástrojů, který se chová jako prvek upravitelné pole se seznamem.  
  
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
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|Přeloží zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. (Přepisuje [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
  
### <a name="remarks"></a>Poznámky  
 Odvození třídy z `CMFCToolBarComboBoxEdit` třídy pro přizpůsobení jeho operací upravit.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbarcomboboxbutton.h  
  
##  <a name="cmfctoolbarcomboboxedit"></a>  CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit  
 Vytvoří `CMFCToolBarComboBoxEdit` objektu.  
  
```  
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `combo`  
 Odkaz na [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objekt, který je tlačítka panelu nástrojů, který obsahuje prvek pole se seznamem.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCToolBarComboBoxEdit` třídy. Tento fragment kódu je součástí [IE Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo#5](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarComboBoxButton – třída](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)
