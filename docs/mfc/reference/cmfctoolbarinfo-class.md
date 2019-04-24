---
title: CMFCToolBarInfo Class
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
ms.openlocfilehash: b2f8af439a2534f24cdba9b0ccdb12b150db6d0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217800"
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo Class

Obsahuje ID obrázků panelu nástrojů v různých stavech prostředků. `CMFCToolBarInfo` je pomocnou třídu, která se používá jako parametr [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) metody.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarInfo
```

## <a name="members"></a>Členové

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|ID prostředku rastrového obrázku panelu nástrojů, který obsahuje obrázky panelu nástrojů regulární (studená).|
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|ID prostředku rastrového obrázku panelu nástrojů, který obsahuje obrázky panelu nástrojů zakázané.|
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|ID prostředku rastrového obrázku panelu nástrojů, který obsahuje obrázky panelu nástrojů vybrané (hot).|
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|ID prostředku, který obsahuje obrázky panelu nástrojů velké a pravidelné rastrového obrázku panelu nástrojů.|
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|ID prostředku rastrového obrázku panelu nástrojů, které obsahuje velké, zakázané obrázky panelu nástrojů.|
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|ID prostředku rastrového obrázku panelu nástrojů, které obsahuje velké, vybrat obrázky panelu nástrojů.|
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|ID prostředku rastrového obrázku panelu nástrojů, který obsahuje zakázané nabídky Image.|
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|ID prostředku rastrového obrázku panelu nástrojů, který obsahuje nabídky Image.|

## <a name="remarks"></a>Poznámky

Rastrový obrázek úplné nástrojů se skládá z nástrojů malé obrázky (tlačítka) s pevnou velikostí. Každé ID prostředku, který je uložený v `CMFCToolBarInfo` rastrový obrázek, který obsahuje úplnou sadu obrázků panelu nástrojů v jednoho státu (pro příklad vybrali, zakázáno, velká nebo nabídky imagí) je objekt.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbar.h

##  <a name="m_uicoldresid"></a>  CMFCToolBarInfo::m_uiColdResID

Určuje Identifikátor prostředku pro všechny Image běžné tlačítko panelu nástrojů.

```
UINT m_uiColdResID;
```

##  <a name="m_uidisabledresid"></a>  CMFCToolBarInfo::m_uiDisabledResID

Určuje Identifikátor prostředku pro Image není k dispozici tlačítko panelu nástrojů.

```
UINT m_uiDisabledResID;
```

##  <a name="m_uihotresid"></a>  CMFCToolBarInfo::m_uiHotResID

Určuje Identifikátor prostředku pro všechny Image zvýrazněné tlačítko panelu nástrojů.

```
UINT m_uiHotResID
```

##  <a name="m_uilargecoldresid"></a>  CMFCToolBarInfo::m_uiLargeColdResID

Určuje Identifikátor prostředku pro všechny Image velké běžné tlačítko panelu nástrojů.

```
UINT m_uiLargeColdResID
```

##  <a name="m_uilargedisabledresid"></a>  CMFCToolBarInfo::m_uiLargeDisabledResID

Určuje Identifikátor prostředku pro všechny Image velké zakázané tlačítko panelu nástrojů.

```
UINT m_uiLargeDisabledResID;
```

##  <a name="m_uilargehotresid"></a>  CMFCToolBarInfo::m_uiLargeHotResID

Určuje Identifikátor prostředku pro všechny velké zvýrazněné obrázky panelu nástrojů.

```
UINT m_uiLargeHotResID;
```

##  <a name="m_uimenudisabledresid"></a>  CMFCToolBarInfo::m_uiMenuDisabledResID

Určuje Identifikátor prostředku není k dispozici příkaz obrázků panelu nástrojů.

```
UINT m_uiMenuDisabledResID;
```

##  <a name="m_uimenuresid"></a>  CMFCToolBarInfo::m_uiMenuResID

Určuje Identifikátor prostředku pro všechny obrázků položek regulární nabídky panelu nástrojů.

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)
