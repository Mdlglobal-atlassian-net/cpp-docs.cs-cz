---
title: Třída CMFCToolBarInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de968fe53348b4cfa3f46e999da37cdca6f88c90
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369359"
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo – třída
Obsahuje ID obrázků panelu nástrojů v různé stavy prostředků. `CMFCToolBarInfo` je pomocná třída, která se používá jako parametr [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarInfo  
```  
  
## <a name="members"></a>Členové  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|ID prostředku rastrového obrázku panelu nástrojů, který obsahuje regulární panelu nástrojů (cold) bitových kopií.|  
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|ID prostředku bitové mapy nástrojů, které obsahuje zakázané nástrojů bitových kopií.|  
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|ID prostředku bitové mapy nástrojů, které obsahuje bitových kopií vybrané panelu nástrojů (aktivní).|  
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|ID prostředku bitové mapy nástrojů, které obsahuje bitových kopií velký, regulární panelu nástrojů.|  
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|ID prostředku rastrového obrázku panelu nástrojů, který obsahuje velký, zakázané obrázků panelu nástrojů.|  
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|ID prostředku rastrového obrázku panelu nástrojů, který obsahuje velký, vybrat obrázků panelu nástrojů.|  
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|ID prostředku bitové mapy nástrojů, které obsahuje zakázané nabídky bitových kopií.|  
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|ID prostředku bitové mapy nástrojů, které obsahuje nabídky bitových kopií.|  
  
## <a name="remarks"></a>Poznámky  
 Rastrový obrázek úplný panel nástrojů se skládá z Image malý panel nástrojů (tlačítka) s pevnou velikostí. Každý ID prostředku, který je uložen v `CMFCToolBarInfo` objekt je rastrový obrázek, který obsahuje úplnou sadu obrázků panelu nástrojů v jednom stavu (pro příklad, vybrali, zakázáno, velký nebo nabídky Image).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbar.h  
  
##  <a name="m_uicoldresid"></a>  CMFCToolBarInfo::m_uiColdResID  
 Určuje ID prostředku pro všechny Image regulární tlačítka panelu nástrojů.  
  
```  
UINT m_uiColdResID;  
```  
  
##  <a name="m_uidisabledresid"></a>  CMFCToolBarInfo::m_uiDisabledResID  
 Určuje ID prostředku pro Image není k dispozici tlačítko panelu nástrojů.  
  
```  
UINT m_uiDisabledResID;  
```  
  
##  <a name="m_uihotresid"></a>  CMFCToolBarInfo::m_uiHotResID  
 Určuje ID prostředku pro všechny Image zvýrazněné tlačítko panelu nástrojů.  
  
```  
UINT m_uiHotResID  
```  
  
##  <a name="m_uilargecoldresid"></a>  CMFCToolBarInfo::m_uiLargeColdResID  
 Určuje ID prostředku pro všechny Image velké regulární tlačítko panelu nástrojů.  
  
```  
UINT m_uiLargeColdResID  
```  
  
##  <a name="m_uilargedisabledresid"></a>  CMFCToolBarInfo::m_uiLargeDisabledResID  
 Určuje ID prostředku pro všechny Image velké zakázané tlačítko panelu nástrojů.  
  
```  
UINT m_uiLargeDisabledResID;  
```  
  
##  <a name="m_uilargehotresid"></a>  CMFCToolBarInfo::m_uiLargeHotResID  
 Určuje ID prostředku pro všechny velkých zvýrazněná obrázků panelu nástrojů.  
  
```  
UINT m_uiLargeHotResID;  
```  
  
##  <a name="m_uimenudisabledresid"></a>  CMFCToolBarInfo::m_uiMenuDisabledResID  
 Určuje ID prostředku není k dispozici příkaz obrázků panelu nástrojů.  
  
```  
UINT m_uiMenuDisabledResID;  
```  
  
##  <a name="m_uimenuresid"></a>  CMFCToolBarInfo::m_uiMenuResID  
 Určuje ID prostředku pro všechny Image položky regulární nabídky panelu nástrojů.  
  
```  
UINT m_uiMenuResID;  
```  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)
