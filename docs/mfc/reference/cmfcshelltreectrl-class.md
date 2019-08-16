---
title: CMFCShellTreeCtrl – třída
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
ms.openlocfilehash: 97136342049a54d45af893962025f01eda4366d4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504912"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl – třída

Třída rozšiřuje funkčnost [třídy CTreeCtrl](../../mfc/reference/ctreectrl-class.md) zobrazením hierarchie položek prostředí. `CMFCShellTreeCtrl`

Další podrobnosti najdete ve zdrojovém kódu ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.
## <a name="syntax"></a>Syntaxe

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Povoluje nebo zakazuje místní nabídku.|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Vrátí kombinaci příznaků, které jsou předány do [IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Načte cestu k položce.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Vrátí ukazatel na objekt [třídy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) , který se používá společně s tímto `CMFCShellTreeCtrl` objektem k vytvoření okna podobného Průzkumníku.|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Tato členská funkce se volá do nadřazeného okna tohoto okna, když obdrží zprávu s oznámením, která se vztahuje na toto okno. (Potlačení [CWnd:: OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl:: Refresh](#refresh)|Aktualizuje a překreslí aktuální `CMFCShellTreeCtrl` objekt.|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Vybere příslušnou položku ovládacího prvku stromu založenou na zadané PIDL nebo cestě k řetězci.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Nastaví příznaky pro filtrování kontextu stromu (podobně jako příznaky používané v `IShellFolder::EnumObjects`).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Nastaví relaci mezi aktuálním `CMFCShellTreeCtrl` objektem `CMFCShellListCtrl` a objektem.|

## <a name="remarks"></a>Poznámky

Tato třída rozšiřuje `CTreeCtrl` třídu tím, že umožňuje programu zahrnout do stromu položky prostředí systému Windows. Tato třída může být přidružena `CMFCShellListCtrl` k objektu pro vytvoření úplného okna Průzkumníka. Po výběru položky ve stromové struktuře se zobrazí seznam položek prostředí Windows v přidruženém seznamu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxshelltreeCtrl. h

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCShellTreeCtrl` třídy. Tento fragment kódu je součástí [ukázky Průzkumníka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

##  <a name="enableshellcontextmenu"></a>  CMFCShellTreeCtrl::EnableShellContextMenu

Povolí místní nabídku.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro Logická hodnota, která určuje, zda má být povolena místní nabídka.

##  <a name="getflags"></a>  CMFCShellTreeCtrl::GetFlags

Vrátí sadu příznaků pro objekt [třídy CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD, která určuje kombinaci příznaků, které jsou aktuálně nastaveny.

### <a name="remarks"></a>Poznámky

Příznaky nastavené v `CMFCShellTreeCtrl` jsou odesílány do metody [IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) při každém obnovení objektu. Příznaky lze změnit pomocí metody [CMFCShellTreeCtrl:: SetFlags](#setflags) .

##  <a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath

Načte cestu položky v objektu [třídy CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
mimo Odkaz na řetězcový parametr. Metoda zapisuje cestu k položce do tohoto parametru.

*htreeItem*<br/>
pro Metoda načte cestu pro tuto položku ovládacího prvku stromu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; 0, jinak.

### <a name="remarks"></a>Poznámky

Pokud tato metoda není úspěšná, *strPath* obsahuje prázdný řetězec.

Pokud nezadáte *hTreeItem*, tato metoda se pokusí získat řetězec pro aktuálně vybranou položku. Pokud není vybrána žádná položka a *hTreeItem* je null, tato metoda se nezdařila.

##  <a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList

Vrátí ukazatel na objekt [třídy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) , který je přidružen k tomuto objektu [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CMFCShellListCtrl` objekt, který je spojen s tímto objektem ovládacího prvku stromové struktury.

### <a name="remarks"></a>Poznámky

Pomocí `CMFCShellListCtrl` objektu spolu `CMFCShellTreeCtrl` s objektem můžete vytvořit okno podobné Průzkumníku. K přidružení dvou tříd použijte metodu [CMFCShellTreeCtrl:: SetRelatedList](#setrelatedlist) . Po jejich přidružení rozhraní automaticky aktualizuje `CMFCShellListCtrl` , pokud je výběr `CMFCShellTreeCtrl` proveden ve změnách.

##  <a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Parametry

pro *zpráva*<br/>
pro *wParam*<br/>
pro *lParam*<br/>
pro *pLResult*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="ongetitemicon"></a>  CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

pro *pItem*<br/>
pro *bSelected*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="ongetitemtext"></a>  CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

pro *pItem*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="refresh"></a>CMFCShellTreeCtrl:: Refresh

Aktualizuje a znovu vykreslí [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).

```
void Refresh();
```

### <a name="remarks"></a>Poznámky

Voláním této metody aktualizujete hierarchii položek zobrazených v `CMFCShellTreeCtrl`.

##  <a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath

Vybere položku ve [třídě CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) na základě zadané cesty.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
pro Řetězec, který určuje cestu k položce.

*lpidl*<br/>
pro PIDL, který určuje položku

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; E_FAIL jinak.

##  <a name="setflags"></a>CMFCShellTreeCtrl::SetFlags

Nastaví příznaky pro filtrování kontextu stromu.

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
pro Příznaky, které mají být nastaveny.

*bRefresh*<br/>
pro Logická hodnota určující, zda `CMFCShellTreeCtrl` má být aktualizace provedena okamžitě.

### <a name="remarks"></a>Poznámky

Projde všechny příznaky nastavené na [IShellFolder:: EnumObjects.](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) `CMFCShellTreeCtrl` Další informace o hodnotách různých příznaků naleznete v tématu [IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

##  <a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList

Přidruží objekt [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) k objektu [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Parametry

*pShellList*<br/>
pro Ukazatel na `CMFCShellListCtrl` objekt.

### <a name="remarks"></a>Poznámky

Tato metoda přidruží k `CMFCShellListCtrl`. `CMFCShellTreeCtrl` Tyto objekty mohou být zobrazeny jako okno podobné Průzkumníku: Pokud uživatel vybere objekt v `CMFCShellTreeCtrl`, `CMFCShellListCtrl` budou přidružené položky v automaticky aktualizovány.

K načtení `CMFCShellListCtrl` přidruženého `CMFCShellTreeCtrl`k použijte metodu [CMFCShellTreeCtrl:: GetRelatedList](#getrelatedlist) .

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl – třída](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl – třída](../../mfc/reference/cmfcshelllistctrl-class.md)
