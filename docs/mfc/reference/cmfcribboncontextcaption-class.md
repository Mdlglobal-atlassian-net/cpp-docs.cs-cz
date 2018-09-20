---
title: Cmfcribboncontextcaption – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetColor
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetRightTabX
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonContextCaption [MFC], GetColor
- CMFCRibbonContextCaption [MFC], GetRightTabX
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5726605af6b9a0d63c15cb232a094d48dd2f95a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405865"
---
# <a name="cmfcribboncontextcaption-class"></a>Cmfcribboncontextcaption – třída

Implementuje barevný titulek, který se zobrazí v horní části pásu karet nebo kategorii kontextu.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonContextCaption : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|`CMFCRibbonContextCaption::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCRibbonContextCaption::GetColor](#getcolor)|Vrátí barvu popisku.|
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||
|`CMFCRibbonContextCaption::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|

## <a name="remarks"></a>Poznámky

Tato třída nemůže být přímo vytvořeny instance. [CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md) tuto třídu třídy interně používá k přidání barva do kategorie pásu karet.

Chcete-li nastavit barvu kategorie pásu karet, zavolejte [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor). Chcete-li nastavit barvu pro kontext kategorie, zavolejte [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)

[Cmfcribbonbutton –](../../mfc/reference/cmfcribbonbutton-class.md)

[Cmfcribboncontextcaption –](../../mfc/reference/cmfcribboncontextcaption-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonBar.h

##  <a name="getcolor"></a>  CMFCRibbonContextCaption::GetColor

Vrátí barvu pozadí popisku.

```
AFX_RibbonCategoryColor GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota může být jeden z následujících hodnot výčtu:

- `AFX_CategoryColor_None`

- `AFX_CategoryColor_Red`

- `AFX_CategoryColor_Orange`

- `AFX_CategoryColor_Yellow`

- `AFX_CategoryColor_Green`

- `AFX_CategoryColor_Blue`

- `AFX_CategoryColor_Indigo`

- `AFX_CategoryColor_Violet`

### <a name="remarks"></a>Poznámky

Barva záhlaví lze nastavit pomocí volání [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor) nebo [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

##  <a name="getrighttabx"></a>  CMFCRibbonContextCaption::GetRightTabX

Načte pozici pravém okraji kategorie pásu karet.

```
int GetRightTabX() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí pravou hodnotu X z ohraničující obdélník `CMFCRibbonCategory` objektu pásu karet, nebo hodnota -1, pokud je zkrácen na kartě.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonCategory – třída](../../mfc/reference/cmfcribboncategory-class.md)<br/>
[CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
