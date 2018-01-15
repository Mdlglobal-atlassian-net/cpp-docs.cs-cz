---
title: "CDocTemplate – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocTemplate
- AFXWIN/CDocTemplate
- AFXWIN/CDocTemplate::CDocTemplate
- AFXWIN/CDocTemplate::AddDocument
- AFXWIN/CDocTemplate::CloseAllDocuments
- AFXWIN/CDocTemplate::CreateNewDocument
- AFXWIN/CDocTemplate::CreateNewFrame
- AFXWIN/CDocTemplate::CreateOleFrame
- AFXWIN/CDocTemplate::CreatePreviewFrame
- AFXWIN/CDocTemplate::GetDocString
- AFXWIN/CDocTemplate::GetFirstDocPosition
- AFXWIN/CDocTemplate::GetNextDoc
- AFXWIN/CDocTemplate::InitialUpdateFrame
- AFXWIN/CDocTemplate::LoadTemplate
- AFXWIN/CDocTemplate::MatchDocType
- AFXWIN/CDocTemplate::OpenDocumentFile
- AFXWIN/CDocTemplate::RemoveDocument
- AFXWIN/CDocTemplate::SaveAllModified
- AFXWIN/CDocTemplate::SetContainerInfo
- AFXWIN/CDocTemplate::SetDefaultTitle
- AFXWIN/CDocTemplate::SetPreviewInfo
- AFXWIN/CDocTemplate::SetServerInfo
dev_langs: C++
helpviewer_keywords:
- CDocTemplate [MFC], CDocTemplate
- CDocTemplate [MFC], AddDocument
- CDocTemplate [MFC], CloseAllDocuments
- CDocTemplate [MFC], CreateNewDocument
- CDocTemplate [MFC], CreateNewFrame
- CDocTemplate [MFC], CreateOleFrame
- CDocTemplate [MFC], CreatePreviewFrame
- CDocTemplate [MFC], GetDocString
- CDocTemplate [MFC], GetFirstDocPosition
- CDocTemplate [MFC], GetNextDoc
- CDocTemplate [MFC], InitialUpdateFrame
- CDocTemplate [MFC], LoadTemplate
- CDocTemplate [MFC], MatchDocType
- CDocTemplate [MFC], OpenDocumentFile
- CDocTemplate [MFC], RemoveDocument
- CDocTemplate [MFC], SaveAllModified
- CDocTemplate [MFC], SetContainerInfo
- CDocTemplate [MFC], SetDefaultTitle
- CDocTemplate [MFC], SetPreviewInfo
- CDocTemplate [MFC], SetServerInfo
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71d44aac1ca7a018be7be1b375dd92920af96dba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdoctemplate-class"></a>CDocTemplate – třída
Abstraktní základní třída, která definuje základní funkce pro šablony dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDocTemplate : public CCmdTarget  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDocTemplate::CDocTemplate](#cdoctemplate)|Vytvoří `CDocTemplate` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDocTemplate::AddDocument](#adddocument)|Přidá do šablony dokumentu.|  
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|Zavře všechny dokumenty, které jsou přidružené k této šabloně.|  
|[CDocTemplate::CreateNewDocument](#createnewdocument)|Vytvoří nový dokument.|  
|[CDocTemplate::CreateNewFrame](#createnewframe)|Vytvoří nové okně s rámečkem obsahující dokumentů a zobrazení.|  
|[CDocTemplate::CreateOleFrame](#createoleframe)|Vytvoří okno s povoleným OLE rámce.|  
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Vytvoří rámec podřízené používá pro bohaté Preview.|  
|[CDocTemplate::GetDocString](#getdocstring)|Načte řetězec přidružený k typu dokumentu.|  
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Načte pozici první dokument přidružená k této šabloně.|  
|[CDocTemplate::GetNextDoc](#getnextdoc)|Načte dokument a pozice dalšímu.|  
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Inicializuje okně s rámečkem a volitelně umožňuje viditelné.|  
|[CDocTemplate::LoadTemplate](#loadtemplate)|Načte prostředky pro danou `CDocTemplate` nebo odvozené třídy.|  
|[CDocTemplate::MatchDocType](#matchdoctype)|Určuje míru důvěru nalezena shoda mezi typ dokumentu a tato šablona.|  
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|Otevře se soubor určený touto cestou.|  
|[CDocTemplate::RemoveDocument](#removedocument)|Odebere z šablony dokumentu.|  
|[CDocTemplate::SaveAllModified](#saveallmodified)|Uloží všechny dokumenty přidružená k této šabloně, které byly upraveny.|  
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|Určuje prostředky pro kontejnery OLE v případě úpravy položky OLE na místě.|  
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Výchozí text se zobrazí v záhlaví okna dokumentu.|  
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Obslužná rutina náhledu nastavení mimo proces.|  
|[CDocTemplate::SetServerInfo](#setserverinfo)|Určuje prostředky a třídy v případě, že dokument serveru vložené nebo upravit na místě.|  
  
## <a name="remarks"></a>Poznámky  
 Obvykle vytvoříte jednu nebo více šablon dokumentů v provádění vaší aplikace `InitInstance` funkce. Šablona dokumentu definuje vztahy mezi tři typy tříd:  
  
-   Třída dokumentu, která je odvozena od **CDocument**.  
  
-   Třídy zobrazení, která zobrazuje data z dokumentu třídy uvedené výše. Můžete dědit z této třídy `CView`, `CScrollView`, `CFormView`, nebo `CEditView`. (Můžete také použít `CEditView` přímo.)  
  
-   Třída okno rámce, který obsahuje zobrazení. Pro jednotlivý dokument aplikaci (SDI rozhraní), odvozena z této třídy `CFrameWnd`. Pro více aplikací rozhraní (MDI) dokumentu odvozen z této třídy `CMDIChildWnd`. Pokud nepotřebujete k přizpůsobení chování rámce okna, můžete použít `CFrameWnd` nebo `CMDIChildWnd` přímo bez odvození vlastní třídy.  
  
 Aplikace má jedna šablona dokumentu pro každý typ dokumentu, který podporuje. Pokud vaše aplikace podporuje tabulky a dokumenty text, například aplikace má dva objekty šablony dokumentu. Každá šablona dokumentu je zodpovědný za vytváření a správa všechny dokumenty daného typu.  
  
 Šablona dokumentu ukládá ukazatele na `CRuntimeClass` objekty pro dokumentu, zobrazení a třídy oken s rámečkem. Tyto `CRuntimeClass` objekty jsou zadány při vytváření šablony dokumentu.  
  
 Šablona dokumentu obsahuje ID prostředků použitý s typem dokumentu (například nabídky, ikona nebo prostředků tabulky akcelerátorů). Šablona dokumentu má také řetězce obsahující další informace o jeho typ dokumentu. Mezi ně patří název typu dokumentu (například "list") a přípona souboru (například "XLS"). Volitelně může obsahovat jiné řetězců v uživatelské rozhraní aplikace, Správce souborů systému Windows a objektů propojení a podporu technologie OLE.  
  
 Pokud je vaše aplikace OLE – kontejner nebo serveru, Šablona dokumentu také definuje ID nabídky použité během aktivace na místě. Pokud je aplikace serveru OLE, Šablona dokumentu definuje ID panelu nástrojů a nabídky použité během aktivace na místě. Zadejte tyto další zdroje OLE voláním `SetContainerInfo` a `SetServerInfo`.  
  
 Protože `CDocTemplate` je abstraktní třída, nelze používat třídu přímo. Typická aplikace používá jednu ze dvou `CDocTemplate`-odvozených třídách poskytované knihovny Microsoft Foundation Class: `CSingleDocTemplate`, který implementuje SDI, a `CMultiDocTemplate`, který implementuje MDI. Tyto třídy pro další informace najdete na pomocí šablony dokumentů.  
  
 Pokud vaše aplikace vyžaduje zlepší uživatelského rozhraní, které se zásadně liší od SDI a MDI, můžete odvodit vlastní třídy z `CDocTemplate`.  
  
 Další informace o `CDocTemplate`, najdete v části [šablony dokumentů a proces tvorby Document/View](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocTemplate`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="adddocument"></a>CDocTemplate::AddDocument  
 Pomocí této funkce můžete přidat do šablony dokumentu.  
  
```  
virtual void AddDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parametry  
 `pDoc`  
 Ukazatel na dokumentu, který má být přidán.  
  
### <a name="remarks"></a>Poznámky  
 Odvozené třídy [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) a [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) funkci přepsat. Pokud odvozujete vlastní třídy šablony dokumentu z `CDocTemplate`, odvozené třídy musí přepsat tuto funkci.  
  
##  <a name="cdoctemplate"></a>CDocTemplate::CDocTemplate  
 Vytvoří `CDocTemplate` objektu.  
  
```  
CDocTemplate (
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDResource`  
 Určuje ID prostředků použitý s typem dokumentu. To může zahrnovat nabídky, ikona, tabulka akcelerátoru a řetězcové prostředky.  
  
 Řetězec prostředku se skládá z až sedm dílčích řetězců oddělenými znakem '\n' (znak '\n, je potřeba jako zástupný symbol, pokud neuvedete dílčí řetězec; však nejsou nutné koncové znaky '\n'); Tyto dílčích řetězců popisují typ dokumentu. Informace o dílčích řetězců najdete v tématu [GetDocString](#getdocstring). Tento řetězec prostředku se nachází v souboru prostředků aplikace. Příklad:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 Všimněte si, že řetězec začíná znakem '\n'; je to proto, že první dílčí řetězec nepoužívá pro aplikace MDI a proto není zahrnutý. Můžete upravit tento řetězec pomocí editoru řetězec; celý řetězec se zobrazí jako jednu položku v editoru řetězec nikoli sedm samostatné položky.  
  
 `pDocClass`  
 Odkazuje na `CRuntimeClass` objekt třídy dokumentu. Tato třída je **CDocument**-odvozené třídy, které definujete, aby představují dokumentů.  
  
 `pFrameClass`  
 Odkazuje na `CRuntimeClass` objekt třídy rámce okna. Tato třída může být `CFrameWnd`-odvozené třídy, nebo může být `CFrameWnd` samotné Pokud chcete použít výchozí chování pro rámec hlavního okna.  
  
 `pViewClass`  
 Odkazuje na `CRuntimeClass` objekt třídy zobrazení. Tato třída je `CView`-odvozené třídy, které definujete pro zobrazení dokumentů.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce člen můžete vytvořit `CDocTemplate` objektu. Dynamicky přidělovat `CDocTemplate` objektu a předejte ji do [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) z `InitInstance` funkce člena třídy vaší aplikace.  
  
##  <a name="closealldocuments"></a>CDocTemplate::CloseAllDocuments  
 Volání této funkce člen zavřete všechny otevřené dokumenty.  
  
```  
virtual void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>Parametry  
 `bEndSession`  
 Určuje, zda relace se se ukončí. Je **TRUE** Pokud relace je zakončeno; jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce se obvykle používá jako součást příkaz Konec souboru. Výchozí implementace této funkce volá [CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents) – členská funkce k odstranění dokumentu data a pak zavře okna s rámečkem pro všechna zobrazení připojené k dokumentu.  
  
 Tato funkce přepsání, pokud chcete vyžadovat, aby uživatel k provedení čištění zvláštní zpracování před zavření dokumentu. Například pokud dokument představuje záznam v databázi, můžete funkci zavřete databázi přepsat.  
  
##  <a name="createnewdocument"></a>CDocTemplate::CreateNewDocument  
 Volání této funkce člen vytvořit nový dokument typu přidruženého k této šabloně dokumentu.  
  
```  
virtual CDocument* CreateNewDocument();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený dokumentu nebo **NULL** Pokud dojde k chybě.  
  
##  <a name="createnewframe"></a>CDocTemplate::CreateNewFrame  
 Vytvoří nové okně s rámečkem obsahující dokumentů a zobrazení.  
  
```  
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,  
    CFrameWnd* pOther);
```  
  
### <a name="parameters"></a>Parametry  
 `pDoc`  
 Dokument, do které by měla odkazovat nové okně s rámečkem. Může být **NULL**.  
  
 `pOther`  
 Okno rámečku, na kterém je založeno nové okně s rámečkem. Může být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený rámce okna, nebo **NULL** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 `CreateNewFrame`používá `CRuntimeClass` objekty předaný konstruktoru vytvoření nové okně s rámečkem s zobrazení a připojený dokument. Pokud `pDoc` parametr je **NULL**, rozhraní výstupy trasování zpráv.  
  
 `pOther` Parametr se používá k implementaci okno Nový příkaz. Poskytuje okně s rámečkem na které se mají modelu nové okno rámce. Obvykle je vytvořena nové okně s rámečkem neviditelná. Volání této funkce k vytvoření oken s rámečkem mimo standardní framework provádění nový soubor a soubor otevřít.  
  
##  <a name="createoleframe"></a>CDocTemplate::CreateOleFrame  
 Vytvoří okno s rámečkem OLE.  
  
```  
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc,  
    BOOL bCreateView);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Ukazatel do nadřazeného okna rámečku.  
  
 `pDoc`  
 Ukazatel na dokument, do které by měla odkazovat nové okně s rámečkem OLE.  
  
 `bCreateView`  
 Určuje, jestli se má vytvořit zobrazení spolu s rámečku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rámec okna v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bCreateView` rovná nule, je vytvořena prázdné rámce.  
  
##  <a name="getdocstring"></a>CDocTemplate::GetDocString  
 Načte řetězec přidružený k typu dokumentu.  
  
```  
virtual BOOL GetDocString(
    CString& rString,  
    enum DocStringIndex index) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `rString`  
 Odkaz na `CString` objekt, který bude obsahovat řetězec, když funkce vrátí hodnotu.  
  
 *index*  
 Index dílčí řetězec načítány z řetězce, který popisuje typ dokumentu. Tento parametr může mít jednu z následujících hodnot:  
  
- **CDocTemplate::windowTitle** název, který se zobrazí v záhlaví okna aplikace (například "Microsoft Excel"). K dispozici pouze v šabloně pro aplikace SDI.  
  
- **CDocTemplate::docName** kořenové umístění pro název výchozího dokumentu (například "Sheet"). Tento kořenový plus číslo, se používá pro výchozí název nový dokument tohoto typu vždy, když uživatel vybere nový příkaz z nabídky soubor (například "List1" nebo "Sheet2"). Pokud není zadaný, "Bez názvu" se používá jako výchozí.  
  
- **CDocTemplate::fileNewName** název tohoto typu dokumentu. Pokud aplikace podporuje víc než jeden typ dokumentu, zobrazí se tento řetězec v dialogovém okně Nový soubor (například "list"). Pokud není zadaný, typ dokumentu je nedostupné, pomocí příkazu nový soubor.  
  
- **CDocTemplate::filterName** popis typ dokumentu a zástupný filtr odpovídající dokumenty tohoto typu. Tento řetězec se zobrazí v seznamu zobrazit soubory typu rozevíracího seznamu v dialogovém okně Otevřít soubor (například "listů (XLS)"). Pokud není zadáno, je nedostupný, pomocí příkazu Otevřít soubor typu dokumentu.  
  
- **CDocTemplate::filterExt** rozšíření pro dokumenty tohoto typu (například "XLS"). Pokud není zadáno, je nedostupný, pomocí příkazu Otevřít soubor typu dokumentu.  
  
- **CDocTemplate::regFileTypeId** identifikátor pro typ dokument má být uložen v databázi registrace spravuje pomocí systému Windows. Tento řetězec je pouze pro interní použití (například "ExcelWorksheet"). Pokud není zadaný, typ dokumentu nelze zaregistrovat pomocí Správce souborů systému Windows.  
  
- **CDocTemplate::regFileTypeName** název typu dokumentu má být uložen v databázi registrace. Tento řetězec nemusí být zobrazeny v dialogových oknech aplikací, které přístup k databázi registrace (například "Microsoft sešit aplikace Excel.").  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl nalezen zadaný dílčí řetězec; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce pro načtení určité dílčí řetězec popisující typ dokumentu. Řetězec obsahující tyto dílčích řetězců je uložen v šabloně a je odvozený z řetězce v souboru prostředků pro aplikaci. Volá rámec této funkce můžete získat řetězce, které potřebuje pro uživatelské rozhraní aplikace. Pokud jste zadali příponu názvu souboru pro dokumenty aplikace, také volá framework tuto funkci při přidání záznamu do databáze registrace Windows; To umožňuje otevírat dokumenty ze Správce souborů systému Windows.  
  
 Volání této funkce pouze v případě, že jsou odvození vlastní třídy z `CDocTemplate`.  
  
##  <a name="getfirstdocposition"></a>CDocTemplate::GetFirstDocPosition  
 Načte pozici první dokument přidružená k této šabloně.  
  
```  
virtual POSITION GetFirstDocPosition() const = 0;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít k iteraci v rámci seznamu dokumentů, které jsou přidružené k této šabloně dokumentu; nebo **NULL** Pokud je seznam prázdný.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete získat pozice první dokument v seznamu dokumentů přidružená k této šabloně. Použití **pozice** hodnotu jako argument pro [CDocTemplate::GetNextDoc](#getnextdoc) k iteraci v rámci seznamu dokumentů, které jsou přidružené k šabloně.  
  
 [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) a [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) obě čistý virtuální funkci přepsat. Jakákoli třída odvozena od `CDocTemplate` musí také přepsat tuto funkci.  
  
##  <a name="getnextdoc"></a>CDocTemplate::GetNextDoc  
 Načte seznam element identifikovaný `rPos`, pak nastaví `rPos` k **pozice** hodnotu další položky v seznamu.  
  
```  
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na další dokument v seznamu dokumentů přidružená k této šabloně.  
  
### <a name="parameters"></a>Parametry  
 `rPos`  
 Odkaz na **pozice** hodnoty vrácené z předchozího volání [GetFirstDocPosition](#getfirstdocposition) nebo `GetNextDoc`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud načtené elementem je poslední v seznamu, pak nová hodnota `rPos` je nastaven na **NULL**.  
  
 Můžete použít `GetNextDoc` ve smyčce dopředného iterace Pokud vytvořit počáteční pozice pomocí volání [GetFirstDocPosition](#getfirstdocposition).  
  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
##  <a name="initialupdateframe"></a>CDocTemplate::InitialUpdateFrame  
 Inicializuje okně s rámečkem a volitelně umožňuje viditelné.  
  
```  
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,  
    CDocument* pDoc,  
    BOOL bMakeVisible = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pFrame`  
 Okně s rámečkem vyžadující počáteční aktualizace.  
  
 `pDoc`  
 Dokument, ke kterému je přidružené rámečku. Může být **NULL**.  
  
 `bMakeVisible`  
 Určuje, zda by měl rámečku se zobrazí a aktivní.  
  
### <a name="remarks"></a>Poznámky  
 Volání **IntitialUpdateFrame** po vytvoření nového rámečku s `CreateNewFrame`. V okně rámce přijímat volání této funkce způsobí zobrazení jejich `OnInitialUpdate` volání. Navíc pokud nebyl k dispozici dříve aktivní zobrazení, primární zobrazení okna rámce přišla active; primární zobrazení je zobrazení s ID podřízeného z **AFX_IDW_PANE_FIRST**. Nakonec se provádí okně s rámečkem viditelné pokud `bMakeVisible` je nulová. Pokud `bMakeVisible` rovná nule, aktuální aktivní a stav viditelnosti okně s rámečkem zůstanou nezměněna.  
  
 Není nutné volat tuto funkci při pomocí implementace rozhraní framework nový soubor a soubor otevřít.  
  
##  <a name="loadtemplate"></a>CDocTemplate::LoadTemplate  
 Načte prostředky pro danou `CDocTemplate` nebo odvozené třídy.  
  
```  
virtual void LoadTemplate();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen je voláno rámcem načíst prostředky pro danou `CDocTemplate` nebo odvozené třídy. Obvykle je volána při vytváření, s výjimkou když šablona je vytvářen globálně. V takovém případě volání `LoadTemplate` je zpožděna, dokud [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) je volána.  
  
##  <a name="matchdoctype"></a>CDocTemplate::MatchDocType  
 Určuje míru důvěru nalezena shoda mezi typ dokumentu a tato šablona.  
  
```  
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,  
    CDocument*& rpDocMatch);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPathName`  
 Cesta k souboru, jehož typ má být určen.  
  
 `rpDocMatch`  
 Ukazatel na dokument, který je přiřazen odpovídající dokumentu, pokud soubor Určuje `lpszPathName` je již otevřeno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota z **spolehlivosti** výčtu, který je definován následujícím způsobem:  
  
```  
enum Confidence  
    {  
    noAttempt,
    maybeAttemptForeign,
    maybeAttemptNative,
    yesAttemptForeign,
    yesAttemptNative,
    yesAlreadyOpen
    };  
```  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete určit typ dokumentu šablonu použít pro otevření souboru. Pokud vaše aplikace podporuje více typů souborů, například tato funkce slouží k určení, které šablony dokumentu k dispozici je vhodný pro daný soubor voláním `MatchDocType` ke každé šabloně v zapnout a výběr šablony podle parametrů Vrácená hodnota spolehlivosti.  
  
 Pokud soubor Určuje `lpszPathName` je již otevřeno, funkce vrátí hodnotu **CDocTemplate::yesAlreadyOpen** a zkopíruje soubor do **CDocument** objektu na objekt v `rpDocMatch`.  
  
 Pokud soubor není otevřený ale rozšíření v `lpszPathName` odpovídá rozšíření určeného **CDocTemplate::filterExt**, funkce vrátí hodnotu **CDocTemplate::yesAttemptNative** a nastaví `rpDocMatch` k **NULL**. Další informace o **CDocTemplate::filterExt**, najdete v části [CDocTemplate::GetDocString](#getdocstring).  
  
 Pokud ani případě je hodnota true, vrátí funkce **CDocTemplate::yesAttemptForeign**.  
  
 Výchozí implementace nevrací **CDocTemplate::maybeAttemptForeign** nebo **CDocTemplate::maybeAttemptNative**. Přepsání této funkci můžete implementovat odpovídající typ logiku pro svou aplikaci, pravděpodobně používá tyto dvě hodnoty z **spolehlivosti** výčtu.  
  
##  <a name="opendocumentfile"></a>CDocTemplate::OpenDocumentFile  
 Otevře se soubor určený touto cestu.  
  
```  
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;  
 
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszPathName`  
 Ukazatel na cestu k souboru, který obsahuje dokument otevřít.  
  
 [v]`bAddToMRU`  
 `TRUE`Označuje, že dokument je jednou z nejnovější soubory; `FALSE` označuje dokument není jedním z nejnovější soubory.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na dokumentů, jejichž soubor název podle `lpszPathName`; `NULL` Pokud neúspěšně.  
  
### <a name="remarks"></a>Poznámky  
 Otevře soubor, jehož cesta je určena `lpszPathName`. Pokud `lpszPathName` je `NULL`, k vytvoření nového souboru, který obsahuje dokument typu přidružená k této šabloně.  
  
##  <a name="removedocument"></a>CDocTemplate::RemoveDocument  
 Odebere dokumentu, na kterou odkazuje `pDoc` ze seznamu dokumentů přidružená k této šabloně.  
  
```  
virtual void RemoveDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parametry  
 `pDoc`  
 Ukazatel na dokumentu, který má být odebrána.  
  
### <a name="remarks"></a>Poznámky  
 Odvozené třídy `CMultiDocTemplate` a `CSingleDocTemplate` funkci přepsat. Pokud odvozujete vlastní třídy šablony dokumentu z `CDocTemplate`, odvozené třídy musí přepsat tuto funkci.  
  
##  <a name="saveallmodified"></a>CDocTemplate::SaveAllModified  
 Uloží všechny dokumenty, které byly upraveny.  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulová v případě úspěšného; jinak 0.  
  
##  <a name="setcontainerinfo"></a>CDocTemplate::SetContainerInfo  
 Určuje prostředky pro kontejnery OLE v případě úpravy položky OLE na místě.  
  
```  
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDOleInPlaceContainer`  
 ID prostředků používané při aktivaci vložený objekt.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto funkci nastavit zdroje, které chcete použít, pokud objekt OLE aktivaci. Tyto prostředky mohou zahrnovat nabídky a tabulky akcelerátoru. Tato funkce je volána obvykle [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) funkce vaší aplikace.  
  
 V nabídce přidružené `nIDOleInPlaceContainer` obsahuje oddělovačů, které umožňují nabídky aktivovaný položky na místě sloučit s v nabídce aplikace kontejneru. Další informace o slučování nabídek serveru a kontejneru, najdete v článku [nabídky a prostředky (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="setdefaulttitle"></a>CDocTemplate::SetDefaultTitle  
 Volání této funkce se načíst výchozí název dokumentu a zobrazit ji v záhlaví okna dokumentu.  
  
```  
virtual void SetDefaultTitle(CDocument* pDocument) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *pDocument*  
 Ukazatel na dokument, jehož název je možné nastavit.  
  
### <a name="remarks"></a>Poznámky  
 Informace o výchozí text, najdete v části Popis **CDocTemplate::docName** v [CDocTemplate::GetDocString](#getdocstring).  
  
##  <a name="setserverinfo"></a>CDocTemplate::SetServerInfo  
 Určuje prostředky a třídy v případě, že dokument serveru vložené nebo upravit na místě.  
  
```  
void SetServerInfo(
    UINT nIDOleEmbedding,  
    UINT nIDOleInPlaceServer = 0,  
    CRuntimeClass* pOleFrameClass = NULL,  
    CRuntimeClass* pOleViewClass = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDOleEmbedding*  
 ID prostředků používá, když je otevřen objekt v samostatném okně.  
  
 `nIDOleInPlaceServer`  
 ID prostředků používá při vložený objekt aktivovat na místě.  
  
 *pOleFrameClass*  
 Ukazatel na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura obsahující informace o třídě pro rámce okna objekt vytvořený při aktivace na místě.  
  
 *pOleViewClass*  
 Ukazatel na `CRuntimeClass` struktura obsahující informace o třídě pro zobrazení objekt vytvořený při aktivace na místě.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen k identifikaci prostředky, které je serverová aplikace se použije, když uživatel požádá aktivace vložený objekt. Tyto prostředky se skládají z nabídky a tabulky akcelerátoru. Tato funkce je volána obvykle `InitInstance` vaší aplikace.  
  
 V nabídce přidružené `nIDOleInPlaceServer` obsahuje oddělovačů umožňujících nabídce serveru sloučit s nabídce kontejneru. Další informace o slučování nabídek serveru a kontejneru, najdete v článku [nabídky a prostředky (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="createpreviewframe"></a>CDocTemplate::CreatePreviewFrame  
 Vytvoří rámec podřízené používá pro bohaté Preview.  
  
```  
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Ukazatel do nadřazeného okna (obvykle poskytuje prostředí).  
  
 `pDoc`  
 Ukazatel na objekt, který dokument, jejichž obsah se zobrazit jejich náhled.  
  
### <a name="return-value"></a>Návratová hodnota  
 Neplatný ukazatel `CFrameWnd` objekt, nebo `NULL` Pokud se vytváření nezdaří.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpreviewinfo"></a>CDocTemplate::SetPreviewInfo  
 Nastaví mimo proces preview obslužné rutiny.  
  
```  
void SetPreviewInfo(
    UINT nIDPreviewFrame,  
    CRuntimeClass* pPreviewFrameClass = NULL,  
    CRuntimeClass* pPreviewViewClass = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDPreviewFrame`  
 Určuje ID prostředku rámce preview.  
  
 `pPreviewFrameClass`  
 Určuje ukazatel na strukturu pro třídy informace runtime preview rámečku.  
  
 `pPreviewViewClass`  
 Určuje ukazatel na strukturu pro třídy informace runtime zobrazení náhledu.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CSingleDocTemplate – třída](../../mfc/reference/csingledoctemplate-class.md)   
 [CMultiDocTemplate – třída](../../mfc/reference/cmultidoctemplate-class.md)   
 [CDocument – třída](../../mfc/reference/cdocument-class.md)   
 [CView – třída](../../mfc/reference/cview-class.md)   
 [CScrollView – třída](../../mfc/reference/cscrollview-class.md)   
 [CEditView – třída](../../mfc/reference/ceditview-class.md)   
 [Třídy CFormView – třída](../../mfc/reference/cformview-class.md)   
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWnd – třída](../../mfc/reference/cmdichildwnd-class.md)
