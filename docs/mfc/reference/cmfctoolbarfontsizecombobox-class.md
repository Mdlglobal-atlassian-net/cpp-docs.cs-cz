---
title: Cmfctoolbarfontsizecombobox – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca2a8f0a2a7a1b6c8be91902f3a239c34857252e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065639"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>Cmfctoolbarfontsizecombobox – třída

Tlačítka panelu nástrojů obsahující ovládací prvek pole se seznamem, který umožňuje uživateli vybrat velikost písma.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|Vytvoří `CMFCToolBarFontSizeComboBox` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Vrátí hodnotu zadejte v twipech velikost vybraného písma.|
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|Vyplní seznamu pole se seznamem všech velikostí podporovanou písma pro zadaný font.|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Nastaví velikost písma v jednotkách twip.|

## <a name="remarks"></a>Poznámky

Můžete použít `CMFCToolBarFontSizeComboBox` objektů spolu s [cmfctoolbarfontcombobox – třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objektu a povolit tak uživateli vybrat písma a velikost písma.

Tlačítko pole se seznamem velikost písmo můžete přidat na panel nástrojů stejně, jako je přidat tlačítko pole se seznamem písma. Další informace najdete v tématu [cmfctoolbarfontcombobox – třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

Když uživatel vybere nový písma v `CMFCToolBarFontComboBox` objektu, můžete přejít k vyplnění pole se seznamem velikost písma s podporované velikosti písma s použitím [CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes) metody.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCToolBarFontSizeComboBox` třída ke konfiguraci `CMFCToolBarFontSizeComboBox` objektu. Tento příklad ukazuje, jak načíst velikost písma, zadejte v twipech, v textovém poli, vyplnit všechna platná velikost písma daného pole se seznamem velikost písma a velikost písma zadejte v twipech. Tento fragment kódu je součástí [slovo panel vzorku](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cmfctoolbarbutton –](../../mfc/reference/cmfctoolbarbutton-class.md)

[Cmfctoolbarcomboboxbutton –](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[Cmfctoolbarfontsizecombobox –](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbarfontcombobox.h

##  <a name="cmfctoolbarfontsizecombobox"></a>  CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

Vytvoří `CMFCToolBarFontSizeComboBox` objektu.

```
CMFCToolBarFontSizeComboBox();
```

##  <a name="gettwipsize"></a>  CMFCToolBarFontSizeComboBox::GetTwipSize

Získá velikost písma, zadejte v twipech, v textovém poli se seznamem velikost písma.

```
int GetTwipSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je návratová hodnota kladná, je velikost písma v jednotkách twip. Je -1, pokud textové pole, pole se seznamem je prázdný. -2 je, pokud dojde k chybě.

##  <a name="rebuildfontsizes"></a>  CMFCToolBarFontSizeComboBox::RebuildFontSizes

Pole se seznamem velikost písma vyplní všechny platné velikosti daného písma.

```
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>Parametry

*strFontName*<br/>
[in] Určuje název písma.

### <a name="remarks"></a>Poznámky

Pokud chcete synchronizovat mezi výběru v poli se seznamem písma a pole se seznamem velikost písma, jako například voláním této funkce [cmfctoolbarfontcombobox – třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

##  <a name="settwipsize"></a>  CMFCToolBarFontSizeComboBox::SetTwipSize

Zaokrouhlí číslo zadaný velikost (v jednotkách twip) na nejbližší velikost v bodech a pak nastaví velikost vybrané v poli se seznamem k dané hodnotě.

```
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
[in] Určuje velikost písma (zadejte v twipech) k nastavení.

### <a name="remarks"></a>Poznámky

Předchozí platnou velikost písma lze načíst později pomocí volání [CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize) metody.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton – třída](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo – třída](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)

