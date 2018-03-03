---
title: "Třída CMDITabInfo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
dev_langs:
- C++
helpviewer_keywords:
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b670b26855f5edcfb955d3dd0f8150a999f3a8e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmditabinfo-class"></a>CMDITabInfo – třída
`CMDITabInfo` Třída se používá k předat parametry do [CMDIFrameWndEx::EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) metoda. – Skupiny se záložkami sadu členů této třídy pro řízení chování MDI.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMDITabInfo   
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMDITabInfo::CMDITabInfo`|Výchozí konstruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMDITabInfo::Serialize](#serialize)|Čtení nebo zápisu tento objekt z nebo do archivu.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Určuje, zda **Zavřít** tlačítko se zobrazí na název active karty.|  
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|Určuje, jestli barvu MDI karty.|  
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|Určit, zda skupina záložek zobrazí místní nabídku, která obsahuje seznam otevřené dokumenty nebo zobrazuje tlačítka posuvníku.|  
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|Určuje, zda uživatel zaměnit polohy karty přetažením.|  
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|Určuje, jestli mají karty ploché rámce.|  
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|Určuje, zda se má zobrazit každý popisek karty **Zavřít** tlačítko.|  
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|Určuje, zda je povoleno vlastní popisky.|  
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|Určuje, jestli se má zobrazit ikony na kartách MDI.|  
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|Určuje ohraničení velikost okna každé kartě.|  
|[CMDITabInfo::m_style](#m_style)|Určuje styl popisků kartě.|  
|[CMDITabInfo::m_tabLocation](#m_tablocation)|Určuje, zda budou popisky karty v horní nebo dolní části stránky.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída určuje parametry MDI karta skupin, které vytvoří rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit hodnoty různých členské proměnné v `CMDITabInfo` třídy.  
  
 [!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmdiclientareawnd.h  
  
##  <a name="m_bactivetabclosebutton_"></a>CMDITabInfo::m_bActiveTabCloseButton;  
 Určuje, zda **Zavřít** tlačítko se zobrazí na název active karty.  
  
```  
BOOL m_bActiveTabCloseButton;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `TRUE`, se zobrazí popisek aktivní karty **Zavřít** tlačítko. **Zavřít** tlačítko bude odebrána z pravém horním rohu oblast karty. Jinak název active karty nezobrazí **Zavřít** tlačítko. **Zavřít** tlačítko se zobrazí v pravém horním rohu oblast karty.  
  
##  <a name="m_bautocolor"></a>CMDITabInfo::m_bAutoColor  
 Určuje, zda je každé kartě MDI vlastní barvy.  
  
```  
BOOL m_bAutoColor;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `TRUE`, každé kartě bude mít svůj vlastní barvy. Knihovny MFC spravuje sadu barev. Karty, jinak se zobrazí v prázdné. Výchozí hodnota je `FALSE`.  
  
##  <a name="m_bdocumentmenu"></a>CMDITabInfo::m_bDocumentMenu  
 Určuje, zda na jednotlivých kartách místní nabídky, které obsahuje seznam otevřených dokumentů na pravé straně oblast karty.  
  
```  
BOOL m_bDocumentMenu;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `TRUE`, každé kartě windows zobrazí místní nabídky, které obsahuje seznam otevřených dokumentů na pravé straně oblast karty; Karta okna, jinak hodnota zobrazí Posunutí tlačítek v pravé hrany oblast karty. Výchozí hodnota je `FALSE`.  
  
##  <a name="m_benabletabswap"></a>CMDITabInfo::m_bEnableTabSwap  
 Určuje, zda uživatel zaměnit polohy karty přetažením.  
  
```  
BOOL m_bEnableTabSwap;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `TRUE`, uživatel může změnit pozice karty přetažením karty. Uživatele nelze změnit, jinak hodnota pozice karty. Výchozí hodnota je `TRUE`.  
  
##  <a name="m_bflatframe"></a>CMDITabInfo::m_bFlatFrame  
 Určuje, zda je každý okno s kartou ploché rámce.  
  
```  
BOOL m_bFlatFrame;  
```  
  
##  <a name="m_btabclosebutton"></a>CMDITabInfo::m_bTabCloseButton  
 Určuje, zda se má zobrazit každý okno s kartou **Zavřít** tlačítko.  
  
```  
BOOL m_bTabCloseButton;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `TRUE`, zobrazí na každé kartě okno **Zavřít** na pravý okraj kartě tlačítko. Jinak **Zavřít** se nezobrazí tlačítko. Výchozí hodnota je `TRUE`.  
  
##  <a name="m_btabcustomtooltips"></a>CMDITabInfo::m_bTabCustomTooltips  
 Určuje, zda karty zobrazí popisy ovládacích prvků.  
  
```  
BOOL m_bTabCustomTooltips;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `TRUE`, odešle aplikace `AFX_WM_ON_GET_TAB_TOOLTIP` zprávu, která se hlavního rámce. Tuto zprávu můžete řešit pomocí `ON_REGISTERED_MESSAGE` makro.  
  
##  <a name="m_btabicons"></a>CMDITabInfo::m_bTabIcons  
 Určuje, jestli se má zobrazit ikony na kartách MDI.  
  
```  
BOOL m_bTabIcons;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `TRUE`, ikony se zobrazí na každé kartě MDI. Ikony, jinak hodnota nejsou zobrazeny na kartách. Výchozí hodnota je `FALSE`.  
  
##  <a name="m_ntabbordersize"></a>CMDITabInfo::m_nTabBorderSize  
 Určuje velikost ohraničení okna v pixelech, každé kartě.  
  
```  
int m_nTabBorderSize;  
```  
  
### <a name="remarks"></a>Poznámky  
 [CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) vrátí výchozí hodnota.  
  
##  <a name="m_style"></a>CMDITabInfo::m_style  
 Určuje styl popisků kartě.  
  
```  
CMFCTabCtrl::Style m_style  
```  
  
### <a name="remarks"></a>Poznámky  
 Určete jednu z následujících styly popisků karty:  
  
 `STYLE_3D`  
 3D styl.  
  
 `STYLE_3D_ONENOTE`  
 Microsoft OneNote styl.  
  
 `STYLE_3D_VS2005`  
 Styl Microsoft Visual Studio 2005.  
  
 `STYLE_3D_SCROLLED`  
 3D stylu obdélníku kartě popisky.  
  
 `STYLE_FLAT_SHARED_HORZ_SCROLL`  
 Plochý s sdílené vodorovného posuvníku.  
  
 `STYLE_3D_ROUNDED_SCROLL`  
 3D styl se zaokrouhlí karta štítky.  
  
##  <a name="m_tablocation"></a>CMDITabInfo::m_tabLocation  
 Určuje, zda budou popisky karty v horní nebo dolní části stránky.  
  
```  
CMFCTabCtrl::Location m_tabLocation;  
```  
  
### <a name="remarks"></a>Poznámky  
 Použít na kartách jeden následující příznaky umístění:  
  
-   LOCATION_BOTTOM: popisky karty jsou umístěné v dolní části stránky.  
  
-   LOCATION_TOP: popisky karty jsou umístěné v horní části stránky  
  
##  <a name="serialize"></a>CMDITabInfo::Serialize  
 Čtení nebo zápisu tento objekt z archivu nebo do archivu.  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`ar`  
 A [CArchive – třída](../../mfc/reference/carchive-class.md) objektu k serializaci.  
  
## <a name="see-also"></a>Viz také  
 [CMDIFrameWndEx – třída](../../mfc/reference/cmdiframewndex-class.md)   
 [MDI – skupiny se záložkami](../../mfc/mdi-tabbed-groups.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
