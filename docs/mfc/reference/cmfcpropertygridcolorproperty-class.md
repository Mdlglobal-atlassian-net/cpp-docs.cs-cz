---
title: CMFCPropertyGridColorProperty Class
ms.date: 11/04/2016
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
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
ms.openlocfilehash: 95dcbbc2b445e2ff67979b90816daed0fb0c0fba
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767714"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty Class

`CMFCPropertyGridColorProperty` Třída podporuje položku ovládacího prvku seznamu s, která se otevře dialogové okno Výběr barvy.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|Vytvoří `CMFCPropertyGridColorProperty` objektu.|
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|Umožňuje *automatické* tlačítko na dialogové okno Výběr barvy. (Standardní automatické tlačítko má název **automatické**.)|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|Umožňuje *jiných* tlačítko na dialogové okno Výběr barvy. (Standardní jiné tlačítko má název **Další barvy**.)|
|`CMFCPropertyGridColorProperty::FormatProperty`|Formátuje textovou reprezentaci hodnoty vlastnosti. (Overrides [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|Získá aktuální barvu vlastnosti.|
|`CMFCPropertyGridColorProperty::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|`CMFCPropertyGridColorProperty::OnClickButton`|Volá se rozhraním, když uživatel klikne na tlačítko, který je obsažen ve vlastnosti. (Overrides [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|
|`CMFCPropertyGridColorProperty::OnDrawValue`|Volá se rozhraním, aby zobrazil hodnotu vlastnosti. (Přepíše [CMFCPropertyGridProperty::OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|
|`CMFCPropertyGridColorProperty::OnEdit`|Volá se rozhraním, když se uživatel chystá upravit hodnotu vlastnosti. (Overrides [CMFCPropertyGridProperty::OnEdit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Volá se rozhraním, se při změně hodnoty vlastnosti upravovat. (Overrides [CMFCPropertyGridProperty::OnUpdateValue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|Nastaví barvu nové vlastnosti.|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|Určuje počet sloupců v mřížce vlastnost aktuální barvu.|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|Nastaví původní hodnoty upravovat vlastnosti.|

## <a name="remarks"></a>Poznámky

`CMFCPropertyGridColorProperty` Třída podporuje vlastnost barvu, která mohou být přidány do ovládacího prvku seznamu vlastností. Další informace najdete v tématu [cmfcpropertygridctrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCPropertyGridColorProperty` třídy a nakonfigurovat tento objekt pomocí různých metod `CMFCPropertyGridColorProperty` třídy. Kód vysvětluje, jak povolit automatické a další tlačítka a jak nastavit barvu a počet sloupců. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxpropertygridctrl.h

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

*strName*<br/>
[in] Název vlastnosti.

*color*<br/>
[in] Hodnota barvy vlastnosti.

*pPalette*<br/>
[in] Ukazatel na paletu barev. Výchozí hodnota je NULL.

*lpszDescr*<br/>
[in] Vlastnost popis. Výchozí hodnota je NULL.

*dwData*<br/>
[in] Specifická data, jako je například celé číslo nebo ukazatel na další data, která souvisí s vlastností. Výchozí hodnota je 0.

##  <a name="enableautomaticbutton"></a>  CMFCPropertyGridColorProperty::EnableAutomaticButton

Umožňuje *automatické* tlačítko na dialogové okno Výběr barvy. (Standardní automatické tlačítko má název **automatické**.)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Text popisku tlačítka pro automatické.

*colorAutomatic*<br/>
[in] Hodnota barvy RGB barvy automaticky (výchozí).

*bEnable*<br/>
[in] TRUE, pokud chcete povolit automatické tlačítko; v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

##  <a name="enableotherbutton"></a>  CMFCPropertyGridColorProperty::EnableOtherButton

Umožňuje *jiných* tlačítko na dialogové okno Výběr barvy. (Standardní jiné tlačítko má název **Další barvy**.)

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Text popisku tlačítka Další.

*bAltColorDlg*<br/>
[in] True pro zobrazení `CMFCColorDialog` dialogové okno; FALSE, pokud chcete zobrazit dialogové okno Výběr standardní barvu. Výchozí hodnota je TRUE.

*bEnable*<br/>
[in] TRUE, pokud chcete zobrazit další tlačítka; v opačném případě hodnota FALSE.  Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

##  <a name="getcolor"></a>  CMFCPropertyGridColorProperty::GetColor

Získá aktuální barvu vlastnosti.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

##  <a name="setcolor"></a>  CMFCPropertyGridColorProperty::SetColor

Nastaví barvu nové vlastnosti.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[in] Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

##  <a name="setcolumnsnumber"></a>  CMFCPropertyGridColorProperty::SetColumnsNumber

Určuje počet sloupců v mřížce vlastnost aktuální barvu.

```
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>Parametry

*nColumnsNumber*<br/>
[in] Upřednostňovaný počet sloupců v mřížce vlastností barev.

### <a name="remarks"></a>Poznámky

Tato metoda nastaví hodnotu vlastnosti `m_nColumnsNumber` chráněný datový člen.

##  <a name="setoriginalvalue"></a>  CMFCPropertyGridColorProperty::SetOriginalValue

Nastaví původní hodnoty upravovat vlastnosti.

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>Parametry

*varValue*<br/>
[in] Hodnota.

### <a name="remarks"></a>Poznámky

Použití [CMFCPropertyGridProperty::ResetOriginalValue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) metoda obnovit původní hodnotu upravených vlastností.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty – třída](../../mfc/reference/cmfcpropertygridproperty-class.md)
