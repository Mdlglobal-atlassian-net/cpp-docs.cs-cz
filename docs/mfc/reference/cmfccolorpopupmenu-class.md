---
title: "Třída CMFCColorPopupMenu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
dev_langs: C++
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f91c8a6929ada133b3c2ab9f6fc26e9477a88d6b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu – třída
Představuje místní nabídky, který uživatelé používat pro výběr barev v dokumentu nebo aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCColorPopupMenu : public CMFCPopupMenu  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|Vytvoří `CMFCColorPopupMenu` objektu.|  
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Vytvoří lze ukotvit úplné vypnutí pruhu barev. (Přepisuje [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|  
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Vrátí [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) , je vložena do místní nabídky. (Přepisuje [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|  
|`CMFCColorPopupMenu::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Nastaví objekt ovládacího prvku mřížky vlastnosti z vložený `CMFCColorBar` objektu.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|Název|Popis|  
|`m_bEnabledInCustomizeMode`|Logická hodnota, která určuje, jestli se má zobrazit pruhu barev.|  
|`m_wndColorBar`|`CMFCColorBar` Objekt, který poskytuje výběr barev.|  
  
### <a name="remarks"></a>Poznámky  
 Tato třída dědí funkce místní nabídky `CMFCPopupMenu` třídy a spravuje `CMFCColorBar` objekt, který poskytuje výběr barev. Pokud rozhraní nástrojů je v režimu přizpůsobení a `m_bEnabledInCustomizeMode` členů je nastaven na `FALSE`, není zobrazena, objekt pruhu barev. Další informace o přizpůsobení režimu najdete v tématu [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)  
  
 Další informace o `CMFCColorBar`, najdete v části [CMFCColorBar třída](../../mfc/reference/cmfccolorbar-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 [CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcolorpopupmenu.h  
  
##  <a name="cmfccolorpopupmenu"></a>CMFCColorPopupMenu::CMFCColorPopupMenu  
 Vytvoří `CMFCColorPopupMenu` objektu.  
  
```  
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    int nHorzDockRows,  
    int nVertDockColumns,  
    COLORREF colorAutomatic,  
    UINT uiCommandID,  
    BOOL bStdColorDlg = FALSE);

 
CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic);

 
CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`colors`  
 Pole barev, které rozhraní zobrazí v místní nabídce.  
  
 [v]`color`  
 Výchozí hodnota vybrat barvu.  
  
 [v]`lpszAutoColor`  
 Textový popisek *automatické* tlačítko barvy (výchozí), nebo `NULL`.  
  
 Standardní popisek tlačítka automatické je **automatické**.  
  
 [v]`lpszOtherColor`  
 Textový popisek *jiných* tlačítko, které zobrazí další volby barev, nebo `NULL`.  
  
 Standardní popisek pro tlačítko Další je **Další barvy...** .  
  
 [v]`lpszDocColors`  
 Textový popisek tlačítka barvy dokumentu. Barevná paleta dokumentu jsou uvedeny všechny barev, které aktuálně používá v dokumentu.  
  
 [v]`lstDocColors`  
 Seznam barev, které aktuálně používá v dokumentu.  
  
 [v]`nColumns`  
 Počet sloupců, které má pole barev.  
  
 [v]`nHorzDockRows`  
 Počet řádků, které má pruhu barev, kde je umístěn vodorovně.  
  
 [v]`nVertDockColumns`  
 Počet sloupců, které nemá pruhu barev, pokud jej ukotven svisle.  
  
 [v]`colorAutomatic`  
 Výchozí barvu, která rozhraní platí po kliknutí na tlačítko Automatická.  
  
 [v]`uiCommandID`  
 ID příkazu řízení pruhu barev.  
  
 [v]`bStdColorDlg`  
 Logická hodnota, která označuje, zda se zobrazí dialogové okno barvy standardní systém nebo [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) dialogové okno.  
  
 [v]`pParentBtn`  
 Ukazatel na nadřazené tlačítko.  
  
 [v]`nID`  
 ID příkazu.  
  
### <a name="remarks"></a>Poznámky  
 Každý přetížený konstruktor nastaví `m_bEnabledInCustomizeMode` člena `FALSE`.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCColorPopupMenu` objektu.  
  
 [!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]  
  
##  <a name="createtearoffbar"></a>CMFCColorPopupMenu::CreateTearOffBar  
 Vytvoří lze ukotvit úplné vypnutí pruhu barev.  
  
```  
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,  
    UINT uiID,  
    LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`pWndMain`|Ukazatel do nadřazeného okna panelu úplné vypnutí.|  
|[v]`uiID`|ID příkazu panel úplné vypnutí.|  
|[v]`lpszName`|Okno text panel úplné vypnutí.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nový objekt panel úplné vypnutí ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří [CMFCColorBar třída](../../mfc/reference/cmfccolorbar-class.md) objektu a obsahuje ji k [CPane třída](../../mfc/reference/cpane-class.md) ukazatel. Tato hodnota může odevzdat zpět na [CMFCColorBar třída](../../mfc/reference/cmfccolorbar-class.md) ukazatele pomocí jednoho z makra přetypování popsané v [typ přetypování třídy MFC objekty](../../mfc/reference/type-casting-of-mfc-class-objects.md).  
  
##  <a name="getmenubar"></a>CMFCColorPopupMenu::GetMenuBar  
 Vrátí [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) , je vložena do místní nabídky.  
  
```  
virtual CMFCPopupMenuBar* GetMenuBar();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na vložený `CMFCPopupMenuBar`.  
  
### <a name="remarks"></a>Poznámky  
 Místní nabídky Barva má embedded [CMFCPopupMenuBar třída](../../mfc/reference/cmfcpopupmenubar-class.md) objektu. Potlačí tuto metodu v odvozené třídě, pokud vaše aplikace používá jiný typ embedded.  
  
##  <a name="setproplist"></a>CMFCColorPopupMenu::SetPropList  
 Nastaví objekt ovládacího prvku mřížky vlastnosti z vložený `CMFCColorBar` objektu.  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndList`  
 Ukazatel na objekt ovládacího prvku mřížky vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
