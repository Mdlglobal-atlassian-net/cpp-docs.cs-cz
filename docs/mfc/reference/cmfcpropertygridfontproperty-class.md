---
title: CMFCPropertyGridFontProperty – třída
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
ms.openlocfilehash: a1c9905d8d7f32a049496c4e164c9eaac13455d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361838"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty – třída

Třída `CMFCPropertyGridFileProperty` podporuje položku ovládacího prvku seznamu vlastností, která otevře dialogové okno pro výběr písma.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::VLASTNOST CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Vytvoří `CMFCPropertyGridFontProperty` objekt.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|Formátuje textovou reprezentaci hodnoty vlastnosti. (Přepíše [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Načte barvu písma, kterou uživatel vybere z dialogového okna písma.|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Načte písmo, které uživatel vybere z dialogového okna písma.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Volat rámci, když uživatel klepne na tlačítko, které je obsaženo ve vlastnosti. (Přepíše [CMFCPropertyProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Vlastnost CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CmFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpropertygridctrl.h

## <a name="cmfcpropertygridfontpropertycmfcpropertygridfontproperty"></a><a name="cmfcpropertygridfontproperty"></a>CMFCPropertyGridFontProperty::VLASTNOST CMFCPropertyGridFontProperty

Vytvoří `CMFCPropertyGridFontProperty` objekt.

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
[v] Název vlastnosti.

*Lf*<br/>
[v] Logická struktura písma, která určuje atributy písma.

*dwFontDialogFlags*<br/>
[v] Styly použité v dialogovém okně písma, které se zobrazí po klepnutí na rozevírací tlačítko Hodnoty vlastnosti. Výchozí hodnota je bitová kombinace (OR) CF_EFFECTS a CF_SCREENFONTS. Další informace naleznete v parametru *Flags* [struktury CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw).

*lpszDescr*<br/>
[v] Popis vlastnosti písma. Výchozí hodnota je NULL.

*dwData*<br/>
[v] Data specifická pro aplikaci, například celé číslo nebo ukazatel na jiná data, která jsou přidružena k vlastnosti. Výchozí hodnota je 0.

*color*<br/>
[v] Barva písma. Výchozí hodnota je výchozí barva.

### <a name="remarks"></a>Poznámky

Objekt `CMFCPropertyGridFontProperty` představuje vlastnost písma v ovládacím prvku písma mřížky vlastností.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCPropertyGridFontProperty` objekt třídy. Tento příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

## <a name="cmfcpropertygridfontpropertygetcolor"></a><a name="getcolor"></a>CMFCPropertyGridFontProperty::GetColor

Načte barvu písma, kterou uživatel vybere z dialogového okna písma.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota barvy RGB, která představuje vybranou barvu písma.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpropertygridfontpropertygetlogfont"></a><a name="getlogfont"></a>CMFCPropertyGridFontProperty::GetLogFont

Načte písmo, které uživatel vybere z dialogového okna písma.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu [LOGFONT,](/windows/win32/api/wingdi/ns-wingdi-logfontw) která popisuje vybrané písmo.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty – třída](../../mfc/reference/cmfcpropertygridproperty-class.md)
