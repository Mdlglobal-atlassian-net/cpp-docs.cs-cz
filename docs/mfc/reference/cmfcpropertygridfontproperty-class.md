---
title: CMFCPropertyGridFontProperty Class
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
ms.openlocfilehash: b348dc2ac68ced89fb0702073f57a114befaf1cb
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769352"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty Class

`CMFCPropertyGridFileProperty` Třída podporuje položku ovládacího prvku seznamu s, která se otevře dialogové okno Výběr písma.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Vytvoří `CMFCPropertyGridFontProperty` objektu.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|Formátuje textovou reprezentaci hodnoty vlastnosti. (Overrides [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Načte barvu písma, kterou uživatel vybere z rozevíracího seznamu písmo dialogového okna.|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Načte písma, kterou uživatel vybere z rozevíracího seznamu písmo dialogového okna.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Volá se rozhraním, když uživatel klikne na tlačítko, který je obsažen ve vlastnosti. (Overrides [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxpropertygridctrl.h

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

*strName*<br/>
[in] Název vlastnosti.

*LF*<br/>
[in] Písmo logickou strukturu, která určuje atributy písma.

*dwFontDialogFlags*<br/>
[in] Styly, které se použijí pro dialogové okno písmo, který se zobrazí po kliknutí na tlačítko Vlastnosti hodnotu rozevíracího seznamu. Výchozí hodnota je bitová kombinace (nebo) CF_EFFECTS a CF_SCREENFONTS. Další informace najdete v tématu *příznaky* parametr [CHOOSEFONT struktura](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta).

*lpszDescr*<br/>
[in] Popis vlastnosti font. Výchozí hodnota je NULL.

*dwData*<br/>
[in] Specifická data, jako je například celé číslo nebo ukazatel na další data, která souvisí s vlastností. Výchozí hodnota je 0.

*color*<br/>
[in] Barva písma. Výchozí hodnota je výchozí barvy.

### <a name="remarks"></a>Poznámky

A `CMFCPropertyGridFontProperty` objekt představuje vlastnost font v ovládacím prvku písma grid vlastnost.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCPropertyGridFontProperty` třídy. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../overview/visual-cpp-samples.md).

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

Ukazatel [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) struktura, která popisuje vybraného písma.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty – třída](../../mfc/reference/cmfcpropertygridproperty-class.md)
