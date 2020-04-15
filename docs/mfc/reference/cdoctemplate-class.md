---
title: Třída CDocTemplate
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
ms.openlocfilehash: 3376b8febe8ae4586ce649f3f83386875acb678f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375509"
---
# <a name="cdoctemplate-class"></a>Třída CDocTemplate

Abstraktní základní třída, která definuje základní funkce pro šablony dokumentů.

## <a name="syntax"></a>Syntaxe

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDocTemplate::CDocTemplate](#cdoctemplate)|Vytvoří `CDocTemplate` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDocTemplate::AddDocument](#adddocument)|Přidá dokument do šablony.|
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|Zavře všechny dokumenty přidružené k této šabloně.|
|[CDocTemplate::CreateNewDocument](#createnewdocument)|Vytvoří nový dokument.|
|[CDocTemplate::CreateNewFrame](#createnewframe)|Vytvoří nové okno rámce obsahující dokument a zobrazení.|
|[CDocTemplate::CreateOleFrame](#createoleframe)|Vytvoří okno rámce s podporou OLE.|
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Vytvoří podřízený rámeček používaný pro rozšířený náhled.|
|[CDocTemplate::GetDocString](#getdocstring)|Načte řetězec přidružený k typu dokumentu.|
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Načte pozici prvního dokumentu přidruženého k této šabloně.|
|[CDocTemplate::GetNextDoc](#getnextdoc)|Načte dokument a pozici dalšího.|
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Inicializuje okno rámce a volitelně jej zviditelní.|
|[CDocTemplate::Načíst šablonu](#loadtemplate)|Načte prostředky pro `CDocTemplate` danou nebo odvozenou třídu.|
|[CDocTemplate::MatchDocType](#matchdoctype)|Určuje míru spolehlivosti v shodě mezi typem dokumentu a touto šablonou.|
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|Otevře soubor určený názvem cesty.|
|[CDocTemplate::RemoveDocument](#removedocument)|Odebere dokument ze šablony.|
|[CDocTemplate::UložitAllModified](#saveallmodified)|Uloží všechny dokumenty přidružené k této šabloně, které byly změněny.|
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|Určuje prostředky pro kontejnery OLE při úpravách položky OLE na místě.|
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Zobrazí výchozí název v záhlaví okna dokumentu.|
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Nastavení mimo obslužnou rutinu náhledu procesu.|
|[CDocTemplate::SetServerInfo](#setserverinfo)|Určuje prostředky a třídy, když je dokument serveru vložen nebo upraven na místě.|

## <a name="remarks"></a>Poznámky

Obvykle vytvořit jednu nebo více šablon dokumentů v `InitInstance` implementaci funkce aplikace. Šablona dokumentu definuje vztahy mezi třemi typy tříd:

- Třída dokumentu, která je `CDocument`odvozena z aplikace .

- Třída zobrazení, která zobrazuje data z výše uvedené třídy dokumentu. Tuto třídu můžete `CView` `CScrollView`odvodit z , , `CFormView`nebo `CEditView`. (Můžete také `CEditView` použít přímo.)

- Třída okna rámce, která obsahuje zobrazení. Pro aplikaci rozhraní jednoho dokumentu (SDI) `CFrameWnd`odvodit tuto třídu z . Pro více dokumentů rozhraní (MDI) aplikace odvodit tuto třídu z `CMDIChildWnd`. Pokud nepotřebujete přizpůsobit chování okna rámce, můžete použít `CFrameWnd` nebo `CMDIChildWnd` přímo bez odvození vlastní třídy.

Aplikace má jednu šablonu dokumentu pro každý typ dokumentu, který podporuje. Pokud například aplikace podporuje tabulky i textové dokumenty, má aplikace dva objekty šablony dokumentu. Každá šablona dokumentu je zodpovědná za vytváření a správu všech dokumentů svého typu.

Šablona dokumentu ukládá ukazatele `CRuntimeClass` na objekty pro třídy okna dokumentu, zobrazení a rámečku. Tyto `CRuntimeClass` objekty jsou určeny při vytváření šablony dokumentu.

Šablona dokumentu obsahuje ID prostředků použitých s typem dokumentu (například menu, ikona nebo zdroje tabulky akcelerátoru). Šablona dokumentu obsahuje také řetězce obsahující další informace o typu dokumentu. Patří mezi ně název typu dokumentu (například "List") a příponu souboru (například ".xls"). Volitelně může obsahovat další řetězce používané uživatelským rozhraním aplikace, správcem souborů systému Windows a podporou OLE (Object Linking and Embedding).

Pokud je vaše aplikace kontejner OLE nebo server, šablona dokumentu také definuje ID nabídky používané během aktivace na místě. Pokud je vaše aplikace serverEM OLE, šablona dokumentu definuje ID panelu nástrojů a nabídky používané při aktivaci na místě. Tyto další prostředky OLE `SetContainerInfo` zadáte `SetServerInfo`voláním a .

Protože `CDocTemplate` je abstraktní třída, nelze použít třídu přímo. Typická aplikace používá jednu ze dvou `CDocTemplate`odvozených tříd poskytovaných `CSingleDocTemplate`knihovnou tříd Microsoft Foundation: , která implementuje Rozhraní SDI a `CMultiDocTemplate`, která implementuje rozhraní MDI. Další informace o používání šablon dokumentů najdete v těchto třídách.

Pokud vaše aplikace vyžaduje paradigma uživatelského rozhraní, které se zásadně liší od SDI nebo MDI, můžete odvodit vlastní třídu z `CDocTemplate`aplikace .

Další informace `CDocTemplate`naleznete v [tématu Document Templates and the Document/View Creation Process](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cdoctemplateadddocument"></a><a name="adddocument"></a>CDocTemplate::AddDocument

Tato funkce slouží k přidání dokumentu do šablony.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Ukazatel na dokument, který má být přidán.

### <a name="remarks"></a>Poznámky

Odvozené třídy [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) a [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) tuto funkci přepíší. Pokud odvodíte vlastní `CDocTemplate`třídu šablony dokumentu z aplikace , musí odvozená třída tuto funkci přepsat.

## <a name="cdoctemplatecdoctemplate"></a><a name="cdoctemplate"></a>CDocTemplate::CDocTemplate

Vytvoří `CDocTemplate` objekt.

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parametry

*nIDZdroj*<br/>
Určuje ID prostředků použitých s typem dokumentu. To může zahrnovat menu, ikonu, tabulku akcelerátoru a prostředky řetězce.

Prostředek řetězce se skládá až ze sedmi podřetězců oddělených znakem \n (znak \n je potřebný jako zástupný symbol, pokud není zahrnut podřetězec; koncové znaky \n však nejsou nutné); tyto podřetězce popisují typ dokumentu. Informace o podřetězec, naleznete v tématu [GetDocString](#getdocstring). Tento řetězec prostředku se nachází v souboru prostředků aplikace. Příklad:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Všimněte si, že řetězec začíná znakem \n; Důvodem je, že první podřetězec se nepoužívá pro aplikace MDI a proto není zahrnuta. Tento řetězec můžete upravit pomocí editoru řetězců; celý řetězec se zobrazí jako jedna položka v editoru řetězců, nikoli jako sedm samostatných položek.

*třída pDocClass*<br/>
Odkazuje na `CRuntimeClass` objekt třídy dokumentu. Tato třída `CDocument`je odvozená třída, kterou definujete, aby reprezentovala vaše dokumenty.

*pFrameClass*<br/>
Odkazuje na `CRuntimeClass` objekt třídy okna rámce. Tato třída může `CFrameWnd`být odvozené třídy, `CFrameWnd` nebo může být sama, pokud chcete výchozí chování pro okno hlavního rámce.

*pViewClass*<br/>
Odkazuje na `CRuntimeClass` objekt třídy zobrazení. Tato třída `CView`je odvozená třída, kterou definujete pro zobrazení dokumentů.

### <a name="remarks"></a>Poznámky

Tato členská funkce `CDocTemplate` slouží k vytvoření objektu. Dynamicky přidělit `CDocTemplate` objekt a předat jej [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) z `InitInstance` členské funkce třídy aplikace.

## <a name="cdoctemplateclosealldocuments"></a><a name="closealldocuments"></a>CDocTemplate::CloseAllDocuments

Volánítéto členské funkce zavřete všechny otevřené dokumenty.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parametry

*bEndSession*<br/>
Nepoužívá se.

### <a name="remarks"></a>Poznámky

Tato členská funkce se obvykle používá jako součást příkazu Ukončení souboru. Výchozí implementace této funkce volá členskou funkci [CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents) k odstranění dat dokumentu a zavře okna rámců pro všechna zobrazení připojená k dokumentu.

Přepsat tuto funkci, pokud chcete požadovat, aby uživatel provést speciální vyčištění zpracování před zavření dokumentu. Pokud například dokument představuje záznam v databázi, můžete tuto funkci přepsat a databázi zavřít.

## <a name="cdoctemplatecreatenewdocument"></a><a name="createnewdocument"></a>CDocTemplate::CreateNewDocument

Voláním této členské funkce vytvořte nový dokument typu přidruženého k této šabloně dokumentu.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený dokument nebo NULL, pokud dojde k chybě.

## <a name="cdoctemplatecreatenewframe"></a><a name="createnewframe"></a>CDocTemplate::CreateNewFrame

Vytvoří nové okno rámce obsahující dokument a zobrazení.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Dokument, na který by měl odkazovat nové okno rámce. Může být NULL.

*pOstatní*<br/>
Okno rámce, na kterém má být založeno nové okno rámce. Může být NULL.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořené okno rámce nebo NULL, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

`CreateNewFrame`používá `CRuntimeClass` objekty předané konstruktoru k vytvoření nového okna rámce s připojeným pohledem a dokumentem. Pokud je parametr *pDoc* NULL, rozhraní vyvede zprávu TRACE.

Parametr *pOther* se používá k implementaci příkazu Window New. Poskytuje okno rámce, na kterém chcete modelovat nové okno rámce. Nové okno rámce je obvykle vytvořeno neviditelné. Volání této funkce vytvořit okna rámce mimo standardní rozhraní implementace File New a File Open.

## <a name="cdoctemplatecreateoleframe"></a><a name="createoleframe"></a>CDocTemplate::CreateOleFrame

Vytvoří okno rámce OLE.

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na nadřazené okno rámce.

*pDoc*<br/>
Ukazatel na dokument, na který by měl odkazovat nové okno rámce OLE.

*bCreateView*<br/>
Určuje, zda bude vytvořeno zobrazení spolu s rámcem.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno rámce v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud *bCreateView* je nula, je vytvořen prázdný snímek.

## <a name="cdoctemplategetdocstring"></a><a name="getdocstring"></a>CDocTemplate::GetDocString

Načte řetězec přidružený k typu dokumentu.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na `CString` objekt, který bude obsahovat řetězec, když se vrátí funkce.

*Index*<br/>
Index podřetězce načteného z řetězce, který popisuje typ dokumentu. Tento parametr může mít jednu z následujících hodnot:

- `CDocTemplate::windowTitle`Název, který se zobrazí v záhlaví okna aplikace (například "Microsoft Excel"). Zobrazí se pouze v šabloně dokumentu pro aplikace SDI.

- `CDocTemplate::docName`Kořen pro výchozí název dokumentu (například "List"). Tento kořen, plus číslo, se používá pro výchozí název nového dokumentu tohoto typu vždy, když uživatel vybere příkaz Nový z nabídky Soubor (například "List1" nebo "List2"). Pokud není zadán, "Bez názvu" se používá jako výchozí.

- `CDocTemplate::fileNewName`Název tohoto typu dokumentu. Pokud aplikace podporuje více než jeden typ dokumentu, zobrazí se tento řetězec v dialogovém okně Nový soubor (například "List"). Pokud není zadán, typ dokumentu je nepřístupný pomocí příkazu Nový soubor.

- `CDocTemplate::filterName`Popis typu dokladu a filtr se zástupnými znaky odpovídající dokumentům tohoto typu. Tento řetězec se zobrazí v rozevíracím seznamu Seznam souborů typu v dialogovém okně Otevřít soubor (například "Listy (*.xls)"). Pokud není zadán, typ dokumentu je nepřístupný pomocí příkazu Otevřít soubor.

- `CDocTemplate::filterExt`Rozšíření pro dokumenty tohoto typu (například ".xls"). Pokud není zadán, typ dokumentu je nepřístupný pomocí příkazu Otevřít soubor.

- `CDocTemplate::regFileTypeId`Identifikátor typu dokumentu, který má být uložen v registrační databázi spravované systémem Windows. Tento řetězec je určen pouze pro interní použití (například "ExcelWorksheet"). Pokud není zadán, nelze typ dokumentu zaregistrovat ve Správci souborů systému Windows.

- `CDocTemplate::regFileTypeName`Název typu dokumentu, který má být uložen v registrační databázi. Tento řetězec může být zobrazen v dialogových oknech aplikací, které přistupují k registrační databázi (například "List aplikace Microsoft Excel").

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl zadán podřetězec; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této funkce načíst konkrétní podřetězec popisující typ dokumentu. Řetězec obsahující tyto podřetězce je uložen v šabloně dokumentu a je odvozen z řetězce v souboru prostředků pro aplikaci. Rozhraní Framework volá tuto funkci získat řetězce, které potřebuje pro uživatelské rozhraní aplikace. Pokud jste zadali příponu názvu souboru pro dokumenty aplikace, rozhraní také volá tuto funkci při přidávání položky do registrační databáze systému Windows; To umožňuje otevřít dokumenty ze Správce souborů systému Windows.

Tuto funkci zavolejte pouze v případě, že `CDocTemplate`odvodíte vlastní třídu z aplikace .

## <a name="cdoctemplategetfirstdocposition"></a><a name="getfirstdocposition"></a>CDocTemplate::GetFirstDocPosition

Načte pozici prvního dokumentu přidruženého k této šabloně.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít k iterátu prostřednictvím seznamu dokumentů přidružených k této šabloně dokumentu; nebo NULL, pokud je seznam prázdný.

### <a name="remarks"></a>Poznámky

Pomocí této funkce můžete získat pozici prvního dokumentu v seznamu dokumentů přidružených k této šabloně. Použijte hodnotu POSITION jako argument [pro CDocTemplate::GetNextDoc](#getnextdoc) k itetovat seznam dokumentů přidružených k šabloně.

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) a [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) přepíší tuto čistou virtuální funkci. Všechny třídy, `CDocTemplate` které odvozujete, musí také přepsat tuto funkci.

## <a name="cdoctemplategetnextdoc"></a><a name="getnextdoc"></a>CDocTemplate::GetNextDoc

Načte prvek seznamu identifikovaný *hodnotami rPos*a potom nastaví *hodnoty RPona* hodnotu POZICE další položky v seznamu.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další dokument v seznamu dokumentů přidružených k této šabloně.

### <a name="parameters"></a>Parametry

*rPos*<br/>
Odkaz na hodnotu POSITION vrácenou předchozím voláním `GetNextDoc` [GetFirstDocPosition](#getfirstdocposition) nebo .

### <a name="remarks"></a>Poznámky

Pokud načtený prvek je poslední v seznamu, pak je nová hodnota *rPos* nastavena na hodnotu NULL.

Můžete použít `GetNextDoc` ve smyčce dopředu iterace, pokud navážete počáteční pozici s voláním [GetFirstDocPosition](#getfirstdocposition).

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

## <a name="cdoctemplateinitialupdateframe"></a><a name="initialupdateframe"></a>CDocTemplate::InitialUpdateFrame

Inicializuje okno rámce a volitelně jej zviditelní.

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>Parametry

*pRám*<br/>
Okno rámce, které potřebuje počáteční aktualizaci.

*pDoc*<br/>
Dokument, ke kterému je rámeček přidružen. Může být NULL.

*bMakeVisible*<br/>
Označuje, zda má být rámeček viditelný a aktivní.

### <a name="remarks"></a>Poznámky

Volat `IntitialUpdateFrame` po vytvoření nového rámce s . `CreateNewFrame` Volání této funkce způsobí, že zobrazení `OnInitialUpdate` v tomto okně rámce přijímat jejich volání. Také pokud dříve nebyl aktivní pohled, primární pohled okna rámce je aktivní; primární zobrazení je zobrazení s podřízeným ID AFX_IDW_PANE_FIRST. Nakonec okno rámce je viditelná, pokud *bMakeVisible* je nenulová. Pokud *bMakeVisible* je nula, aktuální fokus a viditelný stav okna rámce zůstane beze změny.

Není nutné volat tuto funkci při použití implementace rozhraní File New a File Open.

## <a name="cdoctemplateloadtemplate"></a><a name="loadtemplate"></a>CDocTemplate::Načíst šablonu

Načte prostředky pro `CDocTemplate` danou nebo odvozenou třídu.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rámci načíst prostředky pro danou `CDocTemplate` nebo odvozenou třídu. Obvykle se nazývá během výstavby, s výjimkou případů, kdy je šablona vytvářena globálně. V takovém případě `LoadTemplate` je volání zpožděno, dokud [cWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) je volána.

## <a name="cdoctemplatematchdoctype"></a><a name="matchdoctype"></a>CDocTemplate::MatchDocType

Určuje míru spolehlivosti v shodě mezi typem dokumentu a touto šablonou.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Název cesty souboru, jehož typ má být určen.

*rpDocMatch*<br/>
Ukazatel na dokument, kterému je přiřazen odpovídající dokument, pokud je soubor určený *lpszPathName* již otevřen.

### <a name="return-value"></a>Návratová hodnota

Hodnota z výčtu **spolehlivosti,** která je definována takto:

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

Tato funkce slouží k určení typu šablony dokumentu, která se má použít pro otevření souboru. Pokud vaše aplikace podporuje více typů souborů, můžete například tuto funkci použít k určení, která `MatchDocType` z dostupných šablon dokumentů je vhodná pro daný soubor, voláním pro každou šablonu a výběrem šablony podle vrácené hodnoty spolehlivosti.

Pokud je soubor určený *lpszPathName* již otevřen, tato funkce `CDocTemplate::yesAlreadyOpen` `CDocument` vrátí a zkopíruje objekt souboru do objektu na *rpDocMatch*.

Pokud soubor není otevřen, ale přípona v *lpszPathName* odpovídá příponu určené , `CDocTemplate::filterExt`tato funkce vrátí `CDocTemplate::yesAttemptNative` a nastaví *rpDocMatch* na NULL. Další informace `CDocTemplate::filterExt`naleznete v tématu [CDocTemplate::GetDocString](#getdocstring).

Pokud ani jeden případ není `CDocTemplate::yesAttemptForeign`true, funkce vrátí .

Výchozí implementace nevrátí `CDocTemplate::maybeAttemptForeign` nebo `CDocTemplate::maybeAttemptNative`. Přepsat tuto funkci implementovat logiku přiřazování typů vhodné pro vaši aplikaci, případně pomocí těchto dvou hodnot z **výčtu spolehlivosti.**

## <a name="cdoctemplateopendocumentfile"></a><a name="opendocumentfile"></a>CDocTemplate::OpenDocumentFile

Otevře soubor určený cestou.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
[v] Ukazatel na cestu souboru, který obsahuje dokument, který má být otevřen.

*bAddToMRU*<br/>
[v] PRAVDA označuje, že dokument je jedním z nejnovějších souborů; NEPRAVDA označuje, že dokument není jedním z nejnovějších souborů.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument, jehož soubor je pojmenován *lpszPathName*; Null v případě neúspěchu.

### <a name="remarks"></a>Poznámky

Otevře soubor, jehož cesta je určena *lpszPathName*. Pokud *je lpszPathName* NULL, vytvoří se nový soubor obsahující dokument typu přidruženého k této šabloně.

## <a name="cdoctemplateremovedocument"></a><a name="removedocument"></a>CDocTemplate::RemoveDocument

Odebere dokument, na který *pDoc* ukazuje, ze seznamu dokumentů přidružených k této šabloně.

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Ukazatel na dokument, který má být odebrán.

### <a name="remarks"></a>Poznámky

Odvozené `CMultiDocTemplate` třídy `CSingleDocTemplate` a přepsat tuto funkci. Pokud odvodíte vlastní `CDocTemplate`třídu šablony dokumentu z aplikace , musí odvozená třída tuto funkci přepsat.

## <a name="cdoctemplatesaveallmodified"></a><a name="saveallmodified"></a>CDocTemplate::UložitAllModified

Uloží všechny dokumenty, které byly změněny.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

## <a name="cdoctemplatesetcontainerinfo"></a><a name="setcontainerinfo"></a>CDocTemplate::SetContainerInfo

Určuje prostředky pro kontejnery OLE při úpravách položky OLE na místě.

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>Parametry

*nIDOleInPlaceContainer*<br/>
ID prostředků použitých při aktivaci vloženého objektu.

### <a name="remarks"></a>Poznámky

Volání této funkce nastavit prostředky, které mají být použity při aktivaci objektu OLE na místě. Tyto prostředky mohou zahrnovat nabídky a tabulky akcelerátorů. Tato funkce je obvykle volána ve funkci [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) vaší aplikace.

Nabídka přidružená k *nIDOleInPlaceContainer* obsahuje oddělovače, které umožňují sloučení nabídky aktivované položky na místě s nabídkou aplikace kontejneru. Další informace o slučování nabídek serveru a kontejnerů naleznete v článku [Nabídky a prostředky (OLE).](../../mfc/menus-and-resources-ole.md)

## <a name="cdoctemplatesetdefaulttitle"></a><a name="setdefaulttitle"></a>CDocTemplate::SetDefaultTitle

Voláním této funkce načtěte výchozí název dokumentu a zobrazte jej v záhlaví dokumentu.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>Parametry

*pDokument*<br/>
Ukazatel na dokument, jehož název má být nastaven.

### <a name="remarks"></a>Poznámky

Informace o výchozím názvu naleznete `CDocTemplate::docName` v popisu v [cdoctemplate::GetDocString](#getdocstring).

## <a name="cdoctemplatesetserverinfo"></a><a name="setserverinfo"></a>CDocTemplate::SetServerInfo

Určuje prostředky a třídy, když je dokument serveru vložen nebo upraven na místě.

```
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>Parametry

*nIDOleEmbedding*<br/>
ID prostředků použitých při otevření vloženého objektu v samostatném okně.

*nIDOleInPlaceServer*<br/>
ID prostředků používaných při aktivaci vloženého objektu na místě.

*pOleFrameClass*<br/>
Ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obsahující informace o třídě pro objekt okna rámce vytvořený při aktivaci na místě.

*pOleViewClass*<br/>
Ukazatel na `CRuntimeClass` strukturu obsahující informace o třídě pro objekt zobrazení vytvořený při aktivaci na místě.

### <a name="remarks"></a>Poznámky

Volání této členské funkce k identifikaci prostředků, které budou použity serverovou aplikací, když uživatel požádá o aktivaci vloženého objektu. Tyto prostředky se skládají z nabídek a tabulek akcelerátorů. Tato funkce je obvykle `InitInstance` volána v aplikaci.

Nabídka přidružená k *nIDOleInPlaceServer* obsahuje oddělovače, které umožňují slučování nabídky serveru s nabídkou kontejneru. Další informace o slučování nabídek serveru a kontejnerů naleznete v článku [Nabídky a prostředky (OLE).](../../mfc/menus-and-resources-ole.md)

## <a name="cdoctemplatecreatepreviewframe"></a><a name="createpreviewframe"></a>CDocTemplate::CreatePreviewFrame

Vytvoří podřízený rámeček používaný pro rozšířený náhled.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na nadřazené okno (obvykle poskytované prostředím).

*pDoc*<br/>
Ukazatel na objekt dokumentu, jehož obsah bude zobrazen v náhledu.

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na `CFrameWnd` objekt nebo NULL, pokud se vytvoření nezdaří.

### <a name="remarks"></a>Poznámky

## <a name="cdoctemplatesetpreviewinfo"></a><a name="setpreviewinfo"></a>CDocTemplate::SetPreviewInfo

Nastaví obslužnou rutinu náhledu mimo proces.

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>Parametry

*nIDPreviewFrame*<br/>
Určuje ID prostředku rámce náhledu.

*pNáhledTřída frameclass*<br/>
Určuje ukazatel na informační strukturu třídy runtime rámce náhledu.

*pNáhledZobrazittřída*<br/>
Určuje ukazatel na informační strukturu třídy runtime zobrazení náhledu.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)<br/>
[Třída CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)<br/>
[Třída CView](../../mfc/reference/cview-class.md)<br/>
[CScrollView – třída](../../mfc/reference/cscrollview-class.md)<br/>
[Třída CEditView](../../mfc/reference/ceditview-class.md)<br/>
[CFormView – třída](../../mfc/reference/cformview-class.md)<br/>
[Třída CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Třída CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)
