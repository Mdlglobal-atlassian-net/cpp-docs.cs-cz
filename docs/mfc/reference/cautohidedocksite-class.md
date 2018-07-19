---
title: Cautohidedocksite – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f36d6231cfce86314be082a77a39034b619741ad
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336940"
---
# <a name="cautohidedocksite-class"></a>Cautohidedocksite – třída
`CAutoHideDockSite` Rozšiřuje [cdocksite – třída](../../mfc/reference/cdocksite-class.md) k implementaci automatického schovávání panelu ukotvení.  
  
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
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Určuje, zda `CAutoHideDockSite` se zobrazí v nabídce podokna.|  
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|Určuje, zda podokno základní objekt je odvozen z [cmfcautohidebar – třída](../../mfc/reference/cmfcautohidebar-class.md).|  
|[CAutoHideDockSite::DockPane](#dockpane)|Ukotvené podokno této `CAuotHideDockSite` objektu.|  
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|Získá velikost dokovacím místě v souřadnicovém systému obrazovky.|  
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|V podokně překreslí na `CAutoHideDockSite` s globální okraje a mezera na tlačítku.|  
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|Nastaví okraj na levé straně dokovací panel.|  
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|Nastaví okraj na pravé straně panelu ukotvení.|  
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|Volání [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) pro objekty na `CAutoHideDockSite`.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|Název|Popis|  
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|Definuje velikost místa mezi panely nástrojů a okraj ukotvení panelu. Tento prostor se měří z okraji levého nebo horního okraje, v závislosti na zarovnání místa ukotvení.|  
  
## <a name="remarks"></a>Poznámky  
 Při volání [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes), rozhraní automaticky vytvoří `CAutoHideDockSite` objektu. Ve většině případů by neměl muset vytvořit instanci nebo přímo pomocí této třídy.  
  
 Panel ukotvení je mezera mezi levou stranu podokně docku a na levé straně [cmfcautohidebutton – třída](../../mfc/reference/cmfcautohidebutton-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [Cdocksite –](../../mfc/reference/cdocksite-class.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst `CAutoHideDockSite` objektu z `CMFCAutoHideBar` objekt a jak nastavit levý a pravý okraj dokovací panel.  
  
 [!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxautohidedocksite.h  
  
##  <a name="canacceptpane"></a>  CAutoHideDockSite::CanAcceptPane  
 Určuje, zda je základní podokno [cmfcautohidebar –](../../mfc/reference/cmfcautohidebar-class.md) objektu nebo odvozený od `CMFCAutoHideBar`.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[in] *pBar*|Základní panel, který testuje rozhraní framework.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE v případě *pBar* je odvozen z `CMFCAutoHideBar`; FALSE v opačném případě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud podokno základní objekt je odvozen z `CMFCAutoHideBar`, může obsahovat `CAutoHideDockSite`.  
  
##  <a name="dockpane"></a>  CAutoHideDockSite::DockPane  
 Ukotvené podokno této [cautohidedocksite –](../../mfc/reference/cautohidedocksite-class.md) objektu.  
  
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
|[in] *pWnd*|Podokno, které ukotvené rozhraní framework.|  
|[in] *dockMethod*|Možnosti pro podokno ukotvení.|  
|[in] *lprect –*|Obdélník, který určuje hranice pro ukotvené podokno.|  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace nepoužívá parametr *dockMethod*, který je k dispozici pro budoucí použití.  
  
 Pokud *lprect –* má hodnotu NULL, rozhraní umístí v podokně výchozí umístění na dokovacím místě. Při vodorovné dokovacím místě výchozí umístění je na levém okraji dokovacího webu. V opačném případě výchozí umístění je v horní části dokovacího webu.  
  
##  <a name="getalignrect"></a>  CAutoHideDockSite::GetAlignRect  
 Získá velikost dokovacím místě v souřadnicovém systému obrazovky.  
  
```  
void GetAlignRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[in] *rect*|Odkaz na obdélníku. Metoda ukládá velikost dokovacím místě v obdélníku.|  
  
### <a name="remarks"></a>Poznámky  
 Obdélníku je přizpůsobené pro posun okrajů tak, aby nebyly zahrnuty.  
  
##  <a name="m_nextraspace"></a>  CAutoHideDockSite::m_nExtraSpace  
 Velikost místa mezi okraji [cautohidedocksite – třída](../../mfc/reference/cautohidedocksite-class.md) a [cmfcautohidebar – třída](../../mfc/reference/cmfcautohidebar-class.md) objekty.  
  
```  
static int m_nExtraSpace;  
```  
  
### <a name="remarks"></a>Poznámky  
 Při `CMFCAutoHideBar` je ukotven na `CAutoHideDockSite`, to by neměla zabírat celé dokovacího webu. Tato globální proměnná řídí mezery mezi levého nebo horního ohraničení `CMFCAutoHideBar` a odpovídající `CAutoHideDockSite` hrany. Určuje, zda se používá nebo horního okraje závisí na aktuální zarovnání.  
  
##  <a name="setoffsetleft"></a>  CAutoHideDockSite::SetOffsetLeft  
 Nastaví okraj na levé straně dokovací panel.  
  
```  
void SetOffsetLeft(int nOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nOffset*  
 Nové posun.  
  
### <a name="remarks"></a>Poznámky  
 [Cmfcautohidebar –](../../mfc/reference/cmfcautohidebar-class.md) objekty jsou umístěny na staticky `CAutoHideDockSite` objektu. To znamená, že uživatel nemůže ručně změnit umístění `CMFCAutoHideBar` objekty. `SetOffsetLeft` Metodu ovládá mezery mezi nalevo od nejvíce vlevo `CMFCAutoHideBar` a na levé straně `CAutoHideDockSite`.  
  
##  <a name="setoffsetright"></a>  CAutoHideDockSite::SetOffsetRight  
 Nastaví okraj na pravé straně panelu ukotvení.  
  
```  
void SetOffsetRight(int nOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nOffset*  
 Nové posun.  
  
### <a name="remarks"></a>Poznámky  
 [Cmfcautohidebar –](../../mfc/reference/cmfcautohidebar-class.md) objekty jsou umístěny na staticky `CAutoHideDockSite` objektu. To znamená, že uživatel nemůže ručně změnit umístění `CMFCAutoHideBar` objekty. `SetOffsetRight` Metody určuje mezery mezi úplně vpravo pravé straně `CMFCAutoHideBar` a pravé straně `CAutoHideDockSite`.  
  
##  <a name="repositionpanes"></a>  CAutoHideDockSite::RepositionPanes  
 Překreslí podokna na [cautohidedocksite –](../../mfc/reference/cautohidedocksite-class.md).  
  
```  
virtual void RepositionPanes(CRect& rectNewClientArea);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[in] *rectNewClientArea*|Rezervovanou hodnotu.|  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace nepoužívá *rectNewClientArea*. Ho překreslí podoken s globální nástrojů okraje a mezera na tlačítku.  
  
##  <a name="unsetautohidemode"></a>  CAutoHideDockSite::UnSetAutoHideMode  
 Volání [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) objektů na dokovacím místě.  
  
```  
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[in] *pAutoHideToolbar*|Ukazatel [cmfcautohidebar –](../../mfc/reference/cmfcautohidebar-class.md) objektů – podokno umístěn na `CAutoHideDockSite`.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyhledává řádek, který obsahuje *pAutoHideToolbar*. Volá `CMFCAutoHideBar.UnSetAutoHideMode` pro všechny `CMFCAutoHideBar` objekty na daném řádku. Pokud *pAutoHideToolbar* nebyl nalezen nebo má hodnotu NULL, tato metoda volá `CMFCAutoHideBar.UnSetAutoHideMode` pro všechny `CMFCAutoHideBar` objektů `CAutoHideDockSite`.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CDockSite – třída](../../mfc/reference/cdocksite-class.md)
