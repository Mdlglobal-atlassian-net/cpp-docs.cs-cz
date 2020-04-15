---
title: Informace o aplikacích a správa aplikací
description: Odkaz na informace o aplikacích a funkcích správy knihovny Microsoft Foundation Class Library (MFC).
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: fc0b4b09f6c48da68bebe4a2825f49bcf6ab7e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372504"
---
# <a name="application-information-and-management"></a>Informace o aplikacích a správa aplikací

Při psaní aplikace vytvoříte jeden [cwinapp](../../mfc/reference/cwinapp-class.md)odvozený objekt. Někdy můžete chtít získat informace o tomto objektu mimo -derived `CWinApp`objektu. Nebo budete potřebovat přístup k jiným globálním objektům "správce".

Knihovna tříd Microsoft Foundation poskytuje následující globální funkce, které vám pomohou provádět tyto úkoly:

## <a name="application-information-and-management-functions"></a>Informace o aplikaci a funkce správy

|||
|-|-|
|[Afxbeginthread](#afxbeginthread)|Vytvoří nové vlákno.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Ukazatel na správce globální [kontextové nabídky](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Ukončí aktuální vlákno.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Prochází řetězce prostředků a vyhledej konkrétní prostředek podle ID prostředku a typu prostředku. |
|[Afxfreelibrary](#afxfreelibrary)|Sníží počet odkazů načteného modulu dynamické knihovny (DLL). Když počet odkazů dosáhne nuly, modul je nenamapován.|
|[Aplikace AfxGet](#afxgetapp)|Vrátí ukazatel na jeden `CWinApp` objekt aplikace.|
|[Název aplikace AfxGetApp](#afxgetappname)|Vrátí řetězec, který obsahuje název aplikace.|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Vrátí hinstance představující tuto instanci aplikace.|
|[AfxGetMainWnd](#afxgetmainwnd)|Vrátí ukazatel na aktuální "hlavní" okno aplikace bez OLE nebo na místo rámce okna serverové aplikace.|
|[Registrace uživatele AfxGetPer](#afxgetperuserregistration)|Tato funkce slouží k určení, zda aplikace přesměruje přístup registru k uzlu **HKEY_CURRENT_USER** (**HKCU**).|
|[AfxGetResourceHandle](#afxgetresourcehandle)|Vrátí HINSTANCE ke zdroji výchozích prostředků aplikace. Slouží k přímému přístupu k prostředkům aplikace.|
|[AfxGetThread](#afxgetthread)|Načte ukazatel na aktuální [cwinthread](../../mfc/reference/cwinthread-class.md) objekt.|
|[AfxInitRichEditovat](#afxinitrichedit)|Inicializuje ovládací prvek rozšířené úpravy verze 1.0 pro aplikaci.|
|[AfxInitRichEdit2](#afxinitrichedit2)|Inicializuje ovládací prvek verze 2.0 a novější hojné úpravy pro aplikaci.|
|[Třída AfxIsExtendedFrameClass](#afxisextendedframeclass)|Určuje, zda je dané okno objektem rozšířeného rámečku.|
|[Panel nástrojů AfxIsMFC](#afxismfctoolbar)|Určuje, zda je dané okno objektem panelu nástrojů.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Ukazatel na globálního [správce klávesnice](ckeyboardmanager-class.md).|
|[Afxloadlibrary](#afxloadlibrary)|Mapuje modul DLL a vrátí popisovač, který lze použít k získání adresy funkce DLL.|
|[AfxLoadLibraryEx](#afxloadlibraryex)|Mapuje modul DLL pomocí zadaných možností a vrátí popisovač, který lze použít k získání adresy funkce DLL.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Ukazatel na [správce globálního odtržení menu](cmenutearoffmanager-class.md).|
|[AfxMouseManager](#afxmousemanager)|Ukazatel na globálního [správce myši](cmousemanager-class.md).|
|[Třída AfxRegisterClass](#afxregisterclass)|Registruje třídu okna v knihovně DLL, která používá knihovnu MFC.|
|[AfxRegisterWndClass](#afxregisterwndclass)|Zaregistruje třídu okna systému Windows, která doplní ty, které je automaticky registrováno knihovnou MFC.|
|[Registrace uživatele AfxSetPer](#afxsetperuserregistration)|Nastaví, zda aplikace přesměruje přístup registru k uzlu **HKEY_CURRENT_USER** (**HKCU**).|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Nastaví popisovač HINSTANCE, kde jsou načteny výchozí prostředky aplikace.|
|[AfxShellManager](#afxshellmanager)|Ukazatel na globálního [správce prostředí](cshellmanager-class.md). |
|[AfxSocketInit](#afxsocketinit)|Nazývá přepsání `CWinApp::InitInstance` inicializovat Windows Sockets.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Ukazatel na globální [správce uživatelských nástrojů](cusertoolsmanager-class.md).|
|[AfxWinInit](#afxwininit)|Volána mfc dodanou `WinMain` funkcí jako součást inicializace [CWinApp](../../mfc/reference/cwinapp-class.md) aplikace založené na grafickém uživatelském rozhraní, k inicializaci knihovny MFC. Musí být volána přímo pro konzolové aplikace, které používají knihovnu MFC.|

## <a name="afxbeginthread"></a><a name="afxbeginthread"></a>Afxbeginthread

Volání této funkce k vytvoření nového vlákna.

```cpp
CWinThread* AfxBeginThread(
    AFX_THREADPROC pfnThreadProc,
    LPVOID pParam,
    int nPriority = THREAD_PRIORITY_NORMAL,
    UINT nStackSize = 0,
    DWORD dwCreateFlags = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);

CWinThread* AfxBeginThread(
    CRuntimeClass* pThreadClass,
    int nPriority = THREAD_PRIORITY_NORMAL,
    UINT nStackSize = 0,
    DWORD dwCreateFlags = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parametry

*pfnThreadProc*\
Odkazuje na řídící funkci pracovního vlákna. Ukazatel nemůže být NULL. Tato funkce musí být deklarována takto:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*\
RUNTIME_CLASS objektu odvozeného z [CWinThread](../../mfc/reference/cwinthread-class.md).

*pParam*\
Parametr pro předání řídící funkci.

*nPriorita*\
Priorita nastavit pro vlákno. Úplný seznam a popis dostupných priorit naleznete v tématu [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v sadě Windows SDK.

*nStackSize*\
Určuje velikost v bajtů zásobníku pro nové vlákno. Pokud 0, velikost zásobníku výchozí na stejnou velikost zásobníku jako vytváření podprocesu.

*dwCreateFlags*\
Určuje další příznak, který řídí vytváření vlákna. Tento příznak může obsahovat jednu ze dvou hodnot:

- CREATE_SUSPENDED Spusťte vlákno s počtem pozastavení jednoho. Použijte CREATE_SUSPENDED, pokud chcete inicializovat `CWinThread` data členů objektu, například [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) nebo členy odvozené třídy, před spuštěním vlákna. Po dokončení inicializace použijte [CWinThread::ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) ke spuštění vlákna. Vlákno se nespustí, `CWinThread::ResumeThread` dokud nebude voláno.

- **0** Spusťte vlákno ihned po vytvoření.

*lpSecurityAttrs*\
Odkazuje na [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) strukturu, která určuje atributy zabezpečení pro vlákno. Pokud null, stejné atributy zabezpečení jako vytváření vlákna se používají. Další informace o této struktuře naleznete v souboru Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený objekt vlákna nebo NULL, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

První forma `AfxBeginThread` vytvoří pracovní vlákno. Druhý formulář vytvoří vlákno, které může sloužit jako vlákno uživatelského rozhraní nebo jako pracovní podproces.

`AfxBeginThread`vytvoří nový `CWinThread` objekt, zavolá jeho [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) funkce spustit provádění podprocesu a vrátí ukazatel podprocesu. Kontroly jsou prováděny v průběhu celého postupu, aby se ujistil, všechny objekty jsou správně přiděleny v případě, že jakákoli část vytvoření nezdaří. Chcete-li ukončit vlákno, volání [AfxEndThread](#afxendthread) z v rámci vlákna nebo vrátit z řídící funkce pracovního vlákna.

Multithreading musí být povolena aplikací; v opačném případě se tato funkce nezdaří. Další informace o povolení multithreadingu naleznete v [tématu /MD, /MT, /LD (Použít knihovnu za běhu).](../../build/reference/md-mt-ld-use-run-time-library.md)

Další informace `AfxBeginThread`o tématu naleznete v článcích [Multithreading: Creating Worker Threads](../../parallel/multithreading-creating-worker-threads.md) and [Multithreading: Creating User-Interface Threads](../../parallel/multithreading-creating-user-interface-threads.md).

### <a name="example"></a>Příklad

Viz příklad pro [CSocket::Attach](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxcontextmenumanager"></a><a name="afxcontextmenumanager"></a>AfxContextMenuManager

Ukazatel na správce globální [kontextové nabídky](ccontextmenumanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxcontextmenumanager.h

## <a name="afxendthread"></a><a name="afxendthread"></a>AfxEndThread

Volání této funkce ukončit aktuálně spuštěné vlákno.

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>Parametry

*nKód ukončení*\
Určuje ukončovací kód vlákna.

*bOdstranit*\
Odstraní objekt vlákna z paměti.

### <a name="remarks"></a>Poznámky

Musí být volána z vlákna, které má být ukončeno.

Další informace `AfxEndThread`naleznete v článku [Multithreading: Ukončování vláken](../../parallel/multithreading-terminating-threads.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxfindresourcehandle"></a><a name="afxfindresourcehandle"></a>AfxFindResourceHandle

Slouží `AfxFindResourceHandle` ke procházce řetězce prostředků a vyhledání konkrétního prostředku podle ID prostředku a typu prostředku.

### <a name="syntax"></a>Syntaxe

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Parametry

*název lpsz*\
Ukazatel na řetězec obsahující ID prostředku.
*lpszTyp*\
Ukazatel na typ prostředku. Seznam typů prostředků naleznete v tématu [Hledání prostředku](/windows/win32/api/winbase/nf-winbase-findresourcea) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Popisovač modulu, který obsahuje prostředek.

### <a name="remarks"></a>Poznámky

`AfxFindResourceHandle`Vyhledá konkrétní prostředek a vrátí popisovač modulu, který obsahuje prostředek. Prostředek může být v libovolné knihovně DLL rozšíření knihovny MFC, která je načtena. `AfxFindResourceHandle`vám řekne, který z nich má zdroj.

Moduly jsou prohledávány v tomto pořadí:

1. Hlavní modul, pokud se jedná o knihovnu DLL rozšíření knihovny MFC.

1. Nesystémové moduly.

1. Moduly specifické pro jazyk.

1. Hlavní modul, pokud se jedná o systémovou dll.

1. Systémové moduly.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="afxfreelibrary"></a><a name="afxfreelibrary"></a>Afxfreelibrary

Oba `AfxFreeLibrary` `AfxLoadLibrary` a udržovat počet odkazů pro každý modul načtené knihovny.

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Parametry

*hInstLib*\
Popisovač modulu načtené knihovny. [AfxLoadLibrary](#afxloadlibrary) vrátí tento popisovač.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je funkce úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

`AfxFreeLibrary`sníží počet odkazů načteného modulu dynamické knihovny (DLL). Když počet odkazů dosáhne nuly, modul je nenamapován z adresního prostoru volajícího procesu a popisovač již není platný. Tento počet odkazů se zintáží pokaždé, když `AfxLoadLibrary` je volána.

Před zrušením mapování modulu knihovny systém umožňuje knihovnu DLL odpojit od procesů, které ji používají. To dává dll příležitost vyčistit prostředky přidělené pro aktuální proces. Po návratu funkce vstupního bodu je modul knihovny odebrán z adresního prostoru aktuálního procesu.

Slouží `AfxLoadLibrary` k mapování modulu DLL.

Ujistěte `AfxFreeLibrary` se, `AfxLoadLibrary` že použít a (namísto Win32 funkce `FreeLibrary` a `LoadLibrary`) pokud vaše aplikace používá více vláken. Použití `AfxLoadLibrary` `AfxFreeLibrary` a zajišťuje, že spuštění a vypnutí kódu, který se spustí při načtení a uvolnění knihovny DLL rozšíření knihovny MFC, nepoškodí globální stav knihovny MFC.

### <a name="example"></a>Příklad

Viz příklad pro [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdll_.h

## <a name="afxgetapp"></a><a name="afxgetapp"></a>Aplikace AfxGet

Ukazatel vrácený touto funkcí lze použít pro přístup k informacím o aplikaci, jako je například hlavní kód odeslání zprávy nebo nejvyšší okno.

```cpp
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jeden `CWinApp` objekt pro aplikaci.

### <a name="remarks"></a>Poznámky

Pokud tato metoda vrátí hodnotu NULL, může to znamenat, že hlavní okno aplikace ještě nebylo plně inicializováno. Může to také znamenat problém.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxgetappname"></a><a name="afxgetappname"></a>Název aplikace AfxGetApp

Vrácený řetězec lze použít pro diagnostické zprávy nebo jako kořen pro dočasné názvy řetězců.

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Návratová hodnota

Řetězec s nulovým ukončením obsahující název aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxgetinstancehandle"></a><a name="afxgetinstancehandle"></a>AfxGetInstanceHandle

Tato funkce umožňuje načíst popisovač instance aktuální aplikace.

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Návratová hodnota

HINSTANCE aktuální instance aplikace. Pokud je volána z knihovny DLL propojené s verzí knihovny MFC USRDLL, je vrácena knihovna HINSTANCE do knihovny DLL.

### <a name="remarks"></a>Poznámky

`AfxGetInstanceHandle`vždy vrátí HINSTANCE spustitelného souboru (. EXE), pokud je volána z knihovny DLL propojené s usrdll verze knihovny MFC. V tomto případě vrátí HINSTANCE dll.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxgetmainwnd"></a><a name="afxgetmainwnd"></a>AfxGetMainWnd

Pokud je vaše aplikace server EM, volání této funkce načíst ukazatel na aktivní hlavní okno aplikace. Použijte tento výsledek namísto přímého odkazování na [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) člen aplikačního objektu.

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na objekt okna rámce, který obsahuje aktivní dokument na místě, pokud má server objekt, který je aktivní na místě uvnitř aktivního kontejneru.

Pokud neexistuje žádný objekt, který je na místě aktivní v rámci kontejneru nebo aplikace není server OLE, tato funkce vrátí *m_pMainWnd* objektu aplikace.

Pokud `AfxGetMainWnd` je volána z primárního vlákna aplikace, vrátí hlavní okno aplikace podle výše uvedených pravidel. Pokud je funkce volána ze sekundárního vlákna v aplikaci, funkce vrátí hlavní okno přidružené k podprocesu, který volání provedl.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace není server OLE, volání této funkce je ekvivalentní přímo odkazující na *m_pMainWnd* člen objektu aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxgetperuserregistration"></a><a name="afxgetperuserregistration"></a>Registrace uživatele AfxGetPer

Tato funkce slouží k určení, zda aplikace přesměruje přístup registru k uzlu **HKEY_CURRENT_USER** (**HKCU**).

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Návratová hodnota

True označuje, že informace o registru jsou směrovány do uzlu HKCU. NEPRAVDA označuje, že aplikace zapisuje informace registru do výchozího uzlu. Výchozí uzel je **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Poznámky

Pokud povolíte přesměrování registru, rozhraní přesměruje přístup z **HKCR** na **HKEY_CURRENT_USER\Software\Classes**. Pouze architektury knihovny MFC a knihovny ATL jsou ovlivněny přesměrování.

Chcete-li změnit, zda aplikace přesměruje přístup k registru, použijte [AfxSetPerUserRegistration](#afxsetperuserregistration).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxstat_.h

## <a name="afxgetresourcehandle"></a><a name="afxgetresourcehandle"></a>AfxGetResourceHandle

Pomocí popisovače HINSTANCE vrácené touto funkcí můžete přistupovat přímo k prostředkům `FindResource`aplikace, například při volání funkce systému Windows .

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač HINSTANCE, kde jsou načteny výchozí prostředky aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxgetthread"></a><a name="afxgetthread"></a>AfxGetThread

Volání této funkce získat ukazatel na [CWinThread](../../mfc/reference/cwinthread-class.md) objekt představující aktuálně spuštěné vlákno.

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuálně spuštěné vlákno; jinak NULL.

### <a name="remarks"></a>Poznámky

Musí být volána z vlákna.

> [!NOTE]
> Pokud portujete projekt knihovny MFC volající `AfxGetThread` z visual c++ verze 4.2, 5.0 nebo 6.0, zavolá `AfxGetThread` [AfxGetApp,](#afxgetapp) pokud není nalezeno žádné vlákno. V novějších verzích kompilátoru vrátí hodnotu NULL, `AfxGetThread` pokud nebylo nalezeno žádné vlákno. Pokud chcete vlákno aplikace, musíte `AfxGetApp`volat .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxinitrichedit"></a><a name="afxinitrichedit"></a>AfxInitRichEditovat

Volání této funkce k inicializaci bohaté upravit ovládací prvek (verze 1.0) pro aplikaci.

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Poznámky

Tato funkce je k dispozici pro zpětnou kompatibilitu. Nové aplikace by měly používat [AfxInitRichEdit2](#afxinitrichedit2).

`AfxInitRichEdit`zatížení RICHED32. DLL pro inicializaci verze 1.0 bohatého ovládacího prvku pro úpravy. Chcete-li použít verzi 2.0 a 3.0 bohaté ho redigovat ovládací prvek, RICHED20. DLL musí být načtena. Je načten voláním [AfxInitRichEdit2](#afxinitrichedit2).

Chcete-li aktualizovat rozšířené ovládací prvky úprav v existujících aplikacích visual c++ na verzi 2.0, otevřete . RC soubor jako text, změňte název třídy každého bohatého editačního ovládacího prvku z "RICHEDIT" na "RichEdit20a". Potom hovor nahraďte `AfxInitRichEdit` na . `AfxInitRichEdit2`

Tato funkce také inicializuje společnou knihovnu ovládacích prvků, pokud knihovna ještě nebyla inicializována pro proces. Pokud použijete ovládací prvek rich edit přímo z aplikace knihovny MFC, volání této funkce zajistit, že knihovna MFC správně inicializovala bohaté upravit řízení runtime. Pokud voláte `Create` metodu [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)nebo [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), obvykle není nutné volat tuto funkci, ale v některých případech může být nutné.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxinitrichedit2"></a><a name="afxinitrichedit2"></a>AfxInitRichEdit2

Volání této funkce inicializovat rich edit control (verze 2.0 a novější) pro aplikaci.

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Poznámky

Volání této funkce pro načtení RICHED20. DLL a inicializovat verzi 2.0 bohaté ho redigovat. Pokud voláte `Create` metodu [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)nebo [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), obvykle není nutné volat tuto funkci, ale v některých případech může být nutné.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxisextendedframeclass"></a><a name="afxisextendedframeclass"></a>Třída AfxIsExtendedFrameClass

Určuje, zda je dané okno objektem rozšířeného rámečku.

### <a name="syntax"></a>Syntaxe

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Parametry

*pWnd*\
[v] Ukazatel na objekt, který je `CWnd`odvozen z aplikace .

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadaným oknem objekt s rozšířeným rámečkem; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu TRUE, pokud *je hodnota pWnd* odvozena z jedné z následujících tříd:

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

Tato metoda je užitečná, když máte ověřit, že parametr funkce nebo metody je okno rozšířeného rámce.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxpriv.h

## <a name="afxismfctoolbar"></a><a name="afxismfctoolbar"></a>Panel nástrojů AfxIsMFC

Určuje, zda je dané okno objektem panelu nástrojů.

### <a name="syntax"></a>Syntaxe

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*\
[v] Ukazatel na objekt, který je `CWnd`odvozen z aplikace .

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je zadaný majek objektem panelu nástrojů; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda `TRUE` vrátí, pokud *pWnd* pochází z `CMFCToolBar`. Tato metoda je užitečná, pokud máte ověřit, `CMFCToolBar` že parametr funkce nebo metody je objekt.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxpriv.h

## <a name="afxkeyboardmanager"></a><a name="afxkeyboardmanager"></a>AfxKeyboardManager

Ukazatel na globálního [správce klávesnice](ckeyboardmanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxkeyboardmanager.h

## <a name="afxloadlibrary"></a><a name="afxloadlibrary"></a>Afxloadlibrary

Slouží `AfxLoadLibrary` k mapování modulu DLL.

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Parametry

*lpszNázev modulu*\
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje název modulu (buď . DLL nebo . EXE). Zadaný název je název souboru modulu.

Pokud řetězec určuje cestu, ale soubor v zadaném adresáři neexistuje, funkce se nezdaří.

Pokud cesta není zadána a přípona názvu souboru je vynechána, výchozí přípona . Je připojena dll. Řetězec názvu souboru však může obsahovat znak koncového bodu (.) označující, že název modulu nemá žádné rozšíření. Pokud není zadána žádná cesta, funkce používá [pořadí hledání pro desktopové aplikace](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je popisovač modulu. Při selhání je vrácená hodnota NULL.

### <a name="remarks"></a>Poznámky

Vrátí popisovač, který lze použít v [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) získat adresu funkce DLL. `AfxLoadLibrary`lze také mapovat další spustitelné moduly.

Každý proces udržuje počet odkazů pro každý modul načtené knihovny. Tento počet odkazů se zintáží pokaždé, když `AfxLoadLibrary` je `AfxFreeLibrary` volána a je snížena pokaždé, když je volána. Když počet odkazů dosáhne nuly, modul je nenamapován z adresního prostoru volajícího procesu a popisovač již není platný.

Ujistěte `AfxLoadLibrary` se, `AfxFreeLibrary` že použít a (namísto Win32 funkce `LoadLibrary` a `FreeLibrary`) pokud vaše aplikace používá více vláken a pokud dynamicky načte dll rozšíření knihovny MFC. Použití `AfxLoadLibrary` `AfxFreeLibrary` a zajišťuje, že spuštění a vypnutí kódu, který se spustí při načtení a uvolnění knihovny DLL rozšíření knihovny MFC, nepoškodí globální stav knihovny MFC.

Použití `AfxLoadLibrary` v aplikaci vyžaduje dynamické propojení s verzí knihovny MFC knihovny DLL. Soubor záhlaví `AfxLoadLibrary`pro soubor , Afxdll_.h, je zahrnut pouze v případě, že knihovna MFC je propojena s aplikací jako knihovna DLL. Tento požadavek je záměrné, protože je nutné propojit s verzí knihovny MFC knihovny MFC použít nebo vytvořit knihovny DLL rozšíření knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdll_.h

## <a name="afxloadlibraryex"></a><a name="afxloadlibraryex"></a>AfxLoadLibraryEx

Slouží `AfxLoadLibraryEx` k mapování modulu DLL.

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*název lpFileName*\
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje název modulu (buď . DLL nebo . EXE). Zadaný název je název souboru modulu.

Pokud řetězec určuje cestu, ale soubor v zadaném adresáři neexistuje, funkce se nezdaří.

Pokud cesta není zadána a přípona názvu souboru je vynechána, výchozí přípona . Je připojena dll. Řetězec názvu souboru však může obsahovat znak koncového bodu (.) označující, že název modulu nemá žádné rozšíření. Pokud není zadána žádná cesta, funkce používá [pořadí hledání pro desktopové aplikace](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

*hSoubor*\
Tento parametr je vyhrazen pro budoucí použití. Musí být NULL.

*dwFlags*\
Akce, která má být provedena při načítání modulu. Pokud nejsou zadány žádné příznaky, chování této `AfxLoadLibrary` funkce je shodné s funkcí. Možné hodnoty tohoto parametru jsou popsány v dokumentaci [LoadLibraryEx.](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je popisovač modulu. Při selhání je vrácená hodnota NULL.

### <a name="remarks"></a>Poznámky

`AfxLoadLibraryEx`vrátí popisovač, který lze použít v [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) získat adresu funkce DLL. `AfxLoadLibraryEx`lze také mapovat další spustitelné moduly.

Každý proces udržuje počet odkazů pro každý modul načtené knihovny. Tento počet odkazů se zintáží pokaždé, když `AfxLoadLibraryEx` je `AfxFreeLibrary` volána a je snížena pokaždé, když je volána. Když počet odkazů dosáhne nuly, modul je nenamapován z adresního prostoru volajícího procesu a popisovač již není platný.

Ujistěte `AfxLoadLibraryEx` se, `AfxFreeLibrary` že použít a (namísto Win32 funkce `LoadLibraryEx` a `FreeLibrary`) pokud vaše aplikace používá více vláken a pokud dynamicky načte dll rozšíření knihovny MFC. Použití `AfxLoadLibraryEx` `AfxFreeLibrary` a zajišťuje, že spuštění a vypnutí kódu, který se spustí při načtení a uvolnění knihovny DLL rozšíření knihovny MFC, nepoškodí globální stav knihovny MFC.

Použití `AfxLoadLibraryEx` v aplikaci vyžaduje dynamické propojení s verzí knihovny MFC knihovny DLL. Soubor záhlaví `AfxLoadLibraryEx`pro soubor , Afxdll_.h, je zahrnut pouze v případě, že knihovna MFC je propojena s aplikací jako knihovna DLL. Tento požadavek je záměrné, protože je nutné propojit s verzí knihovny MFC knihovny MFC použít nebo vytvořit knihovny DLL rozšíření knihovny MFC.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdll_.h

## <a name="afxmenutearoffmanager"></a><a name="afxmenutearoffmanager"></a>AfxMenuTearOffManager

Ukazatel na [správce globálního odtržení menu](cmenutearoffmanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmenutearoffmanager.h

## <a name="afxmousemanager"></a><a name="afxmousemanager"></a>AfxMouseManager

Ukazatel na globálního [správce myši](cmousemanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmousemanager.h

## <a name="afxregisterclass"></a><a name="afxregisterclass"></a>Třída AfxRegisterClass

Tato funkce slouží k registraci tříd oken v knihovně DLL, která používá knihovnu MFC.

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Parametry

*lpWndClass*\
Ukazatel na [wndclass](/windows/win32/api/winuser/ns-winuser-wndclassw) strukturu obsahující informace o třídě okna, které mají být registrovány. Další informace o této struktuře naleznete v souboru Windows SDK.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je třída úspěšně zaregistrována; jinak FALSE.

### <a name="remarks"></a>Poznámky

Pokud použijete tuto funkci, třída je automaticky nezaregistrována při uvolnění dll.

V sestaveních bez dll `AfxRegisterClass` je identifikátor definován jako makro, `RegisterClass`které se mapuje na funkci systému Windows , protože třídy registrované v aplikaci jsou automaticky neregistrované. Pokud používáte `AfxRegisterClass` `RegisterClass`místo , váš kód lze použít beze změny v aplikaci i v DLL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxregisterwndclass"></a><a name="afxregisterwndclass"></a>AfxRegisterWndClass

Umožňuje zaregistrovat vlastní třídy oken.

```cpp
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Parametry

*nStyl třídy*\
Určuje styl třídy systému Windows nebo kombinaci stylů vytvořených pomocí operátoru Bitwise-OR (**&#124;) **pro třídu okna. Seznam stylů tříd naleznete ve struktuře [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) v sadě Windows SDK. Pokud null, výchozí hodnoty jsou nastaveny takto:

- Nastaví styl myši na CS_DBLCLKS, který odesílá poklepání na zprávy do procedury okna, když uživatel poklepe myší.

- Nastaví styl kurzoru šipky na standardní IDC_ARROW systému Windows.

- Nastaví stopu pozadí na HODNOTU NULL, takže okno nevymaže jeho pozadí.

- Nastaví ikonu na standardní ikonu loga Windows s mávajícívlajkou.

*hKurzor*\
Určuje popisovač prostředku kurzoru, který má být nainstalován v každém okně vytvořeném z třídy okna. Pokud použijete výchozí hodnotu **0**, získáte standardní kurzor IDC_ARROW.

*hbrPozadí*\
Určuje popisovač prostředku stopy, který má být nainstalován v každém okně vytvořeném z třídy okna. Pokud použijete výchozí hodnotu **0**, budete mít stopu na pozadí null a ve výchozím nastavení vaše okno nesmaže pozadí při zpracování [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd).

*hIkona*\
Určuje popisovač prostředku ikony, který má být nainstalován v každém okně vytvořeném z třídy okna. Pokud použijete výchozí hodnotu **0**, zobrazí se standardní ikona loga Windows s mávajícívlajkou.

### <a name="return-value"></a>Návratová hodnota

Řetězec s nulovým ukončeným hodnotou obsahující název třídy. Tento název třídy můžete `Create` předat `CWnd` členské funkce v nebo jiné **cwnd odvozené**třídy k vytvoření okna. Název je generován knihovnou tříd Microsoft Foundation.

> [!NOTE]
> Vrácená hodnota je ukazatel na statickou vyrovnávací paměť. Chcete-li tento řetězec uložit, přiřaďte jej `CString` proměnné.

### <a name="remarks"></a>Poznámky

Knihovna tříd Microsoft Foundation automaticky zaregistruje několik standardních tříd oken. Volání této funkce, pokud chcete zaregistrovat vlastní třídy okna.

Název registrovaný pro třídu závisí `AfxRegisterWndClass` výhradně na parametrech. Pokud zavoláte `AfxRegisterWndClass` vícekrát s identickými parametry, zaregistruje pouze třídu při prvním volání. Pozdější volání `AfxRegisterWndClass` s identickými parametry vrátí již registrovaný název třídy.

Pokud voláte `AfxRegisterWndClass` více CWnd odvozené třídy s identickými parametry, namísto získání samostatné třídy okna pro každou třídu, každá třída sdílí stejnou třídu okna. Toto sdílení může způsobit problémy, pokud je použit styl třídy CS_CLASSDC. Namísto více CS_CLASSDC tříd okna, skončíte pouze s jednou třídou CS_CLASSDC okna. Všechna okna jazyka C++, která používají tuto třídu, sdílejí stejný řadič domény. Chcete-li se tomuto problému vyhnout, volání [AfxRegisterClass](#afxregisterclass) zaregistrovat třídu.

Další informace o registraci třídy okna a funkci naleznete `AfxRegisterWndClass` v technické poznámce [TN001: Registrace třídy okna.](../../mfc/tn001-window-class-registration.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxsetperuserregistration"></a><a name="afxsetperuserregistration"></a>Registrace uživatele AfxSetPer

Nastaví, zda aplikace přesměruje přístup registru k uzlu **HKEY_CURRENT_USER** (**HKCU**).

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*\
[v] True označuje, že informace o registru jsou směrovány do uzlu HKCU. NEPRAVDA označuje, že aplikace zapisuje informace registru do výchozího uzlu. Výchozí uzel je **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Poznámky

Před systémem Windows Vista aplikace, které přistupovaly k registru, běžně používaly **uzel HKEY_CLASSES_ROOT.** Však s operačními systémy Windows Vista nebo novější, je nutné spustit aplikaci ve zvýšeném režimu pro zápis do HKCR.

Tato metoda umožňuje aplikaci číst a zapisovat do registru bez spuštění ve zvýšeném režimu. Funguje tak, že přesměrovává přístup registru z HKCR na HKCU. Další informace naleznete v tématu [Linker Property Pages](../../build/reference/linker-property-pages.md).

Pokud povolíte přesměrování registru, rozhraní přesměruje přístup z HKCR na **HKEY_CURRENT_USER\Software\Classes**. Pouze architektury knihovny MFC a knihovny ATL jsou ovlivněny přesměrování.

Výchozí implementace přistupuje k registru pod HKCR.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxstat_.h

## <a name="afxsetresourcehandle"></a><a name="afxsetresourcehandle"></a>AfxSetResourceHandle

Pomocí této funkce nastavte popisovač HINSTANCE, který určuje, kde jsou načteny výchozí prostředky aplikace.

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Parametry

*hInstZdroj*\
Popisovač instance nebo modulu na . EXE nebo DLL, ze kterého jsou načteny prostředky aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxshellmanager"></a><a name="afxshellmanager"></a>AfxShellManager

Ukazatel na globálního [správce prostředí](cshellmanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxshellmanager.h

## <a name="afxsocketinit"></a><a name="afxsocketinit"></a>AfxSocketInit

Volání této funkce `CWinApp::InitInstance` v přepsání inicializovat Windows Sockets.

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Parametry

*LpwsaData*\
Ukazatel na strukturu [WSADATA.](/windows/win32/api/winsock2/ns-winsock2-wsadata) Pokud *lpwsaData* není rovna NULL, pak `WSADATA` je adresa struktury vyplněna voláním `WSAStartup`. Tato funkce také `WSACleanup` zajišťuje, že je volána pro vás před ukončením aplikace.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Při použití soketů knihovny MFC v sekundárních vláknech `AfxSocketInit` v staticky propojené aplikaci knihovny MFC je nutné volat v každém vlákně, které používá sokety k inicializaci knihoven soketu. Ve výchozím `AfxSocketInit` nastavení se nazývá pouze v primárním vlákně.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxsock.h

## <a name="afxusertoolsmanager"></a><a name="afxusertoolsmanager"></a>AfxUserToolsManager

Ukazatel na globální [správce uživatelských nástrojů](cusertoolsmanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxusertoolsmanager.h

## <a name="afxwininit"></a><a name="afxwininit"></a>AfxWinInit

Tato funkce je volána funkcí `WinMain` dodanou knihovnou MFC jako součást inicializace [cwinapp](../../mfc/reference/cwinapp-class.md) aplikace založené na grafickém uživatelském rozhraní pro inicializaci knihovny MFC.

```cpp
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>Parametry

*hInstance*\
Popisovač aktuálně spuštěného modulu.

*hPrevInstance*\
Popisovač předchozí instance aplikace. Pro aplikaci založenou na win32 je tento parametr vždy **null**.

*lpCmdLine*\
Odkazuje na řetězec s nulovým ukončením určující příkazový řádek pro aplikaci.

*nCmdZobrazit*\
Určuje, jak bude zobrazeno hlavní okno aplikace grafického uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Pro konzolovou aplikaci, která nepoužívá funkci `WinMain` dodanou knihovnou `AfxWinInit` MFC, musíte volat přímo k inicializaci knihovny MFC.

Pokud voláte `AfxWinInit` sami, měli byste `CWinApp` deklarovat instanci třídy. Pro konzolovou aplikaci se můžete rozhodnout, `CWinApp` že nebudete odvozovat vlastní třídu `CWinApp` a místo toho použijete instanci přímo. Tato technika je vhodná, pokud se rozhodnete ponechat všechny funkce pro vaši aplikaci v implementaci **main**.

> [!NOTE]
> Když vytvoří kontext aktivace pro sestavení, knihovna MFC používá prostředek manifestu poskytované uživatelský mno ství. Kontext aktivace je `AfxWinInit`vytvořen v aplikaci . Další informace naleznete [v tématu Podpora kontextů aktivace ve stavu modulu knihovny MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="see-also"></a>Viz také

[Makra a globální](mfc-macros-and-globals.md)\
[Třída CWinApp](cwinapp-class.md)\
[Třída CContextMenuManager](ccontextmenumanager-class.md)\
[Třída CWnd](cwnd-class.md)\
[Třída CFrameWndEx](cframewndex-class.md)\
[Třída CMFCToolBar](cmfctoolbar-class.md)\
[Třída CKeyboardManager](ckeyboardmanager-class.md)\
[Třída CMenuTearoffManager](cmenutearoffmanager-class.md)\
[Třída CMouseManager](cmousemanager-class.md)\
[Třída CShellManager](cshellmanager-class.md)\
[CUserToolsManager – třída](cusertoolsmanager-class.md)
