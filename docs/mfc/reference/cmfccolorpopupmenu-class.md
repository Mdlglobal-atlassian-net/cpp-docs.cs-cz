---
title: CMFCColorPopupMenu – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
ms.openlocfilehash: bcdf60c974ecdc437b90891d2b46a5eec94859d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367683"
---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu – třída

Představuje rozbalovací nabídku, kterou uživatelé používají k výběru barev v dokumentu nebo aplikaci.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Name (Název)|Popis|
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|Vytvoří `CMFCColorPopupMenu` objekt.|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name (Název)|Popis|
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Vytvoří ukotvitelný odtrhnutelný barevný pruh. (Přepíše [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Vrátí [panel CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) vložený do rozbalovací nabídky. (Přepíše [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|
|`CMFCColorPopupMenu::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Nastaví objekt řízení mřížky `CMFCColorBar` vlastností vloženého objektu.|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|Name (Název)|Popis|
|`m_bEnabledInCustomizeMode`|Logická hodnota, která určuje, zda se má zobrazit barevný pruh.|
|`m_wndColorBar`|Objekt, `CMFCColorBar` který poskytuje výběr barev.|

### <a name="remarks"></a>Poznámky

Tato třída zdědí funkce rozbalovací `CMFCPopupMenu` nabídky třídy `CMFCColorBar` a spravuje objekt, který poskytuje výběr barev. Pokud je rozhraní panelu nástrojů `m_bEnabledInCustomizeMode` v režimu přizpůsobení a člen je nastaven na hodnotu FALSE, objekt pruhu barev se nezobrazí. Další informace o režimu vlastního nastavení naleznete v tématu [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

Další informace `CMFCColorBar`naleznete v [tématu CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CmFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CmFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolorpopupmenu.h

## <a name="cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a>CMFCColorPopupMenu::CMFCColorPopupMenu

Vytvoří `CMFCColorPopupMenu` objekt.

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

*Barvy*<br/>
[v] Pole barev, které se zobrazí v rozbalovací nabídce.

*color*<br/>
[v] Výchozí vybraná barva.

*lpszAutoColor*<br/>
[v] Textový popisek *automatického* (výchozího) tlačítka barvy nebo NULL.

Standardní štítek pro automatické tlačítko je **Automatické**.

*lpszOtherColor*<br/>
[v] Textový popisek *druhého* tlačítka, který zobrazuje více voleb barev, nebo NULL.

Standardní popisek pro druhé tlačítko je **Více barev...**.

*lpszDocBarvy*<br/>
[v] Textový popis tlačítka barvy dokumentu. Paleta barev dokumentu obsahuje seznam všech barev, které dokument aktuálně používá.

*Barvy lstDoc*<br/>
[v] Seznam barev, které dokument aktuálně používá.

*nSloupce*<br/>
[v] Počet sloupců, které má pole barev.

*nHorzDockRows*<br/>
[v] Počet řádků, které má barevný pruh, když je ukotven vodorovně.

*nVertDockColumns*<br/>
[v] Počet sloupců, které má barevný pruh, když je ukotven svisle.

*colorAutomaticky*<br/>
[v] Výchozí barva, kterou rozhraní použije po klepnutí na tlačítko automatické.

*uiCommandID*<br/>
[v] ID příkazu ovládacího prvku color bar.

*bStdColorDlg*<br/>
[v] Logická hodnota, která označuje, zda se má zobrazit dialogové okno standardní barvy systému nebo dialogové okno [CMFCColorDialog.](../../mfc/reference/cmfccolordialog-class.md)

*pParentBtn*<br/>
[v] Ukazatel na nadřazené tlačítko.

*Nid*<br/>
[v] ID příkazu.

### <a name="remarks"></a>Poznámky

Každý přetížený konstruktor `m_bEnabledInCustomizeMode` nastaví člen na HODNOTU FALSE.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCColorPopupMenu` vytvořit objekt.

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

## <a name="cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a>CMFCColorPopupMenu::CreateTearOffBar

Vytvoří ukotvitelný odtrhnutelný barevný pruh.

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
|*pWndMain*|[v] Ukazatel na nadřazené okno panelu odtržení.|
|*uiID*|[v] ID příkazu odtrhávací lišty.|
|*název lpsz*|[v] Text okna odtrhávací lišty.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nový odtrhávací ovládací panel objektu.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří objekt [třídy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) a přehodí jej do ukazatele [třídy CPane.](../../mfc/reference/cpane-class.md) Tuto hodnotu můžete přetypovat zpět na ukazatel [třídy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) pomocí jednoho z maker přetypování popsaných v [části Typ lití objektů třídy knihovny MFC](../../mfc/reference/type-casting-of-mfc-class-objects.md).

## <a name="cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a>CMFCColorPopupMenu::GetMenuBar

Vrátí [panel CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) vložený do rozbalovací nabídky.

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vložené `CMFCPopupMenuBar`.

### <a name="remarks"></a>Poznámky

Rozbalovací nabídka barva obsahuje vložený objekt [třídy CMFCPopupMenuBar.](../../mfc/reference/cmfcpopupmenubar-class.md) Přepsat tuto metodu v odvozené třídě, pokud vaše aplikace používá jiný vložený typ.

## <a name="cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a>CMFCColorPopupMenu::SetPropList

Nastaví objekt řízení mřížky `CMFCColorBar` vlastností vloženého objektu.

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parametry

*pWndList*<br/>
[v] Ukazatel na objekt ovládacího prvku mřížky vlastností.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
