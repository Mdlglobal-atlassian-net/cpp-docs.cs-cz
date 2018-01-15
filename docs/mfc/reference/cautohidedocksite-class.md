---
title: "Třída CAutoHideDockSite | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
dev_langs: C++
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e8cc4e9158ae9ff2ef6fd4d48483aa5a75dd9617
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite – třída
`CAutoHideDockSite` Rozšiřuje [CDockSite třída](../../mfc/reference/cdocksite-class.md) implementovat ukotvení automatické skrytí podokna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAutoHideDockSite : public CDockSite  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|`CAutoHideDockSite::CAutoHideDockSite`|Vytvoří `CAutoHideDockSite` objektu.|  
|`CAutoHideDockSite::~CAutoHideDockSite`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Určuje, zda `CAutoHideDockSite` je zobrazen v nabídce panelu.|  
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|Určuje, zda je objekt základní podokně odvozený od [CMFCAutoHideBar třída](../../mfc/reference/cmfcautohidebar-class.md).|  
|[CAutoHideDockSite::DockPane](#dockpane)|K tomuto ukotvené podokno `CAuotHideDockSite` objektu.|  
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|Získá velikost lokality ukotvení v souřadnice obrazovky.|  
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|V podokně překreslí na `CAutoHideDockSite` s globální okraje a mezera na tlačítku.|  
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|Nastaví okraj na levé straně ukotvení panelu.|  
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|Nastaví okraj na pravé straně ukotvení panelu.|  
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|Volání [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) pro objekty, na `CAutoHideDockSite`.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|Název|Popis|  
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|Definuje velikost prostoru mezi panely nástrojů a hrany ukotvení panelu. Tento prostor se měří od levého okraje nebo horní okraj, v závislosti na zarovnání místo na ukotvení.|  
  
## <a name="remarks"></a>Poznámky  
 Při volání [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes), systém automaticky vytvoří `CAutoHideDockSite` objektu. Ve většině případů by neměl mít vytvořit instanci nebo přímo pomocí této třídy.  
  
 Ukotvení panelu je mezera mezi levé části podokna ukotvení a levé straně [CMFCAutoHideButton třída](../../mfc/reference/cmfcautohidebutton-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst `CAutoHideDockSite` objektu z `CMFCAutoHideBar` objekt a jak nastavit levý a pravý okraj ukotvení panelu.  
  
 [!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxautohidedocksite.h  
  
##  <a name="canacceptpane"></a>CAutoHideDockSite::CanAcceptPane  
 Určuje, zda je základní podokně [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objektu nebo odvozené od `CMFCAutoHideBar`.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`pBar`|Základní podokno, které testy rozhraní.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud `pBar` je odvozený od `CMFCAutoHideBar`; `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Pokud objekt základní podokně je odvozený od `CMFCAutoHideBar`, může obsahovat `CAutoHideDockSite`.  
  
##  <a name="dockpane"></a>CAutoHideDockSite::DockPane  
 K tomuto ukotvené podokno [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) objektu.  
  
```  
virtual void DockPane(
    CPane* pWnd,  
    AFX_DOCK_METHOD dockMethod,  
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`pWnd`|V podokně, který ukotvené rozhraní.|  
|[v]`dockMethod`|Ukotvení možnosti v podokně.|  
|[v]`lpRect`|Obdélníku, která určuje za hranice na ukotveného panelu.|  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace nepoužívá parametr `dockMethod`, což zajišťuje pro budoucí použití.  
  
 Pokud `lpRect` je `NULL`, rozhraní framework uloží v podokně ve výchozím umístění na webu ukotvení. Pokud je lokalita ukotvení vodorovné, výchozí umístění je na levém webu ukotvení. Výchozí umístění, jinak hodnota je v horní části webu ukotvení.  
  
##  <a name="getalignrect"></a>CAutoHideDockSite::GetAlignRect  
 Získá velikost lokality ukotvení v souřadnice obrazovky.  
  
```  
void GetAlignRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`rect`|Odkaz na obdélník. Metoda ukládá v obdélníku, velikost webu ukotvení.|  
  
### <a name="remarks"></a>Poznámky  
 Rámeček je přizpůsobené pro posun okrajů tak, aby nejsou zahrnuty.  
  
##  <a name="m_nextraspace"></a>CAutoHideDockSite::m_nExtraSpace  
 Velikost prostoru mezi okraji [CAutoHideDockSite třída](../../mfc/reference/cautohidedocksite-class.md) a [CMFCAutoHideBar třída](../../mfc/reference/cmfcautohidebar-class.md) objekty.  
  
```  
static int m_nExtraSpace;  
```  
  
### <a name="remarks"></a>Poznámky  
 Když `CMFCAutoHideBar` ukotven v `CAutoHideDockSite`, ho by neměla zabírat webu celou ukotvení. Tato globální proměnná Určuje mezery mezi levého nebo horního ohraničení `CMFCAutoHideBar` a odpovídající `CAutoHideDockSite` okraj. Jestli se používá nebo horního okraje závisí na aktuální zarovnání.  
  
##  <a name="setoffsetleft"></a>CAutoHideDockSite::SetOffsetLeft  
 Nastaví okraj na levé straně ukotvení panelu.  
  
```  
void SetOffsetLeft(int nOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nOffset`  
 Nové posun.  
  
### <a name="remarks"></a>Poznámky  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objekty jsou umístěny na staticky `CAutoHideDockSite` objektu. To znamená, že uživatel nemůže ručně změnit umístění `CMFCAutoHideBar` objekty. `SetOffsetLeft` Metoda určuje mezery mezi na levé straně nejvíce vlevo `CMFCAutoHideBar` a levé straně `CAutoHideDockSite`.  
  
##  <a name="setoffsetright"></a>CAutoHideDockSite::SetOffsetRight  
 Nastaví okraj na pravé straně ukotvení panelu.  
  
```  
void SetOffsetRight(int nOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nOffset`  
 Nové posun.  
  
### <a name="remarks"></a>Poznámky  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objekty jsou umístěny na staticky `CAutoHideDockSite` objektu. To znamená, že uživatel nemůže ručně změnit umístění `CMFCAutoHideBar` objekty. `SetOffsetRight` Metoda určuje mezery mezi na pravé straně nejvíce vpravo `CMFCAutoHideBar` a pravé straně `CAutoHideDockSite`.  
  
##  <a name="repositionpanes"></a>CAutoHideDockSite::RepositionPanes  
 Ho překreslí podoken na [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md).  
  
```  
virtual void RepositionPanes(CRect& rectNewClientArea);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`rectNewClientArea`|Rezervovaná hodnota.|  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace nepoužívá `rectNewClientArea`. Ho překreslí podokna s globální nástrojů okraje a mezera na tlačítku.  
  
##  <a name="unsetautohidemode"></a>CAutoHideDockSite::UnSetAutoHideMode  
 Volání [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) pro objekty v lokalitě ukotvení.  
  
```  
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`pAutoHideToolbar`|Ukazatel na [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objekt podokně nachází na `CAutoHideDockSite`.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyhledá na řádek, který obsahuje `pAutoHideToolbar`. Zavolá `CMFCAutoHideBar.UnSetAutoHideMode` pro všechny `CMFCAutoHideBar` objekty na daném řádku. Pokud `pAutoHideToolbar` nebyl nalezen nebo je `NULL`, tato metoda volá `CMFCAutoHideBar.UnSetAutoHideMode` pro všechny `CMFCAutoHideBar` objekty na `CAutoHideDockSite`.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CDockSite – třída](../../mfc/reference/cdocksite-class.md)
