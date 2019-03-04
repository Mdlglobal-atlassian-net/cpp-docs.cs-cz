---
title: Cmfcribbonbuttonsgroup – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButtons
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetCount
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetImageSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetRegularSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::HasImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::OnDrawImage
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::RemoveAll
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetParentCategory
helpviewer_keywords:
- CMFCRibbonButtonsGroup [MFC], CMFCRibbonButtonsGroup
- CMFCRibbonButtonsGroup [MFC], AddButton
- CMFCRibbonButtonsGroup [MFC], AddButtons
- CMFCRibbonButtonsGroup [MFC], GetButton
- CMFCRibbonButtonsGroup [MFC], GetCount
- CMFCRibbonButtonsGroup [MFC], GetImageSize
- CMFCRibbonButtonsGroup [MFC], GetRegularSize
- CMFCRibbonButtonsGroup [MFC], HasImages
- CMFCRibbonButtonsGroup [MFC], OnDrawImage
- CMFCRibbonButtonsGroup [MFC], RemoveAll
- CMFCRibbonButtonsGroup [MFC], SetImages
- CMFCRibbonButtonsGroup [MFC], SetParentCategory
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
ms.openlocfilehash: 3a0806d5c45f429f975b7b8ef0085252fe2b2528
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295887"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>Cmfcribbonbuttonsgroup – třída

`CMFCRibbonButtonsGroup` Třída umožňuje uspořádat sadu tlačítek na pásu karet do skupiny. Všechna tlačítka ve skupině jsou přímo vedle sebe ve vodorovném směru a uzavřena do ohraničení.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|Vytvoří `CMFCRibbonButtonsGroup` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|Přidá tlačítko do skupiny.|
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|Seznam tlačítek, přidá do skupiny.|
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|Vrací ukazatel na tlačítka, které se nachází na zadaném indexu.|
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|Vrátí počet tlačítek ve skupině.|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Vrátí velikost bitové kopie normální bitové kopie do skupiny pásu karet (přepíše [CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Vrátí regulární velikost elementu pásu karet (přepíše [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Sestavy, zda `CMFCRibbonButtonsGroup` objekt obsahuje obrázky panelu nástrojů.|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Nakreslí odpovídající image pro určeného tlačítka, v závislosti na tom, zda tlačítko je normální, zvýrazněné nebo zakázáno.|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|Odebere všechna tlačítka z `CMFCRibbonButtonsGroup` objektu.|
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|Přiřadí bitové kopie do skupiny.|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|Nastaví nadřazeného `CMFCRibbonCategory` z `CMFCRibbonButtonsGroup` objektu a všechna tlačítka v něm (přepíše [CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|

## <a name="remarks"></a>Poznámky

Skupiny je odvozen z [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) a lze manipulovat jako jedna entita. Skupinu lze umístit na libovolné nabídky panelu nebo automaticky otevíraného okna.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCRibbonButtonsGroup` třídy. Tento příklad ukazuje, jak vytvořit `CMFCRibbonButtonsGroup` objekt, přiřaďte imagí skupina tlačítek na pásu karet a přidejte do skupiny tlačítek na pásu karet tlačítko. Tento fragment kódu je součástí [nakreslit Client sample](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribbonbuttonsgroup.h

##  <a name="addbutton"></a>  CMFCRibbonButtonsGroup::AddButton

Přidá tlačítko do skupiny.

```
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parametry

*pButton*<br/>
[in] Ukazatel na tlačítko pro přidání.

##  <a name="addbuttons"></a>  CMFCRibbonButtonsGroup::AddButtons

Seznam tlačítek, přidá do skupiny.

```
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>Parametry

*lstButtons*<br/>
[in] Seznam ukazatelů na tlačítka, který chcete přidat.

##  <a name="cmfcribbonbuttonsgroup"></a>  CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup

Vytvoří `CMFCRibbonButtonsGroup` objektu.

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parametry

*pButton*<br/>
[in] Určuje tlačítko pro přidání do nově vytvořeného `CMFCRibbonButtonsGroup` objektu.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getbutton"></a>  CMFCRibbonButtonsGroup::GetButton

Vrací ukazatel na tlačítka, které se nachází na zadaném indexu.

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>Parametry

*i*<br/>
[in] Index založený na nule tlačítko pro vrácení.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na tlačítka, které se nachází na zadaném indexu. Hodnota NULL, pokud zadaný index je mimo rozsah.

### <a name="remarks"></a>Poznámky

##  <a name="getcount"></a>  CMFCRibbonButtonsGroup::GetCount

Vrátí počet tlačítek ve skupině.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet tlačítek ve skupině.

##  <a name="getimagesize"></a>  CMFCRibbonButtonsGroup::GetImageSize

Načte obrázek velikost zdroje chráněných `CMFCToolBarImages` člen `m_Images`.

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost bitové kopie zdroje obrázků panelu nástrojů, pokud existuje, nebo `CSize` nula, pokud tomu tak není.

### <a name="remarks"></a>Poznámky

##  <a name="getregularsize"></a>  CMFCRibbonButtonsGroup::GetRegularSize

Získá maximální možná velikost prvku skupiny pásu karet.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení ze skupiny pásu karet.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="hasimages"></a>  CMFCRibbonButtonsGroup::HasImages

Sestavy, zda `CMFCRibbonButtonsGroup` objekt obsahuje obrázky panelu nástrojů.

```
BOOL HasImages() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se chráněný `CMFCToolBarImages` člen `m_Images` obsahuje všechny Image, nebo FALSE, pokud není.

### <a name="remarks"></a>Poznámky

##  <a name="ondrawimage"></a>  CMFCRibbonButtonsGroup::OnDrawImage

Nakreslí odpovídající image pro určeného tlačítka, v závislosti na tom, zda tlačítko je normální, zvýrazněné nebo zakázáno.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení `CMFCRibbonButtonsGroup` objektu.

*rectImage*<br/>
[in] Obdélník, ve kterém chcete-li nakreslit obrázek.

*pButton*<br/>
[in] Tlačítko, pro kterou chcete-li nakreslit obrázek.

*nImageIndex*<br/>
[in] Index bitové kopie na nakreslit tlačítko (v jednom z polí tři image u tlačítek, Normální, zvýrazněné nebo zakázáno).

### <a name="remarks"></a>Poznámky

##  <a name="removeall"></a>  CMFCRibbonButtonsGroup::RemoveAll

Odebere všechna tlačítka z `CMFCRibbonButtonsGroup` objektu.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

##  <a name="setimages"></a>  CMFCRibbonButtonsGroup::SetImages

Obrázky přiřadí skupinu tlačítek na pásu karet.

```
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>Parametry

*pImages*<br/>
[in] Běžných bitových kopií.

*pHotImages*<br/>
[in] Horkými obrázky.

*pDisabledImages*<br/>
[in] Zakázané imagí.

### <a name="remarks"></a>Poznámky

Volání `SetImages` předtím, než přidáte tlačítka do skupiny. Počet obrázků musí být větší nebo rovna počtu tlačítka Přidat do skupiny.

> [!NOTE]
>  Horkými obrázky jsou bitové kopie, které se zobrazují, když uživatel najede myší na tlačítko. Zakázané bitové kopie jsou bitové kopie, které se zobrazí, pokud je tlačítko neaktivní.

##  <a name="setparentcategory"></a>  CMFCRibbonButtonsGroup::SetParentCategory

Nastaví nadřazeného `CMFCRibbonCategory` z `CMFCRibbonButtonsGroup` objektu a všechna tlačítka v něm.

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>Parametry

*pCategory*<br/>
[in] Ukazatel do nadřazené kategorie nastavení (skupin s kartami v ovládacích prvků pásu karet se nazývají kategorie).

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
