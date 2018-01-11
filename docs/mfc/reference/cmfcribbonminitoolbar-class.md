---
title: "Třída CMFCRibbonMiniToolBar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 62a2006423f8e6196f9fac4d8f336ced8b5416f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonminitoolbar-class"></a>CMFCRibbonMiniToolBar – třída
Implementuje kontextové místní panel nástrojů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|Výchozí konstruktor.|  
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|`CMFCRibbonMiniToolBar::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||  
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|(Přepisuje `CMFCPopupMenu::IsRibbonMiniToolBar`.)|  
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|Nastaví seznam příkazů, který se má zobrazit na panelu nástrojů.|  
|[CMFCRibbonMiniToolBar::Show](#show)|Zobrazí malém panelu nástrojů v souřadnice zadaný obrazovky.|  
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|Zobrazí mini nástrojů společně s z kontextové nabídky.|  
  
## <a name="remarks"></a>Poznámky  
 Mini nástrojů se obvykle zobrazí, až uživatel vybere objekt v dokumentu. Po výběru blok textu v textovém editoru, například aplikace zobrazí mini nástrojů, který obsahuje příkazy pro formátování textu.  
  
 Mini nástrojů viditelný, když ukazatel myši je mimo hranice malém panelu nástrojů.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 `CMFCRibbonPanelMenu`  
  
 [CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonMiniToolBar.h  
  
##  <a name="setcommands"></a>CMFCRibbonMiniToolBar::SetCommands  
 Nastaví seznam příkazů, který se má zobrazit na panelu nástrojů.  
  
```  
void SetCommands(
    CMFCRibbonBar* pRibbonBar,  
    const CList<UINT,UINT>& lstCommands);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pRibbonBar`  
 Panel pásu karet, který vyhledá malém panelu nástrojů tlačítka pro zobrazení.  
  
 [v]`lstCommands`  
 Seznam příkazů, který se má zobrazit v malém panelu nástrojů. Najít tlačítka přidružené budou prohledány všechny kategorie pásu karet.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete nastavit seznam příkazů, který se má zobrazit v malém panelu nástrojů.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `SetCommands` metodu `CMFCRibbonMiniToolBar` třídy. Tento fragment kódu je součástí [MS Office 2007 Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]  
  
##  <a name="show"></a>CMFCRibbonMiniToolBar::Show  
 Zobrazí malém panelu nástrojů v souřadnice zadaný obrazovky.  
  
```  
BOOL Show(
    int x,  
    int y);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`x`  
 Určuje vodorovné umístění malém panelu nástrojů v souřadnice obrazovky.  
  
 [v]`y`  
 Určuje svislé umístění malém panelu nástrojů v souřadnice obrazovky.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se úspěšně; zobrazila malém panelu nástrojů v opačném `FALSE`.  
  
##  <a name="showwithcontextmenu"></a>CMFCRibbonMiniToolBar::ShowWithContextMenu  
 Zobrazí mini nástrojů společně s z kontextové nabídky.  
  
```  
BOOL ShowWithContextMenu(
    int x,  
    int y,  
    UINT uiMenuResID,  
    CWnd* pWndOwner);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`x`  
 Určuje vodorovné umístění v místní nabídce v souřadnice obrazovky.  
  
 [v]`y`  
 Určuje svislé umístění v místní nabídce v souřadnice obrazovky.  
  
 [v]`uiMenuResID`  
 Určuje ID prostředku v místní nabídce k zobrazení.  
  
 [v]`pWndOwner`  
 Identifikuje okna, která přijímá zprávy z místní nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v místní nabídce zobrazila úspěšně; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete zobrazit mini nástrojů, který má z kontextové nabídky. V místní nabídce je umístěného 15 pixelů níže malém panelu nástrojů.  
  
##  <a name="iscontextmenumode"></a>CMFCRibbonMiniToolBar::IsContextMenuMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsContextMenuMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isribbonminitoolbar"></a>CMFCRibbonMiniToolBar::IsRibbonMiniToolBar  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsRibbonMiniToolBar() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
