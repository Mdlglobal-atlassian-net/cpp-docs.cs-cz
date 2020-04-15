---
title: Třída CMFCToolBarInfo
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
ms.openlocfilehash: 593d1665751f7322fc2a9cee307620df88d46876
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376197"
---
# <a name="cmfctoolbarinfo-class"></a>Třída CMFCToolBarInfo

Obsahuje ID prostředků obrazů panelů nástrojů v různých stavech. `CMFCToolBarInfo`je pomocná třída, která se používá jako parametr metody [CMFCToolBar::LoadToolBarEx.](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex)

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarInfo
```

## <a name="members"></a>Členové

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|ID prostředku bitmapy panelu nástrojů, která obsahuje pravidelné (studené) obrazy panelu nástrojů.|
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|ID prostředku bitmapy panelu nástrojů, která obsahuje zakázané obrazy panelu nástrojů.|
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|ID prostředku bitmapy panelu nástrojů, která obsahuje vybrané (horké) obrazy panelu nástrojů.|
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|ID prostředku bitmapy panelu nástrojů, která obsahuje velké, pravidelné obrazy panelu nástrojů.|
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|ID prostředku bitmapy panelu nástrojů, která obsahuje velké, zakázané obrazy panelu nástrojů.|
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|ID prostředku bitmapy panelu nástrojů, která obsahuje velké vybrané obrazy panelu nástrojů.|
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|ID prostředku bitmapy panelu nástrojů, která obsahuje zakázané obrazy nabídky.|
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|ID prostředku bitmapy panelu nástrojů, která obsahuje obrazy nabídky.|

## <a name="remarks"></a>Poznámky

Plná bitmapa panelu nástrojů se skládá z malých obrazů panelu nástrojů (tlačítek) pevné velikosti. Každé ID prostředku, které `CMFCToolBarInfo` je uloženo v objektu, je bitmapa, která obsahuje úplnou sadu obrazů panelu nástrojů v jednom stavu (například vybrané, zakázané, velké nebo nabídky obrazů).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbar.h

## <a name="cmfctoolbarinfom_uicoldresid"></a><a name="m_uicoldresid"></a>CMFCToolBarInfo::m_uiColdResID

Určuje ID prostředku pro všechny běžné obrazy tlačítek panelu nástrojů.

```
UINT m_uiColdResID;
```

## <a name="cmfctoolbarinfom_uidisabledresid"></a><a name="m_uidisabledresid"></a>CMFCToolBarInfo::m_uiDisabledResID

Určuje ID prostředku pro obrazy panelu nástrojů, které nejsou k dispozici.

```
UINT m_uiDisabledResID;
```

## <a name="cmfctoolbarinfom_uihotresid"></a><a name="m_uihotresid"></a>CMFCToolBarInfo::m_uiHotResID

Určuje ID prostředku pro všechny zvýrazněné obrazy tlačítek panelu nástrojů.

```
UINT m_uiHotResID
```

## <a name="cmfctoolbarinfom_uilargecoldresid"></a><a name="m_uilargecoldresid"></a>CMFCToolBarInfo::m_uiLargeColdResID

Určuje ID prostředku pro všechny velké obrazy pravidelných tlačítek na panelu nástrojů.

```
UINT m_uiLargeColdResID
```

## <a name="cmfctoolbarinfom_uilargedisabledresid"></a><a name="m_uilargedisabledresid"></a>CMFCToolBarInfo::m_uiLargeDisabledResID

Určuje ID prostředku pro všechny velké zakázané obrazy tlačítek panelu nástrojů.

```
UINT m_uiLargeDisabledResID;
```

## <a name="cmfctoolbarinfom_uilargehotresid"></a><a name="m_uilargehotresid"></a>CMFCToolBarInfo::m_uiLargeHotResID

Určuje ID prostředku pro všechny velké zvýrazněné obrazy panelu nástrojů.

```
UINT m_uiLargeHotResID;
```

## <a name="cmfctoolbarinfom_uimenudisabledresid"></a><a name="m_uimenudisabledresid"></a>CMFCToolBarInfo::m_uiMenuDisabledResID

Určuje ID prostředku pro obrazy panelu nástrojů, které nejsou k dispozici příkazem.

```
UINT m_uiMenuDisabledResID;
```

## <a name="cmfctoolbarinfom_uimenuresid"></a><a name="m_uimenuresid"></a>CMFCToolBarInfo::m_uiMenuResID

Určuje ID prostředku pro všechny běžné obrazy položek nabídky na panelu nástrojů.

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)
