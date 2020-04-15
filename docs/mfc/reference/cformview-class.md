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
ms.openlocfilehash: a9b897c661731878f0bf78c9d04ae7c4ba28cd42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373804"
---
# <a name="cformview-class"></a>CFormView – třída

Základní třída používaná pro zobrazení formuláře.

## <a name="syntax"></a>Syntaxe

```
class CFormView : public CScrollView
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CFormView::CFormView](#cformview)|Vytvoří `CFormView` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFormView::IsInitDlgCompleted CFormView::IsInitDlgCompleted CFormView::IsInitDlgCompleted CForm](#isinitdlgcompleted)|Používá se pro synchronizaci během inicializace.|

## <a name="remarks"></a>Poznámky

Zobrazení formuláře je v podstatě zobrazení, které obsahuje ovládací prvky. Tyto ovládací prvky jsou rozloženy na základě prostředku šablony dialogu. Použijte, `CFormView` pokud chcete formuláře v žádosti. Tato zobrazení podporují posouvání, podle potřeby pomocí funkce [CScrollView.](../../mfc/reference/cscrollview-class.md)

Při [vytváření aplikace založené na formulářích](../../mfc/reference/creating-a-forms-based-mfc-application.md)můžete založit `CFormView`její třídu zobrazení na aplikaci založené na formulářích.

Do aplikací založených na zobrazení dokumentu můžete také vložit nová [témata formuláře.](../../mfc/form-views-mfc.md) I v případě, že vaše aplikace zpočátku nepodporovala formuláře, visual c++ přidá tuto podporu při vložení nového formuláře.

Průvodce aplikací knihovny MFC a příkaz Přidat třídu jsou upřednostňované metody pro vytváření aplikací založených na formulářích. Pokud potřebujete vytvořit aplikaci založenou na formulářích bez použití těchto metod, přečtěte si informace [o vytvoření aplikace založené na formulářích](../../mfc/reference/creating-a-forms-based-mfc-application.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="cformviewcformview"></a><a name="cformview"></a>CFormView::CFormView

Vytvoří `CFormView` objekt.

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Obsahuje řetězec s ukončeným hodnotou null, který je názvem prostředku šablony dialogu.

*nIDŠablona*<br/>
Obsahuje id číslo prostředku šablony dialogu.

### <a name="remarks"></a>Poznámky

Když vytvoříte objekt typu odvozeného `CFormView`z , vyvoláte jeden z konstruktorů k vytvoření objektu zobrazení a identifikaci prostředku dialogu, na kterém je zobrazení založeno. Prostředek můžete identifikovat buď podle názvu (předejte řetězec jako argument konstruktoru) nebo jeho ID (předat nepodepsané celé číslo jako argument).

Okno zobrazení formuláře a podřízené ovládací `CWnd::Create` prvky nejsou vytvořeny, dokud není volána. `CWnd::Create`je volána rámci jako součást procesu vytváření dokumentu a zobrazení, který je řízen šablonou dokumentu.

> [!NOTE]
> Odvozené třídy *musí* dodávat vlastní konstruktor. V konstruktoru vyvoláte konstruktor , `CFormView::CFormView`s názvem prostředku nebo ID jako argument, jak je znázorněno v přehledu předchozí třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

## <a name="cformviewisinitdlgcompleted"></a><a name="isinitdlgcompleted"></a>CFormView::IsInitDlgCompleted CFormView::IsInitDlgCompleted CFormView::IsInitDlgCompleted CForm

Používá knihovny MFC k zajištění dokončení inicializace před provedením jiných operací.

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>Návratová hodnota

True, pokud byla dokončena funkce inicializace pro tento dialog.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CScrollView – třída](../../mfc/reference/cscrollview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView – třída](../../mfc/reference/cscrollview-class.md)
