---
title: CWinThread – třída
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
ms.openlocfilehash: 4d3582493489faf44afece9338b1491620ca798a
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504658"
---
# <a name="cwinthread-class"></a>CWinThread – třída

Představuje vlákno provádění v rámci aplikace.

## <a name="syntax"></a>Syntaxe

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CWinThread::CWinThread](#cwinthread)|Vytvoří `CWinThread` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CWinThread::CreateThread](#createthread)|Spustí provádění `CWinThread` objektu.|
|[CWinThread::ExitInstance](#exitinstance)|Přepsání nastavení za účelem vyčištění při ukončení vašeho vlákna.|
|[CWinThread::GetMainWnd](#getmainwnd)|Načte ukazatel do hlavního okna pro vlákno.|
|[CWinThread::GetThreadPriority](#getthreadpriority)|Získá prioritu aktuálního vlákna.|
|[CWinThread::InitInstance](#initinstance)|Přepsání nastavení za účelem provedení inicializace instance podprocesu.|
|[CWinThread::IsIdleMessage](#isidlemessage)|Kontroly pro speciální zprávy.|
|[CWinThread::OnIdle](#onidle)|Přepsání nastavení za účelem zpracování specifické pro vlákno doby nečinnosti.|
|[CWinThread::PostThreadMessage](#postthreadmessage)|Odešle zprávu do jiného `CWinThread` objektu.|
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtruje zprávy před odesláním do funkce Windows [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage).|
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Zachycuje určité zprávy dřív, než dorazí aplikace.|
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Zachycuje všechny neošetřené výjimky vyvolané vlákna zprávu a obslužné rutiny příkazů.|
|[CWinThread::PumpMessage](#pumpmessage)|obsahuje smyčku zpráv vlákna.|
|[CWinThread::ResumeThread](#resumethread)|Dekrementuje vlákna pozastaví count.|
|[CWinThread::Run](#run)|Řídící funkce pro vlákna s pumpu zpráv. Přepsání nastavení za účelem přizpůsobení výchozí smyčku zpráv.|
|[CWinThread::SetThreadPriority](#setthreadpriority)|Nastaví prioritu aktuálního vlákna.|
|[CWinThread::SuspendThread](#suspendthread)|Zvýší a vlákna pozastaví count.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CWinThread::operator POPISOVAČ](#operator_handle)|Načte popisovač `CWinThread` objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Určuje, jestli se má zničit objekt při ukončení vlákna.|
|[CWinThread::m_hThread](#m_hthread)|Zpracování pro aktuální vlákno.|
|[CWinThread::m_nThreadID](#m_nthreadid)|ID aktuálního vlákna.|
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Ukazatel na hlavní okno aplikace typu kontejner, když OLE server je na místě aktivní.|
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Drží ukazatel hlavního okna aplikace.|

## <a name="remarks"></a>Poznámky

Hlavní vlákno provádění obvykle poskytuje objektu odvozeného od `CWinApp`; `CWinApp` je odvozen z `CWinThread`. Další `CWinThread` objekty povolit více vláken v rámci dané aplikace.

Existují dva hlavní typy vláken, která `CWinThread` podporuje: pracovních vláken a vlákna uživatelského rozhraní. Pracovní vlákna mít žádné pumpu zpráv: například vlákno, které provádí výpočty na pozadí v tabulce aplikace. Vlákna uživatelského rozhraní mají pumpu zpráv a zpracovávat zprávy přijaté ze systému. [CWinApp](../../mfc/reference/cwinapp-class.md) a třídy odvozené z něj jsou příkladem vlákna uživatelského rozhraní. Ostatní vlákna uživatelského rozhraní může být také odvozena přímo z `CWinThread`.

Objekty třídy `CWinThread` obvykle existuje po dobu trvání vlákna. Pokud chcete toto chování změnit, nastavte [m_bAutoDelete](#m_bautodelete) na hodnotu FALSE.

`CWinThread` Třída je nutné vytvářet kód a knihovna MFC plně bezpečným pro vlákno. Thread local data používané rozhraním Udržovat informace specifické pro vlákno je spravován `CWinThread` objekty. Z důvodu této závislosti na `CWinThread` zpracování dat thread local, musí být libovolného vlákna, která používá knihovnu MFC vytvořeného rozhraním MFC. Například vlákno vytvořil funkci run-time [_beginthread _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) nelze použít libovolné rozhraní API knihovny MFC.

Chcete-li vytvořit vlákno, volejte [AfxBeginThread](application-information-and-management.md#afxbeginthread). Existují dva typy, v závislosti na tom, zda má být vlákno pracovních procesů nebo uživatelského rozhraní. Pokud chcete, aby vlákno uživatelského rozhraní, předat `AfxBeginThread` ukazatel `CRuntimeClass` z vaší `CWinThread`-odvozené třídy. Pokud chcete vytvořit pracovní vlákno, předat `AfxBeginThread` ukazatel na řídící funkce a parametr řídící funkce. Pracovní vlákna a vlákna uživatelského rozhraní můžete určit volitelné parametry, které mění prioritu, velikost zásobníku, příznaky vytváření a atributy zabezpečení. `AfxBeginThread` vrátí ukazatel na novou `CWinThread` objektu.

Namísto volání metody `AfxBeginThread`, můžete vytvořit `CWinThread`-odvozené objekt a poté zavolejte `CreateThread`. Tato metoda dvoufázová konstrukce je užitečná, pokud chcete znovu použít `CWinThread` objektu mezi po sobě jdoucích vytváření a ukončení vlákna provádění.

Další informace o `CWinThread`, najdete v článcích [Multithreading s C++ a knihovnou MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading: Vytváření vláken uživatelského rozhraní](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading: Vytváření pracovních vláken](../../parallel/multithreading-creating-worker-threads.md), a [Multithreading: Jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="createthread"></a>  CWinThread::CreateThread

Vytvoří vlákno k provedení v rámci adresového prostoru volajícího procesu.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parametry

*dwCreateFlags*<br/>
Určuje další příznak, který řídí vytvoření vlákna. Tento příznak může obsahovat jednu ze dvou hodnot:

- CREATE_SUSPENDED spustit vlákno s pozastaveným počtem jedna. CREATE_SUSPENDED použijte, pokud chcete inicializovat všechna data členů objektu `CWinThread` objektů, jako například [m_bAutoDelete](#m_bautodelete) nebo všechny členy odvozené třídy před spuštěním podprocesu. Po dokončení inicializace použít [CWinThread::ResumeThread](#resumethread) spustit vlákno spuštěné. Vlákno nebude spuštěno až do `CWinThread::ResumeThread` je volána.

- **0** spuštění vlákna ihned po vytvoření.

*nStackSize*<br/>
Určuje velikost v bajtech zásobníku pro nové vlákno. Pokud **0**, výchozí velikost zásobníku se stejnou velikostí jako u primární vlákno procesu.

*lpSecurityAttrs*<br/>
Odkazuje [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) struktura, která určuje atributy zabezpečení pro vlákno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je vlákno vytvořeno úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Použití `AfxBeginThread` k vytvoření objektu vlákna a spustit v jednom kroku. Použití `CreateThread` Pokud chcete znovu použít objekt vlákna mezi po sobě jdoucích vytváření a ukončení vlákna provádění.

##  <a name="cwinthread"></a>  CWinThread::CWinThread

Vytvoří `CWinThread` objektu.

```
CWinThread();
```

### <a name="remarks"></a>Poznámky

Chcete-li zahájit provádění vlákna, zavolejte [CreateThread](#createthread) členskou funkci. Obvykle vytvoříte vlákna voláním [AfxBeginThread](application-information-and-management.md#afxbeginthread), který zavolá tento konstruktor a `CreateThread`.

##  <a name="exitinstance"></a>  CWinThread::ExitInstance

Volá se rozhraním z v rámci zřídka přepsané [spustit](#run) členské funkce ukončila tato instance vlákna, nebo pokud je volání [InitInstance](#initinstance) selže.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Návratová hodnota

Ukončovací kód vlákna; 0 nejsou zjištěny žádné chyby a hodnoty větší než 0 udávající chybu. Tuto hodnotu můžete získat voláním [GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Poznámky

Nevolejte tuto funkci člena z libovolného místa ale v rámci `Run` členskou funkci. Tato členská funkce se používá jenom v vlákna uživatelského rozhraní.

Odstraní výchozí implementaci této funkce `CWinThread` objekt by [m_bAutoDelete](#m_bautodelete) má hodnotu TRUE. Tato funkce přepište, pokud budete chtít provést další vyčištění při ukončení vašeho vlákna. Implementace `ExitInstance` by měly volat základní třídy verzi, po provedení kódu.

##  <a name="getmainwnd"></a>  CWinThread::GetMainWnd

Pokud je vaše aplikace serveru OLE, volání této funkce načtete ukazatel na aktivní hlavní okno aplikace namísto přímo odkazující na `m_pMainWnd` člen objektu aplikace.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>Návratová hodnota

Tato funkce vrací ukazatel na jeden ze dvou typů systému windows. Pokud vašeho vlákna je součástí serveru OLE a má objekt, který je na místě aktivní uvnitř aktivní kontejner, vrátí tato funkce [CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) datový člen třídy `CWinThread` objektu.

Pokud není žádný objekt, který je na místě aktivní v rámci kontejneru nebo aplikace není OLE server, vrátí tato funkce [m_pMainWnd](#m_pmainwnd) datový člen objektu vlákna.

### <a name="remarks"></a>Poznámky

Pro vlákna uživatelského rozhraní, jde o ekvivalent přímo odkazující na `m_pActiveWnd` člen objektu aplikace.

Pokud vaše aplikace není OLE server, pak volání této funkce je ekvivalentní k přímo odkazující na `m_pMainWnd` člen objektu aplikace.

Tuto funkci chcete změnit výchozí chování přepište.

##  <a name="getthreadpriority"></a>  CWinThread::GetThreadPriority

Získá aktuální úroveň priority vlákna tohoto vlákna.

```
int GetThreadPriority();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální úroveň priority vlákna ve své třídě priorit. Vrácená hodnota bude jeden z těchto možností uvedených od nejvyšší priority po nejnižší:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Další informace o těchto priorit, naleznete v tématu [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v sadě Windows SDK.

##  <a name="initinstance"></a>  CWinThread::InitInstance

`InitInstance` musí být potlačena za účelem inicializace každou novou instanci třídy vlákna uživatelského rozhraní.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se inicializace je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Obvykle je přepsat `InitInstance` k provádění úloh, kterou je potřeba provést při prvním vytvoření vlákna.

Tato členská funkce se používá jenom v vlákna uživatelského rozhraní. Provést inicializaci pracovních vláken v řídící funkce předány [AfxBeginThread](application-information-and-management.md#afxbeginthread).

##  <a name="isidlemessage"></a>  CWinThread::IsIdleMessage

Přepsání této funkce můžete zachovat `OnIdle` byla volána po vygenerování konkrétní zprávy.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Odkazuje na aktuální zprávu právě zpracovává.

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `OnIdle` by měla být volána po zpracování zprávy; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace nevolá `OnIdle` po zprávy týkající se myši redundantní a zprávy generované bliká vám kontrolka střížek.

Pokud byla aplikace vytvořena krátký časovače `OnIdle` bude volána často způsobuje problémy s výkonem. Kvůli zvýšení výkonu takovou aplikaci prvku se přepsat `IsIdleMessage` v aplikačním `CWinApp`-odvozené třídy se budou kontrolovat zprávy WM_TIMER následujícím způsobem:

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

Zpracování WM_TIMER tímto způsobem se zvýší výkon aplikací, které používají krátké časovače.

##  <a name="m_bautodelete"></a>  CWinThread::m_bAutoDelete

Určuje, zda `CWinThread` objektu by měla být automaticky odstraněn při ukončení vlákna.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Poznámky

`m_bAutoDelete` Datový člen je veřejná proměnná typu BOOL.

Hodnota `m_bAutoDelete` neovlivní způsob uzavření podkladového popisovač vlákna, ale neovlivní časování uzavření popisovače. Popisovač vlákna je vždy uzavřen, když `CWinThread` objekt zničen.

##  <a name="m_hthread"></a>  CWinThread::m_hThread

Zpracování připojených k tomuto vláknu `CWinThread`.

```
HANDLE m_hThread;
```

### <a name="remarks"></a>Poznámky

`m_hThread` Datový člen je veřejná proměnná typu POPISOVAČ. Platí pouze pokud podkladový objekt vlákna jádra aktuálně existuje a je popisovač ještě nebyly uzavřeny.

CWinThread – destruktor volá CloseHandle `m_hThread`. Pokud [m_bAutoDelete](#m_bautodelete) je hodnotu PRAVDA, pokud se vlákno ukončí, CWinThread objekt je zničen, která zneplatní všechny ukazatele na objekt CWinThread a její členské proměnné. Možná bude nutné `m_hThread` člen ke kontrole hodnoty ukončení vlákna, nebo k čekání na signál. Aby objekt CWinThread a jeho `m_hThread` člena během provádění vlákna a po jeho ukončení `m_bAutoDelete` na hodnotu FALSE, než bude umožněno pokračovat v provádění vlákna. V opačném případě vlákno může ukončit zničit objekt CWinThread a zavřít popisovač, než se pokusíte použít. Pokud použijete tento postup, zodpovídáte za odstranění CWinThread objektu.

##  <a name="m_nthreadid"></a>  CWinThread::m_nThreadID

ID vlákna připojených k tomuto `CWinThread`.

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>Poznámky

`m_nThreadID` Datový člen je veřejná proměnná typu DWORD. Platí pouze pokud podkladový objekt vlákna jádra aktuálně existuje.
Také zobrazit poznámky o [m_hThread](#m_hthread) životnost.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [afxgetthread –](application-information-and-management.md#afxgetthread).

##  <a name="m_pactivewnd"></a>  CWinThread::m_pActiveWnd

Tento datový člen slouží k ukládání ukazatel na objekt aktivní okno vašeho vlákna.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>Poznámky

Knihovny Microsoft Foundation Class se automaticky ukončí vaše vlákno, když v okně odkazuje `m_pActiveWnd` je zavřený. Pokud toto vlákno je primární vlákno pro aplikace, aplikace také bude ukončeno. Pokud tomuto datovému členu má hodnotu NULL, aktivní okno pro aplikace `CWinApp` objektu se budou dědit. `m_pActiveWnd` je veřejná proměnná typu `CWnd*`.

Obvykle, nastavte tuto proměnnou člena při přepsání `InitInstance`. V pracovním vlákně hodnotu tomuto datovému členu je zděděno z jeho nadřazeného vlákna.

##  <a name="m_pmainwnd"></a>  CWinThread::m_pMainWnd

Tento datový člen slouží k ukládání ukazatel na objekt hlavního okna vašeho vlákna.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>Poznámky

Knihovny Microsoft Foundation Class se automaticky ukončí vaše vlákno, když v okně odkazuje `m_pMainWnd` je zavřený. Pokud toto vlákno je primární vlákno pro aplikace, aplikace také bude ukončeno. Pokud tomuto datovému členu má hodnotu NULL, v hlavním okně aplikace `CWinApp` objektu se použije k určení toho, kdy k ukončení vlákna. `m_pMainWnd` je veřejná proměnná typu `CWnd*`.

Obvykle, nastavte tuto proměnnou člena při přepsání `InitInstance`. V pracovním vlákně hodnotu tomuto datovému členu je zděděno z jeho nadřazeného vlákna.

##  <a name="onidle"></a>  CWinThread::OnIdle

Potlačí tuto členskou funkci provádět zpracování doby nečinnosti.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parametry

*lCount*<br/>
Čítače se zvýší pokaždé, když `OnIdle` se volá, když vlákna fronta je prázdná. Toto je čítač nastaven na 0 pokaždé, když se zpracovává novou zprávu. Můžete použít *lCount* parametr k určení relativní časový úsek vlákna byl nečinný bez zpracování zprávy.

### <a name="return-value"></a>Návratová hodnota

Nenulový přijímat další zpracování nečinnosti; 0, pokud je potřeba žádné další zpracování nečinnosti.

### <a name="remarks"></a>Poznámky

`OnIdle` ve výchozí smyčku zpráv se volá, když vlákna fronta je prázdná. Přepsání použijte k volání vlastní pozadí úlohy nečinnosti obslužné rutiny.

`OnIdle` by měl vrátit 0, která znamená, že je vyžadováno žádné další zpracování nečinnosti. *LCount* parametr se zvýší pokaždé, když `OnIdle` se volá, když fronta zpráv je prázdný a nastaven na hodnotu 0 pokaždé, když se zpracovává novou zprávu. Můžete volat vaše různých nečinnosti rutiny založené na tento počet.

Výchozí implementace tato členská funkce uvolnění dočasné objekty a nepoužívané dynamické knihovny z paměti.

Tato členská funkce se používá jenom v vlákna uživatelského rozhraní.

Protože aplikace nemůže zpracovat zprávy do `OnIdle` vrátí, neprovádějte zdlouhavým úlohám v této funkci.

##  <a name="operator_handle"></a>  CWinThread::operator POPISOVAČ

Načte popisovač `CWinThread` objektu.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu popisovač objektu vlákna; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Pomocí popisovač přímo volat rozhraní API Windows.

##  <a name="postthreadmessage"></a>  CWinThread::PostThreadMessage

Jen vytvořit uživatelem definované zprávu do jiného `CWinThread` objektu.

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*message*<br/>
ID uživatelsky definovanou zprávu.

*wParam*<br/>
První parametr message.

*lParam*<br/>
Druhý parametr message.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Publikovaná zpráva mapováno makra map zpráv ON_THREAD_MESSAGE obslužnou rutinu správné zprávy.

> [!NOTE]
> Při volání [PostThreadMessage](/windows/desktop/api/winuser/nf-winuser-postthreadmessagea), zprávy, nachází ve frontě zpráv vlákna. Ale protože zprávy zveřejněné tímto způsobem nejsou přidružené časového období, MFC nebude jejich vypravování do obslužné rutiny příkazu nebo zprávy. Ke zpracování těchto zpráv, přepište `PreTranslateMessage()` funkce vaše CWinApp odvozené třídy a ručně ke zpracování zpráv.

##  <a name="pretranslatemessage"></a>  CWinThread::PreTranslateMessage

Přepsání této funkce filtru okno zprávy před odesláním do funkce Windows [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage).

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Odkazuje [msg – struktura](/windows/desktop/api/winuser/ns-winuser-tagmsg) obsahující zprávu zpracovat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla v plně zpracování zprávy `PreTranslateMessage` a nemají být dále zpracovány. Nula v případě by měl být zpráva zpracována běžným způsobem.

### <a name="remarks"></a>Poznámky

Tato členská funkce se používá jenom v vlákna uživatelského rozhraní.

##  <a name="processmessagefilter"></a>  CWinThread::ProcessMessageFilter

Funkce háku rozhraní framework volá tato členská funkce k filtrování a reagovat na určité zprávy Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*code*<br/>
Určuje kód zavěšení. Tato členská funkce kód používá k určení způsobu zpracování *lpMsg.*

*lpMsg*<br/>
Ukazatel Windows [msg – struktura](/windows/desktop/api/winuser/ns-winuser-tagmsg).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zpráva se zpracuje; jinak 0.

### <a name="remarks"></a>Poznámky

Funkce háku zpracovává události před jejich odesláním do vaší aplikace normální zpráva o zpracování.

Pokud přepíšete tento pokročilé funkce, nezapomeňte volat základní třídy verze rozhraní framework udržovat připojení zpracování.

##  <a name="processwndprocexception"></a>  CWinThread::ProcessWndProcException

Rozhraní volá tuto funkci člena pokaždé, když se obslužná rutina nezachytí výjimku vyvolanou v jednom z vašeho vlákna zprávy nebo obslužné rutiny příkazů.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*e*<br/>
Odkazuje na neošetřené výjimce.

*pMsg*<br/>
Odkazuje [msg – struktura](/windows/desktop/api/winuser/ns-winuser-tagmsg) obsahující informace o zprávě systému windows, která způsobila rozhraní vyvolá výjimku.

### <a name="return-value"></a>Návratová hodnota

-1, pokud je vygenerována výjimka WM_CREATE; jinak 0.

### <a name="remarks"></a>Poznámky

Přímo Nevolejte tuto členskou funkci.

Výchozí implementace tato členská funkce zpracovává pouze výjimky generované z následujících zpráv:

|Příkaz|Akce|
|-------------|------------|
|WM_CREATE|Selhání.|
|WM_PAINT|Ověření oknu, zamezuje tak další zprávu WM_PAINT nefunkční.|

Přepište tato členská funkce poskytnout globální zpracování vašich výjimek. Základní funkce volejte pouze v případě, že si přejete zobrazit výchozí chování.

Tato členská funkce se používá jenom v vlákna, které mají pumpu zpráv.

##  <a name="pumpmessage"></a>  CWinThread::PumpMessage

obsahuje smyčku zpráv vlákna.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>Poznámky

`PumpMessage` obsahuje smyčku zpráv vlákna. `PumpMessage` je volán `CWinThread` k pumpa zpráv vlákna. Můžete volat `PumpMessage` přímo vynutit zpráv pro zpracování, nebo můžete přepsat `PumpMessage` změnit výchozí chování.

Volání `PumpMessage` přímo a přepsání její výchozí chování je doporučeno pouze pro pokročilé uživatele.

##  <a name="resumethread"></a>  CWinThread::ResumeThread

Volá se, aby pokračovat v provádění vlákna, které bylo pozastaveno [SuspendThread](#suspendthread) členská funkce nebo vlákno s příznakem CREATE_SUSPENDED vytvořili.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>Návratová hodnota

Vlákno je předchozí pozastavit počet v případě úspěchu; `0xFFFFFFFF` jinak. Pokud vrácená hodnota je nula, aktuální vlákno nebylo pozastaveno. Pokud vrácená hodnota je jedna, vlákno bylo pozastaveno, ale se teď restartuje. Žádné návratová hodnota větší než jedna znamená, že vlákno činnost průvodce zůstává přerušena.

### <a name="remarks"></a>Poznámky

Pozastaveným počtem aktuální vlákno se sníží o jedna. Pokud je snížen počet pozastavení na nulu, vlákno pokračuje v provádění; v opačném případě vlákno činnost průvodce zůstává přerušena.

##  <a name="run"></a>  CWinThread::Run

Poskytuje výchozí smyčku zpráv pro vlákna uživatelského rozhraní.

```
virtual int Run();
```

### <a name="return-value"></a>Návratová hodnota

**Int** hodnotu, která je vrácena vlákna. Tuto hodnotu můžete získat voláním [GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Poznámky

`Run` Získá a odesílá zprávy Windows, dokud se aplikace obdrží [WM_QUIT](/windows/desktop/winmsg/wm-quit) zprávy. Pokud fronta zpráv vlákna v současné době obsahuje žádné zprávy `Run` volání `OnIdle` provádět zpracování doby nečinnosti. Příchozí zprávy pokračujte [PreTranslateMessage –](#pretranslatemessage) členskou funkci pro zvláštní zpracování a potom na funkci Windows [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) pro překlad standardní klávesnice. Nakonec [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) je volána funkce Windows.

`Run` je přepsána jen zřídka, ale můžete ho implementovat zvláštní chování přepsat.

Tato členská funkce se používá jenom v vlákna uživatelského rozhraní.

##  <a name="setthreadpriority"></a>  CWinThread::SetThreadPriority

Tato funkce nastaví prioritu aktuální vlákno v rámci jeho prioritou.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>Parametry

*nPriority*<br/>
Určuje novou úroveň priority vlákna ve své třídě priorit. Tento parametr musí být jedna z následujících hodnot uvedených od nejvyšší priority po nejnižší:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Další informace o těchto priorit, naleznete v tématu [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud funkce byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Lze volat pouze po [CreateThread](#createthread) úspěšně vrátí.

##  <a name="suspendthread"></a>  CWinThread::SuspendThread

Zvětší aktuální počet pozastavení vlákna.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>Návratová hodnota

Vlákno je předchozí pozastavit počet v případě úspěchu; `0xFFFFFFFF` jinak.

### <a name="remarks"></a>Poznámky

Pokud žádné vlákno má pozastavit počet vyšší než nula, bylo vlákno se nespustí. Vlákna lze obnovit voláním [ResumeThread](#resumethread) členskou funkci.

## <a name="see-also"></a>Viz také:

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWinApp – třída](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
