---
title: Cmfcribbonlabel – třída
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
ms.openlocfilehash: ae185a81267dce68cda6bc27c5e327b3335a1018
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436396"
---
# <a name="cmfcribbonlabel-class"></a>Cmfcribbonlabel – třída

Implementuje neklikatelné textový popisek pro pás karet.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Vytvoří a inicializuje `CMFCRibbonLabel` objektu zadaného textovým řetězcem.|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCRibbonLabel::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCRibbonLabel::SetACCData](#setaccdata)|Určuje usnadnění dat pro aktuální popisek prvek pásu karet. (Přepíše [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

### <a name="remarks"></a>Poznámky

Po vytvoření popisku pásu karet, přidejte ho do panelu voláním [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

Nelze přidat popisek pásu karet na panelu nástrojů Rychlý přístup.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)

[Cmfcribbonbutton –](../../mfc/reference/cmfcribbonbutton-class.md)

[Cmfcribbonlabel –](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonLabel.h

##  <a name="cmfcribbonlabel"></a>  CMFCRibbonLabel::CMFCRibbonLabel

Vytvoří a inicializuje [cmfcribbonlabel –](../../mfc/reference/cmfcribbonlabel-class.md) objekt, který zobrazí zadaný text řetězce.

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[in] Text, který se zobrazí v popisku.

*bIsMultiLine*<br/>
[in] TRUE, pokud chcete určit, že popisek je Víceřádkový popisek; v opačném případě hodnota FALSE.

##  <a name="setaccdata"></a>  CMFCRibbonLabel::SetACCData

Určuje usnadnění dat pro aktuální popisek prvek pásu karet.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
[in] Představuje nadřazené okno aktuální popisku pásu karet.

*data*<br/>
[out] Objekt typu `CAccessibilityData` , který je naplněný daty usnadnění aktuální popisku pásu karet.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud *data* parametr byl úspěšně naplněný daty usnadnění aktuální popisku pásu karet; v opačném případě hodnota FALSE.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
