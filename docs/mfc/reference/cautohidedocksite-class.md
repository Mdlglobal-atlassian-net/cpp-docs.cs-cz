---
title: CAutoHideDockSite – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 3a4593ac17f0af26517144edb7b01a9ca4203b1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352971"
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite – třída

Rozšiřuje `CAutoHideDockSite` [CDockSite třídy](../../mfc/reference/cdocksite-class.md) implementovat automaticky skrýt ukotvení podokna.

## <a name="syntax"></a>Syntaxe

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Name (Název)|Popis|
|`CAutoHideDockSite::CAutoHideDockSite`|Vytvoří `CAutoHideDockSite` objekt.|
|`CAutoHideDockSite::~CAutoHideDockSite`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name (Název)|Popis|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Označuje, `CAutoHideDockSite` zda je zobrazen v nabídce podokna.|
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|Určuje, zda je objekt základního podokna odvozen od [třídy CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md).|
|[CAutoHideDockSite::DockPane](#dockpane)|Ukotví podokno `CAuotHideDockSite` k tomuto objektu.|
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|Načte velikost dokovací sítě v souřadnicích obrazovky.|
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|Překreslí podokno `CAutoHideDockSite` na globálním okraji a mezerách mezi tlačítky.|
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|Nastaví okraj na levé straně dokovacílište.|
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|Nastaví okraj na pravé straně dokovací lišty.|
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|Volá [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) pro `CAutoHideDockSite`objekty na .|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|Name (Název)|Popis|
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|Definuje velikost mezery mezi panely nástrojů a okrajem dokovacílište. Tento prostor se měří buď od levého okraje, nebo od horníhrany v závislosti na zarovnání prostoru doku.|

## <a name="remarks"></a>Poznámky

Při volání [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes), rozhraní `CAutoHideDockSite` automaticky vytvoří objekt. Ve většině případů byste neměli být k oni konkretizovat nebo používat tuto třídu přímo.

Dokovací lišta je mezera mezi levou stranou dokovacího podokna a levou stranou [třídy CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CAutoHideDockSite` načíst `CMFCAutoHideBar` objekt z objektu a jak nastavit levý a pravý okraj ukotvení.

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxautohidedocksite.h

## <a name="cautohidedocksitecanacceptpane"></a><a name="canacceptpane"></a>CAutoHideDockSite::CanAcceptPane

Určuje, zda je základní podokno objektem [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) nebo odvozeným od aplikace `CMFCAutoHideBar`.

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pBar*|[v] Základní podokno, které testuje rozhraní framework.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud *pBar* `CMFCAutoHideBar`je odvozen od ; FALSE jinak.

### <a name="remarks"></a>Poznámky

Pokud je objekt základního `CMFCAutoHideBar`podokna odvozen `CAutoHideDockSite`z , může obsahovat .

## <a name="cautohidedocksitedockpane"></a><a name="dockpane"></a>CAutoHideDockSite::DockPane

Ukotví podokno k tomuto objektu [CAutoHideDockSite.](../../mfc/reference/cautohidedocksite-class.md)

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
|*pWnd*|[v] Podokno, které rozhraní dotáže.|
|*dockMethod*|[v] Možnosti ukotvení podokna.|
|*lpRect*|[v] Obdélník, který určuje hranice ukotveného podokna.|

### <a name="remarks"></a>Poznámky

Výchozí implementace nepoužívá parametr *dockMethod*, který je k dispozici pro budoucí použití.

Pokud *lpRect* je NULL, rozhraní framework umístí podokno ve výchozím umístění na webu dock. Pokud je lokalita ukotvení vodorovná, výchozí umístění je zcela vlevo od doku. V opačném případě je výchozí umístění v horní části lokality docku.

## <a name="cautohidedocksitegetalignrect"></a><a name="getalignrect"></a>CAutoHideDockSite::GetAlignRect

Načte velikost dokovací sítě v souřadnicích obrazovky.

```
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*Rect*|[v] Odkaz na obdélník. Metoda ukládá velikost úložiště v tomto obdélníku.|

### <a name="remarks"></a>Poznámky

Obdélník je upraven pro posun okraje tak, aby nebyly zahrnuty.

## <a name="cautohidedocksitem_nextraspace"></a><a name="m_nextraspace"></a>CAutoHideDockSite::m_nExtraSpace

Velikost mezery mezi okraji [cautohidedocksite třídy](../../mfc/reference/cautohidedocksite-class.md) a [CMFCAutoHideBar třídy](../../mfc/reference/cmfcautohidebar-class.md) objektů.

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>Poznámky

Pokud `CMFCAutoHideBar` je ukotven a `CAutoHideDockSite`, neměl by zabírat celý dokovací web. Tato globální proměnná řídí mezeru mezi levým nebo horním okrajem `CMFCAutoHideBar` a odpovídající `CAutoHideDockSite` hranou. To, zda se použije horní nebo levý okraj, závisí na aktuálním zarovnání.

## <a name="cautohidedocksitesetoffsetleft"></a><a name="setoffsetleft"></a>CAutoHideDockSite::SetOffsetLeft

Nastaví okraj na levé straně dokovacílište.

```
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
[v] Nový posun.

### <a name="remarks"></a>Poznámky

[CmFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objekty jsou umístěny staticky na objekt. `CAutoHideDockSite` To znamená, že uživatel nemůže ručně `CMFCAutoHideBar` změnit umístění objektů. Metoda `SetOffsetLeft` řídí mezery mezi levou stranou na levostranné `CMFCAutoHideBar` a `CAutoHideDockSite`levé straně rozhraní .

## <a name="cautohidedocksitesetoffsetright"></a><a name="setoffsetright"></a>CAutoHideDockSite::SetOffsetRight

Nastaví okraj na pravé straně dokovací lišty.

```
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
[v] Nový posun.

### <a name="remarks"></a>Poznámky

[CmFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objekty jsou umístěny staticky na objekt. `CAutoHideDockSite` To znamená, že uživatel nemůže ručně `CMFCAutoHideBar` změnit umístění objektů. Metoda `SetOffsetRight` určuje mezery mezi pravou stranou vpravo `CMFCAutoHideBar` a pravou stranou `CAutoHideDockSite`rozhraní .

## <a name="cautohidedocksiterepositionpanes"></a><a name="repositionpanes"></a>CAutoHideDockSite::RepositionPanes

Překreslí podokna na [cautohidedocksite](../../mfc/reference/cautohidedocksite-class.md).

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*rectNewClientArea*|[v] Rezervovaná hodnota.|

### <a name="remarks"></a>Poznámky

Výchozí implementace nepoužívá *rectNewClientArea*. Překreslí podokna s globálními okraji panelu nástrojů a mezerami mezi tlačítky.

## <a name="cautohidedocksiteunsetautohidemode"></a><a name="unsetautohidemode"></a>CAutoHideDockSite::UnSetAutoHideMode

Volá [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) pro objekty v dokovací síti.

```
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pAutoHideToolbar*|[v] Ukazatel na podokno objektů [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) umístěné na panelu `CAutoHideDockSite`.|

### <a name="remarks"></a>Poznámky

Tato metoda vyhledá řádek, který obsahuje *pAutoHideToolbar*. Volá `CMFCAutoHideBar.UnSetAutoHideMode` všechny objekty v `CMFCAutoHideBar` tomto řádku. Pokud *pAutoHideToolbar* nebyl nalezen nebo je null, tato `CMFCAutoHideBar` metoda `CAutoHideDockSite`volá `CMFCAutoHideBar.UnSetAutoHideMode` pro všechny objekty na .

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CDocksite](../../mfc/reference/cdocksite-class.md)
