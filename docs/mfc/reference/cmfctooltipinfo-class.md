---
title: CMFCToolTipInfo – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBalloonTooltip
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBoldLabel
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bRoundedCorners
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bVislManagerTheme
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrBorder
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFill
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFillGradient
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrText
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nGradientAngle
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nMaxDescrWidth
helpviewer_keywords:
- CMFCToolTipInfo [MFC], m_bBalloonTooltip
- CMFCToolTipInfo [MFC], m_bBoldLabel
- CMFCToolTipInfo [MFC], m_bDrawDescription
- CMFCToolTipInfo [MFC], m_bDrawIcon
- CMFCToolTipInfo [MFC], m_bDrawSeparator
- CMFCToolTipInfo [MFC], m_bRoundedCorners
- CMFCToolTipInfo [MFC], m_bVislManagerTheme
- CMFCToolTipInfo [MFC], m_clrBorder
- CMFCToolTipInfo [MFC], m_clrFill
- CMFCToolTipInfo [MFC], m_clrFillGradient
- CMFCToolTipInfo [MFC], m_clrText
- CMFCToolTipInfo [MFC], m_nGradientAngle
- CMFCToolTipInfo [MFC], m_nMaxDescrWidth
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
ms.openlocfilehash: 000a2fd33928e59685efa6f145406542a4935819
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377340"
---
# <a name="cmfctooltipinfo-class"></a>CMFCToolTipInfo – třída

Ukládá informace o vizuálnívzhled popisů.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolTipInfo
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCToolTipInfo::operátor=](#operator_eq)||

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCToolTipInfo::m_bBalloonTooltip](#m_bballoontooltip)|Logická proměnná, která označuje, zda má popisek vzhled pozice.|
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|Logická proměnná, která označuje, zda popisky popisků jsou zobrazeny tučným písmem.|
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|Logická proměnná, která označuje, zda popis obsahuje popis.|
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|Logická proměnná, která označuje, zda popis obsahuje ikonu.|
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|Logická proměnná, která označuje, zda je mezi popiskem popisku popisku a popisem popisku zobrazen oddělovač.|
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|Logická proměnná, která označuje, zda má popisek zaoblené rohy.|
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|Logická proměnná, která označuje, zda by měl být vzhled popisku řízen vizuálním manažerem (viz [TŘÍDA CMFCVisualManager).](../../mfc/reference/cmfcvisualmanager-class.md)|
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|Barva ohraničení popisku.|
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|Barva pozadí popisku.|
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|Barva přechodu vyplňuje popis.|
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|Barva textu v popisku.|
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|Úhel přechodu vyplňuje popisek.|
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|Maximální možná šířka popisu v popiscích v obrazových bodech v obrazových bodech.|

## <a name="remarks"></a>Poznámky

Pomocí [třídy CMFCToolTipCtrl class](../../mfc/reference/cmfctooltipctrl-class.md) `CMFCToolTipInfo`a [CTooltipManager class](../../mfc/reference/ctooltipmanager-class.md) společně implementujte vlastní popisy nástrojů ve vaší aplikaci. Příklad použití těchto tříd popisů naleznete v tématu [třídy CMFCToolTipCtrl.](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nastavit hodnoty různých proměnných `CMFCToolTipInfo` členů ve třídě.

[!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CmFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtooltipctrl.h

## <a name="cmfctooltipinfom_bballoontooltip"></a><a name="m_bballoontooltip"></a>CMFCToolTipInfo::m_bBalloonTooltip

Určuje styl zobrazení všech popisků.

```
BOOL m_bBalloonTooltip;
```

### <a name="remarks"></a>Poznámky

PRAVDA označuje, že popisky používají styl pozice, FALSE označuje, že popisky používají obdélníkový styl.

## <a name="cmfctooltipinfom_bboldlabel"></a><a name="m_bboldlabel"></a>CMFCToolTipInfo::m_bBoldLabel

Určuje, zda je písmo textu popisu tučné.

```
BOOL m_bBoldLabel;
```

### <a name="remarks"></a>Poznámky

Nastavte tento člen na HODNOTU TRUE, aby zobrazoval text popisu tučným písmem, nebo NEPRAVDA, chcete-li zobrazit popisky popisků popisků s netučným písmem.

## <a name="cmfctooltipinfom_bdrawdescription"></a><a name="m_bdrawdescription"></a>CMFCToolTipInfo::m_bDrawDescription

Určuje, zda se v jednotlivých popiscích zobrazí popisný text.

```
BOOL m_bDrawDescription;
```

### <a name="remarks"></a>Poznámky

Nastavte tento člen na HODNOTU TRUE, aby se zobrazil popis, nebo NEPRAVDA, chcete-li popis skrýt. Popis v popisku můžete zadat voláním [CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)

## <a name="cmfctooltipinfom_bdrawicon"></a><a name="m_bdrawicon"></a>CMFCToolTipInfo::m_bDrawIcon

Určuje, zda se ve všech popiscích zobrazují ikony.

```
BOOL m_bDrawIcon;
```

### <a name="remarks"></a>Poznámky

Nastavte tento člen na HODNOTU TRUE, aby se v každém popisku zobrazila ikona, nebo NEPRAVDA, chcete-li zobrazit popisky bez ikon.

## <a name="cmfctooltipinfom_bdrawseparator"></a><a name="m_bdrawseparator"></a>CMFCToolTipInfo::m_bDrawSeparator

Určuje, zda má každý popisek oddělovač mezi popiskem a popisem.

```
BOOL m_bDrawSeparator;
```

### <a name="remarks"></a>Poznámky

Nastavte tento člen na HODNOTU TRUE, aby se zobrazil oddělovač mezi popiskem popisku a popisem popisku, nebo NEPRAVDA, chcete-li zobrazit popisky bez oddělovače.

## <a name="cmfctooltipinfom_broundedcorners"></a><a name="m_broundedcorners"></a>CMFCToolTipInfo::m_bRoundedCorners

Určuje, zda mají všechny popisky zaoblené rohy.

```
BOOL m_bRoundedCorners;
```

### <a name="remarks"></a>Poznámky

Nastavte tento člen na HODNOTU TRUE, aby se na popiscích zobrazoval zaoblené rohy, nebo NEPRAVDA, aby se na popiscích zobrazoval obdélníkové rohy.

## <a name="cmfctooltipinfom_clrborder"></a><a name="m_clrborder"></a>CMFCToolTipInfo::m_clrBorder

Určuje barvu ohraničení ve všech popiscích.

```
COLORREF m_clrBorder;
```

## <a name="cmfctooltipinfom_clrfill"></a><a name="m_clrfill"></a>CMFCToolTipInfo::m_clrFill

Určuje barvu pozadí popisu.

```
COLORREF m_clrFill;
```

### <a name="remarks"></a>Poznámky

Pokud [cmfctooltipinfo::m_clrFillGradient](#m_clrfillgradient) je -1, popisek `m_clrFill`pozadí je . V `m_clrFill` opačném případě určuje barvu začátku `m_clrFillGradient` přechodu a barvu konce přechodu. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) určuje směr přechodu.

## <a name="cmfctooltipinfom_clrfillgradient"></a><a name="m_clrfillgradient"></a>CMFCToolTipInfo::m_clrFillGradient

Určuje koncovou barvu pozadí přechodu pro popisky.

```
COLORREF m_clrFillGradient;
```

### <a name="remarks"></a>Poznámky

Pokud `m_clrFillGradient` je -1, neexistuje žádný přechod. V opačném případě je počáteční barva přechodu určena [cmfctooltipinfo::m_clrFill](#m_clrfill) a barva dokončení přechodu je určena . `m_clrFillGradient` [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) určuje směr přechodu.

## <a name="cmfctooltipinfom_clrtext"></a><a name="m_clrtext"></a>CMFCToolTipInfo::m_clrText

Určuje barvu textu všech popisků.

```
COLORREF m_clrText;
```

## <a name="cmfctooltipinfom_ngradientangle"></a><a name="m_ngradientangle"></a>CMFCToolTipInfo::m_nGradientAngle

Určuje úhel, pod kterým je přechod nakreslen na pozadí popisků.

```
int m_nGradientAngle;
```

### <a name="remarks"></a>Poznámky

`m_nGradientAngle`určuje úhel ve stupních, že přechod na pozadí popisků je odsazen od vodorovné polohy. Pokud `m_nGradientAngle` je 0, přechod je nakreslena zleva doprava. Pokud `m_nGradientAngle` je mezi 1 a 360, přechod se otáčí ve směru hodinových ručiček o tento počet stupňů. Pokud `m_nGradientAngle` je -1, což je výchozí hodnota, přechod je nakreslena shora dolů. To je stejné `m_nGradientAngle` jako nastavení na 90.

[CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill` určuje barvu začátku přechodu a [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient` určuje barvu konce přechodu. Pokud `m_clrFillGradient` je -1, neexistuje žádný přechod.

## <a name="cmfctooltipinfom_nmaxdescrwidth"></a><a name="m_nmaxdescrwidth"></a>CMFCToolTipInfo::m_nMaxDescrWidth

Určuje maximální šířku popisu, který se zobrazuje v jednotlivých popiscích. Pokud šířka popisu překročí zadanou hodnotu, text se zalome.

```
int m_nMaxDescrWidth;
```

## <a name="cmfctooltipinfom_bvislmanagertheme"></a><a name="m_bvislmanagertheme"></a>CMFCToolTipInfo::m_bVislManagerTheme

Určuje, zda vizuální správce aplikace řídí vzhled všech popisů.

```
BOOL m_bVislManagerTheme;
```

### <a name="remarks"></a>Poznámky

Pokud `m_bVislManagerTheme` je TRUE, každý popis požaduje nový [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) od vizuálnísprávce aplikace před jejich zobrazení na obrazovce a používá hodnoty v tomto objektu k určení jejich vzhledu. Ostatní členové [cmfcToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) jsou ignorovány.

## <a name="cmfctooltipinfooperator"></a><a name="operator_eq"></a>CMFCToolTipInfo::operátor=

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```

### <a name="parameters"></a>Parametry

[v] *src*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CTooltipManager – třída](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipCtrl – třída](../../mfc/reference/cmfctooltipctrl-class.md)
