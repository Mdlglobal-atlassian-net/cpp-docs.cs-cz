---
title: Třída CMultiDocTemplate
ms.date: 11/04/2016
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
ms.openlocfilehash: 3b3f239b05b1cf7661929333e2d616acce6bedb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319735"
---
# <a name="cmultidoctemplate-class"></a>Třída CMultiDocTemplate

Definuje šablonu dokumentu, která implementuje rozhraní více dokumentů (MDI).

## <a name="syntax"></a>Syntaxe

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|Vytvoří `CMultiDocTemplate` objekt.|

## <a name="remarks"></a>Poznámky

Aplikace MDI používá okno hlavního rámce jako pracovní plochu, ve které může uživatel otevřít nulu nebo více oken rámců dokumentu, z nichž každý zobrazuje dokument. Podrobnější popis rozhraní MDI naleznete v *pokynech rozhraní systému Windows pro návrh softwaru*.

Šablona dokumentu definuje vztahy mezi třemi typy tříd:

- Třída dokumentu, kterou odvozujete z [CDocument](../../mfc/reference/cdocument-class.md).

- Třída zobrazení, která zobrazuje data z výše uvedené třídy dokumentu. Tuto třídu můžete odvodit `CEditView`z [CView](../../mfc/reference/cview-class.md), `CScrollView`, `CFormView`, nebo . (Můžete také `CEditView` použít přímo.)

- Třída okna rámce, která obsahuje zobrazení. Pro šablonu dokumentu MDI můžete tuto `CMDIChildWnd`třídu odvodit z aplikace , nebo pokud nepotřebujete přizpůsobit chování oken rámečků dokumentu, můžete přímo použít [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) bez odvození vlastní třídy.

Aplikace MDI může podporovat více než jeden typ dokumentu a dokumenty různých typů mohou být otevřeny současně. Aplikace má jednu šablonu dokumentu pro každý typ dokumentu, který podporuje. Pokud například aplikace MDI podporuje tabulky i textové dokumenty, `CMultiDocTemplate` má aplikace dva objekty.

Aplikace používá šablony dokumentu, když uživatel vytvoří nový dokument. Pokud aplikace podporuje více než jeden typ dokumentu, pak rozhraní získá názvy podporovaných typů dokumentů ze šablon dokumentů a zobrazí je v seznamu v dialogovém okně Nový soubor. Jakmile uživatel vybere typ dokumentu, aplikace vytvoří objekt třídy dokumentu, objekt okna rámečku a objekt zobrazení a připojí je k sobě.

Není nutné volat žádné členské `CMultiDocTemplate` funkce s výjimkou konstruktoru. Rozhraní framework `CMultiDocTemplate` zpracovává objekty interně.

Další informace `CMultiDocTemplate`naleznete v [tématu Document Templates and the Document/View Creation Process](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Šablona CDoc](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cmultidoctemplatecmultidoctemplate"></a><a name="cmultidoctemplate"></a>CMultiDocTemplate::CMultiDocTemplate

Vytvoří `CMultiDocTemplate` objekt.

```
CMultiDocTemplate(
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
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Všimněte si, že řetězec začíná znakem \n; Důvodem je, že první podřetězec se nepoužívá pro aplikace MDI a proto není zahrnuta. Tento řetězec můžete upravit pomocí editoru řetězců; celý řetězec se zobrazí jako jedna položka v editoru řetězců, nikoli jako sedm samostatných položek.

Další informace o těchto typech prostředků naleznete v [tématu Editory prostředků](../../windows/resource-editors.md).

*třída pDocClass*<br/>
Odkazuje na `CRuntimeClass` objekt třídy dokumentu. Tato třída `CDocument`je odvozená třída, kterou definujete, aby reprezentovala vaše dokumenty.

*pFrameClass*<br/>
Odkazuje na `CRuntimeClass` objekt třídy okno rámce. Tato třída může `CMDIChildWnd`být odvozené třídy, `CMDIChildWnd` nebo může být sama, pokud chcete výchozí chování pro okna rámce dokumentu.

*pViewClass*<br/>
Odkazuje na `CRuntimeClass` objekt třídy zobrazení. Tato třída `CView`je odvozená třída, kterou definujete pro zobrazení dokumentů.

### <a name="remarks"></a>Poznámky

Dynamicky přidělit jeden `CMultiDocTemplate` objekt pro každý typ dokumentu, `CWinApp::AddDocTemplate` který `InitInstance` vaše aplikace podporuje a předat každý z členské funkce třídy aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

Zde je druhý příklad.

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>Viz také

[Třída CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Třída CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CWinApp – třída](../../mfc/reference/cwinapp-class.md)
