---
title: CMFCRibbonButtonsGroup – třída
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
ms.openlocfilehash: d690e8bf306234e7b742a4c6a0917e5430d92d10
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754112"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup – třída

Třída `CMFCRibbonButtonsGroup` umožňuje uspořádat sadu tlačítek pásu karet do skupiny. Všechna tlačítka ve skupině jsou přímo vedle sebe vodorovně a uzavřená v ohraničení.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|Vytvoří `CMFCRibbonButtonsGroup` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|Přidá tlačítko do skupiny.|
|[CMFCRibbonButtonsGroup::Přidat tlačítka](#addbuttons)|Přidá do skupiny seznam tlačítek.|
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|Vrátí ukazatel na tlačítko, které je umístěno na zadaný index.|
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|Vrátí počet tlačítek ve skupině.|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Vrátí velikost obrázku normálních obrazů ve skupině pásu karet (přepíše [CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Vrátí běžnou velikost prvku pásu karet (přepíše [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Hlásí, `CMFCRibbonButtonsGroup` zda objekt obsahuje obrazy panelu nástrojů.|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Nakreslí příslušný obrázek pro zadané tlačítko v závislosti na tom, zda je tlačítko normální, zvýrazněné nebo zakázané.|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|Odebere z objektu `CMFCRibbonButtonsGroup` všechna tlačítka.|
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|Přiřadí obrázky skupině.|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|Nastaví `CMFCRibbonCategory` nadřazený `CMFCRibbonButtonsGroup` objekt a všechna tlačítka v něm (přepíše [CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|

## <a name="remarks"></a>Poznámky

Skupina je odvozena z [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) a může být manipulováno jako jedna entita. Skupinu můžete umístit na libovolném panelu nebo vyskakovací nabídce.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCRibbonButtonsGroup` metody ve třídě. Příklad ukazuje, jak `CMFCRibbonButtonsGroup` vytvořit objekt, přiřadit obrázky ke skupině tlačítek pásu karet a přidat tlačítko do skupiny tlačítek pásu karet. Tento fragment kódu je součástí [ukázky klienta Draw](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CmFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribbonbuttonsgroup.h

## <a name="cmfcribbonbuttonsgroupaddbutton"></a><a name="addbutton"></a>CMFCRibbonButtonsGroup::AddButton

Přidá tlačítko do skupiny.

```cpp
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parametry

*pTlačítko*<br/>
[v] Ukazatel na tlačítko, které chcete přidat.

## <a name="cmfcribbonbuttonsgroupaddbuttons"></a><a name="addbuttons"></a>CMFCRibbonButtonsGroup::Přidat tlačítka

Přidá do skupiny seznam tlačítek.

```cpp
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>Parametry

*lstTlačítka*<br/>
[v] Seznam ukazatelů na tlačítka, která chcete přidat.

## <a name="cmfcribbonbuttonsgroupcmfcribbonbuttonsgroup"></a><a name="cmfcribbonbuttonsgroup"></a>CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup

Vytvoří `CMFCRibbonButtonsGroup` objekt.

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parametry

*pTlačítko*<br/>
[v] Určuje tlačítko, které má být `CMFCRibbonButtonsGroup` k nově vytvořenému objektu přidejte.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonbuttonsgroupgetbutton"></a><a name="getbutton"></a>CMFCRibbonButtonsGroup::GetButton

Vrátí ukazatel na tlačítko, které je umístěno na zadaný index.

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>Parametry

*I*<br/>
[v] Nula na základě indexu tlačítka vrátit.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na tlačítko, které je umístěno na zadaný index. Null, pokud je zadaný index mimo rozsah.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonbuttonsgroupgetcount"></a><a name="getcount"></a>CMFCRibbonButtonsGroup::GetCount

Vrátí počet tlačítek ve skupině.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet tlačítek ve skupině.

## <a name="cmfcribbonbuttonsgroupgetimagesize"></a><a name="getimagesize"></a>CMFCRibbonButtonsGroup::GetImageSize

Načte velikost zdrojového obrazu `CMFCToolBarImages` `m_Images`chráněného člena .

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost zdrojového obrazu obrazů panelu nástrojů, pokud `CSize` jsou k dispozici, nebo nula, pokud ne.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonbuttonsgroupgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonButtonsGroup::GetRegularSize

Načte maximální možnou velikost prvku skupiny pásu karet.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení skupiny pásu karet.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonbuttonsgrouphasimages"></a><a name="hasimages"></a>CMFCRibbonButtonsGroup::HasImages

Hlásí, `CMFCRibbonButtonsGroup` zda objekt obsahuje obrazy panelu nástrojů.

```
BOOL HasImages() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu `CMFCToolBarImages` PRAVDA, pokud chráněný člen `m_Images` obsahuje nějaké obrázky, nebo nepravda, pokud ne.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonbuttonsgroupondrawimage"></a><a name="ondrawimage"></a>CMFCRibbonButtonsGroup::OnDrawImage

Nakreslí příslušný obrázek pro zadané tlačítko v závislosti na tom, zda je tlačítko normální, zvýrazněné nebo zakázané.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení `CMFCRibbonButtonsGroup` objektu.

*rectImage*<br/>
[v] Obdélník, ve kterém chcete nakreslit obrázek.

*pTlačítko*<br/>
[v] Tlačítko, pro které chcete nakreslit obrázek.

*nImageIndex*<br/>
[v] Index obrázku k tomu na tlačítko (v jednom ze tří obrazových polí pro normální, zvýrazněné nebo zakázané tlačítka).

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonbuttonsgroupremoveall"></a><a name="removeall"></a>CMFCRibbonButtonsGroup::RemoveAll

Odebere z objektu `CMFCRibbonButtonsGroup` všechna tlačítka.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonbuttonsgroupsetimages"></a><a name="setimages"></a>CMFCRibbonButtonsGroup::SetImages

Přiřadí obrázky skupině tlačítek pásu karet.

```cpp
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>Parametry

*pObrázky*<br/>
[v] Pravidelné obrázky.

*pHotObrázky*<br/>
[v] Žhavé obrázky.

*pDisabledImages*<br/>
[v] Zakázané obrázky.

### <a name="remarks"></a>Poznámky

Před `SetImages` přidáním tlačítek do skupiny zavolejte. Počet obrázků musí být větší nebo roven počtu tlačítek, která mají být přidána do skupiny.

> [!NOTE]
> Horké obrázky jsou obrázky, které se zobrazí, když uživatel najeví nad tlačítkem. Zakázané obrázky jsou obrázky, které se zobrazí, když je tlačítko zakázáno.

## <a name="cmfcribbonbuttonsgroupsetparentcategory"></a><a name="setparentcategory"></a>CMFCRibbonButtonsGroup::SetParentCategory

Nastaví `CMFCRibbonCategory` nadřazený `CMFCRibbonButtonsGroup` objekt a všechna tlačítka v něm.

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>Parametry

*pKategorie*<br/>
[v] Ukazatel na nadřazenou kategorii nastavit (skupiny s kartami v ovládacích prvcích pásu karet se nazývají kategorie).

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
