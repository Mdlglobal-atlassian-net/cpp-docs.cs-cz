---
title: Třída CMFCShellTreeCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::EnableShellContextMenu
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetItemPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetRelatedList
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnChildNotify
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemIcon
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemText
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::Refresh
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SelectPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetRelatedList
dev_langs:
- C++
helpviewer_keywords:
- CMFCShellTreeCtrl [MFC], EnableShellContextMenu
- CMFCShellTreeCtrl [MFC], GetFlags
- CMFCShellTreeCtrl [MFC], GetItemPath
- CMFCShellTreeCtrl [MFC], GetRelatedList
- CMFCShellTreeCtrl [MFC], OnChildNotify
- CMFCShellTreeCtrl [MFC], OnGetItemIcon
- CMFCShellTreeCtrl [MFC], OnGetItemText
- CMFCShellTreeCtrl [MFC], Refresh
- CMFCShellTreeCtrl [MFC], SelectPath
- CMFCShellTreeCtrl [MFC], SetFlags
- CMFCShellTreeCtrl [MFC], SetRelatedList
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4e014219a12985142c6d45aae711d0410ff12642
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041942"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl – třída
`CMFCShellTreeCtrl` Rozšiřuje třídu [CTreeCtrl – třída](../../mfc/reference/ctreectrl-class.md) funkce zobrazením hierarchie položek prostředí.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCShellTreeCtrl : public CTreeCtrl  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Povolí nebo zakáže místní nabídky.|  
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Vrátí kombinaci příznaky, které se předávají [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066).|  
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Načte cestu k položce.|  
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Vrátí ukazatel [CMFCShellListCtrl třída](../../mfc/reference/cmfcshelllistctrl-class.md) objekt, který se používá spolu s tím `CMFCShellTreeCtrl` objekt k vytvoření okna stylu Průzkumníka.|  
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Tento člen funkce je volána nadřazeného okna toto okno při přijetí oznámení, které se vztahují na toto okno. (Přepisuje [CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|  
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||  
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||  
|[CMFCShellTreeCtrl::Refresh](#refresh)|Aktualizuje a překreslí aktuální `CMFCShellTreeCtrl` objektu.|  
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Vybere odpovídající stromu položka řízení na základě zadané PIDL nebo řetězec cesty.|  
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Nastaví příznaky vyfiltrujete kontextu stromu (podobně jako příznaky použité `IShellFolder::EnumObjects`).|  
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Nastaví vztah mezi aktuální `CMFCShellTreeCtrl` objektu a `CMFCShellListCtrl` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída rozšiřuje `CTreeCtrl` třída povolením váš program zahrnout prostředí systému Windows položky ve stromové struktuře. Tato třída může být přidružené `CMFCShellListCtrl` objekt k vytvoření dokončení okno Průzkumníka. Potom výběrem položky ve stromové struktuře se zobrazí seznam položek prostředí systému Windows v seznamu přidružené.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CTreeCtrl](../../mfc/reference/ctreectrl-class.md)  
  
 `CMFCShellTreeCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxshelltreeCtrl.h  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCShellTreeCtrl` třídy. Tento fragment kódu je součástí [ukázka Průzkumníka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]  
  
##  <a name="enableshellcontextmenu"></a>  CMFCShellTreeCtrl::EnableShellContextMenu  
 Umožňuje místní nabídky.  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bEnable*  
 Logická hodnota, která určuje, jestli se má povolit místní nabídky.  
  
##  <a name="getflags"></a>  CMFCShellTreeCtrl::GetFlags  
 Vrací příznaky pro nastavit [CMFCShellTreeCtrl třída](../../mfc/reference/cmfcshelltreectrl-class.md) objektu.  
  
```  
DWORD GetFlags() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `DWORD` nastavit hodnotu, která určuje kombinaci příznaky aktuálně.  
  
### <a name="remarks"></a>Poznámky  
 Příznaky nastavené `CMFCShellTreeCtrl` se odesílají do metody [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066) vždy, když je aktualizován objekt. Příznaky s, můžete změnit [CMFCShellTreeCtrl::SetFlags](#setflags) metoda.  
  
##  <a name="getitempath"></a>  CMFCShellTreeCtrl::GetItemPath  
 Načte cestu položku v [CMFCShellTreeCtrl třída](../../mfc/reference/cmfcshelltreectrl-class.md) objektu.  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    HTREEITEM htreeItem = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] *strPath*  
 Odkaz na parametr řetězce. Metoda zapíše cesta položky do tohoto parametru.  
  
 [v] *htreeItem*  
 Metoda načte cestu pro tuto položku ovládacího prvku strom.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato metoda selže, *strPath* obsahuje prázdný řetězec.  
  
 Pokud nezadáte *hTreeItem*, tato metoda se pokusí získat řetězec pro aktuálně vybrané položky. Pokud není vybrána žádná položka a *hTreeItem* je `NULL`, tato metoda selže.  
  
##  <a name="getrelatedlist"></a>  CMFCShellTreeCtrl::GetRelatedList  
 Vrátí ukazatel na [CMFCShellListCtrl třída](../../mfc/reference/cmfcshelllistctrl-class.md) objekt, který je přidružen to [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objektu.  
  
```  
CMFCShellListCtrl* GetRelatedList() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CMFCShellListCtrl` objekt, který je přidružený tento objekt ovládacího prvku strom.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí `CMFCShellListCtrl` objektu společně s `CMFCShellTreeCtrl` objekt, můžete vytvořit okno s stylu Průzkumníka. Pomocí této metody [CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist) přidružit dvou tříd. Jakmile jsou přidružené, rozhraní automaticky aktualizuje `CMFCShellListCtrl` Pokud výběr v `CMFCShellTreeCtrl` změny.  
  
##  <a name="onchildnotify"></a>  CMFCShellTreeCtrl::OnChildNotify  

  
```  
virtual BOOL OnChildNotify(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam,  
    LRESULT* pLResult);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *zpráv*  
 [v] *wParam*  
 [v] *lParam*  
 [v] *pLResult*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ongetitemicon"></a>  CMFCShellTreeCtrl::OnGetItemIcon  

  
```  
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pItem*  
 [v] *bSelected*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ongetitemtext"></a>  CMFCShellTreeCtrl::OnGetItemText  

  
```  
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pItem*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="refresh"></a>  CMFCShellTreeCtrl::Refresh  
 Aktualizuje a překreslí [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).  
  
```  
void Refresh();
```  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze aktualizovat zobrazení položek v hierarchii `CMFCShellTreeCtrl`.  
  
##  <a name="selectpath"></a>  CMFCShellTreeCtrl::SelectPath  
 Vybere položku v [CMFCShellTreeCtrl třída](../../mfc/reference/cmfcshelltreectrl-class.md) na základě zadané cesty.  
  
```  
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *lpszPath*  
 Řetězec, který určuje cestu položce.  
  
 [v] *lpidl*  
 PIDL, která určuje položku  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK` v případě úspěšného; `E_FAIL` jinak.  
  
##  <a name="setflags"></a>  CMFCShellTreeCtrl::SetFlags  
 Nastaví příznaky vyfiltrujete kontextu stromu.  
  
```  
void SetFlags(
    DWORD dwFlags,  
    BOOL bRefresh = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *dwFlags*  
 Příznaky nastavit.  
  
 [v] *bRefresh*  
 Logická hodnota, která určuje, zda `CMFCShellTreeCtrl` by měl být aktualizovat okamžitě.  
  
### <a name="remarks"></a>Poznámky  
 `CMFCShellTreeCtrl` Předává všechny příznaky nastaveny na [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066). Další informace o hodnotách různé příznaky najdete v tématu [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066).  
  
##  <a name="setrelatedlist"></a>  CMFCShellTreeCtrl::SetRelatedList  
 Přidruží [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objektu s [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objektu.  
  
```  
void SetRelatedList(CMFCShellListCtrl* pShellList);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pShellList*  
 Ukazatel na `CMFCShellListCtrl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidruží `CMFCShellListCtrl` s `CMFCShellTreeCtrl`. Tyto objekty, může se zobrazit jako okno s stylu Průzkumníka: Pokud uživatel vybere objekt v `CMFCShellTreeCtrl`, související položky v `CMFCShellListCtrl` budou automaticky aktualizovány.  
  
 Použijte metodu [CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist) načíst `CMFCShellListCtrl` přidružené `CMFCShellTreeCtrl`.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CTreeCtrl – třída](../../mfc/reference/ctreectrl-class.md)   
 [CMFCShellListCtrl – třída](../../mfc/reference/cmfcshelllistctrl-class.md)
