---
title: CDocTemplate – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 8044af41a3176d58c09f2c91c52497fa7f59de05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658585"
---
# <a name="cdoctemplate-class"></a>CDocTemplate – třída

Abstraktní základní třída definující základní funkčnost pro šablony dokumentů.

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
|[CDocTemplate::AddDocument](#adddocument)|Přidání dokumentu do šablony.|
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|Zavře všechny dokumenty, které jsou spojené s touto šablonou.|
|[CDocTemplate::CreateNewDocument](#createnewdocument)|Vytvoří nový dokument.|
|[CDocTemplate::CreateNewFrame](#createnewframe)|Vytvoří nový objekt okna rámce obsahující dokumentů a zobrazení.|
|[CDocTemplate::CreateOleFrame](#createoleframe)|Vytvoří okno rámce povolené OLE.|
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Vytvoří podřízený rámec pro náhled ve formátu RTF.|
|[CDocTemplate::GetDocString](#getdocstring)|Načte řetězec přidružený k typu dokumentu.|
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Získá pozici první dokument spojené s touto šablonou.|
|[CDocTemplate::GetNextDoc](#getnextdoc)|Načte dokument a pozice dalším objektem.|
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Inicializuje okno rámce a volitelně stane viditelným.|
|[CDocTemplate::LoadTemplate](#loadtemplate)|Načte prostředky danou `CDocTemplate` nebo odvozené třídy.|
|[CDocTemplate::MatchDocType](#matchdoctype)|Určuje, do jaké míry důvěry mezi typem dokumentu a tato šablona se shodují.|
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|Otevře soubor určené cestou.|
|[CDocTemplate::RemoveDocument](#removedocument)|Dokument se odebere z šablony.|
|[CDocTemplate::SaveAllModified](#saveallmodified)|Uloží všechny dokumenty přidružené k této šablony, které byly změněny.|
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|Určuje, jaké prostředky pro kontejnery OLE při úpravách položky OLE v místě.|
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Zobrazí výchozí text v záhlaví okna dokumentu.|
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Nastavení mimo proces obslužné rutiny ve verzi preview.|
|[CDocTemplate::SetServerInfo](#setserverinfo)|Určuje prostředky a třídy při dokumentu na serveru je vložit nebo upravit místní.|

## <a name="remarks"></a>Poznámky

Obvykle vytvoříte jednu nebo více šablon dokumentů v provádění vaší aplikace `InitInstance` funkce. Šablona dokumentu definuje vztahy mezi tři typy tříd:

- Třídy dokumentu, které jsou odvozeny z `CDocument`.

- Třídy zobrazení, která zobrazuje data ze třídy dokumentu uvedené výše. Z této třídy lze odvodit `CView`, `CScrollView`, `CFormView`, nebo `CEditView`. (Můžete také použít `CEditView` přímo.)

- Třída okno rámce, který obsahuje zobrazení. Pro aplikaci rozhraní (SDI) jeden dokument, odvozovat z této třídy `CFrameWnd`. Pro aplikace (MDI interface) více dokumentů odvození z této třídy `CMDIChildWnd`. Pokud není nutné přizpůsobit chování okna rámce, můžete použít `CFrameWnd` nebo `CMDIChildWnd` přímo bez odvození vlastní třídy.

Vaše aplikace má jednu šablonu dokumentu pro každý typ dokumentu, který podporuje. Například pokud vaše aplikace podporuje tabulky a textové dokumenty, aplikace má dva objekty šablony dokumentu. Každá šablona dokumentu je zodpovědný za vytváření a Správa všech dokumentů jeho typu.

Šablona dokumentu ukládá ukazatele do `CRuntimeClass` objekty dokumentu, zobrazení a třídy oken s rámečkem. Tyto `CRuntimeClass` objekty jsou zadány při vytváření šablony dokumentu.

Šablona dokumentu obsahuje ID prostředku použitého typu dokumentu (například nabídky, ikona nebo prostředků tabulky akcelerátorů). Šablona dokumentu má také řetězce obsahující další informace o jeho typ dokumentu. Mezi ně patří název typu dokumentu (například "list") a přípona souboru (například ".xls"). Volitelně může obsahovat další řetězce používán uživatelské rozhraní aplikace, Správce souborů Windows a objekt propojení a podporu technologie OLE.

Pokud je vaše aplikace kontejneru OLE a/nebo serveru, definuje šablonu dokumentu také ID nabídky použité během místní aktivace. Pokud je vaše aplikace serveru OLE, definuje šablonu dokumentu Identifikátor panelu nástrojů a nabídky použité během místní aktivace. Zadejte tyto další zdroje informací OLE voláním `SetContainerInfo` a `SetServerInfo`.

Protože `CDocTemplate` je abstraktní třídu nelze použít přímo. Typická aplikace využívá jednu ze dvou `CDocTemplate`-odvozených tříd poskytovaných oborem knihovny Microsoft Foundation Class: `CSingleDocTemplate`, který implementuje SDI, a `CMultiDocTemplate`, který implementuje rozhraní MDI. Najdete v těchto tříd pro další informace o použití šablony dokumentů.

Pokud vaše aplikace vyžaduje paradigma uživatelského rozhraní, který je v podstatě totéž SDI nebo MDI, lze odvodit vlastní třídu z `CDocTemplate`.

Další informace o `CDocTemplate`, naleznete v tématu [šablony dokumentů a proces vytváření dokumentů/zobrazení](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="adddocument"></a>  CDocTemplate::AddDocument

Tuto funkci použijte k přidání dokumentu do šablony.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Ukazatel na dokument, který chcete přidat.

### <a name="remarks"></a>Poznámky

Odvozené třídy [cmultidoctemplate –](../../mfc/reference/cmultidoctemplate-class.md) a [csingledoctemplate –](../../mfc/reference/csingledoctemplate-class.md) přepsat tuto funkci. Pokud odvodit vlastní třídu šablony dokumentu z `CDocTemplate`, odvozené třídy musí přepsat tuto funkci.

##  <a name="cdoctemplate"></a>  CDocTemplate::CDocTemplate

Vytvoří `CDocTemplate` objektu.

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parametry

*nIDResource*<br/>
Určuje Identifikátor prostředku použitého typu dokumentu. To může zahrnovat nabídky, ikony, tabulky akcelerátorů a řetězcové prostředky.

Prostředek řetězce se skládá z až sedm dílčích řetězců oddělených znakem "\n" (znak '\n' je potřeba jako zástupný symbol pro Pokud neuvedete podřetězce; ale nejsou nezbytné koncové znaky '\n'); Tyto podřetězců popisují typ dokumentu. Informace o dílčích řetězců naleznete v tématu [GetDocString](#getdocstring). Tento prostředek řetězce najdete v souboru prostředků aplikace. Příklad:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Všimněte si, že řetězec začíná znakem '\n'; je to proto, že první dílčí řetězec se používá pro aplikace MDI a proto není zahrnutý. Můžete upravit tento řetězec pomocí editoru řetězce; celý řetězec se zobrazí jako jedna položka v editoru řetězce, nikoli sedm samostatné položky.

*pDocClass*<br/>
Odkazuje `CRuntimeClass` objekt třídy dokumentu. Tato třída je `CDocument`-odvozené třídy, které definujete k vyjádření vašich dokumentů.

*pFrameClass*<br/>
Odkazuje `CRuntimeClass` objekt okna rámce třídy. Tato třída může být `CFrameWnd`– odvozené třídy, nebo to může být `CFrameWnd` samotný Pokud chcete výchozí chování okna hlavního rámce.

*pViewClass*<br/>
Odkazuje `CRuntimeClass` objekt třídy zobrazení. Tato třída je `CView`-odvozené třídy, které definujete pro zobrazení dokumentů.

### <a name="remarks"></a>Poznámky

Tato členská funkce použít k vytvoření `CDocTemplate` objektu. Dynamicky přidělovat `CDocTemplate` objektu a předejte ji do [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) z `InitInstance` členské funkce třídy aplikace.

##  <a name="closealldocuments"></a>  CDocTemplate::CloseAllDocuments

Voláním této členské funkce, zavřete všechny otevřené dokumenty.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parametry

*bEndSession*<br/>
Nepoužívá se.

### <a name="remarks"></a>Poznámky

Tato členská funkce se obvykle používá jako součást příkazu soubor. Výchozí implementace této funkce se volá [CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents) členskou funkci odstranění dokumentu data a pak zavře oken s rámečkem pro všechna zobrazení připojené k dokumentu.

Tato funkce přepište, pokud chcete vyžadovat, aby uživatel provádět zpracování zvláštního vyčištění před zavřením dokumentu. Například pokud dokument představuje záznam v databázi, můžete přepsat této funkce se zavřít databázi.

##  <a name="createnewdocument"></a>  CDocTemplate::CreateNewDocument

Voláním této členské funkce, chcete-li vytvořit nový dokument typ přidružený k této šabloně dokumentu.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený dokument, nebo hodnota NULL, pokud dojde k chybě.

##  <a name="createnewframe"></a>  CDocTemplate::CreateNewFrame

Vytvoří nový objekt okna rámce obsahující dokumentů a zobrazení.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Dokument, ke kterému by měla odkazovat nový objekt okna rámce. Může mít hodnotu NULL.

*pOther*<br/>
Okno rámce, na kterém je založeno nový objekt okna rámce. Může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený rámec okna, nebo hodnota NULL, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

`CreateNewFrame` používá `CRuntimeClass` objekty předaný konstruktoru vytvořit nový objekt okna rámce s zobrazení a dokument připojené. Pokud *pDoc* parametr hodnotu NULL, rozhraní výstupů zprávy trasování.

*POther* parametr se používá k implementaci nového okna. Poskytuje okno rámce na základě které chcete modelovat nové okno rámce. Nové okno rámce je obvykle vytvořeny neviditelné. Voláním této funkce k vytvoření oken s rámečkem mimo implementaci standardní rozhraní nový soubor a soubor otevřít.

##  <a name="createoleframe"></a>  CDocTemplate::CreateOleFrame

Vytvoří okno rámce OLE.

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel do nadřazeného okna rámce.

*pDoc*<br/>
Ukazatel na dokument, ke kterému by měla odkazovat nové okno rámce OLE.

*bCreateView*<br/>
Určuje, jestli zobrazení je vytvořen společně s rámce.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno rámce v případě úspěchu; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Pokud *bCreateView* je nula, je vytvořen prázdný rámeček.

##  <a name="getdocstring"></a>  CDocTemplate::GetDocString

Načte řetězec přidružený k typu dokumentu.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na `CString` objekt, který bude obsahovat řetězec, pokud funkce vrátí.

*index*<br/>
Index podřetězce načítají z řetězce, který popisuje typ dokumentu. Tento parametr může mít jednu z následujících hodnot:

- `CDocTemplate::windowTitle` Název, který se zobrazí v záhlaví okna aplikace (například "Microsoft Excel"). K dispozici pouze v šabloně dokumentu pro aplikace SDI.

- `CDocTemplate::docName` Kořenové umístění pro výchozí název dokumentu (například "List"). Tento kořenový plus číslo se používá pro výchozí název nového dokumentu tohoto typu pokaždé, když uživatel zvolí nový příkaz v nabídce Soubor (například "List1" nebo "List2"). Pokud není zadán, "Bez názvu" je použito jako výchozí.

- `CDocTemplate::fileNewName` Název tohoto typu dokumentu. Pokud aplikace podporuje více než jeden typ souboru, zobrazí se tento řetězec v dialogovém okně Nový soubor (například "list"). Pokud není zadán, je nedostupný, pomocí příkazu soubor nový typ dokumentu.

- `CDocTemplate::filterName` Popis typu dokumentu a filtr zástupných znaků odpovídajících dokumentů tohoto typu. Tento řetězec se zobrazí v rozevíracím seznamu zobrazit soubory typu v dialogovém okně Otevřít soubor (například "listy (*.xls)"). Pokud není zadán, je nedostupný, pomocí příkazu Otevřít soubor typ dokumentu.

- `CDocTemplate::filterExt` Rozšíření pro dokumenty tohoto typu (například ".xls"). Pokud není zadán, je nedostupný, pomocí příkazu Otevřít soubor typ dokumentu.

- `CDocTemplate::regFileTypeId` Identifikátor pro typ dokument má být uložen v registrační databázi udržuje Windows. Tento řetězec je jen pro interní použití (například "ExcelWorksheet"). Pokud není zadán typ dokumentu nelze zaregistrovat pomocí souboru správce Windows.

- `CDocTemplate::regFileTypeName` Název typu dokumentu, který bude uložen v registrační databázi. Tento řetězec může být zobrazen v dialogových oknech aplikace s přístupem k registrační databázi (například "list aplikace Microsoft Excel").

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl nalezen zadaný podřetězec; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této funkce načtete konkrétní dílčí řetězec popisující typ dokumentu. Řetězec obsahující tyto podřetězce je uložen v šabloně a je odvozena z řetězce v souboru prostředků pro aplikaci. Rozhraní volá tuto funkci zobrazíte řetězců, které potřebuje pro uživatelské rozhraní vaší aplikace. Pokud zadáte příponu názvu souboru pro dokumenty vaší aplikace, rozhraní také tuto funkci volá při přidávání položky na registrační databázi Windows. To umožňuje otevírat dokumenty ze Správce souborů Windows.

Voláním této funkce jenom v případě, že jsou odvození vlastní třídy z `CDocTemplate`.

##  <a name="getfirstdocposition"></a>  CDocTemplate::GetFirstDocPosition

Získá pozici první dokument spojené s touto šablonou.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, který lze použít k iteraci v rámci seznamu dokumentů, které jsou spojené s touto šablonou dokumentu; nebo hodnota NULL, pokud je seznam prázdný.

### <a name="remarks"></a>Poznámky

Získá pozici první dokument v seznamu dokumentů, které jsou spojené s touto šablonou pomocí této funkce. Použijte hodnotu POZICI jako argument [CDocTemplate::GetNextDoc](#getnextdoc) k iteraci v rámci seznamu dokumentů přidružená k šabloně.

[Csingledoctemplate –](../../mfc/reference/csingledoctemplate-class.md) a [cmultidoctemplate –](../../mfc/reference/cmultidoctemplate-class.md) obě přepsat tato čistě virtuální funkce. Všechny třídy, které jsou odvozeny z `CDocTemplate` musí také přepsat tuto funkci.

##  <a name="getnextdoc"></a>  CDocTemplate::GetNextDoc

Načte seznam prvek identifikovaný *rpo*, pak nastaví *rpo* hodnotu pozice další položky v seznamu.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další dokument v seznamu dokumentů, které jsou spojené s touto šablonou.

### <a name="parameters"></a>Parametry

*rpo*<br/>
Odkaz na POZICI hodnotu vrácenou příkazem předchozí volání [GetFirstDocPosition](#getfirstdocposition) nebo `GetNextDoc`.

### <a name="remarks"></a>Poznámky

Pokud je načtený element poslední v seznamu, pak nová hodnota *rpo* nastaven na hodnotu NULL.

Můžete použít `GetNextDoc` v dopředné iteraci smyčky, Pokud zavedete počáteční pozici voláním [GetFirstDocPosition](#getfirstdocposition).

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

##  <a name="initialupdateframe"></a>  CDocTemplate::InitialUpdateFrame

Inicializuje okno rámce a volitelně stane viditelným.

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
Okno rámce, který potřebuje počáteční aktualizace.

*pDoc*<br/>
Dokument, ke kterému je přidružené rámce. Může mít hodnotu NULL.

*bMakeVisible*<br/>
Určuje, zda rámec by měla být viditelné a aktivní.

### <a name="remarks"></a>Poznámky

Volání `IntitialUpdateFrame` po vytvoření nový rámec s `CreateNewFrame`. Volání této funkce způsobí, že zobrazení v tomto okně rámce pro příjem jejich `OnInitialUpdate` volání. Také pokud nebyl k dispozici dříve aktivní zobrazení, primární zobrazení okna rámce se stane aktivní; primární zobrazení je zobrazení s ID AFX_IDW_PANE_FIRST podřízený. Nakonec okno rámce je nastavena jako viditelná Pokud *bMakeVisible* je nulová. Pokud *bMakeVisible* je nula, aktuálním zaměřením a stav viditelnosti okna rámce zůstane beze změny.

Není nutné volat tuto funkci při použití v rámci implementace nový soubor a soubor otevřít.

##  <a name="loadtemplate"></a>  CDocTemplate::LoadTemplate

Načte prostředky danou `CDocTemplate` nebo odvozené třídy.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce se volá se rozhraním pro načtení prostředků pro danou `CDocTemplate` nebo odvozené třídy. Obvykle je volána během konstrukce, s výjimkou případů, když šablona je vytvářen globálně. V takovém případě volání `LoadTemplate` je odložena až do [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) je volána.

##  <a name="matchdoctype"></a>  CDocTemplate::MatchDocType

Určuje, do jaké míry důvěry mezi typem dokumentu a tato šablona se shodují.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Cesta k souboru, jehož typ má být stanovena.

*rpDocMatch*<br/>
Ukazatel na dokument, který je přiřazen odpovídající dokumentu, pokud soubor určený *lpszPathName* je již otevřen.

### <a name="return-value"></a>Návratová hodnota

Hodnota z **spolehlivosti** výčtu, která je definovaná následujícím způsobem:

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

Tuto funkci použijte k určení typu dokumentu šablony má použít pro otevření souboru. Pokud vaše aplikace podporuje více typů souborů, například můžete použít tuto funkci k určení, které šablony dokumentu k dispozici je vhodný pro daný soubor voláním `MatchDocType` ke každé šabloně v důsledku a výběrem šablony podle Vrácená hodnota spolehlivosti.

Pokud soubor určený *lpszPathName* je již otevřen, tato funkce vrací `CDocTemplate::yesAlreadyOpen` a zkopíruje soubor do `CDocument` objektu do objektu na *rpDocMatch*.

Pokud soubor není otevřen, ale rozšíření v *lpszPathName* odpovídá rozšíření určená `CDocTemplate::filterExt`, tato funkce vrací `CDocTemplate::yesAttemptNative` a nastaví *rpDocMatch* na hodnotu NULL. Další informace o `CDocTemplate::filterExt`, naleznete v tématu [CDocTemplate::GetDocString](#getdocstring).

Pokud žádný případ je true, funkce vrátí `CDocTemplate::yesAttemptForeign`.

Výchozí implementace nevrací `CDocTemplate::maybeAttemptForeign` nebo `CDocTemplate::maybeAttemptNative`. Tuto funkci implementovat logiku porovnávání typu vhodné pro vaši aplikaci, případně pomocí těchto dvou hodnot z přepsat **spolehlivosti** výčtu.

##  <a name="opendocumentfile"></a>  CDocTemplate::OpenDocumentFile

Otevře se soubor určený parametrem cestu.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
[in] Ukazatel na cestu k souboru, který obsahuje dokument otevřít.

*bAddToMRU*<br/>
[in] Hodnota TRUE označuje, že dokument je jednou z nejnovější soubory; Hodnota FALSE označuje, že dokument není jeden z posledních souborů.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument, soubor je pojmenován podle *lpszPathName*; Hodnota NULL, pokud není úspěšné.

### <a name="remarks"></a>Poznámky

Otevře soubor, jehož cesta je určena *lpszPathName*. Pokud *lpszPathName* má hodnotu NULL, je vytvořen nový soubor, který obsahuje dokument typu spojené s touto šablonou.

##  <a name="removedocument"></a>  CDocTemplate::RemoveDocument

Odebere dokumentu, na které odkazuje *pDoc* ze seznamu dokumentů, které jsou spojené s touto šablonou.

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Ukazatel na dokument k odebrání.

### <a name="remarks"></a>Poznámky

Odvozené třídy `CMultiDocTemplate` a `CSingleDocTemplate` přepsat tuto funkci. Pokud odvodit vlastní třídu šablony dokumentu z `CDocTemplate`, odvozené třídy musí přepsat tuto funkci.

##  <a name="saveallmodified"></a>  CDocTemplate::SaveAllModified

Uloží všechny dokumenty, které byly změněny.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Návratová hodnota

Nenulový v případě úspěchu; jinak 0.

##  <a name="setcontainerinfo"></a>  CDocTemplate::SetContainerInfo

Určuje, jaké prostředky pro kontejnery OLE při úpravách položky OLE v místě.

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>Parametry

*nIDOleInPlaceContainer*<br/>
ID prostředku použitého při aktivaci vloženého objektu.

### <a name="remarks"></a>Poznámky

Voláním této funkce nastavit prostředky, které se dá použít při místní aktivaci je objekt OLE. Tyto prostředky mohou být nabídky a tabulek akcelerátorů. Tato funkce je obvykle volána [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) funkci vaší aplikace.

Nabídky spojené s *nIDOleInPlaceContainer* obsahuje oddělovače, které umožňují nabídku aktivované místní položky ke sloučení s nabídkou aplikace typu kontejner. Další informace o slučování nabídek serveru a kontejneru, najdete v článku [nabídky a prostředky (OLE)](../../mfc/menus-and-resources-ole.md).

##  <a name="setdefaulttitle"></a>  CDocTemplate::SetDefaultTitle

Voláním této funkce načíst výchozí název dokumentu a zobrazit je v záhlaví okna dokumentu.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>Parametry

*pDocument*<br/>
Ukazatel na dokument, jejíž název má být nastavena.

### <a name="remarks"></a>Poznámky

Informace o výchozí název, najdete v popisu `CDocTemplate::docName` v [CDocTemplate::GetDocString](#getdocstring).

##  <a name="setserverinfo"></a>  CDocTemplate::SetServerInfo

Určuje prostředky a třídy při dokumentu na serveru je vložit nebo upravit místní.

```
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>Parametry

*nIDOleEmbedding*<br/>
ID prostředku použitého při otevření vložený objekt v samostatném okně.

*nIDOleInPlaceServer*<br/>
ID prostředků použít, pokud je vložený objekt zrovna místně aktivuje.

*pOleFrameClass*<br/>
Ukazatel [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura obsahující informace o třídě pro objekt okna rámce vytvoří, když dojde k aktivace na místě.

*pOleViewClass*<br/>
Ukazatel `CRuntimeClass` struktura obsahující informace o třídě pro zobrazení objekt vytvořený při místní aktivaci.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce pro identifikaci prostředků, které aplikace se použije, když uživatel požádá o aktivaci vloženého objektu. Tyto prostředky se skládají z nabídky a tabulek akcelerátorů. Tato funkce je obvykle volána `InitInstance` vaší aplikace.

Nabídky spojené s *nIDOleInPlaceServer* obsahuje oddělovače, které umožňují nabídce server ke sloučení s nabídkou kontejneru. Další informace o slučování nabídek serveru a kontejneru, najdete v článku [nabídky a prostředky (OLE)](../../mfc/menus-and-resources-ole.md).

##  <a name="createpreviewframe"></a>  CDocTemplate::CreatePreviewFrame

Vytvoří podřízený rámec pro náhled ve formátu RTF.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel do nadřazeného okna (obvykle poskytnutého shellem).

*pDoc*<br/>
Ukazatel na objekt dokumentu, jejíž obsah bude zobrazen.

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel `CFrameWnd` objektu, nebo hodnota NULL, pokud se vytváření nezdaří.

### <a name="remarks"></a>Poznámky

##  <a name="setpreviewinfo"></a>  CDocTemplate::SetPreviewInfo

Nastaví na více instancí procesu ve verzi preview obslužné rutiny.

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>Parametry

*nIDPreviewFrame*<br/>
Určuje Identifikátor prostředku ve verzi preview rámce.

*pPreviewFrameClass*<br/>
Určuje ukazatel na strukturu runtime třídy informace rámce ve verzi preview.

*pPreviewViewClass*<br/>
Určuje ukazatel na strukturu runtime třídy informace o zobrazení ve verzi preview.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CSingleDocTemplate – třída](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CMultiDocTemplate – třída](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[CScrollView – třída](../../mfc/reference/cscrollview-class.md)<br/>
[CEditView – třída](../../mfc/reference/ceditview-class.md)<br/>
[CFormView – třída](../../mfc/reference/cformview-class.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)<br/>
[CMDIChildWnd – třída](../../mfc/reference/cmdichildwnd-class.md)
