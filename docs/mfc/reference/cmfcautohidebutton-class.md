---
title: Třída CMFCAutoHideButton
ms.date: 10/18/2018
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
ms.openlocfilehash: 3ea6ce13b8cca7e0130fe14459a832b476391b0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751669"
---
# <a name="cmfcautohidebutton-class"></a>Třída CMFCAutoHideButton

Tlačítko, které zobrazuje nebo skryje [třídu CDockablePane,](../../mfc/reference/cdockablepane-class.md) která je nakonfigurována tak, aby se skryla.

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCAutoHideButton : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCAutoHideButton::BringToTop](#bringtotop)||
|[CMFCAutoHideButton::Vytvořit](#create)|Vytvoří a inicializuje tlačítko automatického skrytí.|
|[CMFCAutoHideButton::GetAlignment](#getalignment)|Načte zarovnání tlačítka automatického skrytí.|
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Vrátí objekt [CDockablePane](../../mfc/reference/cdockablepane-class.md) přidružený k tlačítku automatického skrytí.|
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||
|[CMFCAutoHideButton::GetRect](#getrect)||
|[CMFCAutoHideButton::GetSize](#getsize)|Určuje velikost tlačítka automatického skrytí.|
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|Vrátí velikost textového popisku tlačítka automatického skrytí.|
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|Zvýrazní tlačítko automatického skrytí.|
|[CMFCAutoHideButton::IsActive](#isactive)|Označuje, zda je tlačítko automatického skrytí aktivní.|
|[CMFCAutoHideButton::Zvýrazněno](#ishighlighted)|Vrátí stav zvýraznění tlačítka automatického skrytí.|
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|Určuje, zda je tlačítko automatického skrytí vodorovné nebo svislé.|
|[CMFCAutoHideButton::Istop](#istop)||
|[CMFCAutoHideButton::jeviditelný](#isvisible)|Označuje, zda je tlačítko viditelné.|
|[CMFCAutoHideButton::Přesunout](#move)||
|[CMFCAutoHideButton::OnDraw](#ondraw)|Framework volá tuto metodu při nakreslí tlačítko automatické ho skrýt.|
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|Framework volá tuto metodu při nakreslí ohraničení automaticky skrýt tlačítko.|
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|Framework volá tuto metodu, když vyplní pozadí automaticky skrýt tlačítko.|
|[CMFCAutoHideButton::Replacepane](#replacepane)||
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Zobrazí nebo skryje přidruženou [třídu CDockablePane](../../mfc/reference/cdockablepane-class.md).|
|[CMFCAutoHideButton::ShowButton](#showbutton)|Zobrazí nebo skryje tlačítko automatického skrytí.|
|[CMFCAutoHideButton::UnsetAutoHideMode](#unsetautohidemode)||

## <a name="remarks"></a>Poznámky

Při vytváření `CMFCAutoHideButton` je objekt připojen k [třídě CDockablePane](../../mfc/reference/cdockablepane-class.md). Objekt `CDockablePane` je skrytý nebo zobrazený při interakci `CMFCAutoHideButton` uživatele s objektem.

Ve výchozím nastavení rozhraní `CMFCAutoHideButton` automaticky vytvoří, když uživatel zapne automatické skrytí. Rozhraní framework můžete vytvořit prvek vlastní třídy `CMFCAutoHideButton` ui namísto třídy. Chcete-li určit, kterou vlastní třídu rozhraní by `CMFCAutoHideBar::m_pAutoHideButtonRTS` měla architektura použít, nastavte statickou člennou proměnnou rovnou vlastní třídě rozhraní. Ve výchozím nastavení je `CMFCAutoHideButton`tato proměnná nastavena na hodnotu .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCAutoHideButton` vytvořit objekt a používat `CMFCAutoHideButton` různé metody ve třídě. Příklad ukazuje, jak inicializovat `CMFCAutoHideButton` objekt `Create` pomocí jeho `CDockablePane` metody, zobrazit přidruženou třídu a zobrazit tlačítko automatického skrytí.

[!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CMFCAutoHideButton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxautohidebutton.h

## <a name="cmfcautohidebuttonbringtotop"></a><a name="bringtotop"></a>CMFCAutoHideButton::BringToTop

```cpp
void BringToTop();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebuttoncreate"></a><a name="create"></a>CMFCAutoHideButton::Vytvořit

Vytvoří a inicializuje tlačítko automatického skrytí.

```
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

*pParentBar*<br/>
[v] Ukazatel na nadřazený panel nástrojů.

*pAutoHideWnd*<br/>
[v] Ukazatel na [cDockablePane](../../mfc/reference/cdockablepane-class.md) objektu. Toto tlačítko automatického skrytí `CDockablePane`se skryje a zobrazí to .

*dwAlignment*<br/>
[v] Hodnota, která určuje zarovnání tlačítka s oknem hlavního rámce.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Při vytváření `CMFCAutoHideButton` objektu je nutné přidružit tlačítko `CDockablePane`automatického skrytí k určitému . Uživatel může pomocí tlačítka automatického skrytí skrýt `CDockablePane`a zobrazit přidružené tlačítko .

Parametr *dwAlignment* označuje, kde se v aplikaci nachází tlačítko automatického skrytí. Parametr může být některá z následujících hodnot:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetalignment"></a><a name="getalignment"></a>CMFCAutoHideButton::GetAlignment

Načte zarovnání tlačítka automatického skrytí.

```
DWORD GetAlignment() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD, která obsahuje aktuální zarovnání tlačítka automatického skrytí.

### <a name="remarks"></a>Poznámky

Zarovnání tlačítka automatického skrytí označuje, kde se tlačítko nachází v aplikaci. Může to být některá z následujících hodnot:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CRBS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetautohidewindow"></a><a name="getautohidewindow"></a>CMFCAutoHideButton::GetAutoHideWindow

Vrátí objekt [CDockablePane](../../mfc/reference/cdockablepane-class.md) přidružený k tlačítku automatického skrytí.

```
CDockablePane* GetAutoHideWindow() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidružený `CDockablePane` objekt.

### <a name="remarks"></a>Poznámky

Chcete-li přidružit `CDockablePane`tlačítko automatického skrytí k metodě , předejte `CDockablePane` jej jako parametr metodě [CMFCAutoHideButton::Create.](#create)

## <a name="cmfcautohidebuttongetparenttoolbar"></a><a name="getparenttoolbar"></a>CMFCAutoHideButton::GetParentToolBar

```
CMFCAutoHideBar* GetParentToolBar();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebuttongetrect"></a><a name="getrect"></a>CMFCAutoHideButton::GetRect

```
CRect GetRect() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebuttongetsize"></a><a name="getsize"></a>CMFCAutoHideButton::GetSize

Určuje velikost tlačítka automatického skrytí.

```
CSize GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `CSize` který obsahuje velikost tlačítka.

### <a name="remarks"></a>Poznámky

Vypočtená velikost zahrnuje velikost ohraničení tlačítka automatického skrytí.

## <a name="cmfcautohidebuttongettextsize"></a><a name="gettextsize"></a>CMFCAutoHideButton::GetTextSize

Vrátí velikost textového popisku tlačítka automatického skrytí.

```
virtual CSize GetTextSize() const;
```

### <a name="return-value"></a>Návratová hodnota

[CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který obsahuje velikost textu pro automatické skrýt tlačítko.

## <a name="cmfcautohidebuttonisactive"></a><a name="isactive"></a>CMFCAutoHideButton::IsActive

Označuje, zda je tlačítko automatického skrytí aktivní.

```
BOOL IsActive() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je tlačítko automatického skrytí aktivní; FALSE jinak.

### <a name="remarks"></a>Poznámky

Tlačítko automatického skrytí je aktivní, když je zobrazeno přidružené okno [třídy CDockablePane.](../../mfc/reference/cdockablepane-class.md)

## <a name="cmfcautohidebuttonishorizontal"></a><a name="ishorizontal"></a>CMFCAutoHideButton::IsHorizontal

Určuje, zda je tlačítko automatického skrytí vodorovné nebo svislé.

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je tlačítko vodorovné; 0 jinak.

### <a name="remarks"></a>Poznámky

Rámec nastaví orientaci objektu [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) při jeho vytvoření.  Orientaci můžete ovládat pomocí parametru *dwAlignment* v metodě [CMFCAutoHideButton::Create.](#create)

## <a name="cmfcautohidebuttonistop"></a><a name="istop"></a>CMFCAutoHideButton::Istop

```
BOOL IsTop() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebuttonisvisible"></a><a name="isvisible"></a>CMFCAutoHideButton::jeviditelný

Označuje, zda je tlačítko automatického skrytí viditelné.

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tlačítko viditelné; FALSE jinak.

## <a name="cmfcautohidebuttonondraw"></a><a name="ondraw"></a>CMFCAutoHideButton::OnDraw

Framework volá tuto metodu při nakreslí tlačítko automatické ho skrýt.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

### <a name="remarks"></a>Poznámky

Chcete-li přizpůsobit vzhled tlačítek automatického skrytí v aplikaci, vytvořte novou třídu odvozenou z aplikace `CMFCAutoHideButton`. V odvozené třídě přepsat tuto metodu.

## <a name="cmfcautohidebuttonondrawborder"></a><a name="ondrawborder"></a>CMFCAutoHideButton::OnDrawBorder

Framework volá tuto metodu při nakreslí ohraničení automaticky skrýt tlačítko.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*rectBounds*<br/>
[v] Ohraničovací obdélník tlačítka automatického skrytí.

*rectBorderSize*<br/>
[v] Tloušťka ohraničení pro každou stranu tlačítka automatického skrytí.

### <a name="remarks"></a>Poznámky

Pokud chcete přizpůsobit ohraničení každého tlačítka automatického skrytí v aplikaci, `CMFCAutoHideButton`vytvořte novou třídu odvozenou z . V odvozené třídě přepsat tuto metodu.

## <a name="cmfcautohidebuttononfillbackground"></a><a name="onfillbackground"></a>CMFCAutoHideButton::OnFillBackground

Framework volá tuto metodu, když vyplní pozadí automaticky skrýt tlačítko.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*Rect*<br/>
[v] Ohraničovací obdélník tlačítka automatického skrytí.

### <a name="remarks"></a>Poznámky

Pokud chcete přizpůsobit pozadí pro tlačítka automatického skrytí v aplikaci, `CMFCAutoHideButton`vytvořte novou třídu odvozenou z . V odvozené třídě přepsat tuto metodu.

## <a name="cmfcautohidebuttonshowattachedwindow"></a><a name="showattachedwindow"></a>CMFCAutoHideButton::ShowAttachedWindow

Zobrazí nebo skryje přidruženou [třídu CDockablePane](../../mfc/reference/cdockablepane-class.md).

```cpp
void ShowAttachedWindow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bZobrazit*<br/>
[v] Logická hodnota, která určuje, zda `CDockablePane`tato metoda zobrazuje připojenou .

## <a name="cmfcautohidebuttonshowbutton"></a><a name="showbutton"></a>CMFCAutoHideButton::ShowButton

Zobrazí nebo skryje tlačítko automatického skrytí.

```
virtual void ShowButton(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bZobrazit*<br/>
[v] Logická hodnota, která určuje, zda se má tlačítko automatického skrytí zobrazit.

## <a name="cmfcautohidebuttonmove"></a><a name="move"></a>CMFCAutoHideButton::Přesunout

```cpp
void Move(int nOffset);
```

### <a name="parameters"></a>Parametry

[v] *nOffset*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebuttonreplacepane"></a><a name="replacepane"></a>CMFCAutoHideButton::Replacepane

```cpp
void ReplacePane(CDockablePane* pNewBar);
```

### <a name="parameters"></a>Parametry

[v] *pNewBar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebuttonunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFCAutoHideButton::UnsetAutoHideMode

Zakažte režim automatického skrytí.

```
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```

### <a name="parameters"></a>Parametry

*pFirstBarInGroup*<br/>
[v] Ukazatel na první pruh ve skupině.

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebuttonhighlightbutton"></a><a name="highlightbutton"></a>CMFCAutoHideButton::HighlightButton

Zvýrazní tlačítko automatického skrytí.

```
virtual void HighlightButton(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bZvýraznění*<br/>
Určuje nový stav tlačítka automatického skrytí. PRAVDA označuje, že tlačítko je zvýrazněno, FALSE označuje, že tlačítko není zvýrazněno.

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebuttonishighlighted"></a><a name="ishighlighted"></a>CMFCAutoHideButton::Zvýrazněno

Vrátí stav zvýraznění tlačítka automatického skrytí.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je zvýrazněno tlačítko automatického skrytí; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCAutohidebar](../../mfc/reference/cmfcautohidebar-class.md)<br/>
[CAutoHideDockSite – třída](../../mfc/reference/cautohidedocksite-class.md)
