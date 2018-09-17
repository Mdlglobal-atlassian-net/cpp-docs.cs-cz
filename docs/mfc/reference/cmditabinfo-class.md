---
title: Cmditabinfo – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cd0355c4d0ce203617729142e03860e9960190a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726606"
---
# <a name="cmditabinfo-class"></a>Cmditabinfo – třída
`CMDITabInfo` Třída se používá k předání parametrů [CMDIFrameWndEx::EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) metody. – Skupiny se záložkami nastavení členů této třídy můžete řídit chování MDI.  
  
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
|[CMDITabInfo::Serialize](#serialize)|Čtení nebo zápis tento objekt z nebo do archivu.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Určuje, zda **Zavřít** u popisku na aktivní kartě je zobrazeno tlačítko.|  
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|Určuje, jestli se má barvy karet MDI.|  
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|Určuje, zda skupina karet zobrazí místní nabídka, která zobrazuje seznam otevřených dokumentů nebo zobrazí tlačítka pro posunutí.|  
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|Určuje, zda uživatele lze zaměnit pozice karty přetažením.|  
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|Určuje, jestli karty mají plochý rámce.|  
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|Určuje, zda se zobrazí každý popisek karty **Zavřít** tlačítko.|  
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|Určuje, jestli jsou povolené vlastní popisky.|  
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|Určuje, jestli se má zobrazit ikony na kartách MDI.|  
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|Určuje velikost ohraničení každé okno s kartou.|  
|[CMDITabInfo::m_style](#m_style)|Určuje styl popisků kartu.|  
|[CMDITabInfo::m_tabLocation](#m_tablocation)|Určuje, zda jsou popisky karty v horní nebo dolní části stránky.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída určuje parametry skupin karet MDI, které vytvoří rozhraní framework.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit hodnoty různých členské proměnné v `CMDITabInfo` třídy.  
  
 [!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Cmditabinfo –](../../mfc/reference/cmditabinfo-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmdiclientareawnd.h  
  
##  <a name="m_bactivetabclosebutton_"></a>  CMDITabInfo::m_bActiveTabCloseButton;  
 Určuje, zda **Zavřít** u popisku na aktivní kartě je zobrazeno tlačítko.  
  
```  
BOOL m_bActiveTabCloseButton;  
```  
  
### <a name="remarks"></a>Poznámky  
 Při hodnotě TRUE se zobrazí popisek na aktivní kartě **Zavřít** tlačítko. **Zavřít** odebere tlačítko v pravém horním rohu oblasti karet. V opačném případě nebude zobrazen popisek na aktivní kartě **Zavřít** tlačítko. **Zavřít** tlačítko se zobrazí v pravém horním rohu oblasti karet.  
  
##  <a name="m_bautocolor"></a>  CMDITabInfo::m_bAutoColor  
 Určuje, zda každý karet MDI b má svůj vlastní barvy.  
  
```  
BOOL m_bAutoColor;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je hodnota TRUE, bude mít každá karta vlastní barvu. Sada barev se spravuje přes knihovnu MFC. V opačném případě kartách se zobrazují v prázdné. Výchozí hodnota je FALSE.  
  
##  <a name="m_bdocumentmenu"></a>  CMDITabInfo::m_bDocumentMenu  
 Určuje, zda každá karta zobrazí místní nabídka, která zobrazuje seznam otevřených dokumentů na pravé straně, od oblasti karet.  
  
```  
BOOL m_bDocumentMenu;  
```  
  
### <a name="remarks"></a>Poznámky  
 Při hodnotě TRUE se každá karta windows zobrazí místní nabídka, která zobrazuje seznam otevřených dokumentů na pravé straně, od oblasti karet; V opačném případě okno Karta zobrazí tlačítka pro posunutí na pravé straně, od oblasti karet. Výchozí hodnota je FALSE.  
  
##  <a name="m_benabletabswap"></a>  CMDITabInfo::m_bEnableTabSwap  
 Určuje, zda uživatele lze zaměnit pozice karty přetažením.  
  
```  
BOOL m_bEnableTabSwap;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je hodnota TRUE, uživatel může změnit pozice karty přetažením karet. V opačném případě uživatel nemůže změnit pozice karty. Výchozí hodnota je TRUE.  
  
##  <a name="m_bflatframe"></a>  CMDITabInfo::m_bFlatFrame  
 Určuje, zda má každý okno s kartou plochý rámce.  
  
```  
BOOL m_bFlatFrame;  
```  
  
##  <a name="m_btabclosebutton"></a>  CMDITabInfo::m_bTabCloseButton  
 Určuje, zda se zobrazí každý okno s kartou **Zavřít** tlačítko.  
  
```  
BOOL m_bTabCloseButton;  
```  
  
### <a name="remarks"></a>Poznámky  
 Při hodnotě TRUE se zobrazí každý okno s kartou **Zavřít** tlačítko na pravý okraj na kartě. V opačném případě **Zavřít** není zobrazeno tlačítko. Výchozí hodnota je TRUE.  
  
##  <a name="m_btabcustomtooltips"></a>  CMDITabInfo::m_bTabCustomTooltips  
 Určuje, zda karet zobrazit popisy tlačítek.  
  
```  
BOOL m_bTabCustomTooltips;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je hodnota TRUE, aplikace odešle zprávu o AFX_WM_ON_GET_TAB_TOOLTIP hlavního rámce. Tato zpráva může zpracovávat pomocí ON_REGISTERED_MESSAGE – makro.  
  
##  <a name="m_btabicons"></a>  CMDITabInfo::m_bTabIcons  
 Určuje, jestli se má zobrazit ikony na kartách MDI.  
  
```  
BOOL m_bTabIcons;  
```  
  
### <a name="remarks"></a>Poznámky  
 Při hodnotě TRUE se ikony se zobrazí na každé kartě MDI. V opačném případě ikony nejsou zobrazeny na kartách. Výchozí hodnota je FALSE.  
  
##  <a name="m_ntabbordersize"></a>  CMDITabInfo::m_nTabBorderSize  
 Určuje velikost ohraničení v pixelech každé okno s kartou.  
  
```  
int m_nTabBorderSize;  
```  
  
### <a name="remarks"></a>Poznámky  
 [CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) vrátí výchozí hodnotu.  
  
##  <a name="m_style"></a>  CMDITabInfo::m_style  
 Určuje styl popisků kartu.  
  
```  
CMFCTabCtrl::Style m_style  
```  
  
### <a name="remarks"></a>Poznámky  
 Zadejte jednu z následujících styly popisků kartu:  
  
 STYLE_3D  
 Styl 3D.  
  
 STYLE_3D_ONENOTE  
 Microsoft OneNote style.  
  
 STYLE_3D_VS2005  
 Microsoft Visual Studio 2005 style.  
  
 STYLE_3D_SCROLLED  
 Styl 3D obdélník kartu popisky.  
  
 STYLE_FLAT_SHARED_HORZ_SCROLL  
 Plochý s sdílené vodorovný posuvník.  
  
 STYLE_3D_ROUNDED_SCROLL  
 Styl 3D round kartu popisky.  
  
##  <a name="m_tablocation"></a>  CMDITabInfo::m_tabLocation  
 Určuje, zda jsou popisky karty v horní nebo dolní části stránky.  
  
```  
CMFCTabCtrl::Location m_tabLocation;  
```  
  
### <a name="remarks"></a>Poznámky  
 Platí pro karty jeden z následujících příznaků umístění:  
  
-   LOCATION_BOTTOM: karty popisky jsou umístěné v dolní části stránky.  
  
-   LOCATION_TOP: karty popisky jsou umístěny v horní části stránky  
  
##  <a name="serialize"></a>  CMDITabInfo::Serialize  
 Čtení nebo zápis tento objekt z archivu nebo do archivu.  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
*ar*<br/>
[in] A [CArchive – třída](../../mfc/reference/carchive-class.md) objektu určeného k serializaci.  
  
## <a name="see-also"></a>Viz také  
 [CMDIFrameWndEx – třída](../../mfc/reference/cmdiframewndex-class.md)   
 [MDI – skupiny se záložkami](../../mfc/mdi-tabbed-groups.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
