---
title: Třída CMFCPropertyGridFileProperty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2b123b5c473c834e958263edb926ef25103d788
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty – třída
`CMFCPropertyGridFileProperty` Třída podporuje vlastnost řízení položky seznamu, které se otevře dialogové okno Výběr souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|Vytvoří `CMFCPropertyGridFileProperty` objektu.|  
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCPropertyGridFileProperty::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|`CMFCPropertyGridFileProperty::OnClickButton`|(Přepisuje [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridfileproperty"></a>  CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty  
 Vytvoří `CMFCPropertyGridFileProperty` objektu.  
  
```  
CMFCPropertyGridFileProperty(
    const CString& strName,  
    BOOL bOpenFileDialog,  
    const CString& strFileName,  
    LPCTSTR lpszDefExt=NULL,  
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,  
    LPCTSTR lpszFilter=NULL,  
    LPCTSTR lpszDescr=NULL,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `strName`  
 Název vlastnosti  
  
 [v] `bOpenFileDialog`  
 `TRUE` Chcete-li spustit **otevřít soubor** dialogové okno; `FALSE` otevřete **uložit soubor** dialogové okno.  
  
 [v] `strFileName`  
 Počáteční název.  
  
 [v] `lpszDefExt`  
 Řetězec, jeden nebo více přípon názvů souborů. Výchozí hodnota je `NULL`.  
  
 [v] `dwFlags`  
 Dialogové okno pole příznaky. Výchozí hodnota je bitovou kombinaci (nebo) `OFN_HIDEREADONLY` a `OFN_OVERWRITEPROMPT`.  
  
 [v] `lpszFilter`  
 Řetězec filtry jeden nebo více souborů. Výchozí hodnota je `NULL`.  
  
 [v] `lpszDescr`  
 Vlastnost popis položky. Výchozí hodnota je `NULL`.  
  
 [v] `dwData`  
 Data specifické pro aplikaci, která je přidružená k položce vlastnost. Například 32bitové celé číslo nebo ukazatel na další data. Výchozí hodnota je 0.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Úplný seznam dostupných příznaků, najdete v části [název otevřeného souboru struktura](https://msdn.microsoft.com/library/ms646839.aspx).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt, který používá konstruktoru `CMFCPropertyGridFileProperty` třídy. Tato ukázka je součástí [Visual Studio Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty – třída](../../mfc/reference/cmfcpropertygridproperty-class.md)
