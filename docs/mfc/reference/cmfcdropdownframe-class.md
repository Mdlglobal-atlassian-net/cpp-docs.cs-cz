---
title: Cmfcdropdownframe – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ae1b3dfdd4b5d2160b154a99f76a505a8fb82cf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428041"
---
# <a name="cmfcdropdownframe-class"></a>Cmfcdropdownframe – třída

Poskytuje funkce okna rámce rozevíracího seznamu na panely nástrojů v rozevíracím seznamu a rozevírací tlačítka.

## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|`CMFCDropDownFrame::CMFCDropDownFrame`|Výchozí konstruktor.|
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCDropDownFrame::Create](#create)|Vytvoří `CMFCDropDownFrame` objektu.|
|`CMFCDropDownFrame::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Načte nabídek nadřazeného rámce rozevíracího seznamu.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Načte nadřazené rozbalovací nabídky rámce rozevíracího seznamu.|
|`CMFCDropDownFrame::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Přemístí rámce rozevíracího seznamu.|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Nastaví, zda je automaticky zničen podřízeného okna nástrojů v rozevíracím seznamu.|

### <a name="remarks"></a>Poznámky

Tato třída není určena pro použití přímo v kódu.

Rozhraní používá k poskytování rámce chování této třídy `CMFCDropDownToolbar` a `CMFCDropDownToolbarButton` třídy. Další informace o těchto tříd naleznete v tématu [CMFCDropDownToolbar – třída](../../mfc/reference/cmfcdropdowntoolbar-class.md) a [cmfcdropdowntoolbarbutton – třída](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak se načítají ukazatel na `CMFCDropDownFrame` objektu z `CFrameWnd` třídy a jak nastavit podřízené okno panelu nástrojů v rozevíracím seznamu zničení, automaticky.

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[Cminiframewnd –](../../mfc/reference/cminiframewnd-class.md)

[Cmfcdropdownframe –](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdropdowntoolbar.h

##  <a name="create"></a>  CMFCDropDownFrame::Create

Vytvoří `CMFCDropDownFrame` objektu.

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
|*pWndParent*|[in] Nadřazené okno rámce rozevíracího seznamu.|
|*x*|[in] Vodorovné obrazovky souřadnice umístění rozevírací rámce.|
|*y*|[in] Souřadnice obrazovky svislé umístění rámce rozevírací.|
|*pWndOriginToolbar*|[in] Panel nástrojů, který má rozevíracích tlačítek, které tato metoda používá k naplnění nový objekt rámce rozevíracího seznamu.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud rámec rozevíracího seznamu byl úspěšně vytvořen; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda volá základní [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) metodu pro vytvoření stylem WS_POPUP oknem rámce rozevíracího seznamu. Okno rámce rozevíracího seznamu se zobrazí na souřadnicích zadanou obrazovku. Tato metoda selže, pokud [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) metoda vrátí hodnotu FALSE.

`CMFCDropDownFrame` Třídy vytvoří kopii zadaného `CMFCDropDownToolBar` parametru. Tato metoda zkopíruje obrázky tlačítka a tlačítka stavy z `pWndOriginToolbar` parametr `m_pWndOriginToolbar` datový člen.

##  <a name="getparentmenubar"></a>  CMFCDropDownFrame::GetParentMenuBar

Načte nabídek nadřazeného rámce rozevíracího seznamu.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řádku nabídek nadřazeného rámce rozevíracího seznamu nebo hodnota NULL, pokud rámec nemá žádný nadřazený objekt.

### <a name="remarks"></a>Poznámky

Tato metoda načte panel nabídek nadřazené z nadřazené tlačítka. Tato metoda vrátí hodnotu NULL, pokud má frame rozevíracího seznamu se neobjeví tlačítko nadřazené nebo tlačítko nadřazené má nabídek žádné nadřazené.

##  <a name="getparentpopupmenu"></a>  CMFCDropDownFrame::GetParentPopupMenu

Načte nadřazené rozbalovací nabídky rámce rozevíracího seznamu.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nadřazenou rozevírací nabídky rámce rozevíracího seznamu nebo hodnota NULL, pokud rámec nemá žádný nadřazený objekt.

### <a name="remarks"></a>Poznámky

Tato metoda načte nadřazené nabídky na panelu nadřazené. Tato metoda vrátí hodnotu NULL, pokud má rámec rozevíracího seznamu se neobjeví tlačítko nadřazené nebo nadřazené tlačítko nemá žádný nadřazený nabídky.

##  <a name="recalclayout"></a>  CMFCDropDownFrame::RecalcLayout

Přemístí rámce rozevíracího seznamu.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*bNotify*|[in] Nevyužité.|

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když je vytvořen rámec rozevíracího seznamu nebo změně velikosti nadřazené okno. Tato metoda se vypočítává umístění a velikost rámce rozevíracího seznamu umístění a velikost nadřazeného okna.

##  <a name="setautodestroy"></a>  CMFCDropDownFrame::SetAutoDestroy

Nastaví, zda je automaticky zničen podřízeného okna nástrojů v rozevíracím seznamu.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
[in] TRUE, pokud chcete automaticky odstranit přidružený rozevírací seznam nástrojů okna. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Pokud *bAutoDestroy* má hodnotu TRUE, pak bude `CMFCDropDownFrame` destruktor odstraní přidružené rozevírací seznam nástrojů okno. Výchozí hodnota je TRUE.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar – třída](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton – třída](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
