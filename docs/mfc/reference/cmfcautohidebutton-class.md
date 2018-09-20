---
title: Cmfcautohidebutton – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 072473895bbd041f9b195f02572461b02202be32
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386090"
---
# <a name="cmfcautohidebutton-class"></a>Cmfcautohidebutton – třída

Tlačítko, které zobrazí nebo skryje odkaz [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md) , který je nakonfigurovaný pro skrytí.

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.
## <a name="syntax"></a>Syntaxe

```
class CMFCAutoHideButton : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCAutoHideButton::BringToTop](#bringtotop)||
|[CMFCAutoHideButton::Create](#create)|Vytvoří a inicializuje automaticky skrýt tlačítko.|
|[CMFCAutoHideButton::GetAlignment](#getalignment)|Načte zarovnání automaticky skrýt tlačítko.|
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Vrátí [CDockablePane](../../mfc/reference/cdockablepane-class.md) objekt přidružený k tlačítku automatického skrytí.|
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||
|[CMFCAutoHideButton::GetRect](#getrect)||
|[CMFCAutoHideButton::GetSize](#getsize)|Určuje velikost automaticky skrýt tlačítko.|
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|Vrátí velikost položky textový popisek pro automaticky skrýt tlačítko.|
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|Stručný přehled automaticky skrýt tlačítko.|
|[CMFCAutoHideButton::IsActive](#isactive)|Označuje, zda automaticky skrýt tlačítko je aktivní.|
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|Vrátí zvýraznění automaticky skrýt tlačítko.|
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|Určuje, zda je automaticky skrýt tlačítko vodorovně nebo svisle.|
|[CMFCAutoHideButton::IsTop](#istop)||
|[CMFCAutoHideButton::IsVisible](#isvisible)|Určuje, zda tlačítko je viditelná.|
|[CMFCAutoHideButton::Move](#move)||
|[CMFCAutoHideButton::OnDraw](#ondraw)|Rozhraní volá tuto metodu při kreslení automaticky skrýt tlačítko.|
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|Rozhraní volá tuto metodu při ohraničení automaticky skrýt tlačítko.|
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|Rozhraní volá tuto metodu při vyplní na pozadí automaticky skrýt tlačítko.|
|[CMFCAutoHideButton::ReplacePane](#replacepane)||
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Zobrazí nebo skryje přidruženého [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md).|
|[CMFCAutoHideButton::ShowButton](#showbutton)|Zobrazí nebo skryje tlačítko automatického skrytí.|
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||

## <a name="remarks"></a>Poznámky

Vytvoření se `CMFCAutoHideButton` objekt je připojen k [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md). `CDockablePane` Objektu je skryta nebo zobrazena jako uživatel pracuje se `CMFCAutoHideButton` objektu.

Ve výchozím nastavení, rozhraní automaticky vytvoří `CMFCAutoHideButton` když uživatel zapne automatické skrývání. Rozhraní lze vytvořit prvek vlastní uživatelské rozhraní třídy místo `CMFCAutoHideButton` třídy. Chcete-li určit, které vlastní uživatelské rozhraní třídy rozhraní by měl používat, nastavte proměnnou statického členu `CMFCAutoHideBar::m_pAutoHideButtonRTS` rovna třídu vlastního uživatelského rozhraní. Ve výchozím nastavení je tato proměnná nastavená na `CMFCAutoHideButton`.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCAutoHideButton` objektu a použít různé metody v `CMFCAutoHideButton` třídy. Tento příklad ukazuje způsob inicializace `CMFCAutoHideButton` s použitím jeho `Create` metoda, zobrazit přidružené `CDockablePane` třídy a zobrazit automaticky skrýt tlačítko.

[!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CMFCAutoHideButton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxautohidebutton.h

##  <a name="bringtotop"></a>  CMFCAutoHideButton::BringToTop


```
void BringToTop();
```

### <a name="remarks"></a>Poznámky

##  <a name="create"></a>  CMFCAutoHideButton::Create

Vytvoří a inicializuje automaticky skrýt tlačítko.

```
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

*pParentBar*<br/>
[in] Ukazatel na nadřazeného panelu nástrojů.

*pAutoHideWnd*<br/>
[in] Ukazatel [CDockablePane](../../mfc/reference/cdockablepane-class.md) objektu. Toto tlačítko automatického schovávání skryje a ukazuje, že `CDockablePane`.

*dwAlignment*<br/>
[in] Hodnota, která určuje zarovnání na tlačítko s oknem hlavního rámce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Když vytvoříte `CMFCAutoHideButton` objektu, je třeba automaticky skrýt tlačítko přidružit konkrétní `CDockablePane`. Uživatel může použít automaticky skrýt tlačítko skrytí a zobrazení přidruženého `CDockablePane`.

*DwAlignment* parametr označuje, kde se nachází automaticky skrýt tlačítko v aplikaci. Tento parametr může být jedna z následujících hodnot:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

##  <a name="getalignment"></a>  CMFCAutoHideButton::GetAlignment

Načte zarovnání automaticky skrýt tlačítko.

```
DWORD GetAlignment() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD, který obsahuje aktuální zarovnání automaticky skrýt tlačítko.

### <a name="remarks"></a>Poznámky

Zarovnání automaticky skrýt tlačítko indikuje, ve kterém se nachází na tlačítko v aplikaci. To může být jedna z následujících hodnot:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CRBS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

##  <a name="getautohidewindow"></a>  CMFCAutoHideButton::GetAutoHideWindow

Vrátí [CDockablePane](../../mfc/reference/cdockablepane-class.md) objekt přidružený k tlačítku automatického skrytí.

```
CDockablePane* GetAutoHideWindow() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidruženou `CDockablePane` objektu.

### <a name="remarks"></a>Poznámky

Přidružení automaticky skrýt tlačítko s `CDockablePane`, předat `CDockablePane` jako parametr [CMFCAutoHideButton::Create](#create) metoda.

##  <a name="getparenttoolbar"></a>  CMFCAutoHideButton::GetParentToolBar


```
CMFCAutoHideBar* GetParentToolBar();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getrect"></a>  CMFCAutoHideButton::GetRect


```
CRect GetRect() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getsize"></a>  CMFCAutoHideButton::GetSize

Určuje velikost automaticky skrýt tlačítko.

```
CSize GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

A `CSize` objekt, který obsahuje velikost tlačítka.

### <a name="remarks"></a>Poznámky

Vypočtená velikost zahrnuje velikost ohraničení automaticky skrýt tlačítko.

##  <a name="gettextsize"></a>  CMFCAutoHideButton::GetTextSize

Vrátí velikost položky textový popisek pro automaticky skrýt tlačítko.

```
virtual CSize GetTextSize() const;
```

### <a name="return-value"></a>Návratová hodnota

A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který obsahuje velikost textu pro automaticky skrýt tlačítko.

##  <a name="isactive"></a>  CMFCAutoHideButton::IsActive

Označuje, zda automaticky skrýt tlačítko je aktivní.

```
BOOL IsActive() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je aktivní; automaticky skrýt tlačítko FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

Automaticky skrýt tlačítko je aktivní, kdy přidruženého [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md) okno zobrazeno.

##  <a name="ishorizontal"></a>  CMFCAutoHideButton::IsHorizontal

Určuje, zda je automaticky skrýt tlačítko vodorovně nebo svisle.

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je tlačítko vodorovné; jinak 0.

### <a name="remarks"></a>Poznámky

Rozhraní framework nastavuje orientaci ovládacího prvku [cmfcautohidebutton –](../../mfc/reference/cmfcautohidebutton-class.md) objektu při vytváření.  Orientace můžete řídit pomocí *dwAlignment* parametr [CMFCAutoHideButton::Create](#create) metody.

##  <a name="istop"></a>  CMFCAutoHideButton::IsTop


```
BOOL IsTop() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="isvisible"></a>  CMFCAutoHideButton::IsVisible

Určuje, zda je automaticky skrýt tlačítko viditelná.

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je tlačítko viditelný; FALSE v opačném případě.

##  <a name="ondraw"></a>  CMFCAutoHideButton::OnDraw

Rozhraní volá tuto metodu při kreslení automaticky skrýt tlačítko.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
[in] Ukazatel na kontext zařízení.

### <a name="remarks"></a>Poznámky

Pokud chcete přizpůsobit vzhled tlačítek automatického schovávání ve vaší aplikaci, vytvořte novou třídu odvozenou z `CMFCAutoHideButton`. Tuto metodu přepište v odvozené třídy.

##  <a name="ondrawborder"></a>  CMFCAutoHideButton::OnDrawBorder

Rozhraní volá tuto metodu při ohraničení automaticky skrýt tlačítko.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
[in] Ukazatel na kontext zařízení.

*rectBounds*<br/>
[in] Ohraničující obdélník automaticky skrýt tlačítko.

*rectBorderSize*<br/>
[in] Tloušťka ohraničení pro každé straně automaticky skrýt tlačítko.

### <a name="remarks"></a>Poznámky

Pokud chcete přizpůsobit ohraničení každý automaticky skrýt tlačítko v aplikaci, vytvořte novou třídu odvozenou z `CMFCAutoHideButton`. Tuto metodu přepište v odvozené třídy.

##  <a name="onfillbackground"></a>  CMFCAutoHideButton::OnFillBackground

Rozhraní volá tuto metodu při vyplní na pozadí automaticky skrýt tlačítko.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
[in] Ukazatel na kontext zařízení.

*Rect*<br/>
[in] Ohraničující obdélník automaticky skrýt tlačítko.

### <a name="remarks"></a>Poznámky

Pokud chcete přizpůsobit na pozadí pro tlačítka automatického schovávání ve vaší aplikaci, vytvořte novou třídu odvozenou z `CMFCAutoHideButton`. Tuto metodu přepište v odvozené třídy.

##  <a name="showattachedwindow"></a>  CMFCAutoHideButton::ShowAttachedWindow

Zobrazí nebo skryje přidruženého [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md).

```
void ShowAttachedWindow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
[in] Logická hodnota, která určuje, zda tato metoda ukazuje připojeného `CDockablePane`.

##  <a name="showbutton"></a>  CMFCAutoHideButton::ShowButton

Zobrazí nebo skryje tlačítko automatického skrytí.

```
virtual void ShowButton(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
[in] Logická hodnota, která určuje, jestli se má zobrazit automaticky skrýt tlačítko.

##  <a name="move"></a>  CMFCAutoHideButton::Move


```
void Move(int nOffset);
```

### <a name="parameters"></a>Parametry

[in] *nOffset*

### <a name="remarks"></a>Poznámky

##  <a name="replacepane"></a>  CMFCAutoHideButton::ReplacePane


```
void ReplacePane(CDockablePane* pNewBar);
```

### <a name="parameters"></a>Parametry

[in] *pNewBar*

### <a name="remarks"></a>Poznámky

##  <a name="unsetautohidemode"></a>  CMFCAutoHideButton::UnSetAutoHideMode

Zakážete režim automatického skrytí.

```
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```

### <a name="parameters"></a>Parametry

*pFirstBarInGroup*<br/>
[in] Ukazatel na první řádek ve skupině.

### <a name="remarks"></a>Poznámky

##  <a name="highlightbutton"></a>  CMFCAutoHideButton::HighlightButton

Zvýrazní tlačítko automaticky skrýt.

```
virtual void HighlightButton(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bHighlight*<br/>
Určuje novou automaticky skrýt stav tlačítka. TRUE znamená, že se zvýrazní tlačítko, hodnota FALSE označuje, že nezvýrazní se, tlačítko.

### <a name="remarks"></a>Poznámky

##  <a name="ishighlighted"></a>  CMFCAutoHideButton::IsHighlighted

Vrátí stav zvýraznění automaticky skrýt tlačítko.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud automaticky skrýt tlačítko bude zvýrazněný. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAutoHideBar – třída](../../mfc/reference/cmfcautohidebar-class.md)<br/>
[CAutoHideDockSite – třída](../../mfc/reference/cautohidedocksite-class.md)
