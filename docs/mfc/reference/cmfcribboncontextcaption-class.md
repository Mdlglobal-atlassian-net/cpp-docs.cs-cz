---
title: Třída CMFCFCRibbonContextCaption
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetColor
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetRightTabX
helpviewer_keywords:
- CMFCRibbonContextCaption [MFC], GetColor
- CMFCRibbonContextCaption [MFC], GetRightTabX
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
ms.openlocfilehash: 7aacbe23684914c91129d9962ae847d442cc411b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375223"
---
# <a name="cmfcribboncontextcaption-class"></a>Třída CMFCFCRibbonContextCaption

Implementuje barevný titulek, který se zobrazí v horní části kategorie pásu karet nebo kategorie kontextu.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonContextCaption : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCRibbonContextCaption::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCRibbonContextcaption::GetColor](#getcolor)|Vrátí barvu titulku.|
|[CMFCRibbonContextcaption::GetRightTabX](#getrighttabx)||
|`CMFCRibbonContextCaption::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|

## <a name="remarks"></a>Poznámky

Tuto třídu nelze přímo vytvořit instanci. Třída [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md) používá tuto třídu interně k přidání barvy do kategorií pásu karet.

Chcete-li nastavit barvu pro kategorie pásu karet, zavolejte [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor). Chcete-li nastavit barvu pro kategorie kontextu, zavolejte [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CmFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFC](../../mfc/reference/cmfcribboncontextcaption-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonBar.h

## <a name="cmfcribboncontextcaptiongetcolor"></a><a name="getcolor"></a>CMFCRibbonContextcaption::GetColor

Vrátí barvu pozadí titulku.

```
AFX_RibbonCategoryColor GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota může být jedna z následujících výčtových hodnot:

- `AFX_CategoryColor_None`

- `AFX_CategoryColor_Red`

- `AFX_CategoryColor_Orange`

- `AFX_CategoryColor_Yellow`

- `AFX_CategoryColor_Green`

- `AFX_CategoryColor_Blue`

- `AFX_CategoryColor_Indigo`

- `AFX_CategoryColor_Violet`

### <a name="remarks"></a>Poznámky

Barvu titulku lze nastavit voláním [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor) nebo [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

## <a name="cmfcribboncontextcaptiongetrighttabx"></a><a name="getrighttabx"></a>CMFCRibbonContextcaption::GetRightTabX

Načte pozici pravého okraje karty pásu karet kategorie.

```
int GetRightTabX() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí pravotočivou hodnotu X ohraničujícího obdélníku `CMFCRibbonCategory` karty pásu karet objektu nebo hodnotu -1, pokud je karta zkrácena.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonCategory – třída](../../mfc/reference/cmfcribboncategory-class.md)<br/>
[CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
