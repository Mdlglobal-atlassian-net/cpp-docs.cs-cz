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
ms.openlocfilehash: 41d9a14e379c566f001eda8b10b2669b95beb171
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376143"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl – třída

Třída `CMFCShellTreeCtrl` rozšiřuje funkce [třídy CTreeCtrl](../../mfc/reference/ctreectrl-class.md) zobrazením hierarchie položek prostředí.

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Povolí nebo zakáže místní nabídku.|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Vrátí kombinaci příznaků, které jsou předány [iShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Načte cestu k položce.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Vrátí ukazatel na objekt [třídy CMFCShellListCtrl,](../../mfc/reference/cmfcshelllistctrl-class.md) `CMFCShellTreeCtrl` který se používá společně s tímto objektem k vytvoření okna podobného průzkumníkovi.|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Tato členská funkce je volána nadřazeným oknem tohoto okna, když obdrží oznámení, které se vztahuje k tomuto oknu. (Přepíše [CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Aktualizovat](#refresh)|Aktualizuje a překreslí aktuální `CMFCShellTreeCtrl` objekt.|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Vybere příslušnou položku stromového ovládacího prvku na základě zadané cesty PIDL nebo řetězce.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Nastaví příznaky pro filtrování kontextu stromu `IShellFolder::EnumObjects`(podobně jako příznaky používané ).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Nastaví vztah mezi `CMFCShellTreeCtrl` aktuálním `CMFCShellListCtrl` objektem a objektem.|

## <a name="remarks"></a>Poznámky

Tato třída rozšiřuje `CTreeCtrl` třídu tím, že umožňuje programu zahrnout položky prostředí systému Windows ve stromu. Tato třída může být `CMFCShellListCtrl` přidružena k objektu a vytvořit tak úplné okno Průzkumníka. Potom výběrem položky ve stromu se zobrazí seznam položek prostředí systému Windows v přidruženém seznamu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxshelltreeCtrl.h

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCShellTreeCtrl` třídy. Tento fragment kódu je součástí [ukázky průzkumníka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

## <a name="cmfcshelltreectrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellContextMenu

Povolí místní nabídku.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] Logická hodnota, která určuje, zda má být místní nabídka povolena.

## <a name="cmfcshelltreectrlgetflags"></a><a name="getflags"></a>CMFCShellTreeCtrl::GetFlags

Vrátí příznaky nastavené pro objekt [třídy CMFCShellTreeCtrl.](../../mfc/reference/cmfcshelltreectrl-class.md)

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD, která určuje kombinaci aktuálně nastavených příznaků.

### <a name="remarks"></a>Poznámky

Příznaky nastavené `CMFCShellTreeCtrl` v sadě jsou odesílány metodě [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) při každém aktualizaci objektu. Příznaky můžete změnit pomocí metody [CMFCShellTreeCtrl::SetFlags.](#setflags)

## <a name="cmfcshelltreectrlgetitempath"></a><a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath

Načte cestu k položce v objektu [třídy CMFCShellTreeCtrl.](../../mfc/reference/cmfcshelltreectrl-class.md)

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
[out] Odkaz na parametr řetězce. Metoda zapíše cestu položky k tomuto parametru.

*htreePoložka*<br/>
[v] Metoda načte cestu pro tuto položku stromového ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; 0 jinak.

### <a name="remarks"></a>Poznámky

Pokud se tato metoda nezdaří, *strPath* obsahuje prázdný řetězec.

Pokud nezadáte *hTreeItem*, tato metoda se pokusí získat řetězec pro aktuálně vybranou položku. Pokud není vybrána žádná položka a *hTreeItem* je NULL, tato metoda se nezdaří.

## <a name="cmfcshelltreectrlgetrelatedlist"></a><a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList

Vrátí ukazatel na objekt [třídy CMFCShellListCtrl,](../../mfc/reference/cmfcshelllistctrl-class.md) který je přidružen k tomuto objektu [CMFCShellTreeCtrl.](../../mfc/reference/cmfcshelltreectrl-class.md)

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CMFCShellListCtrl` objekt, který je přidružen k tomuto objektu ovládacího prvku stromu.

### <a name="remarks"></a>Poznámky

Pomocí objektu `CMFCShellListCtrl` společně `CMFCShellTreeCtrl` s objektem můžete vytvořit okno podobné průzkumníkovi. Použijte metodu [CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist) pro přidružení dvou tříd. Poté, co jsou přidruženy, `CMFCShellListCtrl` rozhraní automaticky `CMFCShellTreeCtrl` aktualizuje if výběr ve změnách.

## <a name="cmfcshelltreectrlonchildnotify"></a><a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Parametry

[v] *zpráva*<br/>
[v] *wParam*<br/>
[v] *LParam*<br/>
[v] *pVýsledek*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcshelltreectrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

[v] *pPoložka*<br/>
[v] *bVybrané*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcshelltreectrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

[v] *pPoložka*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcshelltreectrlrefresh"></a><a name="refresh"></a>CMFCShellTreeCtrl::Aktualizovat

Aktualizuje a překreslí [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).

```
void Refresh();
```

### <a name="remarks"></a>Poznámky

Volánítéto metody aktualizovat hierarchii položek zobrazených `CMFCShellTreeCtrl`v .

## <a name="cmfcshelltreectrlselectpath"></a><a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath

Vybere položku ve [třídě CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) na základě zadané cesty.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
[v] Řetězec, který určuje cestu k položce.

*lpidl*<br/>
[v] PidL, který určuje položku

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; E_FAIL jinak.

## <a name="cmfcshelltreectrlsetflags"></a><a name="setflags"></a>CMFCShellTreeCtrl::SetFlags

Nastaví příznaky pro filtrování kontextu stromu.

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
[v] Příznaky nastavit.

*bAktualizovat*<br/>
[v] Logická hodnota, která `CMFCShellTreeCtrl` určuje, zda má být aktualizován okamžitě.

### <a name="remarks"></a>Poznámky

Předá `CMFCShellTreeCtrl` všechny příznaky sady [iShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects). Další informace o hodnotách různých příznaků naleznete v tématu [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

## <a name="cmfcshelltreectrlsetrelatedlist"></a><a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList

Přidruží objekt [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) k objektu [CMFCShellTreeCtrl.](../../mfc/reference/cmfcshelltreectrl-class.md)

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Parametry

*seznam pShellList*<br/>
[v] Ukazatel na `CMFCShellListCtrl` objekt.

### <a name="remarks"></a>Poznámky

Tato metoda přidruží a `CMFCShellListCtrl` s . `CMFCShellTreeCtrl` Tyto objekty mohou být zobrazeny jako okno podobné průzkumníkovi: `CMFCShellTreeCtrl`pokud uživatel vybere `CMFCShellListCtrl` objekt v aplikaci , budou přidružené položky v aplikaci automaticky aktualizovány.

Pomocí metody [CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist) načtěte `CMFCShellListCtrl` `CMFCShellTreeCtrl`přidružené .

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl – třída](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl – třída](../../mfc/reference/cmfcshelllistctrl-class.md)
