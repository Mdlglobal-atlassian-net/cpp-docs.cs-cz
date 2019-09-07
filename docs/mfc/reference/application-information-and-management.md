---
title: Informace o aplikacích a správa aplikací
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: 52e6dbaa07fa8343a07533f071d538d9f76b0f61
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741165"
---
# <a name="application-information-and-management"></a>Informace o aplikacích a správa aplikací

Při psaní aplikace vytvoříte jeden objekt odvozený [od sebe.](../../mfc/reference/cwinapp-class.md) V některých případech můžete chtít získat informace o tomto objektu mimo `CWinApp`objekt odvozený od objektu. Nebo budete možná potřebovat přístup k jiným globálním objektům "Manager".

Knihovna Microsoft Foundation Class poskytuje následující globální funkce, které vám pomůžou dosáhnout těchto úloh:

### <a name="application-information-and-management-functions"></a>Funkce pro informace o aplikaci a funkce správy

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|Vytvoří nové vlákno.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Ukazatel na správce globálních [místních nabídek](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Ukončí aktuální vlákno.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Projde řetěz prostředků a vyhledá konkrétní prostředek podle ID prostředku a typu prostředku. |
|[AfxFreeLibrary](#afxfreelibrary)|Sníží počet odkazů načteného modulu knihovny DLL (Dynamic-Link Library). Pokud počet odkazů dosáhne nuly, modul není namapován.|
|[AfxGetApp](#afxgetapp)|Vrátí ukazatel na jeden `CWinApp` objekt aplikace.|
|[AfxGetAppName](#afxgetappname)|Vrátí řetězec, který obsahuje název aplikace.|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Vrátí HINSTANCE představující tuto instanci aplikace.|
|[AfxGetMainWnd](#afxgetmainwnd)|Vrátí ukazatel na aktuální "hlavní" okno aplikace, která není typu OLE, nebo místní okno rámce serverové aplikace.|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Pomocí této funkce lze určit, zda aplikace přesměrovává přístup k registru do uzlu **HKEY_CURRENT_USER** ( **HKCU**).|
|[AfxGetResourceHandle](#afxgetresourcehandle)|Vrátí HINSTANCE ke zdroji výchozích prostředků aplikace. Toto použijte pro přímý přístup k prostředkům aplikace.|
|[AfxGetThread](#afxgetthread)|Načte ukazatel na aktuální objekt [CWinThread](../../mfc/reference/cwinthread-class.md) .|
|[AfxInitRichEdit](#afxinitrichedit)|Inicializuje ovládací prvek pro úpravy s formátováním verze 1,0 pro aplikaci.|
|[AfxInitRichEdit2](#afxinitrichedit2)|Inicializuje verzi 2,0 a pozdější ovládací prvek pro úpravy s formátováním pro aplikaci.|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Určuje, zda je dané okno objektem rozšířeného rámce.|
|[AfxIsMFCToolBar](#afxismfctoolbar)|Určuje, zda je dané okno objekt panelu nástrojů.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Ukazatel na globálního [správce klávesnice](ckeyboardmanager-class.md).|
|[AfxLoadLibrary](#afxloadlibrary)|Namapuje modul knihovny DLL a vrátí popisovač, který lze použít k získání adresy funkce knihovny DLL.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Ukazatel na globální [správce nabídky odtržené](cmenutearoffmanager-class.md).|
|[AfxMouseManager](#afxmousemanager)|Ukazatel na globálního [správce myši](cmousemanager-class.md).|
|[AfxRegisterClass](#afxregisterclass)|Zaregistruje třídu okna v knihovně DLL, která používá knihovnu MFC.|
|[AfxRegisterWndClass](#afxregisterwndclass)|Zaregistruje třídu okna Windows pro doplnění automaticky registrovaných funkcí MFC.|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Nastaví, zda aplikace přesměrovává přístup k registru do uzlu **HKEY_CURRENT_USER** ( **HKCU**).|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Nastaví popisovač HINSTANCE, kde jsou načteny výchozí prostředky aplikace.|
|[AfxShellManager](#afxshellmanager)|Ukazatel na globální [správce prostředí](cshellmanager-class.md). |
|[AfxSocketInit](#afxsocketinit)|Volá se v `CWinApp::InitInstance` přepsání pro inicializaci Windows Sockets.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Ukazatel na správce globálních [uživatelských nástrojů](cusertoolsmanager-class.md).|
|[AfxWinInit](#afxwininit)|Volá se funkcí poskytnutou `WinMain` knihovnou MFC jako součást inicializace [CWinApp](../../mfc/reference/cwinapp-class.md) aplikace založené na grafickém uživatelském rozhraní pro inicializaci knihovny MFC. Musí být volána přímo pro konzolové aplikace, které používají knihovnu MFC.|

##  <a name="afxbeginthread"></a>AfxBeginThread

Voláním této funkce vytvoříte nové vlákno.

```
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

*pfnThreadProc*<br/>
Odkazuje na řídící funkci pro pracovní vlákno. Nemůže mít hodnotu NULL. Tato funkce musí být deklarována takto:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*<br/>
RUNTIME_CLASS objektu odvozeného od typu [CWinThread](../../mfc/reference/cwinthread-class.md).

*pParam*<br/>
Parametr, který má být předán řídící funkci, jak je znázorněno v parametru pro deklaraci funkce v *pfnThreadProc*.

*nPriority*<br/>
Požadovaná priorita vlákna. Úplný seznam a popis dostupných priorit najdete v tématu [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v Windows SDK.

*nStackSize*<br/>
Určuje velikost zásobníku v bajtech pro nové vlákno. Pokud je nastaveno na hodnotu 0, výchozí velikost zásobníku bude stejná jako velikost zásobníku pro vytvoření vlákna.

*dwCreateFlags*<br/>
Určuje další příznak, který řídí vytvoření vlákna. Tento příznak může obsahovat jednu ze dvou hodnot:

- CREATE_SUSPENDED spustí vlákno s počtem pozastavení. Použijte CREATE_SUSPENDED, pokud chcete inicializovat jakákoli Členská data `CWinThread` objektu, jako je například [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) nebo všechny členy odvozené třídy před spuštěním vlákna. Po dokončení inicializace je nutné použít příkaz [CWinThread:: ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) ke spuštění vlákna spuštěného. Vlákno nebude spuštěno, dokud `CWinThread::ResumeThread` není voláno.

- **0** spustit vlákno ihned po vytvoření.

*lpSecurityAttrs*<br/>
Odkazuje na strukturu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , která určuje atributy zabezpečení pro vlákno. Pokud má hodnotu NULL, budou použity stejné atributy zabezpečení jako vytvoření vlákna. Další informace o této struktuře naleznete v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený objekt vlákna nebo hodnotu NULL, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

První forma `AfxBeginThread` vytvoří pracovní vlákno. Druhý formulář vytvoří vlákno, které může sloužit jako vlákno uživatelského rozhraní nebo jako pracovní vlákno.

`AfxBeginThread`Vytvoří nový `CWinThread` objekt, zavolá jeho funkci [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) , aby zahájil provádění vlákna, a vrátí ukazatel na vlákno. Kontroly jsou prováděny v rámci tohoto postupu, aby se zajistilo, že všechny objekty budou odstraněné správně, pokud nějaká část vytvoření selže. Chcete-li ukončit vlákno, zavolejte [AfxEndThread](#afxendthread) z vlákna nebo se vraťte z řídicí funkce pracovního vlákna.

Multithreading musí povolit aplikace. v opačném případě se tato funkce nezdaří. Další informace o povolení multithreadingu naleznete v tématu [/MD,/MT,/LD (použití běhové knihovny)](../../build/reference/md-mt-ld-use-run-time-library.md) v části *Visual C++ Compiler možnosti*.

Další informace o `AfxBeginThread`najdete v článcích [Multithreading: Vytváření pracovních vláken](../../parallel/multithreading-creating-worker-threads.md) a [Multithreading: Vytváření vláken](../../parallel/multithreading-creating-user-interface-threads.md)uživatelského rozhraní.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CSocket –:: Attach](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxcontextmenumanager"></a> AfxContextMenuManager

Ukazatel na správce globálních [místních nabídek](ccontextmenumanager-class.md).

### <a name="syntax"></a>Syntaxe

```
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxcontextmenumanager. h

##  <a name="afxendthread"></a>AfxEndThread

Voláním této funkce ukončíte aktuálně spuštěné vlákno.

```
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>Parametry

*nExitCode*<br/>
Určuje ukončovací kód vlákna.

*bDelete*<br/>
Odstraní objekt vlákna z paměti.

### <a name="remarks"></a>Poznámky

Musí být volána v rámci vlákna k ukončení.

Další informace o `AfxEndThread`naleznete v článku [Multithreading: Ukončování vláken](../../parallel/multithreading-terminating-threads.md).

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
Použijte `AfxFindResourceHandle` k procházení řetězce prostředků a vyhledání konkrétního prostředku podle ID prostředku a typu prostředku.

### <a name="syntax"></a>Syntaxe

```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec obsahující ID prostředku.
*lpszType*<br/>
Ukazatel na typ prostředku. Seznam typů prostředků naleznete v tématu [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Popisovač modulu, který obsahuje prostředek.

### <a name="remarks"></a>Poznámky

`AfxFindResourceHandle`najde konkrétní prostředek a vrátí popisovač modulu, který obsahuje prostředek. Prostředek může být v libovolné rozšiřující knihovně MFC DLL, kterou jste načetli. `AfxFindResourceHandle`oznamuje vám, že jeden má prostředek.

Moduly se prohledávají v tomto pořadí:

1. Hlavní modul (Pokud se jedná o rozšiřující knihovnu MFC DLL).

1. Moduly, které nejsou systémové.

1. Moduly konkrétního jazyka.

1. Hlavní modul (Pokud se jedná o systémovou knihovnu DLL).

1. Systémové moduly.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="afxfreelibrary"></a>  AfxFreeLibrary

`AfxFreeLibrary` A`AfxLoadLibrary` Udržujte počet odkazů pro každý načtený modul knihovny.

```
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Parametry

*hInstLib*<br/>
Popisovač načteného modulu knihovny. [AfxLoadLibrary](#afxloadlibrary) vrací tento popisovač.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je funkce úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

`AfxFreeLibrary`sníží počet odkazů načteného modulu DLL (Dynamic-Link Library). Pokud počet odkazů dosáhne nuly, modul není namapován z adresního prostoru volajícího procesu a popisovač již není platný. Tento počet odkazů se zvýší pokaždé, `AfxLoadLibrary` když se zavolá.

Před zrušením mapování modulu knihovny umožňuje systému, aby se knihovna DLL odpojila od procesů, které ji používají. Díky tomu má knihovna DLL možnost vyčistit prostředky přidělené jménem aktuálního procesu. Po návratu funkce vstupního bodu se modul knihovny odebere z adresního prostoru aktuálního procesu.

Použijte `AfxLoadLibrary` k namapování modulu knihovny DLL.

Nezapomeňte použít `AfxFreeLibrary` a `AfxLoadLibrary` (namísto funkcí `FreeLibrary` Win32 a `LoadLibrary`), pokud vaše aplikace používá více vláken. Pomocí `AfxLoadLibrary` a`AfxFreeLibrary` zajistí, že kód spuštění a vypnutí, který se spustí, když je načtena knihovna DLL MFC a uvolněna, není poškozen globální stav knihovny MFC.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Požadavky

  **Header** AFXDLL_. h

##  <a name="afxgetapp"></a>AfxGetApp

Ukazatel vrácený touto funkcí lze použít pro přístup k informacím o aplikaci, jako je například hlavní kód pro odeslání zprávy nebo horní okno.

```
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jeden `CWinApp` objekt pro aplikaci.

### <a name="remarks"></a>Poznámky

Pokud tato metoda vrátí hodnotu NULL, může to znamenat, že hlavní okno aplikace ještě není zcela inicializováno. Může to také znamenat problém.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxgetappname"></a>  AfxGetAppName

Řetězec vrácený touto funkcí lze použít pro diagnostické zprávy nebo jako kořenový adresář pro dočasné názvy řetězců.

```
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Návratová hodnota

Řetězec zakončený hodnotou null obsahující název aplikace

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxgetinstancehandle"></a>  AfxGetInstanceHandle

Tato funkce umožňuje načíst popisovač instance aktuální aplikace.

```
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Návratová hodnota

HINSTANCE na aktuální instanci aplikace. Pokud je volána z knihovny DLL propojené s verzí USRDLL knihovny MFC, je vrácena HINSTANCE na knihovnu DLL.

### <a name="remarks"></a>Poznámky

`AfxGetInstanceHandle`vždycky vrátí HINSTANCE spustitelného souboru (. EXE), pokud není volána v rámci knihovny DLL propojené s verzí USRDLL knihovny MFC. V tomto případě vrátí HINSTANCE do knihovny DLL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxgetmainwnd"></a>  AfxGetMainWnd

Pokud je vaše aplikace serverem OLE, zavolejte tuto funkci, aby načetla ukazatel na aktivní hlavní okno aplikace namísto přímo odkazující na člena [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) objektu aplikace.

```
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Návratová hodnota

Pokud má server objekt, který je místně aktivní uvnitř kontejneru a tento kontejner je aktivní, vrátí tato funkce ukazatel na objekt okna rámce, který obsahuje místní aktivní dokument.

Pokud není žádný objekt, který je místně aktivní v rámci kontejneru, nebo vaše aplikace není serverem OLE, tato funkce jednoduše vrátí *m_pMainWnd* objektu aplikace.

Pokud `AfxGetMainWnd` je volána z primárního vlákna aplikace, vrátí hlavní okno aplikace podle výše uvedených pravidel. Pokud je funkce volána ze sekundárního vlákna v aplikaci, vrátí funkce hlavní okno přidružené k vláknu, které volání provedlo.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace není serverem OLE, pak volání této funkce je ekvivalentní přímo odkazující na člena *m_pMainWnd* objektu aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxgetperuserregistration"></a>  AfxGetPerUserRegistration

Pomocí této funkce lze určit, zda aplikace přesměrovává přístup k registru do uzlu **HKEY_CURRENT_USER** ( **HKCU**).

```
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE označuje, že informace registru jsou směrovány na uzel HKCU; Hodnota FALSE znamená, že aplikace zapisuje informace registru do výchozího uzlu. Výchozí uzel je **HKEY_CLASSES_ROOT** ( **HKCR**).

### <a name="remarks"></a>Poznámky

Pokud povolíte přesměrování registru, rozhraní přesměruje přístup z **HKCR** do **HKEY_CURRENT_USER\Software\Classes**. Přesměrování ovlivňují pouze architektury MFC a ATL.

Chcete-li změnit, zda aplikace přesměruje přístup k registru, použijte [AfxSetPerUserRegistration](#afxsetperuserregistration).

### <a name="requirements"></a>Požadavky

  **Header** afxstat_. h

##  <a name="afxgetresourcehandle"></a>  AfxGetResourceHandle

Použijte popisovač HINSTANCE vrácený touto funkcí pro přímý přístup k prostředkům aplikace, například při volání funkce `FindResource`Windows.

```
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Návratová hodnota

HINSTANCE popisovač, kde jsou načteny výchozí prostředky aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxgetthread"></a>  AfxGetThread

Voláním této funkce získáte ukazatel na objekt [CWinThread](../../mfc/reference/cwinthread-class.md) představující aktuálně spuštěné vlákno.

```
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuálně spuštěné vlákno; jinak NULL.

### <a name="remarks"></a>Poznámky

Musí být volána v rámci požadovaného vlákna.

> [!NOTE]
>  Pokud provádíte přenos projektu knihovny MFC voláním `AfxGetThread` z vizuálů C++ verze 4,2, 5,0 nebo 6,0, `AfxGetThread` volání [AfxGetApp](#afxgetapp) , pokud není nalezeno žádné vlákno. V novějších verzích kompilátoru vrátí hodnotu null `AfxGetThread` , pokud nebylo nalezeno žádné vlákno. Pokud chcete vlákno aplikace, je nutné volat `AfxGetApp`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxinitrichedit"></a>AfxInitRichEdit

Voláním této funkce nainicializujete ovládací prvek RichEdit pro úpravy (verze 1,0) pro aplikaci.

```
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Poznámky

Tato funkce je k dispozici kvůli zpětné kompatibilitě. Nové aplikace by měly používat [AfxInitRichEdit2](#afxinitrichedit2).

`AfxInitRichEdit`Načte RICHED32. Knihovna DLL pro inicializaci verze 1,0 ovládacího prvku RichEdit Chcete-li použít verzi 2,0 a 3,0 ovládacího prvku Rich Edit, knihovny RICHED20. Knihovna DLL musí být načtena. To je dosaženo voláním [AfxInitRichEdit2](#afxinitrichedit2).

Chcete-li aktualizovat ovládací prvky s bohatým úpravou ve stávajících vizuálních C++ aplikacích na verzi 2,0, otevřete. Soubor RC jako text, změňte název třídy každého ovládacího prvku Rich Edit z "RICHEDIT" na "RichEdit20a". Pak nahraďte volání `AfxInitRichEdit` pomocí `AfxInitRichEdit2`.

Tato funkce také inicializuje knihovnu běžných ovládacích prvků, pokud knihovna ještě nebyla inicializována pro daný proces. Použijete-li ovládací prvek RichEdit přímo z aplikace MFC, měli byste zavolat tuto funkci, aby se zajistilo, že knihovna MFC správně inicializovala modul runtime ovládacího prvku Rich Edit. Pokud voláte metodu create pro [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView –](../../mfc/reference/cricheditview-class.md)nebo [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), obvykle není nutné volat tuto funkci, ale v některých případech může být nutné.

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxinitrichedit2"></a>  AfxInitRichEdit2

Voláním této funkce inicializujete ovládací prvek RichEdit (verze 2,0 a novější) pro aplikaci.

```
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Poznámky

Voláním této funkce načtete knihovny RICHED20. Knihovna DLL a inicializace verze 2,0 ovládacího prvku RichEdit. Pokud voláte metodu create pro [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView –](../../mfc/reference/cricheditview-class.md)nebo [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), obvykle není nutné volat tuto funkci, ale v některých případech může být nutné.

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

  ## <a name="afxisextendedframeclass"></a>AfxIsExtendedFrameClass
Určuje, zda je dané okno objektem rozšířeného rámce.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Ukazatel na objekt, který je odvozen z `CWnd`.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadané okno Rozšířený objekt Frame; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu TRUE, pokud *pWnd* odvodí z jedné z následujících tříd:

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

Tato metoda je užitečná v případě, že je nutné ověřit, zda je parametrem funkce nebo metody rozšířené okno rámce.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXPRIV. h

## <a name="afxismfctoolbar"></a> AfxIsMFCToolBar

Určuje, zda je dané okno objekt panelu nástrojů.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Ukazatel na objekt, který je odvozen z `CWnd`.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadané okno objekt panelu nástrojů; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrací `TRUE` , pokud je *pWnd* odvozen `CMFCToolBar`z. Tato metoda je užitečná v případě, že je nutné ověřit, zda je `CMFCToolBar` parametrem funkce nebo metody objekt.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXPRIV. h

## <a name="afxkeyboardmanager"></a> AfxKeyboardManager

Ukazatel na globálního [správce klávesnice](ckeyboardmanager-class.md).

### <a name="syntax"></a>Syntaxe

```
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxkeyboardmanager. h

##  <a name="afxloadlibrary"></a>AfxLoadLibrary

Použijte `AfxLoadLibrary` k namapování modulu knihovny DLL.

```
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Parametry

*lpszModuleName*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název modulu (buď. Knihovna DLL nebo. Soubor EXE). Zadaný název je název souboru modulu.

Pokud řetězec Určuje cestu, ale soubor v zadaném adresáři neexistuje, funkce se nezdařila.

Pokud není zadaná cesta a přípona názvu souboru se vynechá, použije se výchozí přípona. Knihovna DLL je připojena. Řetězec filename však může obsahovat znak koncového bodu (.), který označuje, že název modulu nemá žádné rozšíření. Pokud není zadána žádná cesta, funkce vyhledá soubor v následujícím pořadí:

- Adresář, ze kterého byla aplikace načtena.

- Aktuální adresář.

- **Windows 95/98:** Systémový adresář systému Windows. **Windows NT:** 32 systémový adresář systému Windows. Název tohoto adresáře je SYSTEM32.

- **Jenom Windows NT:** 16bitový systémový adresář Windows. Neexistuje žádná funkce Win32, která získá cestu k tomuto adresáři, ale je prohledávána. Název tohoto adresáře je SYSTEM.

- Adresář Windows.

- Adresáře, které jsou uvedeny v proměnné prostředí PATH.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je popisovačem modulu. Pokud dojde k chybě funkce, vrácená hodnota je NULL.

### <a name="remarks"></a>Poznámky

Vrátí popisovač, který lze použít v [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) pro získání adresy funkce knihovny DLL. `AfxLoadLibrary`lze také použít k mapování jiných spustitelných modulů.

Každý proces udržuje počet odkazů pro každý načtený modul knihovny. Tento počet odkazů se zvýší pokaždé, `AfxLoadLibrary` když se zavolá a při `AfxFreeLibrary` každém volání se sníží. Pokud počet odkazů dosáhne nuly, modul není namapován z adresního prostoru volajícího procesu a popisovač již není platný.

Nezapomeňte použít `AfxLoadLibrary` a `AfxFreeLibrary` (namísto funkcí `LoadLibrary` Win32 a `FreeLibrary`), pokud vaše aplikace používá více vláken a v případě, že dynamicky načítá rozšiřující knihovnu MFC DLL. Pomocí `AfxLoadLibrary` a`AfxFreeLibrary` si zajistěte, aby kód spuštění a vypnutí, který se spustí při načtení a uvolnění knihovny MFC DLL, není poškozen globálním stavem MFC.

Použití `AfxLoadLibrary` v aplikaci vyžaduje dynamické propojení s knihovnou DLL knihovny MFC; hlavičkový soubor pro `AfxLoadLibrary`, Afxdll_. h, je zahrnut pouze v případě, že je knihovna MFC propojena s aplikací jako knihovnou DLL. Jedná se o návrh, protože je nutné propojit s knihovnou DLL verze knihovny MFC pro použití nebo vytvoření rozšiřujících knihoven DLL knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** AFXDLL_. h

## <a name="afxmenutearoffmanager"></a> AfxMenuTearOffManager

Ukazatel na globální [správce nabídky odtržené](cmenutearoffmanager-class.md).

### <a name="syntax"></a>Syntaxe

```
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmenutearoffmanager. h

## <a name="afxmousemanager"></a>  AfxMouseManager

Ukazatel na globálního [správce myši](cmousemanager-class.md).

### <a name="syntax"></a>Syntaxe

```
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmousemanager. h

##  <a name="afxregisterclass"></a>  AfxRegisterClass

Pomocí této funkce lze registrovat třídy oken v knihovně DLL, která používá knihovnu MFC.

```
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Parametry

*lpWndClass*<br/>
Ukazatel na strukturu [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) obsahující informace o třídě okna, která má být zaregistrována. Další informace o této struktuře naleznete v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je třída úspěšně registrována; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Použijete-li tuto funkci, třída je automaticky zrušena při uvolnění knihovny DLL.

V sestaveních `AfxRegisterClass` bez knihovny DLL je identifikátor definován jako makro, které je mapováno na funkci `RegisterClass`systému Windows, protože třídy registrované v aplikaci jsou automaticky odregistrovány. Použijete `AfxRegisterClass` `RegisterClass`-li místo, lze kód použít bez změny v aplikaci i v knihovně DLL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxregisterwndclass"></a>  AfxRegisterWndClass

Umožňuje registrovat vlastní třídy okna.

```
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Parametry

*nClassStyle*<br/>
Určuje styl třídy systému Windows nebo kombinaci stylů vytvořené pomocí operátoru bitového operátoru OR ( **&#124;** ) pro třídu okna. Seznam stylů třídy naleznete v tématu struktura [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) v Windows SDK. Pokud má hodnotu NULL, výchozí hodnoty se nastaví takto:

- Nastaví styl myši na CS_DBLCLKS, který odešle dvojitým kliknutím na zprávy do okna, když uživatel dvakrát klikne na myš.

- Nastaví styl ukazatele šipky na IDC_ARROW Windows Standard.

- Nastaví štětec pozadí na hodnotu NULL, takže okno neodstraní své pozadí.

- Nastaví ikonu na standardní ikonu loga Windows mávající-Flag.

*hCursor*<br/>
Určuje popisovač pro prostředek kurzoru, který se má nainstalovat do každého okna vytvořeného z třídy okna. Pokud použijete výchozí **hodnotu 0**, získáte standardní IDC_ARROW kurzor.

*hbrBackground*<br/>
Určuje popisovač prostředku štětce, který se má nainstalovat do každého okna vytvořeného z třídy okna. Použijete-li výchozí **hodnotu 0**, budete mít hodnotu null štětce na pozadí a vaše okno ve výchozím nastavení nevymaže pozadí při zpracování [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd).

*hIcon*<br/>
Určuje popisovač pro prostředek ikony, který se má nainstalovat do každého okna vytvořeného z třídy okna. Pokud použijete výchozí **hodnotu 0**, zobrazí se ikona pro logo Windows Standard, mávající-Flag.

### <a name="return-value"></a>Návratová hodnota

Řetězec zakončený hodnotou null obsahující název třídy. Můžete předat název `Create` této třídy členské funkci v `CWnd` nebo jiné třídy odvozené od **typu CWnd**pro vytvoření okna. Název je vygenerován knihovna Microsoft Foundation Class.

> [!NOTE]
>  Vrácená hodnota je ukazatel na statickou vyrovnávací paměť. Pokud chcete tento řetězec uložit, přiřaďte ho `CString` k proměnné.

### <a name="remarks"></a>Poznámky

Knihovna Microsoft Foundation Class automaticky registruje několik standardních tříd okna za vás. Tuto funkci zavolejte, pokud chcete registrovat vlastní třídy oken.

Název zaregistrovaný pro třídu `AfxRegisterWndClass` závisí výhradně na parametrech. Pokud voláte `AfxRegisterWndClass` víckrát se stejnými parametry, registruje pouze třídu při prvním volání. Následná volání `AfxRegisterWndClass` s identickými parametry jednoduše vracejí již registrovanou hodnotu ClassName.

Pokud voláte `AfxRegisterWndClass` více tříd odvozených od typu CWnd se stejnými parametry, místo získání samostatné třídy okna pro každou třídu, každá třída sdílí stejnou třídu okna. To může způsobit problémy, pokud je použit styl třídy CS_CLASSDC. Místo více tříd okna CS_CLASSDC se ukončí jedna třída CS_CLASSDC oken a všechna C++ okna, která tuto třídu používají, sdílejí stejný řadič domény. Chcete-li se tomuto problému vyhnout, zavolejte [AfxRegisterClass](#afxregisterclass) k registraci třídy.

Přečtěte si technickou [poznámku TN001: Registrace](../../mfc/tn001-window-class-registration.md) třídy okna pro další informace o registraci třídy okna `AfxRegisterWndClass` a funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxsetperuserregistration"></a>  AfxSetPerUserRegistration

Nastaví, zda aplikace přesměrovává přístup k registru do uzlu **HKEY_CURRENT_USER** ( **HKCU**).

```
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro Hodnota TRUE označuje, že informace registru jsou směrovány na uzel HKCU; Hodnota FALSE znamená, že aplikace zapisuje informace registru do výchozího uzlu. Výchozí uzel je **HKEY_CLASSES_ROOT** ( **HKCR**).

### <a name="remarks"></a>Poznámky

Před Windows Vista používaly aplikace, které se k registru získaly, obvykle uzel **HKEY_CLASSES_ROOT** . V systému Windows Vista nebo novějších operačních systémech je však nutné spustit aplikaci v režimu zvýšené úrovně, aby bylo možné zapisovat do HKCR.

Tato metoda umožňuje vaší aplikaci číst a zapisovat do registru bez spuštění v režimu zvýšeného oprávnění přesměrováním přístupu k registru z HKCR na HKCU. Další informace najdete v tématu [stránky vlastností linkeru](../../build/reference/linker-property-pages.md).

Pokud povolíte přesměrování registru, rozhraní přesměruje přístup z HKCR do **HKEY_CURRENT_USER\Software\Classes**. Přesměrování ovlivňují pouze architektury MFC a ATL.

Výchozí implementace přistupuje k registru v HKCR.

### <a name="requirements"></a>Požadavky

  **Header** afxstat_. h

##  <a name="afxsetresourcehandle"></a>AfxSetResourceHandle

Pomocí této funkce lze nastavit popisovač HINSTANCE, který určuje, kde jsou načteny výchozí prostředky aplikace.

```
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Parametry

*hInstResource*<br/>
Obslužná rutina instance nebo modulu. EXE nebo soubor DLL, ze kterého jsou načteny prostředky aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxshellmanager"></a>  AfxShellManager

Ukazatel na globální [správce prostředí](cshellmanager-class.md).

### <a name="syntax"></a>Syntaxe

```
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxshellmanager. h

##  <a name="afxsocketinit"></a>AfxSocketInit

Voláním této funkce v `CWinApp::InitInstance` přepsání inicializujete Windows Sockets.

```
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Parametry

*lpwsaData*<br/>
Ukazatel na strukturu [WSADATA –](/windows/win32/api/winsock2/ns-winsock2-wsadata) . Pokud *lpwsaData* není rovno hodnotě null, pak je adresa `WSADATA` struktury vyplněna voláním metody. `WSAStartup` Tato funkce také zajistí, `WSACleanup` že je volána za vás před ukončením aplikace.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Při použití soketů MFC v sekundárních vláknech v staticky propojené aplikaci MFC je nutné zavolat `AfxSocketInit` do každého vlákna, které používá sokety k inicializaci knihoven soketu. Ve výchozím nastavení `AfxSocketInit` je volána pouze v primárním vlákně.

### <a name="requirements"></a>Požadavky

  **Header** AfxSock. h

## <a name="afxusertoolsmanager"></a>  AfxUserToolsManager

Ukazatel na správce globálních [uživatelských nástrojů](cusertoolsmanager-class.md).

### <a name="syntax"></a>Syntaxe

```
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxusertoolsmanager. h

##  <a name="afxwininit"></a>AfxWinInit

Tato funkce je volána funkcí poskytnutou `WinMain` knihovnou MFC jako součást inicializace [CWinApp](../../mfc/reference/cwinapp-class.md) aplikace založené na grafickém uživatelském rozhraní pro inicializaci knihovny MFC.

```
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Popisovač aktuálně spuštěného modulu.

*hPrevInstance*<br/>
Popisovač předchozí instance aplikace. Pro aplikaci založenou na Win32 má tento parametr vždycky **hodnotu null**.

*lpCmdLine*<br/>
Odkazuje na řetězec zakončený hodnotou null určující příkazový řádek pro aplikaci.

*nCmdShow*<br/>
Určuje, jak se bude zobrazovat hlavní okno aplikace grafického uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Pro konzolovou aplikaci, která nepoužívá funkci poskytnutou `WinMain` knihovnou MFC, je nutné zavolat `AfxWinInit` přímo k inicializaci knihovny MFC.

Pokud voláte `AfxWinInit` sami, měli byste deklarovat instanci `CWinApp` třídy. Pro konzolovou aplikaci se můžete rozhodnout neodvozovat vlastní třídu od `CWinApp` a místo toho použít `CWinApp` instanci přímo. Tato technika je vhodná, pokud se rozhodnete ponechat všechny funkce aplikace v implementaci **Main**.

> [!NOTE]
>  Při vytvoření aktivačního kontextu pro sestavení používá knihovna MFC prostředek manifestu poskytovaný modulem uživatele. Aktivační kontext je vytvořen v `AfxWinInit`. Další informace najdete v tématu [Podpora kontextů aktivace ve stavu modulu MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[CWinApp – třída](cwinapp-class.md)<br/>
[CContextMenuManager – třída](ccontextmenumanager-class.md)<br/>
[CWnd – třída](cwnd-class.md)<br/>
[CFrameWndEx – třída](cframewndex-class.md)<br/>
[CMFCToolBar – třída](cmfctoolbar-class.md)<br/>
[CKeyboardManager – třída](ckeyboardmanager-class.md)<br/>
[CMenuTearOffManager – třída](cmenutearoffmanager-class.md)<br/>
[CMouseManager – třída](cmousemanager-class.md)<br/>
[CShellManager – třída](cshellmanager-class.md)<br/>
[CUserToolsManager – třída](cusertoolsmanager-class.md)
