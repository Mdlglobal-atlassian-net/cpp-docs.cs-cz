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
ms.openlocfilehash: a3c5b806482a97d64a9ffab92877781cb8778b6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505113"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty Class

`CMFCPropertyGridFileProperty` Třída podporuje položku ovládacího prvku seznamu vlastností, která otevře dialogové okno Výběr písma.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|`CMFCPropertyGridFontProperty` Vytvoří objekt.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|Formátuje textovou reprezentaci hodnoty vlastnosti. (Overrides [CMFCPropertyGridProperty:: FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Načte barvu písma, kterou uživatel vybere v dialogovém okně písmo.|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Načte písmo, které uživatel vybere v dialogovém okně písmo.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Volá se rozhraním, když uživatel klikne na tlačítko, které je obsažené ve vlastnosti. (Overrides [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpropertygridctrl. h

##  <a name="cmfcpropertygridfontproperty"></a>CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

`CMFCPropertyGridFontProperty` Vytvoří objekt.

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
pro Název vlastnosti.

*znaky*<br/>
pro Logická struktura písma, která určuje atributy písma.

*dwFontDialogFlags*<br/>
pro Styly použité v dialogovém okně písmo, které se zobrazí po kliknutí na tlačítko s rozevíracím seznamem hodnoty vlastnosti Výchozí hodnota je bitová kombinace (nebo) hodnot CF_EFFECTS a CF_SCREENFONTS. Další informace naleznete v parametru *Flags* [struktury CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw).

*lpszDescr*<br/>
pro Popis vlastnosti Font Výchozí hodnota je NULL.

*dwData*<br/>
pro Data specifická pro aplikaci, například celé číslo nebo ukazatel na další data, která jsou přidružena k vlastnosti. Výchozí hodnota je 0.

*barevných*<br/>
pro Barva písma Výchozí hodnota je výchozí barva.

### <a name="remarks"></a>Poznámky

`CMFCPropertyGridFontProperty` Objekt představuje vlastnost font v ovládacím prvku písmo mřížky vlastností.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCPropertyGridFontProperty` třídy. Tento příklad je součástí [ukázky nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

##  <a name="getcolor"></a>CMFCPropertyGridFontProperty:: GetColor

Načte barvu písma, kterou uživatel vybere v dialogovém okně písmo.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota barvy RGB, která představuje vybranou barvu písma.

### <a name="remarks"></a>Poznámky

##  <a name="getlogfont"></a>CMFCPropertyGridFontProperty::GetLogFont

Načte písmo, které uživatel vybere v dialogovém okně písmo.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) , která popisuje vybrané písmo.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty – třída](../../mfc/reference/cmfcpropertygridproperty-class.md)
