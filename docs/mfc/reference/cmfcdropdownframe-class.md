---
title: CMFCDropDownFrame – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
ms.openlocfilehash: 534dc90443371c8440e0cb317540f2cf80f6eacc
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420328"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame – třída

Poskytuje funkce okna s rozevíracími rámečky pro rozevírací panely nástrojů a tlačítka panelu nástrojů pro rozevírací seznam.

## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|`CMFCDropDownFrame::CMFCDropDownFrame`|Výchozí konstruktor|
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCDropDownFrame:: Create](#create)|Vytvoří objekt `CMFCDropDownFrame`.|
|`CMFCDropDownFrame::CreateObject`|Používá se rozhraním k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Načte nadřazený panel nabídek v rámci rozevíracího seznamu.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Načte nadřazenou místní nabídku pro rozevírací rámeček.|
|`CMFCDropDownFrame::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Přemístí rozevírací rámeček.|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Nastaví, zda bude automaticky zničeno podřízené okno panelu nástrojů.|

### <a name="remarks"></a>Poznámky

Tato třída není určena pro použití přímo v kódu.

Rozhraní používá tuto třídu k zajištění chování rámce pro `CMFCDropDownToolbar` a `CMFCDropDownToolbarButton` třídy. Další informace o těchto třídách naleznete v tématu Třída [CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md) a [Třída CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak načíst ukazatel na objekt `CMFCDropDownFrame` z `CFrameWnd` třídy a jak nastavit podřízené okno panelu nástrojů na Automatické zničení.

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdropdowntoolbar. h

##  <a name="create"></a>CMFCDropDownFrame:: Create

Vytvoří objekt `CMFCDropDownFrame`.

```
virtual BOOL Create(
    CWnd* pWndParent,
    int x,
    int y,
    CMFCDropDownToolBar* pWndOriginToolbar);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pWndParent*|pro Nadřazené okno rámce rozevíracího seznamu.|
|*znak*|pro Souřadnice vodorovné obrazovky pro umístění okolního snímku|
|*požadované*|pro Souřadnice svislé obrazovky pro umístění okolního snímku|
|*pWndOriginToolbar*|pro Panel nástrojů s rozevíracími tlačítky, které tato metoda používá k naplnění nového objektu snímku.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byl rozevírací rámec úspěšně vytvořen; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda volá základní metodu [CMiniFrameWnd:: CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) pro vytvoření okna s rozevíracím rámečkem se stylem WS_POPUP. Okno s rozevíracím rámečkem se zobrazí na zadaných souřadnicích obrazovky. Tato metoda se nezdařila, pokud metoda [CMiniFrameWnd:: CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) vrátí hodnotu false.

Třída `CMFCDropDownFrame` vytvoří kopii zadaného `CMFCDropDownToolBar` parametru. Tato metoda zkopíruje obrázky tlačítek a stavy tlačítek z parametru `pWndOriginToolbar` do datového členu `m_pWndOriginToolbar`.

##  <a name="getparentmenubar"></a>CMFCDropDownFrame::GetParentMenuBar

Načte nadřazený panel nabídek v rámci rozevíracího seznamu.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nadřazený panel nabídek v rámci rozevíracího seznamu nebo hodnotu NULL, pokud rámec nemá nadřazený objekt.

### <a name="remarks"></a>Poznámky

Tato metoda načte nadřazený panel nabídek z nadřazeného tlačítka. Tato metoda vrátí hodnotu NULL, pokud nemá rozevírací rámeček žádné nadřazené tlačítko, nebo nadřazené tlačítko nemá nadřazený řádek nabídek.

##  <a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu

Načte nadřazenou místní nabídku pro rozevírací rámeček.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nadřazenou rozevírací nabídku v rámci rozevíracího seznamu nebo hodnotu NULL, pokud rámec nemá nadřazený objekt.

### <a name="remarks"></a>Poznámky

Tato metoda načte nadřazenou nabídku z nadřazeného tlačítka. Tato metoda vrátí hodnotu NULL, pokud nemá rozevírací rámeček žádné nadřazené tlačítko, nebo nadřazené tlačítko nemá žádnou nadřazenou nabídku.

##  <a name="recalclayout"></a>CMFCDropDownFrame::RecalcLayout

Přemístí rozevírací rámeček.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*bNotify*|pro Nepoužívané.|

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když je vytvořen rozevírací rámeček nebo dojde ke změně velikosti nadřazeného okna. Tato metoda vypočítá pozici a velikost rozevíracího rámečku pomocí pozice a velikosti nadřazeného okna.

##  <a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy

Nastaví, zda bude automaticky zničeno podřízené okno panelu nástrojů.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
pro TRUE pro Automatické zničení přidruženého rozevíracího okna panelu nástrojů; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud má *bAutoDestroy* hodnotu true, pak destruktor `CMFCDropDownFrame` odstraní přidružené okno panelu nástrojů. Výchozí hodnota je TRUE (pravda).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar – třída](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton – třída](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
