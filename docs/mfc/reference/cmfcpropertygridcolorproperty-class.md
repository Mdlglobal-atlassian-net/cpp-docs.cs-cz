---
title: Třída CMFCPropertyGridColorProperty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de336692a821ba374996fac9ee7d282d2990bd08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367991"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty – třída
`CMFCPropertyGridColorProperty` Třída podporuje položka ovládací prvek seznamu vlastnosti, které se otevře dialogové okno Výběr barev.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|Vytvoří `CMFCPropertyGridColorProperty` objektu.|  
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|Umožňuje *automatické* tlačítka v dialogovém okně Výběr barev. (Standardní automatické tlačítko jmenuje **automatické**.)|  
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|Umožňuje *jiných* tlačítka v dialogovém okně Výběr barev. (Standardní jiné tlačítko jmenuje **Další barvy**.)|  
|`CMFCPropertyGridColorProperty::FormatProperty`|Formátuje textové reprezentace hodnotu vlastnosti. (Přepisuje [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|  
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|Získá aktuální barvu vlastnosti.|  
|`CMFCPropertyGridColorProperty::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|`CMFCPropertyGridColorProperty::OnClickButton`|Voláno rámcem po kliknutí na tlačítko, který je obsažený ve vlastnosti. (Přepisuje [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
|`CMFCPropertyGridColorProperty::OnDrawValue`|Voláno rámcem zobrazíte hodnotu vlastnosti. (Přepisuje [CMFCPropertyGridProperty::OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|  
|`CMFCPropertyGridColorProperty::OnEdit`|Voláno rámcem, pokud je uživatel Chystáte se změnit hodnotu vlastnosti. (Přepisuje [CMFCPropertyGridProperty::OnEdit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|  
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Voláno rámcem, pokud došlo ke změně hodnoty upravovat vlastnosti. (Přepisuje [CMFCPropertyGridProperty::OnUpdateValue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|  
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|Nastaví novou barvu pro vlastnost.|  
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|Určuje počet sloupců v aktuální tabulce vlastností barev.|  
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|Nastaví původní hodnota upravovat vlastnosti.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCPropertyGridColorProperty` Třída podporuje vlastnosti barvu, která lze přidat do ovládacího prvku seznam vlastností. Další informace najdete v tématu [CMFCPropertyGridCtrl třída](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCPropertyGridColorProperty` třídy a konfiguraci tohoto objektu pomocí různých metod `CMFCPropertyGridColorProperty` třídy. Kód vysvětluje, jak povolit automatické a dalších tlačítek a jak nastavit barvu a počet sloupců. Tato ukázka je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridcolorproperty"></a>  CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty  
 Vytvoří `CMFCPropertyGridColorProperty` objektu.  
  
```  
CMFCPropertyGridColorProperty(
    const CString& strName,  
    const COLORREF& color,  
    CPalette* pPalette = NULL,  
    LPCTSTR lpszDescr = NULL,  
    DWORD_PTR dwData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `strName`  
 Název vlastnosti  
  
 [v] `color`  
 Barva hodnotu vlastnosti.  
  
 [v] `pPalette`  
 Ukazatel na paletu barev. Výchozí hodnota je `NULL`.  
  
 [v] `lpszDescr`  
 Popis vlastnosti. Výchozí hodnota je `NULL`.  
  
 [v] `dwData`  
 Specifické pro aplikaci data, jako třeba celé číslo nebo ukazatel na další data, která souvisí s vlastností. Výchozí hodnota je 0.  
  
##  <a name="enableautomaticbutton"></a>  CMFCPropertyGridColorProperty::EnableAutomaticButton  
 Umožňuje *automatické* tlačítka v dialogovém okně Výběr barev. (Standardní automatické tlačítko jmenuje **automatické**.)  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszLabel`  
 Text popisku tlačítka automatické.  
  
 [v] `colorAutomatic`  
 Hodnota Barva RGB barvu automaticky (výchozí).  
  
 [v] `bEnable`  
 `TRUE` Chcete-li povolit automatické tlačítko; v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enableotherbutton"></a>  CMFCPropertyGridColorProperty::EnableOtherButton  
 Umožňuje *jiných* tlačítka v dialogovém okně Výběr barev. (Standardní jiné tlačítko jmenuje **Další barvy**.)  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg = TRUE,  
    BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszLabel`  
 Text popisku tlačítko Další.  
  
 [v] `bAltColorDlg`  
 `TRUE` Chcete-li zobrazit `CMFCColorDialog` dialogové okno; `FALSE` zobrazíte dialogové okno Výběr standardní barev. Výchozí hodnota je `TRUE`.  
  
 [v] `bEnable`  
 `TRUE` Chcete-li zobrazit další tlačítka; v opačném `FALSE`.  Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcolor"></a>  CMFCPropertyGridColorProperty::GetColor  
 Získá aktuální barvu vlastnosti.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu barva RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setcolor"></a>  CMFCPropertyGridColorProperty::SetColor  
 Nastaví novou barvu pro vlastnost.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `color`  
 Hodnotu barva RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setcolumnsnumber"></a>  CMFCPropertyGridColorProperty::SetColumnsNumber  
 Určuje počet sloupců v aktuální tabulce vlastností barev.  
  
```  
void SetColumnsNumber(int nColumnsNumber);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nColumnsNumber`  
 Upřednostňovaný počet sloupců v tabulce vlastností barev.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví hodnotu `m_nColumnsNumber` chráněné – datový člen.  
  
##  <a name="setoriginalvalue"></a>  CMFCPropertyGridColorProperty::SetOriginalValue  
 Nastaví původní hodnota upravovat vlastnosti.  
  
```  
virtual void SetOriginalValue(const COleVariant& varValue);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `varValue`  
 Hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCPropertyGridProperty::ResetOriginalValue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) metoda resetovat původní hodnota upravená vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty – třída](../../mfc/reference/cmfcpropertygridproperty-class.md)
