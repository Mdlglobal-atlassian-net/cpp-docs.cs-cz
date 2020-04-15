---
title: Třída CWinThread
ms.date: 11/04/2016
f1_keywords:
- CWinThread
- AFXWIN/CWinThread
- AFXWIN/CWinThread::CWinThread
- AFXWIN/CWinThread::CreateThread
- AFXWIN/CWinThread::ExitInstance
- AFXWIN/CWinThread::GetMainWnd
- AFXWIN/CWinThread::GetThreadPriority
- AFXWIN/CWinThread::InitInstance
- AFXWIN/CWinThread::IsIdleMessage
- AFXWIN/CWinThread::OnIdle
- AFXWIN/CWinThread::PostThreadMessage
- AFXWIN/CWinThread::PreTranslateMessage
- AFXWIN/CWinThread::ProcessMessageFilter
- AFXWIN/CWinThread::ProcessWndProcException
- AFXWIN/CWinThread::PumpMessage
- AFXWIN/CWinThread::ResumeThread
- AFXWIN/CWinThread::Run
- AFXWIN/CWinThread::SetThreadPriority
- AFXWIN/CWinThread::SuspendThread
- AFXWIN/CWinThread::m_bAutoDelete
- AFXWIN/CWinThread::m_hThread
- AFXWIN/CWinThread::m_nThreadID
- AFXWIN/CWinThread::m_pActiveWnd
- AFXWIN/CWinThread::m_pMainWnd
helpviewer_keywords:
- CWinThread [MFC], CWinThread
- CWinThread [MFC], CreateThread
- CWinThread [MFC], ExitInstance
- CWinThread [MFC], GetMainWnd
- CWinThread [MFC], GetThreadPriority
- CWinThread [MFC], InitInstance
- CWinThread [MFC], IsIdleMessage
- CWinThread [MFC], OnIdle
- CWinThread [MFC], PostThreadMessage
- CWinThread [MFC], PreTranslateMessage
- CWinThread [MFC], ProcessMessageFilter
- CWinThread [MFC], ProcessWndProcException
- CWinThread [MFC], PumpMessage
- CWinThread [MFC], ResumeThread
- CWinThread [MFC], Run
- CWinThread [MFC], SetThreadPriority
- CWinThread [MFC], SuspendThread
- CWinThread [MFC], m_bAutoDelete
- CWinThread [MFC], m_hThread
- CWinThread [MFC], m_nThreadID
- CWinThread [MFC], m_pActiveWnd
- CWinThread [MFC], m_pMainWnd
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
ms.openlocfilehash: f2e95dd3ba8be31633590e37d95dedc8749ebdd8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367422"
---
# <a name="cwinthread-class"></a>Třída CWinThread

Představuje vlákno provádění v rámci aplikace.

## <a name="syntax"></a>Syntaxe

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CWinThread::CWinThread](#cwinthread)|Vytvoří `CWinThread` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CWinThread::Vytvořit vlákno](#createthread)|Spustí spuštění `CWinThread` objektu.|
|[CWinThread::Instance ukončení](#exitinstance)|Přepište vyčistit, když vaše vlákno ukončí.|
|[CWinThread::GetMainWnd](#getmainwnd)|Načte ukazatel na hlavní okno pro vlákno.|
|[CWinThread::GetThreadPriority](#getthreadpriority)|Získá prioritu aktuální vlákno.|
|[CWinThread::InitInstance](#initinstance)|Přepište provést inicializaci instancí vlákna.|
|[CWinThread::IsidleMessage](#isidlemessage)|Kontroluje speciální zprávy.|
|[CWinThread::OnIdle](#onidle)|Přepsat provádět zpracování nečinnosti specifické pro vlákno.|
|[CWinThread::PostThreadMessage](#postthreadmessage)|Odešle zprávu `CWinThread` jinému objektu.|
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtruje zprávy před jejich odesláním do funkcí systému Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).|
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Zachytí určité zprávy dříve, než se dostanou do aplikace.|
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Zachytí všechny neošetřené výjimky vyzývané obslužnými rutinami zpráv a příkazů vlákna.|
|[CWinThread::PumpMessage](#pumpmessage)|Obsahuje smyčku zpráv vlákna.|
|[CWinThread::ResumeThread](#resumethread)|Sníží počet pozastavení vlákna.|
|[CWinThread::Spustit](#run)|Ovládání funkce pro závity s čerpadlem zpráv. Přepsáním můžete přizpůsobit výchozí smyčku zpráv.|
|[CWinThread::SetThreadPriority](#setthreadpriority)|Nastaví prioritu aktuálního vlákna.|
|[CWinThread::Pozastavit vlákno](#suspendthread)|Zintáží počet pozastavení vlákna.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CWinThread::POPISOVAČ operátora](#operator_handle)|Načte popisovač `CWinThread` objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Určuje, zda má být objekt při ukončení podprocesu znečit.|
|[CWinThread::m_hThread](#m_hthread)|Zpracovat aktuální vlákno.|
|[CWinThread::m_nThreadID](#m_nthreadid)|ID aktuálního vlákna.|
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Ukazatel na hlavní okno aplikace kontejneru, když je server OLE aktivní.|
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Obsahuje ukazatel na hlavní okno aplikace.|

## <a name="remarks"></a>Poznámky

Hlavní vlákno provádění je obvykle poskytováno objektem `CWinApp`odvozeným z ; `CWinApp` je odvozen `CWinThread`od . Další `CWinThread` objekty umožňují více vláken v rámci dané aplikace.

Existují dva obecné typy podprocesů, které `CWinThread` podporuje: pracovní vlákna a vlákna uživatelského rozhraní. Pracovní vlákna nemají žádné čerpadlo zpráv: například vlákno, které provádí výpočty na pozadí v tabulkové matné aplikaci. Vlákna uživatelského rozhraní mají čerpadlo zpráv a zpracovávají zprávy přijaté ze systému. [CWinApp](../../mfc/reference/cwinapp-class.md) a třídy odvozené z něj jsou příklady vláken uživatelského rozhraní. Ostatní vlákna uživatelského rozhraní lze také `CWinThread`odvodit přímo z aplikace .

Objekty `CWinThread` třídy obvykle existují po dobu trvání vlákna. Chcete-li toto chování změnit, nastavte [m_bAutoDelete](#m_bautodelete) na hodnotu NEPRAVDA.

Třída `CWinThread` je nezbytné, aby váš kód a Knihovna MFC plně zřetězené. Místní data podprocesu používaná v rámci k `CWinThread` udržování informací specifických pro vlákno jsou spravována objekty. Z důvodu této `CWinThread` závislosti na zpracování místních dat podprocesu, všechny podprocesy, které používá knihovnu MFC musí být vytvořen knihovnou MFC. Například vlákno vytvořené funkcí za běhu [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) nelze použít žádná rozhraní API knihovny MFC.

Chcete-li vytvořit vlákno, volejte [AfxBeginThread](application-information-and-management.md#afxbeginthread). Existují dva formuláře, v závislosti na tom, zda chcete pracovní nebo uživatelské rozhraní podprocesu. Pokud chcete vlákno uživatelského rozhraní, `AfxBeginThread` předejte `CRuntimeClass` ukazatel `CWinThread`na třídu -derived. Pokud chcete vytvořit pracovní podproces, `AfxBeginThread` přejděte ukazatel na řídící funkci a parametr na řídící funkci. Pro pracovní vlákna i vlákna uživatelského rozhraní můžete určit volitelné parametry, které upravují prioritu, velikost zásobníku, příznaky vytvoření a atributy zabezpečení. `AfxBeginThread`vrátí ukazatel na nový `CWinThread` objekt.

Místo volání `AfxBeginThread`můžete vytvořit `CWinThread`odvozený objekt a `CreateThread`potom volat . Tato dvoustupňová metoda konstrukce je užitečná, `CWinThread` pokud chcete znovu použít objekt mezi následným vytvářením a ukončením provádění podprocesů.

Další informace `CWinThread`o tématu naleznete v článcích [Multithreading s c++ a MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading: Vytváření vláken uživatelského rozhraní](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading: Vytváření pracovních vláken](../../parallel/multithreading-creating-worker-threads.md)a [Multithreading: Jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cwinthreadcreatethread"></a><a name="createthread"></a>CWinThread::Vytvořit vlákno

Vytvoří vlákno, které se provede v adresním prostoru volajícího procesu.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parametry

*dwCreateFlags*<br/>
Určuje další příznak, který řídí vytváření vlákna. Tento příznak může obsahovat jednu ze dvou hodnot:

- CREATE_SUSPENDED Spusťte vlákno s počtem pozastavení jednoho. Použijte CREATE_SUSPENDED, pokud chcete inicializovat `CWinThread` data členů objektu, například [m_bAutoDelete](#m_bautodelete) nebo členy odvozené třídy, před spuštěním vlákna. Po dokončení inicializace použijte [CWinThread::ResumeThread](#resumethread) ke spuštění vlákna. Vlákno se nespustí, dokud `CWinThread::ResumeThread` není voláno.

- **0** Spusťte vlákno ihned po vytvoření.

*nStackSize*<br/>
Určuje velikost v bajtů zásobníku pro nové vlákno. Pokud **0**, velikost zásobníku výchozí na stejnou velikost jako v procesu primární vlákno.

*lpSecurityAttrs*<br/>
Odkazuje na [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) strukturu, která určuje atributy zabezpečení pro vlákno.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je vlákno úspěšně vytvořeno; jinak 0.

### <a name="remarks"></a>Poznámky

Slouží `AfxBeginThread` k vytvoření objektu vlákna a jeho spuštění v jednom kroku. Použijte, `CreateThread` pokud chcete znovu použít objekt podprocesu mezi po sobě jdoucí vytváření a ukončení spuštění podprocesů.

## <a name="cwinthreadcwinthread"></a><a name="cwinthread"></a>CWinThread::CWinThread

Vytvoří `CWinThread` objekt.

```
CWinThread();
```

### <a name="remarks"></a>Poznámky

Chcete-li zahájit provádění vlákna, zavolejte člennou funkci [CreateThread.](#createthread) Obvykle vytvoříte vlákna voláním [AfxBeginThread](application-information-and-management.md#afxbeginthread), který `CreateThread`bude volat tento konstruktor a .

## <a name="cwinthreadexitinstance"></a><a name="exitinstance"></a>CWinThread::Instance ukončení

Volat rámci z v rámci zřídka přepsané [Run](#run) členské funkce ukončit tuto instanci podprocesu, nebo pokud volání [InitInstance](#initinstance) nezdaří.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Návratová hodnota

Ukončovací kód vlákna; 0 označuje žádné chyby a hodnoty větší než 0 označují chybu. Tuto hodnotu lze načíst voláním [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Poznámky

Nevolejte tuto člennou funkci odkudkoliv, ale v rámci `Run` členské funkce. Tato členská funkce se používá pouze v vláknech uživatelského rozhraní.

Výchozí implementace této funkce odstraní `CWinThread` objekt, pokud [je m_bAutoDelete](#m_bautodelete) TRUE. Přepsat tuto funkci, pokud chcete provést další vyčištění při ukončení podprocesu. Implementace `ExitInstance` by měla volat verzi základní třídy po spuštění kódu.

## <a name="cwinthreadgetmainwnd"></a><a name="getmainwnd"></a>CWinThread::GetMainWnd

Pokud je vaše aplikace server OLE, volání této funkce načíst ukazatel na aktivní hlavní `m_pMainWnd` okno aplikace namísto přímo odkazovat na člena objektu aplikace.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>Návratová hodnota

Tato funkce vrátí ukazatel na jeden ze dvou typů oken. Pokud je vlákno součástí serveru OLE a má objekt, který je aktivní uvnitř aktivního kontejneru, vrátí tato `CWinThread` funkce datový člen [CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) objektu.

Pokud neexistuje žádný objekt, který je aktivní v rámci kontejneru nebo aplikace není server EM, vrátí tato funkce [m_pMainWnd](#m_pmainwnd) datový člen objektu podprocesu.

### <a name="remarks"></a>Poznámky

Pro vlákna uživatelského rozhraní je to ekvivalentní `m_pActiveWnd` přímému odkazování na člen objektu aplikace.

Pokud vaše aplikace není server OLE, volání této funkce je `m_pMainWnd` ekvivalentní přímo odkazující na člen objektu aplikace.

Přepište tuto funkci a upravte výchozí chování.

## <a name="cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a>CWinThread::GetThreadPriority

Získá aktuální úroveň priority vlákna tohoto vlákna.

```
int GetThreadPriority();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální úroveň priority podprocesu v rámci své třídy priority. Vrácená hodnota bude jedna z následujících hodnot, která je uvedena od nejvyšší priority po nejnižší:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Další informace o těchto prioritách naleznete v tématu [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v sadě Windows SDK.

## <a name="cwinthreadinitinstance"></a><a name="initinstance"></a>CWinThread::InitInstance

`InitInstance`musí být přepsána, aby se inicializovala každá nová instance vlákna uživatelského rozhraní.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je inicializace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Obvykle přepsat `InitInstance` provádět úkoly, které musí být dokončeny při prvním vytvoření vlákna.

Tato členská funkce se používá pouze v vláknech uživatelského rozhraní. Proveďte inicializaci pracovních podprocesů v řídící funkci předané [afxBeginThread](application-information-and-management.md#afxbeginthread).

## <a name="cwinthreadisidlemessage"></a><a name="isidlemessage"></a>CWinThread::IsidleMessage

Přepsat tuto funkci `OnIdle` zabránit volání po vygenerování určitých zpráv.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Odkazuje na aktuální zprávu, která je zpracovávána.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud `OnIdle` by měla být volána po zpracování zprávy; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace nevolá `OnIdle` po redundantní zprávy myši a zprávy generované blikající stříšky.

Pokud aplikace vytvořila krátký `OnIdle` časovač, bude volána často, což způsobuje problémy s výkonem. Chcete-li zlepšit výkon takové aplikace, přepište `IsIdleMessage` `CWinApp`v odvozené třídě aplikace a zkontrolujte WM_TIMER zprávy následujícím způsobem:

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

Zpracování WM_TIMER tímto způsobem zlepší výkon aplikací, které používají krátké časovače.

## <a name="cwinthreadm_bautodelete"></a><a name="m_bautodelete"></a>CWinThread::m_bAutoDelete

Určuje, `CWinThread` zda má být objekt automaticky odstraněn při ukončení podprocesu.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Poznámky

Datový `m_bAutoDelete` člen je veřejná proměnná typu BOOL.

Hodnota `m_bAutoDelete` nemá vliv na to, jak je uzavřen základní popisovač vlákna, ale má vliv na časování zavření popisovače. Popisovač podprocesu je `CWinThread` vždy uzavřen, když je objekt zničen.

## <a name="cwinthreadm_hthread"></a><a name="m_hthread"></a>CWinThread::m_hThread

Rukojeť k závitu připojenému k tomuto `CWinThread`.

```
HANDLE m_hThread;
```

### <a name="remarks"></a>Poznámky

Datový `m_hThread` člen je veřejná proměnná typu HANDLE. Je platný pouze v případě, že základní objekt vlákna jádra v současné době existuje a popisovač ještě nebyl uzavřen.

Destruktor CWinThread volá `m_hThread`closeHandle na . Pokud [m_bAutoDelete](#m_bautodelete) je true při ukončení podprocesu, CWinThread objekt je zničen, což zruší platnost všech ukazatelů cWinThread objektu a jeho členské proměnné. Může být `m_hThread` nutné člen zkontrolovat hodnotu ukončení podprocesu nebo čekat na signál. Chcete-li zachovat CWinThread `m_hThread` objekt a jeho člen během `m_bAutoDelete` provádění podprocesu a po jeho ukončení, nastavte na FALSE před povolením provádění podprocesu pokračovat. V opačném případě může vlákno ukončit, zničit cwinthread objekt a zavřít popisovač před pokusem o jeho použití. Pokud použijete tuto techniku, jste zodpovědní za odstranění CWinThread objektu.

## <a name="cwinthreadm_nthreadid"></a><a name="m_nthreadid"></a>CWinThread::m_nThreadID

ID závitu připojeného `CWinThread`k tomuto .

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>Poznámky

Datový `m_nThreadID` člen je veřejná proměnná typu DWORD. Je platný pouze v případě, že základní objekt vlákna jádra v současné době existuje.
Viz také poznámky o [m_hThread](#m_hthread) životnosti.

### <a name="example"></a>Příklad

  Viz příklad pro [AfxGetThread](application-information-and-management.md#afxgetthread).

## <a name="cwinthreadm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinThread::m_pActiveWnd

Tento datový člen slouží k uložení ukazatele na aktivní objekt okna vlákna.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>Poznámky

Knihovna tříd Microsoft Foundation automaticky ukončí vaše vlákno, když je okno, na které `m_pActiveWnd` odkazuje. Pokud toto vlákno je primární vlákno pro aplikaci, aplikace bude také ukončena. Pokud je tento datový člen NULL, bude `CWinApp` zděděno aktivní okno pro objekt aplikace. `m_pActiveWnd`je veřejná proměnná typu `CWnd*`.

Obvykle nastavíte tuto členovou proměnnou při přepsání `InitInstance`. V pracovním vlákně je hodnota tohoto datového člena zděděna z nadřazeného vlákna.

## <a name="cwinthreadm_pmainwnd"></a><a name="m_pmainwnd"></a>CWinThread::m_pMainWnd

Tento datový člen slouží k uložení ukazatele na hlavní objekt okna vlákna.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>Poznámky

Knihovna tříd Microsoft Foundation automaticky ukončí vaše vlákno, když je okno, na které `m_pMainWnd` odkazuje. Pokud toto vlákno je primární vlákno pro aplikaci, aplikace bude také ukončena. Pokud je tento datový člen NULL, hlavní `CWinApp` okno pro objekt aplikace se použije k určení, kdy ukončit vlákno. `m_pMainWnd`je veřejná proměnná typu `CWnd*`.

Obvykle nastavíte tuto členovou proměnnou při přepsání `InitInstance`. V pracovním vlákně je hodnota tohoto datového člena zděděna z nadřazeného vlákna.

## <a name="cwinthreadonidle"></a><a name="onidle"></a>CWinThread::OnIdle

Přepsat tuto člennou funkci provádět zpracování nečinnosti.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parametry

*lPočet*<br/>
Čítač se pokaždé, když `OnIdle` je volána, když je prázdná fronta zpráv vlákna. Tento počet se při každém zpracování nové zprávy resetuje na 0. Parametr *lCount* můžete použít k určení relativní doby, po kterou bylo vlákno nečinné bez zpracování zprávy.

### <a name="return-value"></a>Návratová hodnota

Nenulová pro příjem více času zpracování nečinnosti; 0, pokud není potřeba žádná další doba zpracování nečinnosti.

### <a name="remarks"></a>Poznámky

`OnIdle`je volána ve výchozí smyčce zpráv, když je fronta zpráv vlákna prázdná. Pomocí přepsání můžete volat vlastní úlohy obslužné rutiny na pozadí.

`OnIdle`by měl vrátit 0 označuje, že není vyžadována žádná další doba zpracování nečinnosti. Parametr *lCount* se zpřísňuje pokaždé, když `OnIdle` je volána fronta zpráv prázdná a při každém zpracování nové zprávy se obnoví na 0. Můžete volat různé nečinné rutiny na základě tohoto počtu.

Výchozí implementace této členské funkce uvolní dočasné objekty a nepoužívané knihovny dynamických odkazů z paměti.

Tato členská funkce se používá pouze v vláknech uživatelského rozhraní.

Vzhledem k tomu, `OnIdle` že aplikace nemůže zpracovat zprávy, dokud nevrátí, neprovádějte zdlouhavé úlohy v této funkci.

## <a name="cwinthreadoperator-handle"></a><a name="operator_handle"></a>CWinThread::POPISOVAČ operátora

Načte popisovač `CWinThread` objektu.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač objektu podprocesu; jinak NULL.

### <a name="remarks"></a>Poznámky

Pomocí popisovače můžete přímo volat řešení API systému Windows.

## <a name="cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a>CWinThread::PostThreadMessage

Volána k odeslání uživatelem `CWinThread` definované zprávy do jiného objektu.

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Zprávu*<br/>
ID uživatelem definované zprávy.

*wParam*<br/>
První parametr zprávy.

*Lparam*<br/>
Druhý parametr zprávy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Zaúčtovaná zpráva je mapována na správnou obslužnou rutinu zprávy makro ON_THREAD_MESSAGE mapy zprávy.

> [!NOTE]
> Při volání [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew), zpráva je umístěna ve frontě zpráv vlákna. Protože však zprávy zaúčtované tímto způsobem nejsou přidruženy k oknu, knihovna MFC je neodešle do obslužných rutin zpráv nebo příkazů. Chcete-li zpracovat tyto zprávy, přepsat `PreTranslateMessage()` funkci třídy odvozené CWinApp a zpracovat zprávy ručně.

## <a name="cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a>CWinThread::PreTranslateMessage

Přepsat tuto funkci filtrovat okno zprávy před jejich odesláním do funkcí systému Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Odkazuje na [strukturu MSG](/windows/win32/api/winuser/ns-winuser-msg) obsahující zprávu ke zpracování.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla zpráva `PreTranslateMessage` plně zpracována a neměla by být dále zpracována. Nula, pokud by zpráva měla být zpracována normálním způsobem.

### <a name="remarks"></a>Poznámky

Tato členská funkce se používá pouze v vláknech uživatelského rozhraní.

## <a name="cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinThread::ProcessMessageFilter

Funkce zavěšení rozhraní volá tuto členská funkci k filtrování a odpovědi na určité zprávy systému Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*Kód*<br/>
Určuje kód háku. Tato členská funkce používá kód k určení způsobu zpracování *lpMsg.*

*lpMsg*<br/>
Ukazatel na [strukturu MSG](/windows/win32/api/winuser/ns-winuser-msg)systému Windows .

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je zpráva zpracována; jinak 0.

### <a name="remarks"></a>Poznámky

Háček funkce zpracovává události před jejich odesláním do aplikace normální zpracování zpráv.

Pokud přepíšete tuto pokročilou funkci, nezapomeňte volat verzi základní třídy pro zachování zpracování zavěšení rozhraní.

## <a name="cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinThread::ProcessWndProcException

Rozhraní Framework volá tuto členskou funkci vždy, když obslužná rutina nezachytí výjimku vyženou v jedné z obslužných rutin zprávy nebo příkazu vašeho vlákna.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*E*<br/>
Odkazuje na neošetřenou výjimku.

*pMsg*<br/>
Odkazuje na [strukturu MSG](/windows/win32/api/winuser/ns-winuser-msg) obsahující informace o zprávě systému Windows, která způsobila, že rozhraní bylo vyvoláno výjimkou.

### <a name="return-value"></a>Návratová hodnota

-1, pokud je generována WM_CREATE výjimka; jinak 0.

### <a name="remarks"></a>Poznámky

Nevolejte tuto člennou funkci přímo.

Výchozí implementace této členské funkce zpracovává pouze výjimky generované z následujících zpráv:

|Příkaz|Akce|
|-------------|------------|
|WM_CREATE|Selhání.|
|WM_PAINT|Ověřte ovlivněné okno, čímž zabráníte generování jiné WM_PAINT zprávy.|

Přepsat tuto členská funkci poskytnout globální zpracování výjimek. Základní funkce zavolejte pouze v případě, že chcete zobrazit výchozí chování.

Tato členská funkce se používá pouze ve vláknech, která mají čerpadlo zpráv.

## <a name="cwinthreadpumpmessage"></a><a name="pumpmessage"></a>CWinThread::PumpMessage

Obsahuje smyčku zpráv vlákna.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>Poznámky

`PumpMessage`obsahuje smyčku zpráv vlákna. `PumpMessage`je volána `CWinThread` k čerpání zprávy vlákna. Můžete volat `PumpMessage` přímo vynutit zprávy, které mají `PumpMessage` být zpracovány, nebo můžete přepsat změnit jeho výchozí chování.

Volání `PumpMessage` přímo a přepsání jeho výchozí chování se doporučuje pouze pro pokročilé uživatele.

## <a name="cwinthreadresumethread"></a><a name="resumethread"></a>CWinThread::ResumeThread

Nazývá se pokračovat v provádění podprocesu, který byl pozastaven funkce člena [SuspendThread](#suspendthread) nebo podproces vytvořený s příznakem CREATE_SUSPENDED.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>Návratová hodnota

Předchozí počet pozastavení podprocesu v případě úspěchu; `0xFFFFFFFF` v opačném případě. Pokud je vrácená hodnota nulová, aktuální vlákno nebylo pozastaveno. Pokud je vrácená hodnota jedna, vlákno bylo pozastaveno, ale nyní je restartováno. Jakákoli vrácená hodnota větší než jedna znamená, že vlákno zůstane pozastaveno.

### <a name="remarks"></a>Poznámky

Počet pozastavení aktuálního vlákna je snížen o jednu. Pokud je počet pozastavení snížen na nulu, podproces obnoví provádění; jinak vlákno zůstane pozastaveno.

## <a name="cwinthreadrun"></a><a name="run"></a>CWinThread::Spustit

Poskytuje výchozí smyčku zpráv pro vlákna uživatelského rozhraní.

```
virtual int Run();
```

### <a name="return-value"></a>Návratová hodnota

**Int** hodnota, která je vrácena podprocesem. Tuto hodnotu lze načíst voláním [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Poznámky

`Run`získává a odesílá zprávy systému Windows, dokud aplikace neobdrží [zprávu WM_QUIT.](/windows/win32/winmsg/wm-quit) Pokud fronta zpráv vlákna aktuálně neobsahuje žádné zprávy, `Run` volání `OnIdle` k provedení zpracování nečinnosti. Příchozí zprávy přejdou na členskou funkci [PreTranslateMessage](#pretranslatemessage) pro speciální zpracování a potom na funkci Systému Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) pro standardní překlad klávesnice. Nakonec [dispatchmessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) windows funkce je volána.

`Run`je zřídka přepsána, ale můžete přepsat implementovat zvláštní chování.

Tato členská funkce se používá pouze v vláknech uživatelského rozhraní.

## <a name="cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a>CWinThread::SetThreadPriority

Tato funkce nastaví úroveň priority aktuálního vlákna v rámci své třídy priority.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>Parametry

*nPriorita*<br/>
Určuje novou úroveň priority vlákna v rámci třídy priority. Tento parametr musí být jednou z následujících hodnot, které jsou uvedeny od nejvyšší priority po nejnižší:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Další informace o těchto prioritách naleznete v tématu [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Může být volána pouze po [CreateThread](#createthread) úspěšně vrátí.

## <a name="cwinthreadsuspendthread"></a><a name="suspendthread"></a>CWinThread::Pozastavit vlákno

Zintáží počet pozastavení aktuálního vlákna.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>Návratová hodnota

Předchozí počet pozastavení podprocesu v případě úspěchu; `0xFFFFFFFF` v opačném případě.

### <a name="remarks"></a>Poznámky

Pokud má některé vlákno počet pozastavení nad nulou, toto vlákno se nespustí. Vlákno lze obnovit voláním funkce člena [ResumeThread.](#resumethread)

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWinApp – třída](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
