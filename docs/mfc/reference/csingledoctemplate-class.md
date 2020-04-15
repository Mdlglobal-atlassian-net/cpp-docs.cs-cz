---
title: Třída CSingleDocTemplate
ms.date: 11/04/2016
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
ms.openlocfilehash: 5a014b35a6cd2d12367e190e4d6dd689e28eae66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318351"
---
# <a name="csingledoctemplate-class"></a>Třída CSingleDocTemplate

Definuje šablonu dokumentu, která implementuje rozhraní jednoho dokumentu (SDI).

## <a name="syntax"></a>Syntaxe

```
class CSingleDocTemplate : public CDocTemplate
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSingleDocTemplate::CSingleDocTemplate](#csingledoctemplate)|Vytvoří `CSingleDocTemplate` objekt.|

## <a name="remarks"></a>Poznámky

Aplikace SDI používá okno hlavního rámce k zobrazení dokumentu; současně lze otevřít pouze jeden dokument.

Šablona dokumentu definuje vztah mezi třemi typy tříd:

- Třída dokumentu, která je `CDocument`odvozena z aplikace .

- Třída zobrazení, která zobrazuje data z výše uvedené třídy dokumentu. Tuto třídu můžete `CView` `CScrollView`odvodit z , , `CFormView`nebo `CEditView`. (Můžete také `CEditView` použít přímo.)

- Třída okna rámce, která obsahuje zobrazení. Pro šablonu dokumentu SDI můžete tuto `CFrameWnd`třídu odvodit z ; Pokud nepotřebujete přizpůsobit chování okna hlavního rámce, můžete `CFrameWnd` použít přímo bez odvození vlastní třídy.

Aplikace SDI obvykle podporuje jeden typ dokumentu, takže `CSingleDocTemplate` má pouze jeden objekt. Současně lze otevřít pouze jeden dokument.

Není nutné volat žádné členské funkce `CSingleDocTemplate` s výjimkou konstruktoru. Rozhraní framework `CSingleDocTemplate` zpracovává objekty interně.

Další informace o `CSingleDocTemplate`použití naleznete v [tématu Document Templates and the Document/View Creation Process](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Šablona CDoc](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="csingledoctemplatecsingledoctemplate"></a><a name="csingledoctemplate"></a>CSingleDocTemplate::CSingleDocTemplate

Vytvoří `CSingleDocTemplate` objekt.

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parametry

*nIDZdroj*<br/>
Určuje ID prostředků použitých s typem dokumentu. To může zahrnovat menu, ikonu, tabulku akcelerátoru a prostředky řetězce.

Prostředek řetězce se skládá až ze sedmi podřetězců oddělených znakem \n (znak \n je potřebný jako zástupný symbol, pokud není zahrnut podřetězec; koncové znaky \n však nejsou nutné); tyto podřetězce popisují typ dokumentu. Informace o podřetězec, naleznete v tématu [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Tento řetězec prostředku se nachází v souboru prostředků aplikace. Příklad:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

Tento řetězec můžete upravit pomocí editoru řetězců; celý řetězec se zobrazí jako jedna položka v editoru řetězců, nikoli jako sedm samostatných položek.

Další informace o těchto typech prostředků naleznete v [Editoru řetězců](../../windows/string-editor.md).

*třída pDocClass*<br/>
Odkazuje na `CRuntimeClass` objekt třídy dokumentu. Tato třída `CDocument`je odvozená třída, kterou definujete, aby reprezentovala vaše dokumenty.

*pFrameClass*<br/>
Odkazuje na `CRuntimeClass` objekt třídy okna rámce. Tato třída může `CFrameWnd`být odvozené třídy, `CFrameWnd` nebo může být sama, pokud chcete výchozí chování pro okno hlavního rámce.

*pViewClass*<br/>
Odkazuje na `CRuntimeClass` objekt třídy zobrazení. Tato třída `CView`je odvozená třída, kterou definujete pro zobrazení dokumentů.

### <a name="remarks"></a>Poznámky

Dynamicky přidělit `CSingleDocTemplate` objekt a `CWinApp::AddDocTemplate` předat `InitInstance` jej z členské funkce třídy aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>Viz také

[MFC Ukázka DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[Třída CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)<br/>
[Třída CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Třída CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[Třída CView](../../mfc/reference/cview-class.md)<br/>
[CWinApp – třída](../../mfc/reference/cwinapp-class.md)
