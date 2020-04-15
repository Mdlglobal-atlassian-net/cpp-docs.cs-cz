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
ms.openlocfilehash: a5e95efe1880f1177490d55988ca1fe42c606b15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367542"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame – třída

Poskytuje funkci rozevíracího okna pro rozevírací panely nástrojů a tlačítka rozevíracího panelu nástrojů.

## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Name (Název)|Popis|
|`CMFCDropDownFrame::CMFCDropDownFrame`|Výchozí konstruktor.|
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name (Název)|Popis|
|[CMFCDropDownFrame::Vytvořit](#create)|Vytvoří `CMFCDropDownFrame` objekt.|
|`CMFCDropDownFrame::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCDropDownFrame::Panel getparentmenubar](#getparentmenubar)|Načte nadřazený řádek nabídek rozevíracího rámečku.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Načte nadřazenou rozbalovací nabídku rozevíracího rámečku.|
|`CMFCDropDownFrame::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCDropDownFrame::Rozložení rekalc](#recalclayout)|Přemístí rozevírací rámeček.|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Nastaví, zda bude podřízené okno rozevíracího panelu nástrojů automaticky zničeno.|

### <a name="remarks"></a>Poznámky

Tato třída není určena pro použití přímo z vašeho kódu.

Rámec používá tuto třídu k `CMFCDropDownToolbar` poskytování `CMFCDropDownToolbarButton` chování rámce a třídy. Další informace o těchto třídách naleznete v [tématu CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md) a [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak načíst `CMFCDropDownFrame` ukazatel na `CFrameWnd` objekt z třídy a jak nastavit podřízené rozevírací panel nástrojů, které mají být zničeny automaticky.

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CmFCDropDownRám](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdropdowntoolbar.h

## <a name="cmfcdropdownframecreate"></a><a name="create"></a>CMFCDropDownFrame::Vytvořit

Vytvoří `CMFCDropDownFrame` objekt.

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
|*pWndParent*|[v] Nadřazené okno rozevíracího rámečku.|
|*X*|[v] Souřadnice vodorovné obrazovky pro umístění rámečku dolů.|
|*Y*|[v] Svislá souřadnice obrazovky pro umístění rámečku dolů.|
|*pWndOriginToolbar*|[v] Panel nástrojů, který má rozevírací tlačítka, která tato metoda používá k naplnění nového objektu rozevíracího rámce.|

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl rozbalovací rámeček úspěšně vytvořen; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda volá základní [Metodu CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) k vytvoření rozevíracího okna s WS_POPUP stylem. Okno rozevíracího rámečku se zobrazí na určených souřadnicích obrazovky. Tato metoda se nezdaří, pokud metoda [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) vrátí hodnotu FALSE.

Třída `CMFCDropDownFrame` vytvoří kopii zadaný `CMFCDropDownToolBar` parametr. Tato metoda zkopíruje obrázky tlačítek `pWndOriginToolbar` a `m_pWndOriginToolbar` stavy tlačítek z parametru do datového prvku.

## <a name="cmfcdropdownframegetparentmenubar"></a><a name="getparentmenubar"></a>CMFCDropDownFrame::Panel getparentmenubar

Načte nadřazený řádek nabídek rozevíracího rámečku.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nadřazený řádek nabídek rozevíracího rámečku nebo NULL, pokud rámeček nemá nadřazenou položku.

### <a name="remarks"></a>Poznámky

Tato metoda načte nadřazený řádek nabídek z nadřazeného tlačítka. Tato metoda vrátí hodnotu NULL, pokud rozevírací rámeček nemá žádné nadřazené tlačítko nebo nadřazené tlačítko nemá žádný nadřazený řádek nabídek.

## <a name="cmfcdropdownframegetparentpopupmenu"></a><a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu

Načte nadřazenou rozbalovací nabídku rozevíracího rámečku.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nadřazenou rozevírací nabídku rozevíracího rámečku nebo HODNOTU NULL, pokud rámeček nemá nadřazenou položku.

### <a name="remarks"></a>Poznámky

Tato metoda načte nadřazenou nabídku z nadřazeného tlačítka. Tato metoda vrátí hodnotu NULL, pokud rozevírací rámeček nemá žádné nadřazené tlačítko nebo nadřazené tlačítko nemá žádnou nadřazenou nabídku.

## <a name="cmfcdropdownframerecalclayout"></a><a name="recalclayout"></a>CMFCDropDownFrame::Rozložení rekalc

Přemístí rozevírací rámeček.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*bUpozornit*|[v] Nepoužité.|

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto metodu při vytvoření rozevíracího rámce nebo při změní velikost nadřazeného okna. Tato metoda vypočítá umístění a velikost rozevíracího rámečku pomocí umístění a velikosti nadřazeného okna.

## <a name="cmfcdropdownframesetautodestroy"></a><a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy

Nastaví, zda bude podřízené okno rozevíracího panelu nástrojů automaticky zničeno.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
[v] TRUE automaticky zničit přidružené rozevírací panel panelu nástrojů; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud *bAutoDestroy* je PRAVDA, pak `CMFCDropDownFrame` destruktor zničí přidružené rozevírací panel nástrojů. Výchozí hodnota je TRUE.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar – třída](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton – třída](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
