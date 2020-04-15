---
title: CMFCToolBarFontSizeComboBox – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
ms.openlocfilehash: 09811b14ed805b1965015a32a25c0b67c947ff4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358309"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox – třída

Tlačítko panelu nástrojů, které obsahuje ovládací prvek pole se seznamem, který umožňuje uživateli vybrat velikost písma.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontFontSizeComboBox](#cmfctoolbarfontsizecombobox)|Vytvoří `CMFCToolBarFontSizeComboBox` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Vrátí vybranou velikost písma v twipech.|
|[CMFCToolBarFontSizeComboBox::Znovu vytvořit velikostpísma](#rebuildfontsizes)|Vyplní seznam polí se seznamem všemi podporovanými velikostmi písma pro zadané písmo.|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Nastaví velikost písma v twips.|

## <a name="remarks"></a>Poznámky

Objekt můžete `CMFCToolBarFontSizeComboBox` použít společně s objektem [třídy CMFCToolBarFontComboBox,](../../mfc/reference/cmfctoolbarfontcombobox-class.md) který uživateli umožní vybrat písmo a velikost písma.

Tlačítko pole se seznamem velikosti písma můžete přidat do panelu nástrojů stejně jako tlačítko pole se seznamem písem. Další informace naleznete v tématu [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

Když uživatel vybere nové písmo `CMFCToolBarFontComboBox` v objektu, můžete vyplnit pole se seznamem velikosti písma podporovanými velikostmi tohoto písma pomocí metody [CMFCToolBarFontSizeComboBox::RebuildFontSizes.](#rebuildfontsizes)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCToolBarFontSizeComboBox` metody ve `CMFCToolBarFontSizeComboBox` třídě ke konfiguraci objektu. Příklad ukazuje, jak načíst velikost písma v twips, z textového pole, vyplnit pole se seznamem velikosti písma se všemi platnými velikostmi daného písma a určit velikost písma v twips. Tento fragment kódu je součástí [ukázky aplikace Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CmFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CmFCToolBarComboBoxTlačítko](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbarfontcombobox.h

## <a name="cmfctoolbarfontsizecomboboxcmfctoolbarfontsizecombobox"></a><a name="cmfctoolbarfontsizecombobox"></a>CMFCToolBarFontSizeComboBox::CMFCToolBarFontFontSizeComboBox

Vytvoří `CMFCToolBarFontSizeComboBox` objekt.

```
CMFCToolBarFontSizeComboBox();
```

## <a name="cmfctoolbarfontsizecomboboxgettwipsize"></a><a name="gettwipsize"></a>CMFCToolBarFontSizeComboBox::GetTwipSize

Načte velikost písma v twips z textového pole pole se seznamem velikosti písma.

```
int GetTwipSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je vrácená hodnota kladná, je to velikost písma v twips. Je -1, pokud je textové pole pole se seznamem prázdné. Je -2, pokud dojde k chybě.

## <a name="cmfctoolbarfontsizecomboboxrebuildfontsizes"></a><a name="rebuildfontsizes"></a>CMFCToolBarFontSizeComboBox::Znovu vytvořit velikostpísma

Vyplní pole se seznamem velikosti písma všemi platnými velikostmi daného písma.

```
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>Parametry

*strNázev_písmo*<br/>
[v] Určuje název písma.

### <a name="remarks"></a>Poznámky

Tuto funkci zavolejte, pokud chcete synchronizovat mezi výběrem v poli se seznamem písem a polem se seznamem velikosti písma, například [třídu CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

## <a name="cmfctoolbarfontsizecomboboxsettwipsize"></a><a name="settwipsize"></a>CMFCToolBarFontSizeComboBox::SetTwipSize

Zaokrouhlí zadanou velikost (v twipech) na nejbližší velikost v bodech a pak nastaví vybranou velikost v poli se seznamem na tuto hodnotu.

```
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nVelikost*<br/>
[v] Určuje velikost písma (v twips), které chcete nastavit.

### <a name="remarks"></a>Poznámky

Předchozí platnou velikost písma můžete později načíst voláním metody [CMFCToolBarFontSizeComboBox::GetTwipSize.](#gettwipsize)

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Třída CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Třída CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[Třída CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
