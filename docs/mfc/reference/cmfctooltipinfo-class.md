---
title: Cmfctooltipinfo – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: babc490d63f6c7e1692877e53b4971fc85ec4c24
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850888"
---
# <a name="cmfctooltipinfo-class"></a>Cmfctooltipinfo – třída
Ukládá informace o vzhled popisů tlačítek.  
  
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
|[CMFCToolTipInfo::m_bBalloonTooltip](#m_bballoontooltip)|Proměnné typu Boolean určující, zda má popisek bublinu vzhled.|  
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|Proměnné typu Boolean označující, zda popisek popisky jsou zobrazeny tučným písmem.|  
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|Proměnné typu Boolean označující, zda popisek obsahuje popis.|  
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|Proměnné typu Boolean označující, zda popisek obsahuje ikonu.|  
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|Proměnné typu Boolean určující, zda je zobrazen oddělovač mezi popiskem popisek a Popis popisku.|  
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|Proměnné typu Boolean označující, zda má popisek zaoblené rohy.|  
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|Proměnné typu Boolean označující, zda by měl vzhled ovládacího prvku tooltip řídí správce vzhledu (viz [cmfcvisualmanager – třída](../../mfc/reference/cmfcvisualmanager-class.md)).|  
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|Barva ohraničení popisu tlačítka.|  
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|Barva pozadí popisu tlačítka.|  
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|Barva přechodu výplně v popisu.|  
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|Barva textu v popisku.|  
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|Úhel přechodovou výplní v popisu.|  
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|Maximální možná šířka v pixelech popis v popisu.|  
  
## <a name="remarks"></a>Poznámky  
 Použití [cmfctooltipctrl – třída](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, a [ctooltipmanager – třída](../../mfc/reference/ctooltipmanager-class.md) společně k implementaci vlastní popisy ve vaší aplikaci. Příklad použití těchto tříd popisu tlačítka, najdete v článku [cmfctooltipctrl – třída](../../mfc/reference/cmfctooltipctrl-class.md) tématu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit hodnoty různých členské proměnné `CMFCToolTipInfo` třídy.  
  
 [!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Cmfctooltipinfo –](../../mfc/reference/cmfctooltipinfo-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtooltipctrl.h  
  
##  <a name="m_bballoontooltip"></a>  CMFCToolTipInfo::m_bBalloonTooltip  
 Určuje styl zobrazení všechny popisky.  
  
```  
BOOL m_bBalloonTooltip;  
```  
  
### <a name="remarks"></a>Poznámky  
 TRUE znamená, že popisky použít stylu bublin, hodnota FALSE označuje, že popisky používat obdélníkové styl.  
  
##  <a name="m_bboldlabel"></a>  CMFCToolTipInfo::m_bBoldLabel  
 Určuje, zda je tučné písmo textu popisku.  
  
```  
BOOL m_bBoldLabel;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte tento člen na true pro zobrazení popisu tlačítka text tučné písmo, nebo hodnotu NEPRAVDA pro zobrazení popisu tlačítka popisky s tučné písmo.  
  
##  <a name="m_bdrawdescription"></a>  CMFCToolTipInfo::m_bDrawDescription  
 Určuje, zda každý popisek zobrazí text popisu.  
  
```  
BOOL m_bDrawDescription;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte tento člen pro hodnotu PRAVDA, zobrazení popisu, nebo FALSE, chcete-li skrýt popis. Můžete zadat popis v popisu voláním [CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)  
  
##  <a name="m_bdrawicon"></a>  CMFCToolTipInfo::m_bDrawIcon  
 Určuje, zda všechny popisy zobrazení ikon.  
  
```  
BOOL m_bDrawIcon;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen nastavte na TRUE zobrazíte ikonu na každý popisek, nebo FALSE, pokud chcete zobrazit popisy tlačítek bez ikony.  
  
##  <a name="m_bdrawseparator"></a>  CMFCToolTipInfo::m_bDrawSeparator  
 Určuje, zda má každý popis oddělovač mezi popiskem a jeho popis.  
  
```  
BOOL m_bDrawSeparator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen nastavena na hodnotu TRUE, chcete-li zobrazit oddělovač mezi popisek popisek a popis nebo FALSE, pokud chcete zobrazit popisy tlačítek s žádný oddělovač.  
  
##  <a name="m_broundedcorners"></a>  CMFCToolTipInfo::m_bRoundedCorners  
 Určuje, zda všechny popisky mají zaoblené rohy.  
  
```  
BOOL m_bRoundedCorners;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte tento člen pro hodnotu PRAVDA, zobrazení zaoblení rohů popisy tlačítek, nebo hodnotu FALSE pro zobrazení obdélníkové rohů na popisky.  
  
##  <a name="m_clrborder"></a>  CMFCToolTipInfo::m_clrBorder  
 Určuje barvu ohraničení na všechny popisky.  
  
```  
COLORREF m_clrBorder;  
```  
  
##  <a name="m_clrfill"></a>  CMFCToolTipInfo::m_clrFill  
 Určuje barvu pozadí popisku.  
  
```  
COLORREF m_clrFill;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) se -1, je barvě pozadí `m_clrFill`. V opačném případě `m_clrFill` Určuje barvu počátek přechodu a `m_clrFillGradient` určuje barvy ukončení přechodu. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) Určuje směr přechodu.  
  
##  <a name="m_clrfillgradient"></a>  CMFCToolTipInfo::m_clrFillGradient  
 Určuje koncovou barvu barevného přechodu pozadí pro popisy tlačítek.  
  
```  
COLORREF m_clrFillGradient;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `m_clrFillGradient` se -1, neexistuje žádný přechod. V opačném případě je určená počáteční barva přechodu [CMFCToolTipInfo::m_clrFill](#m_clrfill) a barvy ukončení přechodu je určená `m_clrFillGradient`. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) Určuje směr přechodu.  
  
##  <a name="m_clrtext"></a>  CMFCToolTipInfo::m_clrText  
 Určuje barvu textu všechny popisky.  
  
```  
COLORREF m_clrText;  
```  
  
##  <a name="m_ngradientangle"></a>  CMFCToolTipInfo::m_nGradientAngle  
 Určuje úhel, ve kterém je přechod vykreslen na pozadí popisy tlačítek.  
  
```  
int m_nGradientAngle;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_nGradientAngle` Určuje úhel ve stupních, že přechodu na pozadí popisků je posun od vodorovně. Pokud `m_nGradientAngle` je 0, přechodu vykreslením zleva doprava. Pokud `m_nGradientAngle` je mezi 1 a 360, je po směru hodinových ručiček otáčení přechodu počet stupňů. Pokud `m_nGradientAngle` -1, což je výchozí hodnota je přechodu vykreslením shora dolů. Jedná se o stejné nastavení jako `m_nGradientAngle` na hodnotu 90.  
  
 [CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill` Určuje barvu počátek přechodu a [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient` určuje barvy ukončení přechodu. Pokud `m_clrFillGradient` se -1, neexistuje žádný přechod.  
  
##  <a name="m_nmaxdescrwidth"></a>  CMFCToolTipInfo::m_nMaxDescrWidth  
 Určuje maximální šířku popis, který se zobrazí v každé popisu tlačítka. Pokud šířka popis překročí zadanou hodnotu, je zabalena text.  
  
```  
int m_nMaxDescrWidth;  
```  
  
##  <a name="m_bvislmanagertheme"></a>  CMFCToolTipInfo::m_bVislManagerTheme  
 Určuje, zda správce vzhledu aplikace řídí vzhled všechny popisky.  
  
```  
BOOL m_bVislManagerTheme;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `m_bVislManagerTheme` má hodnotu TRUE, každý popis požaduje novou [cmfctooltipinfo –](../../mfc/reference/cmfctooltipinfo-class.md) ze Správce vzhledu aplikace předtím, než se zobrazí na obrazovce a používá hodnoty v tomto objektu určit jejich výskytu. Ostatní členové vaší [cmfctooltipinfo –](../../mfc/reference/cmfctooltipinfo-class.md) jsou ignorovány.  
  
##  <a name="operator_eq"></a>  CMFCToolTipInfo::operator =  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *src*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Ctooltipmanager – třída](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipCtrl – třída](../../mfc/reference/cmfctooltipctrl-class.md)
