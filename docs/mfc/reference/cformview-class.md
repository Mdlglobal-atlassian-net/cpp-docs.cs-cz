---
title: CFormView – třída
ms.date: 11/04/2016
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
ms.openlocfilehash: 8a0c11352ffab37f50ede5c67aa810fa20e838ed
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777269"
---
# <a name="cformview-class"></a>CFormView – třída

Základní třída použitá pro zobrazení formuláře.

## <a name="syntax"></a>Syntaxe

```
class CFormView : public CScrollView
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name|Popis|
|----------|-----------------|
|[CFormView::CFormView](#cformview)|Vytvoří `CFormView` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|Používán k synchronizaci během inicializace.|

## <a name="remarks"></a>Poznámky

Zobrazení formuláře je v podstatě zobrazení, která obsahuje ovládací prvky. Tyto ovládací prvky jsou podrobně popsány podle prostředku šablony dialogového okna. Použití `CFormView` Pokud chcete, aby formuláře v aplikaci. Podporují se tato zobrazení posouvání, podle potřeby [cscrollview –](../../mfc/reference/cscrollview-class.md) funkce.

Až budete [vytvoření aplikace založené na formulářích](../../mfc/reference/creating-a-forms-based-mfc-application.md), jeho třída zobrazení můžete založit na `CFormView`, takže aplikace založené na formulářích.

Můžete také vložit nový [formuláře témata](../../mfc/form-views-mfc.md) do aplikace pro systém zobrazení dokumentu. I když aplikace nepodporují zpočátku formulářů, Visual C++ se přidání této podpory, když vložíte nový formulář.

Průvodce aplikací knihovny MFC a příkaz Přidat třídu, jsou upřednostňovanou metodou pro vytvoření aplikace založené na formulářích. Pokud je potřeba vytvořit aplikaci založené na formulářích bez použití těchto metod, viz [vytvoření aplikace založené na formulářích](../../mfc/reference/creating-a-forms-based-mfc-application.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

##  <a name="cformview"></a>  CFormView::CFormView

Vytvoří `CFormView` objektu.

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Obsahuje řetězec zakončený hodnotou null, který je název prostředku šablony dialogového okna.

*nIDTemplate*<br/>
Obsahuje identifikační číslo prostředku šablony dialogového okna.

### <a name="remarks"></a>Poznámky

Při vytváření objektu typu odvozené z `CFormView`, vyvolat jeden z konstruktorů k vytvoření objektu zobrazení a k identifikaci prostředku dialogového okna, na kterých je založena zobrazení. Název (pass řetězec jako argument konstruktoru) nebo jeho ID (pass celé číslo bez znaménka jako argument) můžete identifikovat prostředek.

Formulářové zobrazení okna a podřízené ovládací prvky nejsou vytvořeny až do `CWnd::Create` je volána. `CWnd::Create` je voláno rozhraním jako součást dokumentů a zobrazení proces vytváření, který doprovází šablonu dokumentu.

> [!NOTE]
>  Odvozené třídy *musí* zadat vlastní konstruktor. V konstruktoru, vyvolání konstruktoru, `CFormView::CFormView`, s názvem prostředku nebo ID jako argument, jak je znázorněno v předchozí přehled třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

##  <a name="isinitdlgcompleted"></a>  CFormView::IsInitDlgCompleted

Využívané prostředím MFC zajistit, že inicializace je dokončena před prováděním dalších operací.

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>Návratová hodnota

True, pokud byla dokončena inicializace funkce pro tento dialog.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CScrollView – třída](../../mfc/reference/cscrollview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView – třída](../../mfc/reference/cscrollview-class.md)
