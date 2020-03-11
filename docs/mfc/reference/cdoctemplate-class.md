---
title: CDocTemplate – – třída
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
ms.openlocfilehash: 3b2d84af9be8e5c606cde8794b51e12207dcdec9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855471"
---
# <a name="cdoctemplate-class"></a>CDocTemplate – – třída

Abstraktní základní třída, která definuje základní funkce pro šablony dokumentů.

## <a name="syntax"></a>Syntaxe

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDocTemplate –:: CDocTemplate –](#cdoctemplate)|Vytvoří objekt `CDocTemplate`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDocTemplate –:: AddDocument](#adddocument)|Přidá dokument do šablony.|
|[CDocTemplate –:: CloseAllDocuments](#closealldocuments)|Zavře všechny dokumenty přidružené k této šabloně.|
|[CDocTemplate –:: CreateNewDocument](#createnewdocument)|Vytvoří nový dokument.|
|[CDocTemplate –:: CreateNewFrame](#createnewframe)|Vytvoří nové okno rámce obsahující dokument a zobrazení.|
|[CDocTemplate –:: CreateOleFrame](#createoleframe)|Vytvoří okno rámce s povoleným OLE.|
|[CDocTemplate –:: CreatePreviewFrame](#createpreviewframe)|Vytvoří podřízený rámec používaný pro bohatou verzi Preview.|
|[CDocTemplate –:: GetDocString](#getdocstring)|Načte řetězec přidružený k typu dokumentu.|
|[CDocTemplate –:: GetFirstDocPosition](#getfirstdocposition)|Načte pozici prvního dokumentu přidruženého k této šabloně.|
|[CDocTemplate –:: GetNextDoc](#getnextdoc)|Načte dokument a pozici dalšího.|
|[CDocTemplate –:: InitialUpdateFrame](#initialupdateframe)|Inicializuje okno rámce a volitelně ho zviditelní.|
|[CDocTemplate –:: LoadTemplate](#loadtemplate)|Načte prostředky pro daný `CDocTemplate` nebo odvozenou třídu.|
|[CDocTemplate –:: MatchDocType](#matchdoctype)|Určuje stupeň spolehlivosti ve shodě mezi typem dokumentu a touto šablonou.|
|[CDocTemplate –:: OpenDocumentFile](#opendocumentfile)|Otevře soubor určený cestou.|
|[CDocTemplate –:: RemoveDocument](#removedocument)|Odebere dokument ze šablony.|
|[CDocTemplate –:: SaveAllModified](#saveallmodified)|Uloží všechny dokumenty přidružené k této šabloně, které byly změněny.|
|[CDocTemplate –:: SetContainerInfo](#setcontainerinfo)|Určuje prostředky pro kontejnery OLE při úpravách místní položky OLE.|
|[CDocTemplate –:: SetDefaultTitle](#setdefaulttitle)|Zobrazí výchozí název v záhlaví okna dokumentu.|
|[CDocTemplate –:: SetPreviewInfo](#setpreviewinfo)|Instalační program mimo obslužné rutiny procesu Preview.|
|[CDocTemplate –:: SetServerInfo](#setserverinfo)|Určuje prostředky a třídy, pokud je dokument serveru vložený nebo upravován místně.|

## <a name="remarks"></a>Poznámky

Obvykle vytvoříte jednu nebo více šablon dokumentů v implementaci funkce `InitInstance` vaší aplikace. Šablona dokumentu definuje vztahy mezi třemi typy tříd:

- Třída dokumentu, kterou lze odvodit z `CDocument`.

- Třída zobrazení, která zobrazuje data z třídy dokumentu uvedené výše. Tuto třídu můžete odvodit z `CView`, `CScrollView`, `CFormView`nebo `CEditView`. (Můžete také použít `CEditView` přímo.)

- Třída oken s rámečkem, která obsahuje zobrazení. Pro aplikaci jednotného dokumentu (SDI) je tato třída odvozena od `CFrameWnd`. V případě aplikace pro více dokumentů (MDI) je tato třída odvozena od `CMDIChildWnd`. Pokud nepotřebujete přizpůsobit chování okna rámce, můžete použít `CFrameWnd` nebo `CMDIChildWnd` přímo bez odvození vlastní třídy.

Vaše aplikace má jednu šablonu dokumentu pro každý typ dokumentu, který podporuje. Například pokud vaše aplikace podporuje tabulky i textové dokumenty, aplikace má dva objekty šablony dokumentu. Každá šablona dokumentu zodpovídá za vytváření a správu všech dokumentů svého typu.

Šablona dokumentu ukládá ukazatele na objekty `CRuntimeClass` pro třídy okna dokumentu, zobrazení a rámečku. Tyto objekty `CRuntimeClass` jsou určeny při sestavování šablony dokumentu.

Šablona dokumentu obsahuje ID prostředků použitých s typem dokumentu (například nabídka, ikona nebo prostředky tabulky akcelerátoru). Šablona dokumentu obsahuje také řetězce obsahující další informace o typu dokumentu. Mezi ně patří název typu dokumentu (například "list") a Přípona souboru (například ". xls"). Volitelně může obsahovat i jiné řetězce, které používá uživatelské rozhraní aplikace, správce souborů systému Windows a podpora technologie OLE (Object Linking and Embedding).

Pokud je vaše aplikace kontejnerem OLE nebo serverem, šablona dokumentu také definuje ID nabídky použité během místní aktivace. Pokud je vaše aplikace serverem OLE, šablona dokumentu definuje ID panelu nástrojů a nabídky použité během místní aktivace. Tyto další prostředky OLE zadáte tak, že zavoláte `SetContainerInfo` a `SetServerInfo`.

Vzhledem k tomu, že `CDocTemplate` je abstraktní třída, nelze třídu použít přímo. Typická aplikace používá jednu ze dvou `CDocTemplate`odvozených tříd poskytovaných knihovna Microsoft Foundation Class: `CSingleDocTemplate`, které implementují SDI a `CMultiDocTemplate`, které implementují MDI. Další informace o používání šablon dokumentů naleznete v těchto třídách.

Pokud vaše aplikace vyžaduje paradigma uživatelského rozhraní, které se zásadním rozdílem od SDI nebo MDI, můžete odvodit svou vlastní třídu z `CDocTemplate`.

Další informace o `CDocTemplate`naleznete v tématu [šablony dokumentů a proces tvorby dokumentu/zobrazení](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="adddocument"></a>CDocTemplate –:: AddDocument

Pomocí této funkce lze přidat dokument do šablony.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Ukazatel na dokument, který se má přidat

### <a name="remarks"></a>Poznámky

Tato funkce přepíše odvozené třídy [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) a [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) . Pokud odvodíte vlastní třídu šablony dokumentu z `CDocTemplate`, vaše odvozená třída musí tuto funkci přepsat.

##  <a name="cdoctemplate"></a>CDocTemplate –:: CDocTemplate –

Vytvoří objekt `CDocTemplate`.

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parametry

*nIDResource*<br/>
Určuje ID prostředků použitých s typem dokumentu. To může zahrnovat nabídku, ikonu, tabulku akcelerátorů a prostředky řetězců.

Prostředek řetězce se skládá z až sedmi podřetězců oddělených znakem "\n" (znak \n je nutný jako zástupný symbol, pokud není obsažený dílčí řetězec, ale koncové znaky \n nejsou nutné); Tyto podřetězce popisují typ dokumentu. Informace o podřetězcích naleznete v tématu [GetDocString](#getdocstring). Tento prostředek řetězce se nachází v souboru prostředků aplikace. Příklad:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Všimněte si, že řetězec začíná znakem \n; Důvodem je to, že první podřetězec se pro aplikace MDI nepoužívá, a proto není zahrnutý. Tento řetězec lze upravit pomocí editoru řetězců; celý řetězec se zobrazí jako jediná položka v editoru řetězců, nikoli jako sedm samostatných položek.

*pDocClass*<br/>
Odkazuje na objekt `CRuntimeClass` třídy dokumentu. Tato třída je odvozenou třídou `CDocument`, kterou definujete pro reprezentaci vašich dokumentů.

*pFrameClass*<br/>
Odkazuje na objekt `CRuntimeClass` třídy okna rámce. Tato třída může být odvozená třída `CFrameWnd`, nebo může být `CFrameWnd` sama sebe, pokud chcete výchozí chování pro hlavní okno rámce.

*pViewClass*<br/>
Odkazuje na objekt `CRuntimeClass` třídy zobrazení. Tato třída je odvozenou třídou `CView`, kterou definujete pro zobrazení dokumentů.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci použijte k vytvoření objektu `CDocTemplate`. Dynamicky přidělte objekt `CDocTemplate` a předejte ho do [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) z členské funkce `InitInstance` vaší třídy aplikace.

##  <a name="closealldocuments"></a>CDocTemplate –:: CloseAllDocuments

Chcete-li zavřít všechny otevřené dokumenty, zavolejte tuto členskou funkci.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parametry

*bEndSession*<br/>
Nepoužívá se.

### <a name="remarks"></a>Poznámky

Tato členská funkce se obvykle používá jako součást příkazu pro ukončení souboru. Výchozí implementace této funkce volá členskou funkci [objektu CDocument::D eletecontents](../../mfc/reference/cdocument-class.md#deletecontents) , která odstraní data dokumentu a pak zavře okna s rámečkem pro všechna zobrazení připojená k dokumentu.

Tuto funkci můžete přepsat, pokud chcete, aby uživatel před zavřením dokumentu vyžadoval speciální zpracování čištění. Pokud dokument například představuje záznam v databázi, může být vhodné tuto funkci přepsat, aby se databáze zavřela.

##  <a name="createnewdocument"></a>CDocTemplate –:: CreateNewDocument

Chcete-li vytvořit nový dokument typu přidruženého k této šabloně dokumentu, zavolejte tuto členskou funkci.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený dokument nebo hodnotu NULL, pokud dojde k chybě.

##  <a name="createnewframe"></a>CDocTemplate –:: CreateNewFrame

Vytvoří nové okno rámce obsahující dokument a zobrazení.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Dokument, na který má nové okno rámce odkazovat Může mít hodnotu NULL.

*pOther*<br/>
Okno rámce, na kterém má být založeno nové okno rámce. Může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořené okno rámce nebo hodnotu NULL, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

`CreateNewFrame` používá objekty `CRuntimeClass` předané konstruktoru k vytvoření nového okna rámce s připojeným zobrazením a dokumentem. Pokud má parametr *pDoc* hodnotu null, rozhraní vytvoří výstup zprávy trasování.

Parametr *pOther* slouží k implementaci nového příkazu okna. Poskytuje okno rámce, na které se má modelovat nové okno rámce. Nové okno rámce je obvykle vytvořeno neviditelné. Voláním této funkce můžete vytvořit okna s rámečkem mimo standardní implementaci rozhraní File New a soubor Open.

##  <a name="createoleframe"></a>CDocTemplate –:: CreateOleFrame

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
Ukazatel na dokument, na který má nové okno rámce OLE odkazovat.

*bCreateView*<br/>
Určuje, zda je vytvořeno zobrazení spolu s rámcem.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno rámce, pokud bylo úspěšné. jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud je *bCreateView* nula, je vytvořen prázdný rámeček.

##  <a name="getdocstring"></a>CDocTemplate –:: GetDocString

Načte řetězec přidružený k typu dokumentu.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na objekt `CString`, který bude obsahovat řetězec, když funkce vrátí.

*indexovacím*<br/>
Index podřetězce, který je načten z řetězce, který popisuje typ dokumentu. Tento parametr může mít jednu z následujících hodnot:

- `CDocTemplate::windowTitle` název, který se zobrazí v záhlaví okna aplikace (například "Microsoft Excel"). Prezentovat pouze v šabloně dokumentu pro aplikace SDI.

- `CDocTemplate::docName` kořen pro výchozí název dokumentu (například "list"). Tento kořen a číslo se použijí pro výchozí název nového dokumentu tohoto typu vždy, když uživatel zvolí nový příkaz v nabídce soubor (například "List1" nebo "List2"). Pokud není zadaný, použije se jako výchozí hodnota "Untitled".

- `CDocTemplate::fileNewName` název tohoto typu dokumentu Pokud aplikace podporuje více než jeden typ dokumentu, tento řetězec se zobrazí v dialogovém okně Nový soubor (například "list"). Pokud není zadaný, typ dokumentu je nepřístupný pomocí příkazu soubor nový.

- `CDocTemplate::filterName` popis typu dokumentu a filtr zástupných znaků vyhovujících dokumentům tohoto typu. Tento řetězec se zobrazí v rozevíracím seznamu soubory typu v dialogovém okně Otevřít v souboru (například "listy (*. xls)"). Pokud není zadaný, typ dokumentu je nepřístupný pomocí příkazu otevřít soubor.

- `CDocTemplate::filterExt` rozšíření pro dokumenty tohoto typu (například ". xls"). Pokud není zadaný, typ dokumentu je nepřístupný pomocí příkazu otevřít soubor.

- `CDocTemplate::regFileTypeId` identifikátor pro typ dokumentu, který bude uložen v registrační databázi udržované systémem Windows. Tento řetězec je určen pouze pro interní použití (například "ExcelWorksheet"). Pokud tento parametr nezadáte, nemůže být tento typ dokumentu zaregistrován ve Správci souborů systému Windows.

- `CDocTemplate::regFileTypeName` název typu dokumentu, který bude uložen v registrační databázi. Tento řetězec může být zobrazen v dialogových oknech aplikací, které přistupují k registrační databázi (například list aplikace Microsoft Excel).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl nalezen zadaný dílčí řetězec; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Voláním této funkce načtete konkrétní podřetězec popisující typ dokumentu. Řetězec obsahující tyto podřetězce je uložen v šabloně dokumentu a je odvozen z řetězce v souboru prostředků pro aplikaci. Rozhraní volá tuto funkci, aby získala řetězce, které potřebuje pro uživatelské rozhraní aplikace. Pokud jste zadali příponu filename pro dokumenty vaší aplikace, rozhraní volá tuto funkci také při přidávání položky do registrační databáze systému Windows. To umožňuje otevírání dokumentů ze Správce souborů systému Windows.

Tuto funkci volejte pouze v případě, že je odvozena vaše vlastní třída z `CDocTemplate`.

##  <a name="getfirstdocposition"></a>CDocTemplate –:: GetFirstDocPosition

Načte pozici prvního dokumentu přidruženého k této šabloně.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, kterou lze použít k iterování seznamu dokumentů přidružených k této šabloně dokumentu. nebo hodnotu NULL, pokud je seznam prázdný.

### <a name="remarks"></a>Poznámky

Pomocí této funkce lze získat pozici prvního dokumentu v seznamu dokumentů přidružených k této šabloně. Použijte hodnotu pozice jako argument pro [CDocTemplate –:: GetNextDoc](#getnextdoc) , aby se opakoval seznam dokumentů spojených se šablonou.

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) a [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) přepíší tuto čistě virtuální funkci. Tato funkce musí také přepsat libovolnou třídu odvozenou od `CDocTemplate`.

##  <a name="getnextdoc"></a>CDocTemplate –:: GetNextDoc

Načte element seznamu identifikovaný *RPO*a pak nastaví *RPO* na hodnotu pozice další položky v seznamu.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další dokument v seznamu dokumentů přidružených k této šabloně.

### <a name="parameters"></a>Parametry

*RPO*<br/>
Odkaz na hodnotu pozice vrácený předchozím voláním [GetFirstDocPosition](#getfirstdocposition) nebo `GetNextDoc`.

### <a name="remarks"></a>Poznámky

Pokud je načtený prvek poslední v seznamu, pak je nová hodnota *RPO* nastavena na hodnotu null.

Pokud vytvoříte počáteční pozici s voláním [GetFirstDocPosition](#getfirstdocposition), můžete použít `GetNextDoc` v cyklu dopředné iterace.

Je nutné zajistit, aby hodnota pozice představovala platné umístění v seznamu. Pokud je neplatný, ladicí verze knihovna Microsoft Foundation Class výrazy.

##  <a name="initialupdateframe"></a>CDocTemplate –:: InitialUpdateFrame

Inicializuje okno rámce a volitelně ho zviditelní.

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
Okno rámce, které vyžaduje počáteční aktualizaci.

*pDoc*<br/>
Dokument, ke kterému je přidružen rámec. Může mít hodnotu NULL.

*bMakeVisible*<br/>
Označuje, zda by měl být rámec viditelný a aktivní.

### <a name="remarks"></a>Poznámky

Po vytvoření nového rámce pomocí `CreateNewFrame`volejte `IntitialUpdateFrame`. Volání této funkce způsobí, že zobrazení v tomto okně rámce obdrží jejich `OnInitialUpdate` volání. V případě, že dříve existovalo aktivní zobrazení, je primární zobrazení okna rámce aktivní; primární zobrazení je zobrazení s podřízeným ID AFX_IDW_PANE_FIRST. Nakonec je okno rámce viditelné, pokud *bMakeVisible* není nula. Pokud je *bMakeVisible* nula, aktuální fokus a viditelný stav okna rámce zůstanou beze změny.

Není nutné volat tuto funkci při použití implementace souboru New a souboru Open v rozhraní Framework.

##  <a name="loadtemplate"></a>CDocTemplate –:: LoadTemplate

Načte prostředky pro daný `CDocTemplate` nebo odvozenou třídu.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána rozhraním pro načtení prostředků pro daný `CDocTemplate` nebo odvozenou třídu. Obvykle je volána během vytváření, s výjimkou případů, kdy je šablona vytvořena globálně. V takovém případě je volání `LoadTemplate` zpožděno až do volání [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) .

##  <a name="matchdoctype"></a>CDocTemplate –:: MatchDocType

Určuje stupeň spolehlivosti ve shodě mezi typem dokumentu a touto šablonou.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Cesta k souboru, jehož typ má být určen.

*rpDocMatch*<br/>
Ukazatel na dokument, kterému je přiřazen odpovídající dokument, pokud je soubor určený parametrem *lpszPathName* již otevřen.

### <a name="return-value"></a>Návratová hodnota

Hodnota z výčtu **spolehlivosti** , která je definována takto:

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

Pomocí této funkce lze určit typ šablony dokumentu, která se má použít pro otevření souboru. Pokud vaše aplikace podporuje více typů souborů, můžete například pomocí této funkce určit, který z dostupných šablon dokumentů je vhodný pro daný soubor, voláním `MatchDocType` pro každou šablonu a volbou šablony podle hodnoty spolehlivosti vráceného.

Pokud je soubor určený parametrem *lpszPathName* již otevřen, vrátí tato funkce `CDocTemplate::yesAlreadyOpen` a zkopíruje objekt `CDocument` souboru do objektu na *rpDocMatch*.

Pokud soubor není otevřený, ale rozšíření v *lpszPathName* odpovídá rozšíření určenému parametrem `CDocTemplate::filterExt`, vrátí tato funkce `CDocTemplate::yesAttemptNative` a nastaví *rpDocMatch* na hodnotu null. Další informace o `CDocTemplate::filterExt`najdete v tématu [CDocTemplate –:: GetDocString](#getdocstring).

Pokud žádný z těchto případů není true, vrátí funkce `CDocTemplate::yesAttemptForeign`.

Výchozí implementace nevrací `CDocTemplate::maybeAttemptForeign` ani `CDocTemplate::maybeAttemptNative`. Tuto funkci můžete přepsat pro implementaci logiky odpovídající typu, která je vhodná pro vaši aplikaci, například pomocí těchto dvou hodnot z výčtu **spolehlivosti** .

##  <a name="opendocumentfile"></a>CDocTemplate –:: OpenDocumentFile

Otevře soubor určený cestou.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
pro Ukazatel na cestu k souboru, který obsahuje dokument, který má být otevřen.

*bAddToMRU*<br/>
pro Hodnota TRUE označuje, že dokument je jedním z nejaktuálnějších souborů; Hodnota FALSE znamená, že dokument není jedním z nejaktuálnějších souborů.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument, jehož soubor je pojmenován *lpszPathName*; Hodnota NULL, pokud neproběhla úspěšně.

### <a name="remarks"></a>Poznámky

Otevře soubor, jehož cesta je určena parametrem *lpszPathName*. Pokud má *lpszPathName* hodnotu null, vytvoří se nový soubor, který obsahuje dokument typu přidruženého k této šabloně.

##  <a name="removedocument"></a>CDocTemplate –:: RemoveDocument

Odebere dokument, na který odkazuje *pDoc* ze seznamu dokumentů přidružených k této šabloně.

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Ukazatel na dokument, který se má odebrat

### <a name="remarks"></a>Poznámky

Odvozené třídy `CMultiDocTemplate` a `CSingleDocTemplate` tuto funkci potlačí. Pokud odvodíte vlastní třídu šablony dokumentu z `CDocTemplate`, vaše odvozená třída musí tuto funkci přepsat.

##  <a name="saveallmodified"></a>CDocTemplate –:: SaveAllModified

Uloží všechny dokumenty, které byly změněny.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové v případě úspěchu; v opačném případě 0.

##  <a name="setcontainerinfo"></a>CDocTemplate –:: SetContainerInfo

Určuje prostředky pro kontejnery OLE při úpravách místní položky OLE.

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>Parametry

*nIDOleInPlaceContainer*<br/>
ID prostředků použitých při aktivaci vloženého objektu.

### <a name="remarks"></a>Poznámky

Voláním této funkce nastavíte prostředky, které se mají použít, když je objekt OLE aktivovaný na místě. Tyto prostředky můžou zahrnovat nabídky a tabulky akcelerátorů. Tato funkce je obvykle volána ve funkci [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) vaší aplikace.

Nabídka přidružená k *nIDOleInPlaceContainer* obsahuje oddělovače, které umožňují sloučit nabídku aktivované místní položky s nabídkou aplikace typu kontejner. Další informace o slučování nabídek serverů a kontejnerů najdete v článcích [nabídky a prostředky (OLE)](../../mfc/menus-and-resources-ole.md).

##  <a name="setdefaulttitle"></a>CDocTemplate –:: SetDefaultTitle

Voláním této funkce načtete výchozí název dokumentu a zobrazíte ho v záhlaví dokumentu.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>Parametry

*pDocument*<br/>
Ukazatel na dokument, jehož název má být nastaven.

### <a name="remarks"></a>Poznámky

Informace o výchozím názvu naleznete v popisu `CDocTemplate::docName` v [CDocTemplate –:: GetDocString](#getdocstring).

##  <a name="setserverinfo"></a>CDocTemplate –:: SetServerInfo

Určuje prostředky a třídy, pokud je dokument serveru vložený nebo upravován místně.

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
ID prostředků použitých při místní aktivaci vloženého objektu.

*pOleFrameClass*<br/>
Ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obsahující informace třídy pro objekt okna rámce, který byl vytvořen při místní aktivaci.

*pOleViewClass*<br/>
Ukazatel na `CRuntimeClass` strukturu obsahující informace o třídě objektu zobrazení vytvořeného při místní aktivaci.

### <a name="remarks"></a>Poznámky

Zavolejte tuto členskou funkci pro identifikaci prostředků, které bude používat serverová aplikace, když uživatel požádá o aktivaci vloženého objektu. Tyto prostředky se skládají z nabídek a tabulek akcelerátorů. Tato funkce se obvykle volá v `InitInstance` vaší aplikace.

Nabídka přidružená k *nIDOleInPlaceServer* obsahuje oddělovače, které umožňují, aby se nabídka serveru mohla sloučit s nabídkou kontejneru. Další informace o slučování nabídek serverů a kontejnerů najdete v článcích [nabídky a prostředky (OLE)](../../mfc/menus-and-resources-ole.md).

##  <a name="createpreviewframe"></a>CDocTemplate –:: CreatePreviewFrame

Vytvoří podřízený rámec používaný pro bohatou verzi Preview.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na nadřazené okno (obvykle poskytované prostředím).

*pDoc*<br/>
Ukazatel na objekt dokumentu, jehož obsah bude zobrazen náhled.

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na objekt `CFrameWnd` nebo hodnotu NULL, pokud vytvoření se nezdařilo.

### <a name="remarks"></a>Poznámky

##  <a name="setpreviewinfo"></a>CDocTemplate –:: SetPreviewInfo

Nastaví obslužnou rutinu mimo proces Preview.

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>Parametry

*nIDPreviewFrame*<br/>
Určuje ID prostředku rámce náhledu.

*pPreviewFrameClass*<br/>
Určuje ukazatel na strukturu informací třídy modulu runtime snímku náhledu.

*pPreviewViewClass*<br/>
Určuje ukazatel na strukturu informací třídy modulu runtime zobrazení náhledu.

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
