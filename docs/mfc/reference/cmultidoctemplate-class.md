---
title: Cmultidoctemplate – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 01988097d2b05daa6fc056c16f34ec00b45d6893
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071780"
---
# <a name="cmultidoctemplate-class"></a>Cmultidoctemplate – třída
Definuje šablonu dokumentu, který implementuje rozhraní více dokumentů (MDI).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMultiDocTemplate : public CDocTemplate  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|Vytvoří `CMultiDocTemplate` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Aplikace MDI používá jako pracovní prostor ve kterém může uživatel otevřít nula nebo více rámečkem v dokumentu, z nichž každý zobrazí dokument hlavní okno rámce. Podrobnější popis MDI, naleznete v tématu *Windows rozhraní pokyny pro návrh softwaru*.  
  
 Šablona dokumentu definuje vztahy mezi tři typy tříd:  
  
-   Třídy dokumentu, které jsou odvozeny z [CDocument](../../mfc/reference/cdocument-class.md).  
  
-   Třídy zobrazení, která zobrazuje data ze třídy dokumentu uvedené výše. Z této třídy lze odvodit [CView](../../mfc/reference/cview-class.md), `CScrollView`, `CFormView`, nebo `CEditView`. (Můžete také použít `CEditView` přímo.)  
  
-   Třída okno rámce, který obsahuje zobrazení. Pro šablonu dokumentu MDI, lze odvodit z této třídy `CMDIChildWnd`, nebo pokud není nutné přizpůsobit chování oken s rámečkem dokumentu, můžete použít [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) přímo bez odvození vlastní třídy.  
  
 Aplikace MDI může podporovat více než jeden typ dokumentu a dokumenty různých typů může být otevřeno ve stejnou dobu. Vaše aplikace má jednu šablonu dokumentu pro každý typ dokumentu, který ji podporuje. Například pokud aplikace MDI podporuje tabulky a textové dokumenty, aplikace má dva `CMultiDocTemplate` objekty.  
  
 Aplikace používá šablony dokumentu, když uživatel vytvoří nový dokument. Pokud aplikace podporuje více než jeden typ dokumentu, rozhraní získá názvy typů podporovaných dokumentu z šablony dokumentů a zobrazí je v seznamu v dialogovém okně Nový soubor. Jakmile uživatel vybral typu dokumentu, aplikace vytvoří objekt třídy dokumentu, objekt okna rámce a objekt zobrazení a připojí je k sobě navzájem.  
  
 Není potřeba volat jakékoli členské funkce `CMultiDocTemplate` s výjimkou konstruktoru. Obslužné rutiny framework `CMultiDocTemplate` objekty interně.  
  
 Další informace o `CMultiDocTemplate`, naleznete v tématu [šablony dokumentů a proces vytváření dokumentů/zobrazení](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate –](../../mfc/reference/cdoctemplate-class.md)  
  
 `CMultiDocTemplate`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cmultidoctemplate"></a>  CMultiDocTemplate::CMultiDocTemplate  
 Vytvoří `CMultiDocTemplate` objektu.  
  
```  
CMultiDocTemplate(
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDResource*  
 Určuje Identifikátor prostředku použitého typu dokumentu. To může zahrnovat nabídky, ikony, tabulky akcelerátorů a řetězcové prostředky.  
  
 Prostředek řetězce se skládá z až sedm dílčích řetězců oddělených znakem "\n" (znak '\n' je potřeba jako zástupný symbol pro Pokud neuvedete podřetězce; ale nejsou nezbytné koncové znaky '\n'); Tyto podřetězců popisují typ dokumentu. Informace o dílčích řetězců naleznete v tématu [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Tento prostředek řetězce najdete v souboru prostředků aplikace. Příklad:  
  
```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```
  
 Všimněte si, že řetězec začíná znakem '\n'; je to proto, že první dílčí řetězec se používá pro aplikace MDI a proto není zahrnutý. Můžete upravit tento řetězec pomocí editoru řetězce; celý řetězec se zobrazí jako jedna položka v editoru řetězce, nikoli sedm samostatné položky.  
  
 Další informace o těchto typech prostředků najdete v tématu [editory prostředků](../../windows/resource-editors.md).  
  
 *pDocClass*  
 Odkazuje `CRuntimeClass` objekt třídy dokumentu. Tato třída je `CDocument`-odvozené třídy, které definujete k vyjádření vašich dokumentů.  
  
 *pFrameClass*  
 Odkazuje `CRuntimeClass` objekt třídy oken s rámečkem. Tato třída může být `CMDIChildWnd`-odvozené třídy, nebo to může být `CMDIChildWnd` samotný Pokud chcete výchozí chování pro vaše oken s rámečkem v dokumentu.  
  
 *pViewClass*  
 Odkazuje `CRuntimeClass` objekt třídy zobrazení. Tato třída je `CView`-odvozené třídy, které definujete pro zobrazení dokumentů.  
  
### <a name="remarks"></a>Poznámky  
 Dynamicky přidělit jednu `CMultiDocTemplate` objekt pro každý typ dokumentu, která vaše aplikace podporuje a předat každému z nich `CWinApp::AddDocTemplate` z `InitInstance` členské funkce třídy aplikace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]  
  
 Tady je druhý příklad.  
  
 [!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)   
 [Csingledoctemplate – třída](../../mfc/reference/csingledoctemplate-class.md)   
 [CWinApp – třída](../../mfc/reference/cwinapp-class.md)
