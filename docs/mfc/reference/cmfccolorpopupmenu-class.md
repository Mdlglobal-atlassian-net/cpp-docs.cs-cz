---
title: Cmfccolorpopupmenu – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2bcb8a6781c9563f1017060dcfca64841a15f69
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079166"
---
# <a name="cmfccolorpopupmenu-class"></a>Cmfccolorpopupmenu – třída

Představuje místní nabídka, která uživatelům umožňuje vybírat barvy v dokumentu nebo aplikace.

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
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Vytvoří panel barev ukotvitelné odnímatelnými nabídkami. (Přepíše [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Vrátí [cmfcpopupmenubar –](../../mfc/reference/cmfcpopupmenubar-class.md) , který je vložená do místní nabídky. (Přepíše [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|
|`CMFCColorPopupMenu::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Nastaví objekt ovládacího prvku mřížky vlastností Embedded `CMFCColorBar` objektu.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|Název|Popis|
|`m_bEnabledInCustomizeMode`|Logická hodnota, která určuje, jestli se má zobrazit pruhu barev.|
|`m_wndColorBar`|`CMFCColorBar` Objekt, který poskytuje výběr barvy.|

### <a name="remarks"></a>Poznámky

Tato třída dědí funkce rozbalovací nabídky `CMFCPopupMenu` třídy a spravuje `CMFCColorBar` objekt, který poskytuje výběr barvy. Když rozhraní nástrojů je v režimu úprav a `m_bEnabledInCustomizeMode` člen je nastavený na hodnotu NEPRAVDA, nezobrazí se objekt pruhu barev. Další informace o režimu přizpůsobení, najdete v části [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

Další informace o `CMFCColorBar`, naleznete v tématu [cmfccolorbar – třída](../../mfc/reference/cmfccolorbar-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[Cminiframewnd –](../../mfc/reference/cminiframewnd-class.md)

[Cmfcpopupmenu –](../../mfc/reference/cmfcpopupmenu-class.md)

[Cmfccolorpopupmenu –](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolorpopupmenu.h

##  <a name="cmfccolorpopupmenu"></a>  CMFCColorPopupMenu::CMFCColorPopupMenu

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

*Barvy*<br/>
[in] Pole barvy, které zobrazí rozhraní v místní nabídce.

*Barva*<br/>
[in] Výchozí vybraná barva.

*lpszAutoColor*<br/>
[in] Textový popisek *automatické* tlačítko barvy (výchozí), nebo hodnota NULL.

Standardní popisek bude automatické tlačítka je **automatické**.

*lpszOtherColor*<br/>
[in] Textový popisek *jiných* tlačítko, které zobrazuje více volby barev, nebo hodnotu NULL.

Standardní popisek pro jiné tlačítko je **Další barvy...** .

*lpszDocColors*<br/>
[in] Textový popisek tlačítka pro barvy dokumentu. Barevná paleta dokumentu jsou uvedeny všechny barvy, které aktuálně používá dokumentu.

*lstDocColors*<br/>
[in] Seznam barvy, které se aktuálně používá dokumentu.

*nColumns*<br/>
[in] Počet sloupců, které má škály barev.

*nHorzDockRows*<br/>
[in] Počet řádků, které nemá pruhu barev, pokud je ukotven vodorovně.

*nVertDockColumns*<br/>
[in] Počet sloupců, které nemá pruhu barev, pokud je ukotven svisle.

*barvaAutomatická*<br/>
[in] Výchozí barva, která se použije rozhraní po kliknutí na tlačítko Automatické.

*uiCommandID*<br/>
[in] ID příkazu pro ovládací prvek pruhu barev.

*bStdColorDlg*<br/>
[in] Logická hodnota, která určuje, jestli se má zobrazit dialogové okno Barva standardní systém nebo [cmfccolordialog –](../../mfc/reference/cmfccolordialog-class.md) dialogové okno.

*pParentBtn*<br/>
[in] Ukazatel na tlačítku nadřazené.

*nID*<br/>
[in] ID příkazu.

### <a name="remarks"></a>Poznámky

Každý přetížení konstruktoru sady `m_bEnabledInCustomizeMode` člena na hodnotu FALSE.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCColorPopupMenu` objektu.

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

##  <a name="createtearoffbar"></a>  CMFCColorPopupMenu::CreateTearOffBar

Vytvoří panel barev ukotvitelné odnímatelnými nabídkami.

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
|*pWndMain*|[in] Ukazatel na nadřazené okno přemístitelný panel.|
|*uiID*|[in] ID příkazu přemístitelný panel.|
|*lpszName*|[in] Text okna přemístitelný panel.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nový objekt panelu odtržených ovládacího prvku.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří [cmfccolorbar – třída](../../mfc/reference/cmfccolorbar-class.md) objektu a tak přetypování [cpane – třída](../../mfc/reference/cpane-class.md) ukazatele. Tuto hodnotu můžete přetypovat zpět [cmfccolorbar – třída](../../mfc/reference/cmfccolorbar-class.md) ukazatele pomocí jednoho z makra přetypování je popsáno v [typu přetypování třídy knihovny MFC objektů](../../mfc/reference/type-casting-of-mfc-class-objects.md).

##  <a name="getmenubar"></a>  CMFCColorPopupMenu::GetMenuBar

Vrátí [cmfcpopupmenubar –](../../mfc/reference/cmfcpopupmenubar-class.md) , který je vložená do místní nabídky.

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vložený `CMFCPopupMenuBar`.

### <a name="remarks"></a>Poznámky

V rozbalovací nabídce Barva obsahuje vložený [cmfcpopupmenubar – třída](../../mfc/reference/cmfcpopupmenubar-class.md) objektu. Pokud vaše aplikace používá jiné vložený typ, přepište tuto metodu v odvozené třídě.

##  <a name="setproplist"></a>  CMFCColorPopupMenu::SetPropList

Nastaví objekt ovládacího prvku mřížky vlastností Embedded `CMFCColorBar` objektu.

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parametry

*pWndList*<br/>
[in] Ukazatel na objekt ovládacího prvku mřížky vlastností.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
