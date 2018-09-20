---
title: Csingledoctemplate – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 66b5ff9f2cae462ebd7e5bb90cd51f02600e6a85
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395866"
---
# <a name="csingledoctemplate-class"></a>Csingledoctemplate – třída

Definuje šablonu dokumentu, která implementuje rozhraní jednoho dokumentu (SDI).

## <a name="syntax"></a>Syntaxe

```
class CSingleDocTemplate : public CDocTemplate
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSingleDocTemplate::CSingleDocTemplate](#csingledoctemplate)|Vytvoří `CSingleDocTemplate` objektu.|

## <a name="remarks"></a>Poznámky

Aplikace SDI hlavní okno rámce používá k zobrazení dokumentu. najednou může být otevřeno pouze jeden dokument.

Definuje šablonu dokumentu vztah mezi tři typy tříd:

- Třídy dokumentu, které jsou odvozeny z `CDocument`.

- Třídy zobrazení, která zobrazuje data ze třídy dokumentu uvedené výše. Z této třídy lze odvodit `CView`, `CScrollView`, `CFormView`, nebo `CEditView`. (Můžete také použít `CEditView` přímo.)

- Třída okno rámce, který obsahuje zobrazení. Pro šablonu aplikace SDI dokumentu, lze odvodit z této třídy `CFrameWnd`; Pokud není potřeba přizpůsobit chování hlavní okno rámce, můžete použít `CFrameWnd` přímo bez odvození vlastní třídy.

Aplikace SDI obvykle podporuje jeden typ souboru, takže má jenom jednu `CSingleDocTemplate` objektu. Najednou může být otevřeno pouze jeden dokument.

Není nutné volat jakékoli členské funkce `CSingleDocTemplate` s výjimkou konstruktoru. Obslužné rutiny framework `CSingleDocTemplate` objekty interně.

Další informace o používání `CSingleDocTemplate`, naleznete v tématu [šablony dokumentů a proces vytváření dokumentů/zobrazení](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate –](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="csingledoctemplate"></a>  CSingleDocTemplate::CSingleDocTemplate

Vytvoří `CSingleDocTemplate` objektu.

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parametry

*nIDResource*<br/>
Určuje Identifikátor prostředku použitého typu dokumentu. To může zahrnovat nabídky, ikony, tabulky akcelerátorů a řetězcové prostředky.

Prostředek řetězce se skládá z až sedm dílčích řetězců oddělených znakem "\n" (znak '\n' je potřeba jako zástupný symbol, pokud neuvedete podřetězce; ale nejsou nezbytné koncové znaky '\n'); Tyto podřetězců popisují typ dokumentu. Informace o dílčích řetězců naleznete v tématu [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Tento prostředek řetězce najdete v souboru prostředků aplikace. Příklad:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

Můžete upravit tento řetězec pomocí editoru řetězce; celý řetězec se zobrazí jako jedna položka v editoru řetězce, nikoli sedm samostatné položky.

Další informace o těchto typech prostředků najdete v tématu [Editor řetězců](../../windows/string-editor.md).

*pDocClass*<br/>
Odkazuje `CRuntimeClass` objekt třídy dokumentu. Tato třída je `CDocument`-odvozené třídy, které definujete k vyjádření vašich dokumentů.

*pFrameClass*<br/>
Odkazuje `CRuntimeClass` objekt okna rámce třídy. Tato třída může být `CFrameWnd`– odvozené třídy, nebo to může být `CFrameWnd` samotný Pokud chcete výchozí chování okna hlavního rámce.

*pViewClass*<br/>
Odkazuje `CRuntimeClass` objekt třídy zobrazení. Tato třída je `CView`-odvozené třídy, které definujete pro zobrazení dokumentů.

### <a name="remarks"></a>Poznámky

Dynamicky přidělovat `CSingleDocTemplate` objektu a předejte ji do `CWinApp::AddDocTemplate` z `InitInstance` členské funkce třídy aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC DOCKTOOL](../../visual-cpp-samples.md)<br/>
[CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)<br/>
[CMultiDocTemplate – třída](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[CWinApp – třída](../../mfc/reference/cwinapp-class.md)
