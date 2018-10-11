---
title: Informace o aplikacích a Správa | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9783da47a22260f0edbe5ddf6d8f5021aae31e5c
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083798"
---
# <a name="application-information-and-management"></a>Informace o aplikacích a správa aplikací

Při psaní aplikace, můžete vytvořit samostatný [CWinApp](../../mfc/reference/cwinapp-class.md)-odvozenému objektu. V některých případech můžete chtít získat informace o tomto objektu z mimo `CWinApp`-odvozenému objektu. Nebo pokud potřebujete přístup k jiným objektům globální "Manager".

Knihovny Microsoft Foundation Class poskytuje následující globální funkce umožňují provedení následujících úkolů:

### <a name="application-information-and-management-functions"></a>Informace o aplikaci a funkce pro správu

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|Vytvoří nové vlákno.|
|[Afxcontextmenumanager –](#afxcontextmenumanager)|Ukazatel na globální [kontextové nabídky správce](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Ukončí aktuální vlákno.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Provede řetězce prostředků a vyhledejte konkrétní prostředky podle ID a typ prostředku. |
|[AfxFreeLibrary](#afxfreelibrary)|Sníží počet referenční modulu načíst dynamickou knihovnu (DLL); Když počet odkazů dosáhne nuly, modul není mapován.|
|[AfxGetApp](#afxgetapp)|Vrací ukazatel na aplikaci prvku jednoho `CWinApp` objektu.|
|[Afxgetappname –](#afxgetappname)|Vrátí řetězec, který obsahuje název aplikace.|
|[Afxgetinstancehandle –](#afxgetinstancehandle)|Vrátí HINSTANCE představující tuto instanci aplikace.|
|[Afxgetmainwnd –](#afxgetmainwnd)|Vrací ukazatel aktuální "hlavní"-OLE – aplikace, rámečkem na místě okno nebo serverové aplikace.|
|[Afxgetperuserregistration –](#afxgetperuserregistration)|Tato funkce slouží k určení, zda aplikace přesměrovává přístup k registru do **HKEY_CURRENT_USER** ( **HKCU**) uzlu.|
|[AfxGetResourceHandle –](#afxgetresourcehandle)|Vrátí HINSTANCE zdroj aplikace výchozí prostředky. Použijte pro přímý přístup k prostředkům aplikace.|
|[Afxgetthread –](#afxgetthread)|Načte ukazatel na aktuální [CWinThread](../../mfc/reference/cwinthread-class.md) objektu.|
|[Afxinitrichedit –](#afxinitrichedit)|Inicializuje verze ovládacího prvku pro aplikace pro úpravy s formátováním 1.0.|
|[Afxinitrichedit2 –](#afxinitrichedit2)|Inicializuje ovládací prvek pro aplikace pro úpravy s formátováním 2.0 a vyšší verze.|
|[Afxisextendedframeclass –](#afxisextendedframeclass)|Určuje, zda je daném okně Rozšířené orámovat objekt.|
|[Afxismfctoolbar –](#afxismfctoolbar)|Určuje, zda je okno daný objekt panelu nástrojů.|
|[Afxkeyboardmanager –](#afxkeyboardmanager)|Ukazatel na globální [klávesnice správce](ckeyboardmanager-class.md).|
|[AfxLoadLibrary](#afxloadlibrary)|Mapuje modul knihovny DLL a vrátí popisovač, který slouží k získání adresy funkce knihovny DLL.|
|[Afxmenutearoffmanager –](#afxmenutearoffmanager)|Ukazatel na globální [odtržené nabídky správce](cmenutearoffmanager-class.md).|
|[Afxmousemanager –](#afxmousemanager)|Ukazatel na globální [myši správce](cmousemanager-class.md).|
|[Afxregisterclass –](#afxregisterclass)|Zaregistruje třídu okna v knihovně DLL, která používá knihovnu MFC.|
|[Afxregisterwndclass –](#afxregisterwndclass)|Zaregistruje třídu okna Windows k doplnění ty automaticky registrovaných knihovny MFC.|
|[Afxsetperuserregistration –](#afxsetperuserregistration)|Nastaví, zda aplikace přesměrovává přístup k registru do **HKEY_CURRENT_USER** ( **HKCU**) uzlu.|
|[Afxsetresourcehandle –](#afxsetresourcehandle)|Nastaví HINSTANCE popisovač, kde jsou načteny výchozích prostředků aplikace.|
|[Afxshellmanager –](#afxshellmanager)|Ukazatel na globální [správce prostředí](cshellmanager-class.md). |
|[Afxsocketinit –](#afxsocketinit)|Volá se `CWinApp::InitInstance` přepsání se inicializovat rozhraní Windows Sockets.|
|[Afxusertoolsmanager –](#afxusertoolsmanager)|Ukazatel na globální [nástroje Správce uživatelů](cusertoolsmanager-class.md).|
|[Afxwininit –](#afxwininit)|Volá zadaný MFC `WinMain` funkce, jako součást [CWinApp](../../mfc/reference/cwinapp-class.md) inicializace aplikace využívající grafické rozhraní, se inicializovat knihovnu MFC. Je nutné volat přímo pro konzolové aplikace, které používají knihovnu MFC.|



##  <a name="afxbeginthread"></a>  AfxBeginThread

Voláním této funkce vytvořit nové vlákno.

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
Odkazuje na řídící funkce pro pracovní vlákno. Nemůže mít hodnotu NULL. Tato funkce musí být deklarována takto:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*<br/>
RUNTIME_CLASS objekt odvozený od [CWinThread](../../mfc/reference/cwinthread-class.md).

*pParam*<br/>
Parametr má být předán řídící funkci jako parametru za účelem deklarace funkce v *pfnThreadProc*.

*nPriority*<br/>
Požadovaná priorita vlákna. Úplný seznam a popis dostupných priorit naleznete v tématu [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v sadě Windows SDK.

*nStackSize*<br/>
Určuje velikost v bajtech zásobníku pro nové vlákno. Pokud je 0, výchozí velikost zásobníku stejná velikost zásobníku jako u vytvářeného vlákna.

*dwCreateFlags*<br/>
Určuje další příznak, který řídí vytvoření vlákna. Tento příznak může obsahovat jednu ze dvou hodnot:

- CREATE_SUSPENDED spustit vlákno s pozastaveným počtem jedna. CREATE_SUSPENDED použijte, pokud chcete inicializovat všechna data členů objektu `CWinThread` objektů, jako například [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) nebo všechny členy odvozené třídy před spuštěním podprocesu. Po dokončení inicializace použijte [CWinThread::ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) spustit vlákno spuštěné. Vlákno nebude spuštěno až do `CWinThread::ResumeThread` je volána.

- **0** spuštění vlákna ihned po vytvoření.

*lpSecurityAttrs*<br/>
Odkazuje [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, která určuje atributy zabezpečení pro vlákno. Pokud má hodnotu NULL, použije se stejné atributy zabezpečení jako u vytvářeného vlákna. Další informace o této struktuře naleznete v tématu Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený objekt vlákna, nebo hodnota NULL, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

První formulář `AfxBeginThread` vytvoří pracovní vlákno. Druhý formulář vytvoří vlákno, které může sloužit jako vlákno uživatelského rozhraní nebo jako pracovní vlákno.

`AfxBeginThread` Vytvoří novou `CWinThread` objektu, zavolá jeho [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) funkce spustí provádění vlákna a vrací ukazatel na vlákno. Kontroly jsou prováděny v celém procesu zajistit, aby že všechny objekty jsou správně uvolněny by selhat některá část vytvoření. Chcete-li ukončit vlákno, volejte [AfxEndThread](#afxendthread) z v rámci vlákna nebo proveďte návrat z řídící funkce pracovního podprocesu.

Multithreading musí být povolen v aplikaci; v opačném případě tato funkce se nezdaří. Další informace o povolení multithreadingu naleznete [/ / MD, / MT, /LD (použití knihovny Run-Time)](../../build/reference/md-mt-ld-use-run-time-library.md) pod *Visual C++ – možnosti kompilátoru*.

Další informace o `AfxBeginThread`, najdete v článcích [Multithreading: vytváření pracovních vláken](../../parallel/multithreading-creating-worker-threads.md) a [Multithreading: vytváření vláken uživatelského rozhraní](../../parallel/multithreading-creating-user-interface-threads.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CSocket::Attach](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

## <a name="afxcontextmenumanager"></a> Afxcontextmenumanager –

Ukazatel na globální [kontextové nabídky správce](ccontextmenumanager-class.md).

### <a name="syntax"></a>Syntaxe

```
CContextMenuManager* afxContextMenuManager;
```
### <a name="requirements"></a>Požadavky

**Záhlaví:** afxcontextmenumanager.h

### <a name="see-also"></a>Viz také

[CContextMenuManager – třída](ccontextmenumanager-class.md)


##  <a name="afxendthread"></a>  AfxEndThread

Voláním této funkce k ukončení aktuálně spuštěné vlákno.

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

Musí být volána z v rámci vlákno ukončeno.

Další informace o `AfxEndThread`, najdete v článku [Multithreading: ukončení vláken](../../parallel/multithreading-terminating-threads.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
Použití `AfxFindResourceHandle` vás řetězce prostředků a vyhledejte konkrétní prostředek podle ID a zdroj typem prostředku.

### <a name="syntax"></a>Syntaxe

```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```
### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec obsahující ID prostředku.
*lpszType*<br/>
Ukazatel na typ prostředku. Seznam typů prostředků najdete v tématu [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Popisovač pro modul, který obsahuje prostředek.

### <a name="remarks"></a>Poznámky

`AfxFindResourceHandle` Vyhledá konkrétní prostředek a vrátí popisovač do modulu, který obsahuje prostředek. Prostředek může být v rozšíření MFC DLL, které jste načetli. `AfxFindResourceHandle` zjistíte, které je prostředek.

Moduly jsou prohledávány v tomto pořadí:

1. Hlavní modul (Pokud je rozšiřující knihovny DLL MFC).

1. Jiné než systémové moduly.

1. Moduly pro konkrétní jazyk.

1. Hlavní modul (je-li systémové knihovny DLL).

1. Systém modulů.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

### <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)

##  <a name="afxfreelibrary"></a>  AfxFreeLibrary

Obě `AfxFreeLibrary` a `AfxLoadLibrary` spravovat počet odkazů pro každý modul načíst knihovny.

```
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Parametry

*hInstLib*<br/>
Popisovač modul načíst knihovny. [AfxLoadLibrary](#afxloadlibrary) vrátí tento popisovač.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud funkce uspěje; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

`AfxFreeLibrary` sníží počet referenční modulu načíst dynamickou knihovnu (DLL). Když počet odkazů dosáhne nuly, modul není mapován z adresního prostoru volajícího procesu a již není platný popisovač. Tento počet odkazů je zvýšen pokaždé, když `AfxLoadLibrary` je volána.

Před unmapping modul knihovny, umožňuje systém knihovnu DLL k odpojení od procesů jeho použití. To poskytuje knihovnu DLL příležitost k uvolnění prostředků přidělených jménem aktuální proces. Po návratu funkce vstupního bodu knihovny, odebere se z adresního prostoru aktuálního procesu.

Použití `AfxLoadLibrary` pro mapování modulu DLL.

Nezapomeňte použít `AfxFreeLibrary` a `AfxLoadLibrary` (namísto funkce Win32 `FreeLibrary` a `LoadLibrary`) Pokud vaše aplikace používá více vláken. Pomocí `AfxLoadLibrary` a `AfxFreeLibrary` zajistí, že spuštění a vypnutí kód, který se spustí po MFC – rozšiřující knihovny DLL je načteny nebo uvolněny nejsou poškozeny globální stav knihovny MFC.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdll_.h

##  <a name="afxgetapp"></a>  AfxGetApp

Ukazatel vrácená touto funkcí můžete použít pro přístup k aplikaci informace, jako je hlavní odeslání zpráv kódu nebo okně nejvyšší.

```
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jedné `CWinApp` objektu pro aplikaci.

### <a name="remarks"></a>Poznámky

Pokud tato metoda vrátí hodnotu NULL, může to znamenat, že hlavní okno aplikace dosud nebyla inicializována plně. Také to může znamenat problém.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxgetappname"></a>  Afxgetappname –

Řetězec vrácený touto funkcí je možné pro diagnostické zprávy nebo jako kořen pro dočasné řetězcové názvy.

```
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Návratová hodnota

Řetězec zakončený hodnotou null obsahující název aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxgetinstancehandle"></a>  Afxgetinstancehandle –

Tato funkce umožňuje načíst popisovač instance aktuální aplikace.

```
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Návratová hodnota

HINSTANCE na aktuální instanci aplikace. Pokud volat v rámci knihovny DLL propojené s USRDLL verze knihovny MFC, vrátí se HINSTANCE na knihovnu DLL.

### <a name="remarks"></a>Poznámky

`AfxGetInstanceHandle` vždy vrátí HINSTANCE spustitelný soubor (. Soubor EXE) Pokud je volána v rámci knihovny DLL propojené s USRDLL verze knihovny MFC. V takovém případě vrátí HINSTANCE na knihovnu DLL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxgetmainwnd"></a>  Afxgetmainwnd –

Pokud je vaše aplikace serveru OLE, volání této funkce načtete ukazatel na aktivní hlavní okno aplikace namísto přímo odkazující na [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) člen objektu aplikace.

```
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Návratová hodnota

Pokud má objekt, který je místní server aktivní uvnitř kontejneru a tento kontejner je aktivní, tato funkce vrací ukazatel na objekt okna rámce, který obsahuje místní aktivní dokument.

Neexistuje žádný objekt, který je na místě aktivní v rámci kontejneru, zda vaše aplikace není OLE server, jednoduše vrátí tato funkce *m_pMainWnd* objektu aplikace.

Pokud `AfxGetMainWnd` je volána z aplikace primární vlákno, vrátí hlavní okno aplikace podle výše uvedených pravidel. Pokud funkce je volána v sekundární vlákno v aplikaci, funkce vrátí hlavní okno, které jsou spojené s vláknem, které provedených volání.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace není OLE server, pak volání této funkce je ekvivalentní k přímo odkazující na *m_pMainWnd* člen objektu aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxgetperuserregistration"></a>  Afxgetperuserregistration –

Tato funkce slouží k určení, zda aplikace přesměrovává přístup k registru do **HKEY_CURRENT_USER** ( **HKCU**) uzlu.

```
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE označuje, že informace registru během směřuje k uzlu HKCU; Hodnota FALSE označuje, že aplikace zapíše informace registru do uzlu výchozí. Je výchozí uzel **HKEY_CLASSES_ROOT** ( **HKCR**).

### <a name="remarks"></a>Poznámky

Pokud povolíte registru přesměrování, rozhraní přesměrovává přístup k z **HKCR** k **HKEY_CURRENT_USER\Software\Classes**. Pouze rozhraní MFC a ATL jsou ovlivněny přesměrování.

Chcete-li změnit, zda aplikace přesměrovává přístup k registru, použijte [afxsetperuserregistration –](#afxsetperuserregistration).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxstat_.h

##  <a name="afxgetresourcehandle"></a>  AfxGetResourceHandle –

Použití HINSTANCE zpracování vrácená touto funkcí přístup k prostředkům aplikace přímo, například ve volání Windows fungovat `FindResource`.

```
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač HINSTANCE, ve kterém jsou načteny výchozích prostředků aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxgetthread"></a>  Afxgetthread –

Volání této funkce získáte ukazatel [CWinThread](../../mfc/reference/cwinthread-class.md) objekt představující aktuálně spuštěné vlákno.

```
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuálně spuštěné vlákno; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Musí být volána z požadovaného vlákna.

> [!NOTE]
>  Pokud se přenos volání projektu knihovny MFC `AfxGetThread` z verzí Visual C++ 4.2, 5.0 nebo 6.0, `AfxGetThread` volání [AfxGetApp](#afxgetapp) Pokud se nenajde žádné vlákno. V novějších verzích kompilátoru `AfxGetThread` vrátí hodnotu NULL, pokud nebyla nalezena žádná vlákna. Pokud chcete, aby vlákno aplikace, musíte zavolat `AfxGetApp`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxinitrichedit"></a>  Afxinitrichedit –

Volání této funkce lze inicializovat ovládací prvek RTF (verze 1.0) pro aplikaci.

```
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Poznámky

Tato funkce je poskytována pro zpětnou kompatibilitu. Nová aplikace by měly používat [afxinitrichedit2 –](#afxinitrichedit2).

`AfxInitRichEdit` načte RICHED32. Knihovnu DLL inicializovat verzi ovládacího prvku RichEdit 1.0. Chcete-li použít verzi 2.0 a 3.0 ovládacího prvku RichEdit, RICHED20. Knihovna DLL je třeba načíst. To lze provést voláním [afxinitrichedit2 –](#afxinitrichedit2).

Chcete-li aktualizovat RichEdit ovládacích prvků v existujících aplikací Visual C++ verze 2.0, otevřete. RC soubor jako text, změnit název třídy pro každý ovládací prvek RTF z "RICHEDIT" k "RichEdit20a". Potom nahraďte volání `AfxInitRichEdit` s `AfxInitRichEdit2`.

Tato funkce také inicializuje společné knihovny ovládacích prvků, pokud ještě nebyl inicializován knihovny pro proces. Pokud používáte nástroj RichEdit přímo z aplikace knihovny MFC, byste měli volat tuto funkci, aby zajistil, že MFC správně inicializovat modul runtime ovládacího prvku RichEdit. Pokud volání metody vytvořit [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [cricheditview –](../../mfc/reference/cricheditview-class.md), nebo [cricheditdoc –](../../mfc/reference/cricheditdoc-class.md), obvykle není nutné volat tuto funkci, ale v některých případech může být nezbytné.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxinitrichedit2"></a>  Afxinitrichedit2 –

Volání této funkce lze inicializovat ovládací prvek RTF (verze 2.0 a novější) pro aplikaci.

```
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Poznámky

Voláním této funkce RICHED20 načíst. Knihovny DLL a inicializovat verze 2.0 získáte bohaté ovládacích prvků pro úpravy. Pokud volání metody vytvořit [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [cricheditview –](../../mfc/reference/cricheditview-class.md), nebo [cricheditdoc –](../../mfc/reference/cricheditdoc-class.md), obvykle není nutné volat tuto funkci, ale v některých případech může být nezbytné.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

  ## <a name="afxisextendedframeclass"></a>  Afxisextendedframeclass –
Určuje, zda je daném okně Rozšířené orámovat objekt.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```
### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Ukazatel na objekt, který je odvozen z `CWnd`.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud zadaná okno je objekt rozšířeného rámce; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu PRAVDA, pokud *pWnd* je odvozena z jednoho z následujících tříd:

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

Tato metoda je užitečná, když se musí ověřit, že parametr funkce nebo metoda je okno rozšířeného rámce.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxpriv.h

### <a name="see-also"></a>Viz také

[CWnd – třída](cwnd-class.md)<br/>
[CFrameWndEx – třída](cframewndex-class.md)

## <a name="afxismfctoolbar"></a> Afxismfctoolbar –

Určuje, zda je okno daný objekt panelu nástrojů.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```
### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Ukazatel na objekt, který je odvozen z `CWnd`.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je okno zadaný objekt na panelu nástrojů v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí `TRUE` Pokud *pWnd* je odvozena z `CMFCToolBar`. Tato metoda je užitečná, když budete muset ověřit, že je parametr funkce nebo metoda `CMFCToolBar` objektu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxpriv.h

### <a name="see-also"></a>Viz také

[CWnd – třída](cwnd-class.md)<br/>
[CMFCToolBar – třída](cmfctoolbar-class.md)


## <a name="afxkeyboardmanager"></a> Afxkeyboardmanager –

Ukazatel na globální [klávesnice správce](ckeyboardmanager-class.md).

### <a name="syntax"></a>Syntaxe

```
CKeyboardManager* afxKeyboardManager;
```
### <a name="requirements"></a>Požadavky

**Záhlaví:** afxkeyboardmanager.h

### <a name="see-also"></a>Viz také

[Makra, globální funkce a globální proměnné](mfc-macros-and-globals.md)<br/>
[CKeyboardManager – třída](ckeyboardmanager-class.md)


##  <a name="afxloadlibrary"></a>  AfxLoadLibrary

Použití `AfxLoadLibrary` pro mapování modulu DLL.

```
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Parametry

*lpszModuleName*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název modulu (buď. Knihovna DLL nebo. Soubor EXE). Zadaný název je název souboru modulu.

Pokud řetězec Určuje cestu, ale soubor neexistuje v zadaném adresáři, funkce selže.

Pokud nezadáte cestu a příponu názvu souboru je vynechán, je výchozí příponou. Knihovna DLL je připojen. Název souboru řetězec však mohou obsahovat koncové bodu znak (.) k označení, že název modulu nemá žádná rozšíření. Pokud není zadaná žádná cesta, funkce hledá soubor v následujícím pořadí:

- Adresář, ze kterého se načíst aplikace.

- Aktuální adresář.

- **Windows 95/98:** systémový adresář Windows. **Windows NT:** systémový adresář Windows 32-bit. Název tohoto adresáře je SYSTEM32.

- **Pouze Windows NT:** systémový adresář Windows 16 bitů. Neexistuje žádná funkce Win32, který získá cestu tohoto adresáře, ale je prohledána. Název tohoto adresáře je systém.

- Adresář Windows.

- Adresáře, které jsou uvedeny v proměnné prostředí PATH.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota je popisovač modulu. Pokud funkce selže, vrácená hodnota je NULL.

### <a name="remarks"></a>Poznámky

Vrátí popisovač, který lze použít v [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress) k získání adresy funkce knihovny DLL. `AfxLoadLibrary` je také možné mapovat jiné spustitelných modulů.

Každý proces udržuje počet odkazů pro každý modul načíst knihovny. Tento počet odkazů je zvýšen pokaždé, když `AfxLoadLibrary` se nazývá a je snížen pokaždé, když `AfxFreeLibrary` je volána. Když počet odkazů dosáhne nuly, modul není mapován z adresního prostoru volajícího procesu a již není platný popisovač.

Nezapomeňte použít `AfxLoadLibrary` a `AfxFreeLibrary` (namísto funkce Win32 `LoadLibrary` a `FreeLibrary`) v případě, že vaše aplikace používá více vláken a dynamicky načtení rozšiřující knihovny DLL MFC. Pomocí `AfxLoadLibrary` a `AfxFreeLibrary` zajistí, že spuštění a vypnutí kód, který provede, když je načteny nebo uvolněny MFC – rozšiřující knihovny DLL nejsou poškozeny globální stav knihovny MFC.

Pomocí `AfxLoadLibrary` v aplikaci vyžaduje, abyste dynamicky propojené ke knihovně DLL verze knihovny MFC; hlavičkový soubor pro `AfxLoadLibrary`, Afxdll_.h, pouze je zahrnuta, pokud se MFC je propojena s aplikací jako knihovny DLL. To je záměrné, protože budete muset odkaz na knihovnu DLL verze knihovny MFC použít nebo vytvořit MFC – rozšiřující knihovny DLL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdll_.h

## <a name="afxmenutearoffmanager"></a> Afxmenutearoffmanager –

Ukazatel na globální [odtržené nabídky správce](cmenutearoffmanager-class.md).

### <a name="syntax"></a>Syntaxe

```
CMenuTearOffManager* g_pTearOffMenuManager;
```
### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmenutearoffmanager.h

### <a name="see-also"></a>Viz také

[CMenuTearOffManager – třída](cmenutearoffmanager-class.md)

## <a name="afxmousemanager"></a>  Afxmousemanager –

Ukazatel na globální [myši správce](cmousemanager-class.md).

### <a name="syntax"></a>Syntaxe

```
CMouseManager* afxMouseManager;
```
### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmousemanager.h

### <a name="see-also"></a>Viz také

[CMouseManager – třída](cmousemanager-class.md)



##  <a name="afxregisterclass"></a>  Afxregisterclass –

Tuto funkci použijte k registraci tříd oken v knihovně DLL, která používá knihovnu MFC.

```
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Parametry

*lpWndClass*<br/>
Ukazatel [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) struktura obsahující informace o třídě okna k registraci. Další informace o této struktuře naleznete v tématu Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je úspěšně zaregistrovaný třídy; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud použijete tuto funkci, třída je automaticky zrušit po uvolnění knihovny DLL.

V sestavení – knihovna DLL `AfxRegisterClass` identifikátor je definován jako makra, která se mapuje na funkci Windows `RegisterClass`, protože jsou automaticky odregistrovat třídy registrované v aplikaci. Pokud používáte `AfxRegisterClass` místo `RegisterClass`, svůj kód můžete použít beze změny v aplikaci a v knihovně DLL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxregisterwndclass"></a>  Afxregisterwndclass –

Umožňuje registrovat vlastní třídy oken.

```
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Parametry

*nClassStyle*<br/>
Určuje styl třídu Windows nebo kombinace stylů, vytvořené pomocí bitového operátoru OR ( **&#124;**) operátoru pro třídu okna. Seznam tříd stylů, najdete v článku [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) struktura v sadě Windows SDK. Pokud má hodnotu NULL, výchozí hodnoty nastavte následujícím způsobem:

- Nastaví styl myši CS_DBLCLKS, která odešle dvakrát klikněte na panel zpráv pro proceduru okna při poklepání myši.

- Nastaví styl šipky kurzor na standardní IDC_ARROW Windows.

- Nastaví štětec pozadí na hodnotu NULL, takže okna nebude vymazání jeho pozadí.

- Ikona loga Windows standard, Mávající příznak nastaví na ikonu.

*hCursor*<br/>
Určuje popisovač prostředku kurzoru nainstalovaný v každé okno vytvořené ze třídy okna. Pokud použijete výchozí hodnotu **0**, obdržíte standardní IDC_ARROW kurzoru.

*hbrBackground*<br/>
Určuje popisovač pro prostředek štětce nainstalovaný v každé okno vytvořené ze třídy okna. Pokud použijete výchozí hodnotu **0**, budete mít štětec pozadí NULL a okno, ve výchozím nastavení, nikoli vymaže jeho pozadí při zpracování [WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd).

*hIcon*<br/>
Určuje popisovač prostředku ikony nainstalovaný v každé okno vytvořené ze třídy okna. Pokud použijete výchozí hodnotu **0**, zobrazí se ikona loga Windows standard, Mávající příznak.

### <a name="return-value"></a>Návratová hodnota

Řetězec zakončený hodnotou null obsahující název třídy. Můžete předat tento název třídy a `Create` členské funkce v `CWnd` nebo jiné **CWnd –** odvozené třídy vytvořit okno. Název je generován knihovny Microsoft Foundation Class.

> [!NOTE]
>  Vrácená hodnota je ukazatel na statické vyrovnávací paměti. Uložte tento řetězec je přiřadit `CString` proměnné.

### <a name="remarks"></a>Poznámky

Knihovny Microsoft Foundation Class automaticky zaregistruje několik tříd standardní okno. Pokud chcete zaregistrovat vlastní třídy oken s voláním této funkce.

Název zaregistrovat pro třídu podle `AfxRegisterWndClass` závisí výhradně na parametry. Při volání `AfxRegisterWndClass` více než jednou s shodné parametry pouze registruje třídu při prvním volání. Následující volání `AfxRegisterWndClass` s shodné parametry jednoduše vrátit classname už zaregistrovaný.

Při volání `AfxRegisterWndClass` pro více třídy odvozené z CWnd s shodné parametry místo zobrazování samostatném okně třídy pro každou třídu, každá třída sdílí stejnou třídu okna. Pokud se používá třída stylu CS_CLASSDC to může způsobovat problémy. Místo více tříd oken CS_CLASSDC skončíte se jednu třídu okna CS_CLASSDC a všechny systémy windows C++, které používají tuto sdílenou složku třídy stejné řadič domény. Chcete-li tomuto problému vyhnout, zavolejte [afxregisterclass –](#afxregisterclass) registrovat třídu.

Odkazovat na technická Poznámka [TN001: registrace tříd oken](../../mfc/tn001-window-class-registration.md) Další informace o registrace tříd oken a `AfxRegisterWndClass` funkce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxsetperuserregistration"></a>  Afxsetperuserregistration –

Nastaví, zda aplikace přesměrovává přístup k registru do **HKEY_CURRENT_USER** ( **HKCU**) uzlu.

```
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] Hodnota TRUE označuje, že informace registru během směřuje k uzlu HKCU; Hodnota FALSE označuje, že aplikace zapíše informace registru do uzlu výchozí. Je výchozí uzel **HKEY_CLASSES_ROOT** ( **HKCR**).

### <a name="remarks"></a>Poznámky

Před Windows Vista, aplikace, které získat přístup k registru obvykle používají **HKEY_CLASSES_ROOT** uzlu. Windows Vista nebo novější operační systémy, však musíte spustit aplikaci v režimu se zvýšenými oprávněními pro zápis pro HKCR.

Tato metoda umožňuje vaší aplikaci ke čtení a zápis do registru bez spuštění v režimu se zvýšenými oprávněními přesměrováním přístup k registru z HKCR do HKCU. Další informace najdete v tématu [stránky vlastností Linkeru](../../ide/linker-property-pages.md).

Pokud povolíte registru přesměrování, rozhraní přesměrovává přístup k z HKCR **HKEY_CURRENT_USER\Software\Classes**. Pouze rozhraní MFC a ATL jsou ovlivněny přesměrování.

Výchozí implementace nemá přístup k registru pod HKCR.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxstat_.h

##  <a name="afxsetresourcehandle"></a>  Afxsetresourcehandle –

Pomocí této funkce můžete nastavit HINSTANCE popisovač, který určuje, kde jsou načteny výchozích prostředků aplikace.

```
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Parametry

*hInstResource*<br/>
Popisovač instance nebo modul. Souboru EXE nebo DLL souboru, ze kterého jsou načteny prostředků.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

## <a name="afxshellmanager"></a>  Afxshellmanager –

Ukazatel na globální [správce prostředí](cshellmanager-class.md).

### <a name="syntax"></a>Syntaxe

```
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxshellmanager.h

### <a name="see-also"></a>Viz také

[CShellManager – třída](cshellmanager-class.md)

##  <a name="afxsocketinit"></a>  Afxsocketinit –

Volejte tuto funkce ve vaší `CWinApp::InitInstance` přepsání se inicializovat rozhraní Windows Sockets.

```
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Parametry

*lpwsaData*<br/>
Ukazatel [wsadata –](../../mfc/reference/wsadata-structure.md) struktury. Pokud *lpwsaData* není shodný s hodnotou NULL, pak adresu `WSADATA` struktura je vyplněna voláním `WSAStartup`. Tato funkce také zajišťuje, že `WSACleanup` je volána pro vás předtím, než se aplikace ukončí.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Při použití soketů knihovny MFC v sekundárních vláken aplikace staticky propojené knihovny MFC, je nutné volat `AfxSocketInit` v každém vlákně, který používá sockets k inicializaci soketu knihovny. Ve výchozím nastavení `AfxSocketInit` je volána pouze v primárním vlákně.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxsock.h

## <a name="afxusertoolsmanager"></a>  Afxusertoolsmanager –

Ukazatel na globální [nástroje Správce uživatelů](cusertoolsmanager-class.md).

### <a name="syntax"></a>Syntaxe

```
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxusertoolsmanager.h

### <a name="see-also"></a>Viz také

[CUserToolsManager – třída](cusertoolsmanager-class.md)


##  <a name="afxwininit"></a>  Afxwininit –

Tato funkce je volána pomocí knihovny MFC zadané `WinMain` funkce, jako součást [CWinApp](../../mfc/reference/cwinapp-class.md) inicializace aplikace využívající grafické rozhraní, se inicializovat knihovnu MFC.

```
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Obslužná rutina modulu aktuálně spuštěné.

*hPrevInstance*<br/>
Popisovač pro předchozí instanci aplikace. Pro aplikace založené na Win32, tento parametr je vždy **NULL**.

*lpCmdLine*<br/>
Odkazuje na řetězec zakončený hodnotou null se zadáním příkazového řádku pro aplikaci.

*nCmdShow*<br/>
Určuje, jak by být zobrazena hlavní okno aplikace s grafickým uživatelským rozhraním.

### <a name="remarks"></a>Poznámky

Pro konzolovou aplikaci, která nepoužívá zadané MFC `WinMain` funkce, je nutné volat `AfxWinInit` přímo se inicializovat knihovnu MFC.

Při volání `AfxWinInit` sami, by měla deklarovat instanci `CWinApp` třídy. Pro konzolovou aplikaci, můžete se rozhodnout nechcete odvodit vlastní třídu z `CWinApp` a místo toho použít instanci `CWinApp` přímo. Tato technika je vhodné, pokud se rozhodnete opustit všechny funkce pro vaši aplikaci ve vaší implementaci **hlavní**.

> [!NOTE]
>  Při vytváření aktivační kontext pro sestavení, knihovna MFC používá prostředek manifestu modulu pro uživatele k dispozici. Aktivační kontext je vytvořen v `AfxWinInit`. Další informace najdete v tématu [podpora kontextů aktivace ve stavu modulu MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CWinApp – třída](../../mfc/reference/cwinapp-class.md)
