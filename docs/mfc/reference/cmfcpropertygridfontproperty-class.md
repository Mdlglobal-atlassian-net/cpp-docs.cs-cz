---
title: Třída CMFCPropertyGridFontProperty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e7acda3bf3734a325c7d603489c1305cb63bc3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367611"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty – třída
`CMFCPropertyGridFileProperty` Třída podporuje ovládací prvek položky seznamu vlastnosti, které se otevře dialogové okno Výběr písma.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Vytvoří `CMFCPropertyGridFontProperty` objektu.|  
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCPropertyGridFontProperty::FormatProperty`|Formátuje textové reprezentace hodnotu vlastnosti. (Přepisuje [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|  
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Načte Barva písma, který si uživatel vybere ze dialogové okno písmo.|  
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Načte písmo, které si uživatel vybere ze dialogové okno písmo.|  
|`CMFCPropertyGridFontProperty::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|`CMFCPropertyGridFontProperty::OnClickButton`|Voláno rámcem po kliknutí na tlačítko, který je obsažený ve vlastnosti. (Přepisuje [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridfontproperty"></a>  CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty  
 Vytvoří `CMFCPropertyGridFontProperty` objektu.  
  
```  
CMFCPropertyGridFontProperty(
    const CString& strName,  
    LOGFONT& lf,  
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,  
    LPCTSTR lpszDescr = NULL,  
    DWORD_PTR dwData = 0,  
    COLORREF color = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `strName`  
 Název vlastnosti  
  
 [v] `lf`  
 Struktura logické písma, která určuje atributy písma.  
  
 [v] `dwFontDialogFlags`  
 Styly, které se použijí pro dialogové okno písmo, který se zobrazí po kliknutí na tlačítko Vlastnosti hodnota rozevíracího seznamu. Výchozí hodnota je bitová kombinace (nebo) CF_EFFECTS a CF_SCREENFONTS. Další informace najdete v tématu `Flags` parametr [CHOOSEFONT struktura](http://msdn.microsoft.com/library/windows/desktop/ms646832).  
  
 [v] `lpszDescr`  
 Popis vlastnosti písma. Výchozí hodnota je `NULL`.  
  
 [v] `dwData`  
 Specifické pro aplikaci data, jako třeba celé číslo nebo ukazatel na další data, která souvisí s vlastností. Výchozí hodnota je 0.  
  
 [v] `color`  
 Barva písma. Výchozí hodnota je výchozí barvu.  
  
### <a name="remarks"></a>Poznámky  
 A `CMFCPropertyGridFontProperty` objekt představuje vlastnost písma v ovládacím prvku mřížky písma vlastnost.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCPropertyGridFontProperty` třídy. Tato ukázka je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]  
  
##  <a name="getcolor"></a>  CMFCPropertyGridFontProperty::GetColor  
 Načte Barva písma, který si uživatel vybere ze dialogové okno písmo.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota Barva RGB představující barvy vybraných písma.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont  
 Načte písmo, které si uživatel vybere ze dialogové okno písmo.  
  
```  
LPLOGFONT GetLogFont();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktura, která popisuje vybrané písmo.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty – třída](../../mfc/reference/cmfcpropertygridproperty-class.md)
