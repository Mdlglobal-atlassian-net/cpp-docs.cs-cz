---
title: Cmfcpropertygridfontproperty – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 3ea43fefabe43bec8a5bf9b00404491a405e5416
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852978"
---
# <a name="cmfcpropertygridfontproperty-class"></a>Cmfcpropertygridfontproperty – třída
`CMFCPropertyGridFileProperty` Třída podporuje položku ovládacího prvku seznamu s, která se otevře dialogové okno Výběr písma.  
  
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
|`CMFCPropertyGridFontProperty::FormatProperty`|Formátuje textovou reprezentaci hodnoty vlastnosti. (Přepíše [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|  
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Načte barvu písma, kterou uživatel vybere z rozevíracího seznamu písmo dialogového okna.|  
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Načte písma, kterou uživatel vybere z rozevíracího seznamu písmo dialogového okna.|  
|`CMFCPropertyGridFontProperty::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|  
|`CMFCPropertyGridFontProperty::OnClickButton`|Volá se rozhraním, když uživatel klikne na tlačítko, který je obsažen ve vlastnosti. (Přepíše [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfcpropertygridproperty –](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [Cmfcpropertygridfontproperty –](../../mfc/reference/cmfcpropertygridfontproperty-class.md)  
  
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
 [in] *%{strName/*  
 Název vlastnosti  
  
 [in] *lf*  
 Písmo logickou strukturu, která určuje atributy písma.  
  
 [in] *dwFontDialogFlags*  
 Styly, které se použijí pro dialogové okno písmo, který se zobrazí po kliknutí na tlačítko Vlastnosti hodnotu rozevíracího seznamu. Výchozí hodnota je bitová kombinace (nebo) CF_EFFECTS a CF_SCREENFONTS. Další informace najdete v tématu *příznaky* parametr [CHOOSEFONT struktura](http://msdn.microsoft.com/library/windows/desktop/ms646832).  
  
 [in] *lpszDescr*  
 Popis vlastnosti font. Výchozí hodnota je NULL.  
  
 [in] *dwData*  
 Specifická data, jako je například celé číslo nebo ukazatel na další data, která souvisí s vlastností. Výchozí hodnota je 0.  
  
 [in] *barva*  
 Barva písma. Výchozí hodnota je výchozí barvy.  
  
### <a name="remarks"></a>Poznámky  
 A `CMFCPropertyGridFontProperty` objekt představuje vlastnost font v ovládacím prvku písma grid vlastnost.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCPropertyGridFontProperty` třídy. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]  
  
##  <a name="getcolor"></a>  CMFCPropertyGridFontProperty::GetColor  
 Načte barvu písma, kterou uživatel vybere z rozevíracího seznamu písmo dialogového okna.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota barvy RGB, který představuje barvu vybraného písma.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont  
 Načte písma, kterou uživatel vybere z rozevíracího seznamu písmo dialogového okna.  
  
```  
LPLOGFONT GetLogFont();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktura, která popisuje vybraného písma.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Cmfcpropertygridctrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty – třída](../../mfc/reference/cmfcpropertygridproperty-class.md)
