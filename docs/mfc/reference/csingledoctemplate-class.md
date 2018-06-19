---
title: Třída CSingleDocTemplate | Microsoft Docs
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
ms.openlocfilehash: 413b7b4a7cf11ff7e83596ecc61423d4bc4f0358
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371618"
---
# <a name="csingledoctemplate-class"></a>CSingleDocTemplate – třída
Definuje šablonu dokumentu, který implementuje rozhraní s jedním dokumentem (SDI).  
  
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
 Aplikace SDI používá hlavního okna rámce pro zobrazení dokumentu; najednou může být otevřena pouze jeden dokument.  
  
 Šablona dokumentu definuje vztahy mezi tři typy tříd:  
  
-   Třída dokumentu, která je odvozena od **CDocument**.  
  
-   Třídy zobrazení, která zobrazuje data z dokumentu třídy uvedené výše. Můžete dědit z této třídy `CView`, `CScrollView`, `CFormView`, nebo `CEditView`. (Můžete také použít `CEditView` přímo.)  
  
-   Třída okno rámce, který obsahuje zobrazení. Pro šablonu dokumentu SDI odvozujete Tato třída z `CFrameWnd`; Pokud není potřeba přizpůsobit chování hlavních rámce okna, můžete použít `CFrameWnd` přímo bez odvození vlastní třídy.  
  
 Aplikace SDI obvykle podporuje jeden typ souboru, takže má jen jeden `CSingleDocTemplate` objektu. Najednou může být otevřena pouze jeden dokument.  
  
 Nemusíte volání funkce kteréhokoli člena `CSingleDocTemplate` s výjimkou konstruktoru. Obslužné rutiny framework `CSingleDocTemplate` objekty interně.  
  
 Další informace o používání `CSingleDocTemplate`, najdete v části [šablony dokumentů a proces tvorby Document/View](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
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
 `nIDResource`  
 Určuje ID prostředků použitý s typem dokumentu. To může zahrnovat nabídky, ikona, tabulka akcelerátoru a řetězcové prostředky.  
  
 Řetězec prostředku se skládá z až sedm dílčích řetězců oddělenými znakem '\n' (znak '\n, je potřeba jako zástupný znak, pokud neuvedete dílčí řetězec; však nejsou nutné koncové znaky '\n'); Tyto dílčích řetězců popisují typ dokumentu. Informace o dílčích řetězců najdete v tématu [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Tento řetězec prostředku se nachází v souboru prostředků aplikace. Příklad:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"`  
  
 `END`  
  
 Můžete upravit tento řetězec pomocí editoru řetězec; celý řetězec se zobrazí jako jednu položku v editoru řetězec nikoli sedm samostatné položky.  
  
 Další informace o těchto typech prostředků najdete v tématu [Editor řetězce](../../windows/string-editor.md).  
  
 `pDocClass`  
 Odkazuje na `CRuntimeClass` objekt třídy dokumentu. Tato třída je **CDocument**-odvozené třídy, které definujete, aby představují dokumentů.  
  
 `pFrameClass`  
 Odkazuje na `CRuntimeClass` objekt třídy rámce okna. Tato třída může být `CFrameWnd`-odvozené třídy, nebo může být `CFrameWnd` samotné Pokud chcete použít výchozí chování pro rámec hlavního okna.  
  
 `pViewClass`  
 Odkazuje na `CRuntimeClass` objekt třídy zobrazení. Tato třída je `CView`-odvozené třídy, které definujete pro zobrazení dokumentů.  
  
### <a name="remarks"></a>Poznámky  
 Dynamicky přidělovat `CSingleDocTemplate` objektu a předejte ji do `CWinApp::AddDocTemplate` z `InitInstance` funkce člena třídy vaší aplikace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC DOCKTOOL](../../visual-cpp-samples.md)   
 [CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument – třída](../../mfc/reference/cdocument-class.md)   
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)   
 [CMultiDocTemplate – třída](../../mfc/reference/cmultidoctemplate-class.md)   
 [CView – třída](../../mfc/reference/cview-class.md)   
 [CWinApp – třída](../../mfc/reference/cwinapp-class.md)
