---
title: Informace o aplikacích a správa aplikací
description: Odkaz na informace o aplikaci a funkce správy knihovny Microsoft Foundation Class (MFC).
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: c372f43bc5184349e70f29b6c0ae6a490f2102ed
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419159"
---
# <a name="application-information-and-management"></a>Informace o aplikacích a správa aplikací

Při psaní aplikace vytvoříte jeden objekt odvozený [od sebe.](../../mfc/reference/cwinapp-class.md) V některých případech můžete chtít získat informace o tomto objektu mimo objekt odvozený od `CWinApp`. Nebo budete možná potřebovat přístup k jiným globálním objektům "Manager".

Knihovna Microsoft Foundation Class poskytuje následující globální funkce, které vám pomůžou dosáhnout těchto úloh:

## <a name="application-information-and-management-functions"></a>Funkce pro informace o aplikaci a funkce správy

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|Vytvoří nové vlákno.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Ukazatel na správce globálních [místních nabídek](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Ukončí aktuální vlákno.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Projde řetěz prostředků a vyhledá konkrétní prostředek podle ID prostředku a typu prostředku. |
|[AfxFreeLibrary](#afxfreelibrary)|Sníží počet odkazů načteného modulu DLL (Dynamic-Link Library). Pokud počet odkazů dosáhne nuly, modul není namapován.|
|[AfxGetApp](#afxgetapp)|Vrátí ukazatel na objekt jednoho `CWinApp` aplikace.|
|[AfxGetAppName](#afxgetappname)|Vrátí řetězec, který obsahuje název aplikace.|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Vrátí HINSTANCE představující tuto instanci aplikace.|
|[AfxGetMainWnd](#afxgetmainwnd)|Vrátí ukazatel na aktuální "hlavní" okno aplikace, která není typu OLE, nebo místní okno rámce serverové aplikace.|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Pomocí této funkce lze určit, zda aplikace přesměrovává přístup k registru do uzlu **HKEY_CURRENT_USER** (**HKCU**).|
|[AfxGetResourceHandle](#afxgetresourcehandle)|Vrátí HINSTANCE ke zdroji výchozích prostředků aplikace. Použijte pro přímý přístup k prostředkům aplikace.|
|[AfxGetThread](#afxgetthread)|Načte ukazatel na aktuální objekt [CWinThread](../../mfc/reference/cwinthread-class.md) .|
|[AfxInitRichEdit](#afxinitrichedit)|Inicializuje ovládací prvek pro úpravy s formátováním verze 1,0 pro aplikaci.|
|[AfxInitRichEdit2](#afxinitrichedit2)|Inicializuje verzi 2,0 a pozdější ovládací prvek pro úpravy s formátováním pro aplikaci.|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Určuje, zda je dané okno objektem rozšířeného rámce.|
|[AfxIsMFCToolBar](#afxismfctoolbar)|Určuje, zda je dané okno objekt panelu nástrojů.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Ukazatel na globálního [správce klávesnice](ckeyboardmanager-class.md).|
|[AfxLoadLibrary](#afxloadlibrary)|Namapuje modul knihovny DLL a vrátí popisovač, který lze použít k získání adresy funkce knihovny DLL.|
|[AfxLoadLibraryEx](#afxloadlibraryex)|Namapuje modul knihovny DLL pomocí zadaných možností a vrátí popisovač, který lze použít k získání adresy funkce knihovny DLL.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Ukazatel na globální [vytrhnoutelné nabídky Správce](cmenutearoffmanager-class.md).|
|[AfxMouseManager](#afxmousemanager)|Ukazatel na globálního [správce myši](cmousemanager-class.md).|
|[AfxRegisterClass](#afxregisterclass)|Zaregistruje třídu okna v knihovně DLL, která používá knihovnu MFC.|
|[AfxRegisterWndClass –](#afxregisterwndclass)|Zaregistruje třídu okna systému Windows, aby doplnila automaticky registrované knihovny MFC.|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Nastaví, zda aplikace přesměrovává přístup k registru do uzlu **HKEY_CURRENT_USER** (**HKCU**).|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Nastaví popisovač HINSTANCE, kde jsou načteny výchozí prostředky aplikace.|
|[AfxShellManager](#afxshellmanager)|Ukazatel na globální [správce prostředí](cshellmanager-class.md). |
|[AfxSocketInit](#afxsocketinit)|Volá se v přepsání `CWinApp::InitInstance` pro inicializaci Windows Sockets.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Ukazatel na správce globálních [uživatelských nástrojů](cusertoolsmanager-class.md).|
|[AfxWinInit](#afxwininit)|Volá se funkcí `WinMain` poskytnutou knihovnou MFC jako součást inicializace [CWinApp](../../mfc/reference/cwinapp-class.md) aplikace založené na grafickém uživatelském rozhraní pro inicializaci knihovny MFC. Musí být volána přímo pro konzolové aplikace, které používají knihovnu MFC.|

## <a name="afxbeginthread"></a>AfxBeginThread

Voláním této funkce vytvoříte nové vlákno.

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
Odkazuje na řídící funkci pro pracovní vlákno. Ukazatel nemůže mít hodnotu NULL. Tato funkce musí být deklarována takto:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*\
RUNTIME_CLASS objektu odvozeného od typu [CWinThread](../../mfc/reference/cwinthread-class.md).

*pParam*\
Parametr, který se má předat řídící funkci

*nPriority*\
Priorita, která se má nastavit pro vlákno. Úplný seznam a popis dostupných priorit najdete v tématu [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v Windows SDK.

*nStackSize*\
Určuje velikost zásobníku v bajtech pro nové vlákno. Pokud je nastaveno na hodnotu 0, výchozí velikost zásobníku bude stejná jako velikost zásobníku pro vytvoření vlákna.

*dwCreateFlags*\
Určuje další příznak, který řídí vytvoření vlákna. Tento příznak může obsahovat jednu ze dvou hodnot:

- CREATE_SUSPENDED spustit vlákno s počtem pozastavení jednoho. Použijte CREATE_SUSPENDED, pokud chcete inicializovat jakákoli Členská data objektu `CWinThread`, jako je [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) nebo jakékoli členy odvozené třídy, před spuštěním vlákna. Po dokončení inicializace je nutné použít příkaz [CWinThread:: ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) ke spuštění vlákna spuštěného. Vlákno se neprovede, dokud se nevolá `CWinThread::ResumeThread`.

- **0** spustit vlákno ihned po vytvoření.

*lpSecurityAttrs*\
Odkazuje na strukturu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , která určuje atributy zabezpečení pro vlákno. Pokud má hodnotu NULL, jsou použity stejné atributy zabezpečení jako vytvoření vlákna. Další informace o této struktuře naleznete v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený objekt vlákna nebo hodnotu NULL, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

První tvar `AfxBeginThread` vytvoří pracovní vlákno. Druhý formulář vytvoří vlákno, které může sloužit jako vlákno uživatelského rozhraní nebo jako pracovní vlákno.

`AfxBeginThread` vytvoří nový objekt `CWinThread`, zavolá jeho funkci [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) , aby zahájil provádění vlákna, a vrátí ukazatel na vlákno. Kontroly jsou prováděny v rámci tohoto postupu, aby se zajistilo, že všechny objekty budou odstraněné správně, pokud nějaká část vytvoření selže. Chcete-li ukončit vlákno, zavolejte [AfxEndThread](#afxendthread) z vlákna nebo se vraťte z řídicí funkce pracovního vlákna.

Multithreading musí povolit aplikace. v opačném případě se tato funkce nezdaří. Další informace o povolení multithreadingu naleznete v tématu [/MD,/MT,/LD (použití běhové knihovny)](../../build/reference/md-mt-ld-use-run-time-library.md).

Další informace o `AfxBeginThread`naleznete v článcích [Multithreading: vytváření pracovních vláken](../../parallel/multithreading-creating-worker-threads.md) a [Multithreading: vytváření vláken uživatelského rozhraní](../../parallel/multithreading-creating-user-interface-threads.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CSocket –:: Attach](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxcontextmenumanager"></a>AfxContextMenuManager

Ukazatel na správce globálních [místních nabídek](ccontextmenumanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxcontextmenumanager. h

## <a name="afxendthread"></a>AfxEndThread

Voláním této funkce ukončíte aktuálně spuštěné vlákno.

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>Parametry

*nExitCode*\
Určuje ukončovací kód vlákna.

*bDelete*\
Odstraní objekt vlákna z paměti.

### <a name="remarks"></a>Poznámky

Musí být volána v rámci vlákna k ukončení.

Další informace o `AfxEndThread`naleznete v článku [Multithreading: ukončení vláken](../../parallel/multithreading-terminating-threads.md).

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle

Pomocí `AfxFindResourceHandle` Projděte řetězec prostředku a vyhledejte konkrétní prostředek podle ID prostředku a typu prostředku.

### <a name="syntax"></a>Syntaxe

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Parametry

*lpszName*\
Ukazatel na řetězec obsahující ID prostředku.
*lpszType*\
Ukazatel na typ prostředku. Seznam typů prostředků naleznete v tématu [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Popisovač modulu, který obsahuje prostředek.

### <a name="remarks"></a>Poznámky

`AfxFindResourceHandle` najde konkrétní prostředek a vrátí popisovač modulu, který obsahuje prostředek. Prostředek může být v jakémkoli rozšiřující knihovně DLL knihovny MFC, která je načtena. `AfxFindResourceHandle` oznamuje, který z nich má prostředek.

Moduly se prohledávají v tomto pořadí:

1. Hlavní modul, pokud se jedná o rozšiřující knihovnu MFC DLL.

1. Moduly, které nejsou systémové.

1. Moduly konkrétního jazyka.

1. Hlavní modul, pokud se jedná o systémovou knihovnu DLL.

1. Systémové moduly.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

## <a name="afxfreelibrary"></a>AfxFreeLibrary

Jak `AfxFreeLibrary`, tak `AfxLoadLibrary` udržovat počet odkazů pro každý načtený modul knihovny.

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Parametry

*hInstLib*\
Popisovač načteného modulu knihovny. [AfxLoadLibrary](#afxloadlibrary) vrací tento popisovač.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je funkce úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

`AfxFreeLibrary` sníží počet odkazů načteného modulu DLL (Dynamic-Link Library). Pokud počet odkazů dosáhne nuly, modul není namapován z adresního prostoru volajícího procesu a popisovač již není platný. Tento počet odkazů se zvýší pokaždé, když je zavolána `AfxLoadLibrary`.

Před zrušením mapování modulu knihovny umožňuje systému, aby se knihovna DLL odpojila od procesů, které ji používají. Díky tomu má knihovna DLL možnost vyčistit prostředky přidělené pro aktuální proces. Po návratu funkce vstupního bodu se modul knihovny odebere z adresního prostoru aktuálního procesu.

K namapování modulu DLL použijte `AfxLoadLibrary`.

Nezapomeňte použít `AfxFreeLibrary` a `AfxLoadLibrary` (namísto funkcí Win32 `FreeLibrary` a `LoadLibrary`), pokud vaše aplikace používá více vláken. Pomocí `AfxLoadLibrary` a `AfxFreeLibrary` je zajištěno, že spouštěcí a ukončovací kód, který se spustí, když je načtena a uvolněna knihovna MFC DLL, není poškozen globální stav knihovny MFC.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Požadavky

  Afxdll_ **záhlaví** . h

## <a name="afxgetapp"></a>AfxGetApp

Ukazatel vrácený touto funkcí lze použít pro přístup k informacím o aplikaci, jako je například hlavní kód pro odeslání zprávy nebo horní okno.

```cpp
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jeden objekt `CWinApp` pro aplikaci.

### <a name="remarks"></a>Poznámky

Pokud tato metoda vrátí hodnotu NULL, může to znamenat, že hlavní okno aplikace ještě není zcela inicializováno. Může to také znamenat problém.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxgetappname"></a>AfxGetAppName

Vrácený řetězec lze použít pro diagnostické zprávy nebo jako kořenový adresář pro dočasné názvy řetězců.

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Návratová hodnota

Řetězec zakončený hodnotou null obsahující název aplikace

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxgetinstancehandle"></a>AfxGetInstanceHandle

Tato funkce umožňuje načíst popisovač instance aktuální aplikace.

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Návratová hodnota

HINSTANCE na aktuální instanci aplikace. Pokud je volána z knihovny DLL propojené s verzí USRDLL knihovny MFC, je vrácena HINSTANCE na knihovnu DLL.

### <a name="remarks"></a>Poznámky

`AfxGetInstanceHandle` vždy vrátí HINSTANCE spustitelného souboru (. EXE), pokud není volána v rámci knihovny DLL propojené s verzí USRDLL knihovny MFC. V tomto případě vrátí HINSTANCE do knihovny DLL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxgetmainwnd"></a>AfxGetMainWnd

Pokud je vaše aplikace serverem OLE, zavolejte tuto funkci, aby načetla ukazatel na aktivní hlavní okno aplikace. Použijte tento výsledek místo přímého odkazu na [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) člen objektu aplikace.

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na objekt okna rámce, který obsahuje místní aktivní dokument, pokud server obsahuje objekt, který je místně aktivní uvnitř aktivního kontejneru.

Pokud není žádný objekt, který je místně aktivní v rámci kontejneru, nebo vaše aplikace není serverem OLE, vrátí tato funkce *m_pMainWnd* objektu aplikace.

Pokud je zavolána `AfxGetMainWnd` z primárního vlákna aplikace, vrátí hlavní okno aplikace podle výše uvedených pravidel. Pokud je funkce volána ze sekundárního vlákna v aplikaci, vrátí funkce hlavní okno přidružené k vláknu, které volání provedlo.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace není serverem OLE, pak volání této funkce je ekvivalentní přímo odkazující na *m_pMainWnd* člena objektu aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxgetperuserregistration"></a>AfxGetPerUserRegistration

Pomocí této funkce lze určit, zda aplikace přesměrovává přístup k registru do uzlu **HKEY_CURRENT_USER** (**HKCU**).

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE označuje, že informace registru jsou směrovány na uzel HKCU. FALSE znamená, že aplikace zapisuje informace registru do výchozího uzlu. Výchozí uzel je **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Poznámky

Pokud povolíte přesměrování registru, rozhraní přesměruje přístup z **HKCR** do **HKEY_CURRENT_USER \software\classes**. Přesměrování ovlivňují pouze architektury MFC a ATL.

Chcete-li změnit, zda aplikace přesměruje přístup k registru, použijte [AfxSetPerUserRegistration](#afxsetperuserregistration).

### <a name="requirements"></a>Požadavky

  Afxstat_ **záhlaví** . h

## <a name="afxgetresourcehandle"></a>AfxGetResourceHandle

Použijte popisovač HINSTANCE vrácený touto funkcí pro přímý přístup k prostředkům aplikace, například při volání funkce Windows `FindResource`.

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Návratová hodnota

HINSTANCE popisovač, kde jsou načteny výchozí prostředky aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxgetthread"></a>AfxGetThread

Voláním této funkce získáte ukazatel na objekt [CWinThread](../../mfc/reference/cwinthread-class.md) představující aktuálně spuštěné vlákno.

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuálně spuštěné vlákno; jinak NULL.

### <a name="remarks"></a>Poznámky

Musí být volána v rámci vlákna.

> [!NOTE]
> Pokud provádíte přenos projektu knihovny MFC volání `AfxGetThread` z Visual C++ verze 4,2, 5,0 nebo 6,0, `AfxGetThread` volá [AfxGetApp](#afxgetapp) , pokud není nalezeno žádné vlákno. V novějších verzích kompilátoru `AfxGetThread` vrátí hodnotu NULL, pokud nebylo nalezeno žádné vlákno. Pokud chcete vlákno aplikace, musíte volat `AfxGetApp`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxinitrichedit"></a>AfxInitRichEdit

Voláním této funkce nainicializujete ovládací prvek RichEdit pro úpravy (verze 1,0) pro aplikaci.

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Poznámky

Tato funkce je k dispozici kvůli zpětné kompatibilitě. Nové aplikace by měly používat [AfxInitRichEdit2](#afxinitrichedit2).

`AfxInitRichEdit` načte RICHED32. Knihovna DLL pro inicializaci verze 1,0 ovládacího prvku RichEdit Chcete-li použít verzi 2,0 a 3,0 ovládacího prvku Rich Edit, knihovny RICHED20. Knihovna DLL musí být načtena. Načte se voláním metody [AfxInitRichEdit2](#afxinitrichedit2).

Chcete-li aktualizovat ovládací prvky s bohatým úpravou ve stávajících vizuálních C++ aplikacích na verzi 2,0, otevřete. Soubor RC jako text, změňte název třídy každého ovládacího prvku Rich Edit z "RICHEDIT" na "RichEdit20a". Potom volání `AfxInitRichEdit` nahraďte `AfxInitRichEdit2`.

Tato funkce také inicializuje knihovnu běžných ovládacích prvků, pokud knihovna ještě nebyla inicializována pro daný proces. Použijete-li ovládací prvek RichEdit přímo z vaší aplikace MFC, zavolejte tuto funkci, aby se zajistilo, že knihovna MFC správně inicializovala modul runtime ovládacího prvku Rich Edit. Pokud voláte metodu `Create` [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView –](../../mfc/reference/cricheditview-class.md)nebo [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), obvykle není nutné volat tuto funkci, ale v některých případech může být nutné.

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxinitrichedit2"></a>AfxInitRichEdit2

Voláním této funkce inicializujete ovládací prvek RichEdit (verze 2,0 a novější) pro aplikaci.

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Poznámky

Voláním této funkce načtete knihovny RICHED20. Knihovna DLL a inicializace verze 2,0 ovládacího prvku RichEdit. Pokud voláte metodu `Create` [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView –](../../mfc/reference/cricheditview-class.md)nebo [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), obvykle není nutné volat tuto funkci, ale v některých případech může být nutné.

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxisextendedframeclass"></a>AfxIsExtendedFrameClass

Určuje, zda je dané okno objektem rozšířeného rámce.

### <a name="syntax"></a>Syntaxe

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Parametry

*pWnd*\
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

## <a name="afxismfctoolbar"></a>AfxIsMFCToolBar

Určuje, zda je dané okno objekt panelu nástrojů.

### <a name="syntax"></a>Syntaxe

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*\
pro Ukazatel na objekt, který je odvozen z `CWnd`.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadané okno objekt panelu nástrojů; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrací `TRUE`, je-li *pWnd* odvozen od `CMFCToolBar`. Tato metoda je užitečná v případě, že je nutné ověřit, zda je parametrem funkce nebo metody objekt `CMFCToolBar`.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXPRIV. h

## <a name="afxkeyboardmanager"></a>AfxKeyboardManager

Ukazatel na globálního [správce klávesnice](ckeyboardmanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxkeyboardmanager. h

## <a name="afxloadlibrary"></a>AfxLoadLibrary

K namapování modulu DLL použijte `AfxLoadLibrary`.

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Parametry

*lpszModuleName*\
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název modulu (buď. Knihovna DLL nebo. Soubor EXE). Zadaný název je název souboru modulu.

Pokud řetězec Určuje cestu, ale soubor v zadaném adresáři neexistuje, funkce se nezdařila.

Pokud není zadaná cesta a přípona názvu souboru je vynechána, výchozí přípona. Knihovna DLL je připojena. Řetězec filename však může obsahovat znak koncového bodu (.), který označuje, že název modulu nemá žádné rozšíření. Pokud není zadána žádná cesta, funkce použije [pořadí hledání pro aplikace klasické pracovní plochy](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je popisovačem modulu. Při selhání je vrácená hodnota NULL.

### <a name="remarks"></a>Poznámky

Vrátí popisovač, který lze použít v [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) pro získání adresy funkce knihovny DLL. `AfxLoadLibrary` lze také použít k mapování dalších spustitelných modulů.

Každý proces udržuje počet odkazů pro každý načtený modul knihovny. Tento počet odkazů se zvyšuje při každém volání `AfxLoadLibrary` a při každém volání `AfxFreeLibrary` snižuje. Pokud počet odkazů dosáhne nuly, modul není namapován z adresního prostoru volajícího procesu a popisovač již není platný.

Nezapomeňte použít `AfxLoadLibrary` a `AfxFreeLibrary` (namísto funkcí Win32 `LoadLibrary` a `FreeLibrary`), pokud vaše aplikace používá více vláken a v případě, že dynamicky načítá rozšiřující knihovnu MFC DLL. Pomocí `AfxLoadLibrary` a `AfxFreeLibrary` si zajistěte, že spouštěcí a ukončovací kód, který se spustí, když je načtena a uvolněna knihovna MFC DLL, není poškozen globální stav knihovny MFC.

Použití `AfxLoadLibrary` v aplikaci vyžaduje dynamickou vazbu na verzi knihovny MFC DLL. Hlavičkový soubor pro `AfxLoadLibrary`, Afxdll_. h, je zahrnut pouze v případě, že je knihovna MFC propojena s aplikací jako knihovnou DLL. Tento požadavek je záměrné, protože pro použití nebo vytvoření knihoven DLL knihovny MFC musíte propojit s knihovnou DLL verze knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Požadavky

  Afxdll_ **záhlaví** . h

## <a name="afxloadlibraryex"></a>AfxLoadLibraryEx

K namapování modulu DLL použijte `AfxLoadLibraryEx`.

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*lpFileName*\
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název modulu (buď. Knihovna DLL nebo. Soubor EXE). Zadaný název je název souboru modulu.

Pokud řetězec Určuje cestu, ale soubor v zadaném adresáři neexistuje, funkce se nezdařila.

Pokud není zadaná cesta a přípona názvu souboru je vynechána, výchozí přípona. Knihovna DLL je připojena. Řetězec filename však může obsahovat znak koncového bodu (.), který označuje, že název modulu nemá žádné rozšíření. Pokud není zadána žádná cesta, funkce použije [pořadí hledání pro aplikace klasické pracovní plochy](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

*hFile*\
Tento parametr je vyhrazený pro budoucí použití. Musí mít hodnotu NULL.

*dwFlags*\
Akce, která má být provedena při načítání modulu. Pokud nejsou zadány žádné příznaky, chování této funkce je stejné jako funkce `AfxLoadLibrary`. Možné hodnoty tohoto parametru jsou popsány v dokumentaci k [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) .

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je popisovačem modulu. Při selhání je vrácená hodnota NULL.

### <a name="remarks"></a>Poznámky

`AfxLoadLibraryEx` vrátí popisovač, který lze použít v [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) pro získání adresy funkce knihovny DLL. `AfxLoadLibraryEx` lze také použít k mapování dalších spustitelných modulů.

Každý proces udržuje počet odkazů pro každý načtený modul knihovny. Tento počet odkazů se zvyšuje při každém volání `AfxLoadLibraryEx` a při každém volání `AfxFreeLibrary` snižuje. Pokud počet odkazů dosáhne nuly, modul není namapován z adresního prostoru volajícího procesu a popisovač již není platný.

Nezapomeňte použít `AfxLoadLibraryEx` a `AfxFreeLibrary` (namísto funkcí Win32 `LoadLibraryEx` a `FreeLibrary`), pokud vaše aplikace používá více vláken a v případě, že dynamicky načítá rozšiřující knihovnu MFC DLL. Pomocí `AfxLoadLibraryEx` a `AfxFreeLibrary` je zajištěno, že spouštěcí a ukončovací kód, který se spustí, když je načtena a uvolněna knihovna MFC DLL, není poškozen globální stav knihovny MFC.

Použití `AfxLoadLibraryEx` v aplikaci vyžaduje dynamickou vazbu na verzi knihovny MFC DLL. Hlavičkový soubor pro `AfxLoadLibraryEx`, Afxdll_. h, je zahrnut pouze v případě, že je knihovna MFC propojena s aplikací jako knihovnou DLL. Tento požadavek je záměrné, protože pro použití nebo vytvoření knihoven DLL knihovny MFC musíte propojit s knihovnou DLL verze knihovny MFC.

### <a name="requirements"></a>Požadavky

  Afxdll_ **záhlaví** . h

## <a name="afxmenutearoffmanager"></a>AfxMenuTearOffManager

Ukazatel na globální [vytrhnoutelné nabídky Správce](cmenutearoffmanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmenutearoffmanager. h

## <a name="afxmousemanager"></a>AfxMouseManager

Ukazatel na globálního [správce myši](cmousemanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmousemanager. h

## <a name="afxregisterclass"></a>AfxRegisterClass

Pomocí této funkce lze registrovat třídy oken v knihovně DLL, která používá knihovnu MFC.

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Parametry

*lpWndClass*\
Ukazatel na strukturu [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) obsahující informace o třídě okna, která má být zaregistrována. Další informace o této struktuře naleznete v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je třída úspěšně registrována; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Použijete-li tuto funkci, třída je automaticky zrušena při uvolnění knihovny DLL.

V případě sestavení bez knihoven DLL je identifikátor `AfxRegisterClass` definován jako makro, které je mapováno na `RegisterClass`funkcí systému Windows, protože třídy registrované v aplikaci jsou automaticky odregistrovány. Použijete-li `AfxRegisterClass` místo `RegisterClass`, lze kód použít bez změny v aplikaci i v knihovně DLL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxregisterwndclass"></a>AfxRegisterWndClass –

Umožňuje registrovat vlastní třídy okna.

```cpp
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Parametry

*nClassStyle*\
Určuje styl třídy systému Windows nebo kombinaci stylů vytvořené pomocí operátoru bitového operátoru OR ( **&#124;** ) pro třídu okna. Seznam stylů třídy naleznete v tématu struktura [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) v Windows SDK. Pokud má hodnotu NULL, výchozí nastavení jsou následující:

- Nastaví styl myši na CS_DBLCLKS, který pošle dvojitým kliknutím zprávy do procedury okna, když uživatel dvakrát klikne na myš.

- Nastaví styl ukazatele šipky na standardní IDC_ARROW Windows.

- Nastaví štětec pozadí na hodnotu NULL, takže okno nesmaže své pozadí.

- Nastaví ikonu na standardní ikonu loga Windows mávající-Flag.

*hCursor*\
Určuje popisovač pro prostředek kurzoru, který se má nainstalovat do každého okna vytvořeného z třídy okna. Pokud použijete výchozí **hodnotu 0**, dostanete standardní IDC_ARROW kurzor.

*hbrBackground*\
Určuje popisovač prostředku štětce, který se má nainstalovat do každého okna vytvořeného z třídy okna. Použijete-li výchozí **hodnotu 0**, budete mít k dispozici znak štětce na pozadí a ve výchozím nastavení okno nebude při zpracovávání [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)smazáno pozadí.

*hIcon*\
Určuje popisovač pro prostředek ikony, který se má nainstalovat do každého okna vytvořeného z třídy okna. Pokud použijete výchozí **hodnotu 0**, zobrazí se ikona pro logo Windows úrovně Standard, mávající-Flag.

### <a name="return-value"></a>Návratová hodnota

Řetězec zakončený hodnotou null obsahující název třídy. Tento název třídy můžete předat `Create` členské funkci v `CWnd` nebo jiných třídách, které jsou odvozeny v **CWnd**, k vytvoření okna. Název je vygenerován knihovna Microsoft Foundation Class.

> [!NOTE]
> Vrácená hodnota je ukazatel na statickou vyrovnávací paměť. Pokud chcete tento řetězec uložit, přiřaďte ho k proměnné `CString`.

### <a name="remarks"></a>Poznámky

Knihovna Microsoft Foundation Class automaticky registruje několik standardních tříd okna za vás. Tuto funkci zavolejte, pokud chcete registrovat vlastní třídy oken.

Název zaregistrovaný pro třídu `AfxRegisterWndClass` závisí výhradně na parametrech. Pokud zavoláte `AfxRegisterWndClass` vícekrát se stejnými parametry, registruje pouze třídu při prvním volání. Pozdější volání `AfxRegisterWndClass` se stejnými parametry vrací již registrovanou hodnotu ClassName.

Pokud zavoláte `AfxRegisterWndClass` pro více tříd odvozených od typu CWnd se stejnými parametry namísto získání samostatné třídy okna pro každou třídu, každá třída sdílí stejnou třídu okna. Toto sdílení může způsobit problémy, pokud je použit styl CS_CLASSDC třídy. Místo více CS_CLASSDCch tříd oken, skončíte pouze s jednou třídou okna CS_CLASSDC. Všechna C++ okna, která používají tuto třídu, sdílejí stejný řadič domény. Chcete-li se tomuto problému vyhnout, zavolejte [AfxRegisterClass](#afxregisterclass) k registraci třídy.

Další informace o registraci třídy okna a funkci `AfxRegisterWndClass` naleznete v tématu technická Poznámka [TN001: registrace třídy okna](../../mfc/tn001-window-class-registration.md) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxsetperuserregistration"></a>AfxSetPerUserRegistration

Nastaví, zda aplikace přesměrovává přístup k registru do uzlu **HKEY_CURRENT_USER** (**HKCU**).

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*\
pro Hodnota TRUE označuje, že informace registru jsou směrovány na uzel HKCU. FALSE znamená, že aplikace zapisuje informace registru do výchozího uzlu. Výchozí uzel je **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Poznámky

Před Windows Vista aplikace, které se k registru použily, běžně používaly uzel **HKEY_CLASSES_ROOT** . V systému Windows Vista nebo novějších operačních systémech je však nutné spustit aplikaci v režimu zvýšené úrovně, aby bylo možné zapisovat do HKCR.

Tato metoda umožňuje vaší aplikaci číst a zapisovat do registru bez spuštění v režimu zvýšeného úrovně. Funguje tak, že přesměruje přístup registru z HKCR na HKCU. Další informace najdete v tématu [stránky vlastností linkeru](../../build/reference/linker-property-pages.md).

Pokud povolíte přesměrování registru, rozhraní přesměruje přístup z HKCR do **HKEY_CURRENT_USER \software\classes**. Přesměrování ovlivňují pouze architektury MFC a ATL.

Výchozí implementace přistupuje k registru v HKCR.

### <a name="requirements"></a>Požadavky

  Afxstat_ **záhlaví** . h

## <a name="afxsetresourcehandle"></a>AfxSetResourceHandle

Pomocí této funkce lze nastavit popisovač HINSTANCE, který určuje, kde jsou načteny výchozí prostředky aplikace.

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Parametry

*hInstResource*\
Obslužná rutina instance nebo modulu. EXE nebo soubor DLL, ze kterého jsou načteny prostředky aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="afxshellmanager"></a>AfxShellManager

Ukazatel na globální [správce prostředí](cshellmanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxshellmanager. h

## <a name="afxsocketinit"></a>AfxSocketInit

Voláním této funkce v přepsání `CWinApp::InitInstance` inicializujete Windows Sockets.

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Parametry

*lpwsaData*\
Ukazatel na strukturu [WSADATA –](/windows/win32/api/winsock2/ns-winsock2-wsadata) . Pokud *lpwsaData* není rovno null, adresa `WSADATA` struktury je vyplněna voláním `WSAStartup`. Tato funkce také zajistí, že je před ukončením aplikace volána `WSACleanup`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Při použití soketů MFC v sekundárních vláknech v staticky propojené aplikaci MFC je nutné volat `AfxSocketInit` v každém vlákně, které používá sokety k inicializaci knihoven soketu. Ve výchozím nastavení je `AfxSocketInit` volána pouze v primárním vlákně.

### <a name="requirements"></a>Požadavky

  **Header** AfxSock. h

## <a name="afxusertoolsmanager"></a>AfxUserToolsManager

Ukazatel na správce globálních [uživatelských nástrojů](cusertoolsmanager-class.md).

### <a name="syntax"></a>Syntaxe

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxusertoolsmanager. h

## <a name="afxwininit"></a>AfxWinInit

Tato funkce je volána funkcí `WinMain` poskytnutou knihovnou MFC jako součást inicializace [CWinApp](../../mfc/reference/cwinapp-class.md) aplikace založené na grafickém uživatelském rozhraní pro inicializaci knihovny MFC.

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
Popisovač předchozí instance aplikace. Pro aplikaci založenou na Win32 má tento parametr vždycky **hodnotu null**.

*lpCmdLine*\
Odkazuje na řetězec zakončený hodnotou null určující příkazový řádek pro aplikaci.

*nCmdShow*\
Určuje, jak se bude zobrazovat hlavní okno aplikace grafického uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Pro konzolovou aplikaci, která nepoužívá funkci `WinMain` dodané pomocí knihovny MFC, je nutné volat `AfxWinInit` přímo pro inicializaci knihovny MFC.

Pokud zavoláte `AfxWinInit` sami, měli byste deklarovat instanci `CWinApp` třídy. Pro konzolovou aplikaci se můžete rozhodnout neodvozovat vlastní třídu od `CWinApp` a místo toho použít instanci `CWinApp` přímo. Tato technika je vhodná, pokud se rozhodnete ponechat všechny funkce aplikace v implementaci **Main**.

> [!NOTE]
> Při vytvoření aktivačního kontextu pro sestavení používá knihovna MFC prostředek manifestu poskytovaný modulem uživatele. Aktivační kontext je vytvořen v `AfxWinInit`. Další informace najdete v tématu [Podpora kontextů aktivace ve stavu modulu MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

## <a name="see-also"></a>Viz také

[Makra a globální](mfc-macros-and-globals.md)\
[CWinApp](cwinapp-class.md) –\ třídy
\ [třídy CContextMenuManager](ccontextmenumanager-class.md)
\ [třídy CWnd](cwnd-class.md)
\ [třídy CFrameWndEx](cframewndex-class.md)
\ [třídy CMFCToolBar](cmfctoolbar-class.md)
\ [třídy CKeyboardManager](ckeyboardmanager-class.md)
\ [třídy CMenuTearOffManager](cmenutearoffmanager-class.md)
\ [třídy CMouseManager](cmousemanager-class.md)
\ [třídy CShellManager](cshellmanager-class.md)
[CUserToolsManager – třída](cusertoolsmanager-class.md)
