---
title: Třída CMultiDocTemplate | Microsoft Docs
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
ms.openlocfilehash: 7b53228b6983c0293eb288cd0f38669d1b5db928
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate – třída
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
 Aplikace MDI používá hlavního okna rámce jako pracovní prostor ve kterém může uživatel otevřít nula nebo více dokumentů okna s rámečkem, z nichž každý dokument zobrazí. Podrobnější popis MDI najdete v tématu *Windows rozhraní pokyny pro návrh softwaru*.  
  
 Šablona dokumentu definuje vztahy mezi tři typy tříd:  
  
-   Třída dokumentu, která je odvozena od [CDocument](../../mfc/reference/cdocument-class.md).  
  
-   Třídy zobrazení, která zobrazuje data z dokumentu třídy uvedené výše. Můžete dědit z této třídy [CView](../../mfc/reference/cview-class.md), `CScrollView`, `CFormView`, nebo `CEditView`. (Můžete také použít `CEditView` přímo.)  
  
-   Třída okno rámce, který obsahuje zobrazení. Pro šablonu dokumentu MDI odvozujete Tato třída z `CMDIChildWnd`, nebo, pokud nepotřebujete k přizpůsobení chování okna s rámečkem v dokumentu, můžete použít [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) přímo bez odvození vlastní třídy.  
  
 Aplikace MDI může podporovat více než jeden typ dokumentu a dokumenty různých typů můžou být otevřené ve stejnou dobu. Aplikace má jedna šablona dokumentu pro každý typ dokumentu, který podporuje. Například pokud aplikace MDI podporuje tabulky a text dokumentů, aplikace má dva `CMultiDocTemplate` objekty.  
  
 Aplikace používá šablony dokumentu, když uživatel vytvoří nový dokument. Pokud aplikace podporuje víc než jeden typ dokumentu, rozhraní získá názvy typů podporovaných dokumentů z šablony dokumentů a zobrazí je v seznamu v dialogovém okně Nový soubor. Jakmile uživatel vybral typu dokumentu, aplikace vytvoří objekt třídy dokumentů, objektem rámce okna a objekt zobrazení a připojí je k sobě navzájem.  
  
 Není potřeba volat funkce z kteréhokoli člena `CMultiDocTemplate` s výjimkou konstruktoru. Obslužné rutiny framework `CMultiDocTemplate` objekty interně.  
  
 Další informace o `CMultiDocTemplate`, najdete v části [šablony dokumentů a proces tvorby Document/View](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
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
 `nIDResource`  
 Určuje ID prostředků použitý s typem dokumentu. To může zahrnovat nabídky, ikona, tabulka akcelerátoru a řetězcové prostředky.  
  
 Řetězec prostředku se skládá z až sedm dílčích řetězců oddělenými znakem '\n' (znak '\n, je potřeba jako zástupný symbol, pokud neuvedete dílčí řetězec; však nejsou nutné koncové znaky '\n'); Tyto dílčích řetězců popisují typ dokumentu. Informace o dílčích řetězců najdete v tématu [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Tento řetězec prostředku se nachází v souboru prostředků aplikace. Příklad:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 Všimněte si, že řetězec začíná znakem '\n'; je to proto, že první dílčí řetězec nepoužívá pro aplikace MDI a proto není zahrnutý. Můžete upravit tento řetězec pomocí editoru řetězec; celý řetězec se zobrazí jako jednu položku v editoru řetězec nikoli sedm samostatné položky.  
  
 Další informace o těchto typech prostředků najdete v tématu [editory prostředků](../../windows/resource-editors.md).  
  
 `pDocClass`  
 Odkazuje na `CRuntimeClass` objekt třídy dokumentu. Tato třída je **CDocument**-odvozené třídy, které definujete, aby představují dokumentů.  
  
 `pFrameClass`  
 Odkazuje na `CRuntimeClass` objekt třídy oken s rámečkem. Tato třída může být `CMDIChildWnd`-odvozené třídy, nebo může být `CMDIChildWnd` samotné Pokud chcete použít výchozí chování pro vaše okna s rámečkem dokumentu.  
  
 `pViewClass`  
 Odkazuje na `CRuntimeClass` objekt třídy zobrazení. Tato třída je `CView`-odvozené třídy, které definujete pro zobrazení dokumentů.  
  
### <a name="remarks"></a>Poznámky  
 Dynamicky přidělovat jeden `CMultiDocTemplate` objekt pro každý typ dokumentu, který vaše aplikace podporuje a předat každému z nich `CWinApp::AddDocTemplate` z `InitInstance` funkce člena třídy vaší aplikace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]  
  
 Zde je druhém příkladu.  
  
 [!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)   
 [CSingleDocTemplate – třída](../../mfc/reference/csingledoctemplate-class.md)   
 [CWinApp – třída](../../mfc/reference/cwinapp-class.md)
