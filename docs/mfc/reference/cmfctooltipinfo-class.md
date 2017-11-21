---
title: "Třída CMFCToolTipInfo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d846818d7b0ac7df07ad00ffbb2e71e1e5be8a7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfctooltipinfo-class"></a>CMFCToolTipInfo – třída
Obsahuje informace o vzhled popisů tlačítek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolTipInfo  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolTipInfo::operator =](#operator_eq)||  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolTipInfo::m_bBalloonTooltip](#m_bballoontooltip)|Logická hodnota proměnné, která označuje, zda má popisek vzhled bublina.|  
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|Logická hodnota proměnné, která označuje, zda jsou zobrazeny popisky popisek tučným písmem.|  
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|Logická hodnota proměnné, která určuje, zda se popisek obsahuje popis.|  
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|Logická hodnota proměnné, která určuje, zda se popisek obsahuje ikonu.|  
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|Logická hodnota proměnné, která označuje, zda oddělovač zobrazuje až popis popisek popisek popisek.|  
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|Logická hodnota proměnné, která označuje, zda má popisek zaokrouhlené rozích.|  
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|Logická hodnota proměnné, která označuje, zda visual Správce by měl řídí vzhled popisek (najdete v části [CMFCVisualManager třída](../../mfc/reference/cmfcvisualmanager-class.md)).|  
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|Barva ohraničení popisku.|  
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|Barva pozadí popisu tlačítka.|  
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|Barva výplně přechodu v popisu tlačítka.|  
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|Barva textu v popisu tlačítka.|  
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|Úhel přechod, který v popisu tlačítka.|  
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|Maximální možné šířka v pixelech popis v popisu tlačítka.|  
  
## <a name="remarks"></a>Poznámky  
 Použití [CMFCToolTipCtrl třída](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, a [CTooltipManager třída](../../mfc/reference/ctooltipmanager-class.md) dohromady a implementovat vlastní popisy tlačítek v aplikaci. Příklad použití těchto tříd popis v tématu [CMFCToolTipCtrl třída](../../mfc/reference/cmfctooltipctrl-class.md) tématu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit hodnoty různých členské proměnné v `CMFCToolTipInfo` třídy.  
  
 [!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtooltipctrl.h  
  
##  <a name="m_bballoontooltip"></a>CMFCToolTipInfo::m_bBalloonTooltip  
 Určuje styl zobrazení všechny popisy tlačítek.  
  
```  
BOOL m_bBalloonTooltip;  
```  
  
### <a name="remarks"></a>Poznámky  
 `TRUE`Označuje, že popisy tlačítek používat styl bublinách `FALSE` označuje, že popisy tlačítek používat styl obdélníkový.  
  
##  <a name="m_bboldlabel"></a>CMFCToolTipInfo::m_bBoldLabel  
 Určuje, jestli je tučné písmo textu popisku.  
  
```  
BOOL m_bBoldLabel;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen nastavit na `TRUE` zobrazíte text popisu tlačítka s tučným písmem nebo `FALSE` pro zobrazení popisků popisek s-tučné písmo.  
  
##  <a name="m_bdrawdescription"></a>CMFCToolTipInfo::m_bDrawDescription  
 Určuje, zda každý popisek zobrazí text popisu.  
  
```  
BOOL m_bDrawDescription;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen nastavit na `TRUE` zobrazíte popis, nebo `FALSE` ke skrytí popis. Můžete zadat popis na popisek voláním [CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)  
  
##  <a name="m_bdrawicon"></a>CMFCToolTipInfo::m_bDrawIcon  
 Určuje, zda všechny popisy tlačítek zobrazení ikon.  
  
```  
BOOL m_bDrawIcon;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen nastavit na `TRUE` zobrazíte ikonu na každý popisek nebo `FALSE` zobrazíte popisy tlačítek bez ikon.  
  
##  <a name="m_bdrawseparator"></a>CMFCToolTipInfo::m_bDrawSeparator  
 Určuje, zda je každý popisek oddělovač mezi její popisek a její popis.  
  
```  
BOOL m_bDrawSeparator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen nastavit na `TRUE` zobrazíte oddělovače mezi popisek popisek a popis, nebo `FALSE` zobrazíte popisy tlačítek bez oddělovače.  
  
##  <a name="m_broundedcorners"></a>CMFCToolTipInfo::m_bRoundedCorners  
 Určuje, zda mají všechny popisy tlačítek zaokrouhlené rozích.  
  
```  
BOOL m_bRoundedCorners;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen nastavit na `TRUE` zobrazíte zaoblenými hranami na popisy tlačítek, nebo `FALSE` zobrazíte obdélníková rozích na popisy tlačítek.  
  
##  <a name="m_clrborder"></a>CMFCToolTipInfo::m_clrBorder  
 Určuje barvu ohraničení na všechny popisy tlačítek.  
  
```  
COLORREF m_clrBorder;  
```  
  
##  <a name="m_clrfill"></a>CMFCToolTipInfo::m_clrFill  
 Určuje barvu pozadí popisku.  
  
```  
COLORREF m_clrFill;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) je -1, je barvě pozadí `m_clrFill`. V opačném `m_clrFill` Určuje barvu barevného přechodu začátku a `m_clrFillGradient` Určuje barvu konce přechodu. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) Určuje směr, barevného přechodu.  
  
##  <a name="m_clrfillgradient"></a>CMFCToolTipInfo::m_clrFillGradient  
 Určuje koncovou barvu barevného přechodu pozadí pro popisy tlačítek.  
  
```  
COLORREF m_clrFillGradient;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `m_clrFillGradient` je -1, neexistuje žádný přechodu. Jinak je zadána počáteční barvu barevného přechodu [CMFCToolTipInfo::m_clrFill](#m_clrfill) a je zadána barvu barevného přechodu Dokončit `m_clrFillGradient`. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) Určuje směr, barevného přechodu.  
  
##  <a name="m_clrtext"></a>CMFCToolTipInfo::m_clrText  
 Určuje barvu textu všechny popisy tlačítek.  
  
```  
COLORREF m_clrText;  
```  
  
##  <a name="m_ngradientangle"></a>CMFCToolTipInfo::m_nGradientAngle  
 Určuje úhel, ve kterém se nevykreslí přechod na pozadí popisy tlačítek.  
  
```  
int m_nGradientAngle;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_nGradientAngle`Určuje, o úhel ve stupních, že je přechodu na pozadí popisy tlačítek UN od vodorovných. Pokud `m_nGradientAngle` je 0, má barevný přechod vykreslením zleva doprava. Pokud `m_nGradientAngle` je mezi 1 a 360, je po směru hodinových ručiček otáčení přechodu počet stupňů. Pokud `m_nGradientAngle` -1, což je výchozí hodnota, se má barevný přechod vykreslením shora dolů. Je to stejné jako nastavení `m_nGradientAngle` a 90.  
  
 [CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill` Určuje barvu barevného přechodu začátku a [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient` Určuje barvu konce přechodu. Pokud `m_clrFillGradient` je -1, neexistuje žádný přechodu.  
  
##  <a name="m_nmaxdescrwidth"></a>CMFCToolTipInfo::m_nMaxDescrWidth  
 Určuje maximální šířku popis, který se zobrazí v každé popisku. Pokud šířku popis překročí zadanou hodnotu, je zabalená text.  
  
```  
int m_nMaxDescrWidth;  
```  
  
##  <a name="m_bvislmanagertheme"></a>CMFCToolTipInfo::m_bVislManagerTheme  
 Určuje, zda správce visual aplikace řídí vzhled všechny popisy tlačítek.  
  
```  
BOOL m_bVislManagerTheme;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `m_bVislManagerTheme` je `TRUE`, každý popisek požadavky nové [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) ze visual správce aplikace předtím, než se zobrazí na obrazovce a určit jejich vzhled používá hodnoty v tomto objektu. Ostatní členové vaší [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) jsou ignorovány.  
  
##  <a name="operator_eq"></a>CMFCToolTipInfo::operator =  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`src`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CTooltipManager – třída](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipCtrl – třída](../../mfc/reference/cmfctooltipctrl-class.md)
