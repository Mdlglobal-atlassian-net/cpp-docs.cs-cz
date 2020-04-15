---
title: CMFCPropertyGridColorProperty – třída
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
ms.openlocfilehash: 62015f384fa5f72ceeceed2605cbf9a6b646a1eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375315"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty – třída

Třída `CMFCPropertyGridColorProperty` podporuje položku ovládacího prvku seznamu vlastností, která otevře dialogové okno výběru barev.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCPropertyGridColorPropertyProperty::VLASTNOST CMFCPropertyColorProperty](#cmfcpropertygridcolorproperty)|Vytvoří `CMFCPropertyGridColorProperty` objekt.|
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCPropertyGridColorPropertyProperty::EnableAutomaticButton](#enableautomaticbutton)|Povolí *automatické* tlačítko v dialogovém okně výběru barev. (Standardní automatické tlačítko je označeno **automaticky**.)|
|[CMFCPropertyGridColorPropertyProperty::EnableOtherButton](#enableotherbutton)|Povolí *druhé* tlačítko v dialogovém okně výběru barev. (Standardní jiné tlačítko je označeno **více barev**.)|
|`CMFCPropertyGridColorProperty::FormatProperty`|Formátuje textovou reprezentaci hodnoty vlastnosti. (Přepíše [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridColorPropertyProperty::GetColor](#getcolor)|Získá aktuální barvu vlastnosti.|
|`CMFCPropertyGridColorProperty::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|`CMFCPropertyGridColorProperty::OnClickButton`|Volat rámci, když uživatel klepne na tlačítko, které je obsaženo ve vlastnosti. (Přepíše [CMFCPropertyProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|
|`CMFCPropertyGridColorProperty::OnDrawValue`|Volat rámci k zobrazení hodnoty vlastnosti. (Přepíše [CMFCPropertyProperty::OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|
|`CMFCPropertyGridColorProperty::OnEdit`|Volat rámci, když se uživatel chystá změnit hodnotu vlastnosti. (Přepíše [CMFCPropertyGridProperty::OnEdit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Volat rámci při změně hodnoty upravitelné vlastnosti. (Přepíše [CMFCPropertyProperty::OnUpdateValue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|
|[CMFCPropertyGridColorPropertyProperty::SetColor](#setcolor)|Nastaví novou barvu vlastnosti.|
|[CMFCPropertyGridColorPropertyProperty::SetColumnsNumber](#setcolumnsnumber)|Určuje počet sloupců v aktuální mřížce vlastností barev.|
|[CMFCPropertyGridColorPropertyProperty::SetOriginalValue](#setoriginalvalue)|Nastaví původní hodnotu upravitelné vlastnosti.|

## <a name="remarks"></a>Poznámky

Třída `CMFCPropertyGridColorProperty` podporuje vlastnost color, kterou lze přidat do ovládacího prvku seznamu vlastností. Další informace naleznete v [části TŘÍDA CMFCPropertyGridCtrl .](../../mfc/reference/cmfcpropertygridctrl-class.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCPropertyGridColorProperty` třídy a nakonfigurovat tento `CMFCPropertyGridColorProperty` objekt pomocí různých metod třídy. Kód vysvětluje, jak povolit automatická a další tlačítka a jak nastavit barvu a číslo sloupce. Tento příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Vlastnost CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CmFCPropertyGridColorPropertyPropertyProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpropertygridctrl.h

## <a name="cmfcpropertygridcolorpropertycmfcpropertygridcolorproperty"></a><a name="cmfcpropertygridcolorproperty"></a>CMFCPropertyGridColorPropertyProperty::VLASTNOST CMFCPropertyColorProperty

Vytvoří `CMFCPropertyGridColorProperty` objekt.

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
[v] Název vlastnosti.

*color*<br/>
[v] Hodnota barvy vlastnosti.

*pPaleta*<br/>
[v] Ukazatel na paletu barev. Výchozí hodnota je NULL.

*lpszDescr*<br/>
[v] Popis vlastnosti. Výchozí hodnota je NULL.

*dwData*<br/>
[v] Data specifická pro aplikaci, například celé číslo nebo ukazatel na jiná data, která jsou přidružena k vlastnosti. Výchozí hodnota je 0.

## <a name="cmfcpropertygridcolorpropertyenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCPropertyGridColorPropertyProperty::EnableAutomaticButton

Povolí *automatické* tlačítko v dialogovém okně výběru barev. (Standardní automatické tlačítko je označeno **automaticky**.)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Text popisku automatického tlačítka.

*colorAutomaticky*<br/>
[v] Hodnota barvy RGB automatické (výchozí) barvy.

*bEnable*<br/>
[v] TRUE pro povolení automatického tlačítka; jinak NEPRAVDA. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpropertygridcolorpropertyenableotherbutton"></a><a name="enableotherbutton"></a>CMFCPropertyGridColorPropertyProperty::EnableOtherButton

Povolí *druhé* tlačítko v dialogovém okně výběru barev. (Standardní jiné tlačítko je označeno **více barev**.)

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Text popisku druhého tlačítka.

*bAltColorDlg*<br/>
[v] TRUE pro `CMFCColorDialog` zobrazení dialogového okna; NEPRAVDA pro zobrazení dialogového okna standardního výběru barev. Výchozí hodnota je TRUE.

*bEnable*<br/>
[v] TRUE pro zobrazení druhého tlačítka; jinak NEPRAVDA.  Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpropertygridcolorpropertygetcolor"></a><a name="getcolor"></a>CMFCPropertyGridColorPropertyProperty::GetColor

Získá aktuální barvu vlastnosti.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpropertygridcolorpropertysetcolor"></a><a name="setcolor"></a>CMFCPropertyGridColorPropertyProperty::SetColor

Nastaví novou barvu vlastnosti.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[v] Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

## <a name="cmfcpropertygridcolorpropertysetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCPropertyGridColorPropertyProperty::SetColumnsNumber

Určuje počet sloupců v aktuální mřížce vlastností barev.

```
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>Parametry

*nSloupceČíslo*<br/>
[v] Upřednostňovaný počet sloupců v mřížce vlastností barev.

### <a name="remarks"></a>Poznámky

Tato metoda nastaví `m_nColumnsNumber` hodnotu chráněného datového člena.

## <a name="cmfcpropertygridcolorpropertysetoriginalvalue"></a><a name="setoriginalvalue"></a>CMFCPropertyGridColorPropertyProperty::SetOriginalValue

Nastaví původní hodnotu upravitelné vlastnosti.

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>Parametry

*varValue*<br/>
[v] Hodnota.

### <a name="remarks"></a>Poznámky

Pomocí metody [CMFCPropertyGridProperty::ResetOriginalValue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) obnovte původní hodnotu upravené vlastnosti.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty – třída](../../mfc/reference/cmfcpropertygridproperty-class.md)
