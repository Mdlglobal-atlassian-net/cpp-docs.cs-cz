---
title: CMFCRibbonLabel – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
ms.openlocfilehash: cd30e374441661368d3ea7abf5177424f8dffb3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375127"
---
# <a name="cmfcribbonlabel-class"></a>CMFCRibbonLabel – třída

Implementuje textový popisek pásu karet, na který se neklikat.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Vytvoří a inicializuje `CMFCRibbonLabel` objekt se zadaným textovým řetězcem.|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCRibbonLabel::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCRibbonLabel::SetACCData](#setaccdata)|Určuje data usnadnění pro aktuální prvek popisku pásu karet. (Přepíše [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

### <a name="remarks"></a>Poznámky

Po vytvoření štítku pásu karet jej přidejte do panelu voláním [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

Popisek pásu karet nelze přidat na panel nástrojů Rychlý přístup.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CmFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CmFCještítek](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonLabel.h

## <a name="cmfcribbonlabelcmfcribbonlabel"></a><a name="cmfcribbonlabel"></a>CMFCRibbonLabel::CMFCRibbonLabel

Vytvoří a inicializuje objekt [CMFCRibbonLabel,](../../mfc/reference/cmfcribbonlabel-class.md) který zobrazuje zadaný textový řetězec.

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[v] Text, který se zobrazí v popisku.

*bIsMultiLine*<br/>
[v] TRUE, chcete-li určit, že popisek je víceřádkový popisek; jinak NEPRAVDA.

## <a name="cmfcribbonlabelsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonLabel::SetACCData

Určuje data usnadnění pro aktuální prvek popisku pásu karet.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
[v] Představuje nadřazené okno aktuálního popisku pásu karet.

*Dat*<br/>
[out] Objekt typu, `CAccessibilityData` který je naplněn daty usnadnění aktuálního popisku pásu karet.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl parametr *dat* úspěšně naplněn daty usnadnění aktuálního štítku pásu karet; jinak NEPRAVDA.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
