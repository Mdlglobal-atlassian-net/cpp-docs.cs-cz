---
title: CMFCShellTreeCtrl Class
ms.date: 11/04/2016
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
ms.openlocfilehash: 3fa829c5333a87d908d36438fe8ffcd253f9fb5a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279988"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl Class

`CMFCShellTreeCtrl` Třída rozšiřuje [ctreectrl – třída](../../mfc/reference/ctreectrl-class.md) funkce zobrazením hierarchie položek prostředí.

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.
## <a name="syntax"></a>Syntaxe

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Povoluje nebo zakazuje místní nabídku.|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Vrátí kombinace příznaků, které jsou předány [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Načte cestu k položce.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Vrátí ukazatel [CMFCShellListCtrl – třída](../../mfc/reference/cmfcshelllistctrl-class.md) objekt, který se používá spolu s tím `CMFCShellTreeCtrl` objekt k vytvoření okna Průzkumníka jako.|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Tato členská funkce je volána toto okno nadřazené okno při přijetí oznámení, která se vztahuje na toto okno. (Přepíše [CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Refresh](#refresh)|Aktualizuje a překreslí aktuální `CMFCShellTreeCtrl` objektu.|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Vybere položku odpovídající stromu ovládacího prvku, na základě zadané PIDL nebo řetězec cesty.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Nastaví příznaky stromu kontext filtru (podobně jako příznaky používané `IShellFolder::EnumObjects`).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Nastaví vztah mezi aktuálním `CMFCShellTreeCtrl` objektu a `CMFCShellListCtrl` objektu.|

## <a name="remarks"></a>Poznámky

Tato třída rozšiřuje `CTreeCtrl` třídy tím, že váš program zahrnout prostředí Windows položky ve stromové struktuře. Tato třída je možné přidružit `CMFCShellListCtrl` objekt k vytvoření kompletní okno Průzkumníka. Potom výběrem položky ve stromové struktuře se zobrazí seznam položek prostředí Windows v přidruženém seznamu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Požadavky

**Header:** afxshelltreeCtrl.h

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCShellTreeCtrl` třídy. Tento fragment kódu je součástí [ukázka Průzkumníka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

##  <a name="enableshellcontextmenu"></a>  CMFCShellTreeCtrl::EnableShellContextMenu

Umožňuje v místní nabídce.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] Logická hodnota, která určuje, jestli se má povolit nabídku.

##  <a name="getflags"></a>  CMFCShellTreeCtrl::GetFlags

Vrátí nastavení pro příznaků [CMFCShellTreeCtrl – třída](../../mfc/reference/cmfcshelltreectrl-class.md) objektu.

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Návratová hodnota

Nastavte hodnotu DWORD s aktuálně Určuje kombinaci příznaků.

### <a name="remarks"></a>Poznámky

Nastavení příznaků v `CMFCShellTreeCtrl` jsou odesílány do metody [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) vždy, když se aktualizuje objekt. Příznaky s můžete změnit [CMFCShellTreeCtrl::SetFlags](#setflags) metody.

##  <a name="getitempath"></a>  CMFCShellTreeCtrl::GetItemPath

Načte cestu položky v [CMFCShellTreeCtrl – třída](../../mfc/reference/cmfcshelltreectrl-class.md) objektu.

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
[out] Odkaz na parametr řetězce. Metoda zapíše cesta položky do tohoto parametru.

*htreeItem*<br/>
[in] Metoda načte cestu pro tuto položku ovládacího prvku stromu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Pokud tato metoda selže, *strPath* obsahuje prázdný řetězec.

Pokud nezadáte *hTreeItem*, tato metoda se pokusí získat řetězec pro aktuálně vybrané položky. Pokud není vybrána žádná položka a *hTreeItem* má hodnotu NULL, tato metoda se nezdaří.

##  <a name="getrelatedlist"></a>  CMFCShellTreeCtrl::GetRelatedList

Vrátí ukazatel [CMFCShellListCtrl – třída](../../mfc/reference/cmfcshelllistctrl-class.md) objekt, který je spojen s tímto [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objektu.

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CMFCShellListCtrl` objekt, který je spojen s tímto objektem ovládací prvek stromu.

### <a name="remarks"></a>Poznámky

Pomocí `CMFCShellListCtrl` objektů spolu s `CMFCShellTreeCtrl` objektu, můžete vytvořit oknem Průzkumníka jako. Pomocí této metody [CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist) přidružení dvou tříd. Jakmile jsou přidružené, rozhraní automaticky aktualizuje `CMFCShellListCtrl` Pokud výběr v `CMFCShellTreeCtrl` změny.

##  <a name="onchildnotify"></a>  CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Parametry

[in] *zprávy*<br/>
[in] *wParam*<br/>
[in] *lParam*<br/>
[in] *pLResult*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="ongetitemicon"></a>  CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

[in] *pItem*<br/>
[in] *bSelected*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="ongetitemtext"></a>  CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

[in] *pItem*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="refresh"></a>  CMFCShellTreeCtrl::Refresh

Aktualizuje a překreslí [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).

```
void Refresh();
```

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem aktualizace položek zobrazených v hierarchii `CMFCShellTreeCtrl`.

##  <a name="selectpath"></a>  CMFCShellTreeCtrl::SelectPath

Vybere položku v [CMFCShellTreeCtrl – třída](../../mfc/reference/cmfcshelltreectrl-class.md) na základě zadané cesty.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
[in] Řetězec, který určuje cestu položce.

*lpidl*<br/>
[in] PIDL, které určuje položku

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; Jinak E_FAIL.

##  <a name="setflags"></a>  CMFCShellTreeCtrl::SetFlags

Nastaví příznaky stromu kontext filtru.

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
[in] Příznaky pro nastavení.

*bRefresh*<br/>
[in] Logická hodnota určující, zda `CMFCShellTreeCtrl` by měl být aktualizace okamžitě.

### <a name="remarks"></a>Poznámky

`CMFCShellTreeCtrl` Předá všechny nastaveny příznaky na [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects). Další informace o hodnotách jiné příznaky, naleznete v tématu [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

##  <a name="setrelatedlist"></a>  CMFCShellTreeCtrl::SetRelatedList

Přidruží [CMFCShellListCtrl –](../../mfc/reference/cmfcshelllistctrl-class.md) objektu [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objektu.

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Parametry

*pShellList*<br/>
[in] Ukazatel `CMFCShellListCtrl` objektu.

### <a name="remarks"></a>Poznámky

Tato metoda přidruží `CMFCShellListCtrl` s `CMFCShellTreeCtrl`. Tyto objekty může zobrazit jako oknem Průzkumníka podobném: když uživatel vybere objekt `CMFCShellTreeCtrl`, související položky v `CMFCShellListCtrl` se automaticky aktualizují.

Pomocí této metody [CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist) načíst `CMFCShellListCtrl` přidružené `CMFCShellTreeCtrl`.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl – třída](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl – třída](../../mfc/reference/cmfcshelllistctrl-class.md)
