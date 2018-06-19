---
title: CWinThread – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7cbdcc1c5534d8dd9ba5d4f895af70a8ec16ac5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376963"
---
# <a name="cwinthread-class"></a>CWinThread – třída
Představuje vlákno při provádění v rámci aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CWinThread : public CCmdTarget  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinThread::CWinThread](#cwinthread)|Vytvoří `CWinThread` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinThread::CreateThread](#createthread)|Spustí provádění `CWinThread` objektu.|  
|[CWinThread::ExitInstance](#exitinstance)|Přepsání nastavení za účelem vyčištění po ukončení vaše vlákna.|  
|[CWinThread::GetMainWnd](#getmainwnd)|Načte ukazatel na hlavní okno pro vlákno.|  
|[CWinThread::GetThreadPriority](#getthreadpriority)|Získá prioritu aktuální vlákno.|  
|[CWinThread::InitInstance](#initinstance)|Přepsání nastavení za účelem provede inicializaci instance vlákna.|  
|[CWinThread::IsIdleMessage](#isidlemessage)|Kontroluje pro speciální zprávy.|  
|[CWinThread::OnIdle](#onidle)|Přepsání nastavení za účelem provedení zpracování specifické pro vlákno doby nečinnosti.|  
|[CWinThread::PostThreadMessage](#postthreadmessage)|Odešle zprávu do jiného `CWinThread` objektu.|  
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtry zpráv předtím, než jsou odeslány do funkce Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).|  
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Zachytí některé zprávy předtím, než nedostanou aplikace.|  
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Zachycuje všechny neošetřené výjimky vyvolané vlákna zprávu a obslužné rutiny příkazů.|  
|[CWinThread::PumpMessage](#pumpmessage)|Obsahuje vlákna zpráva smyčky.|  
|[CWinThread::ResumeThread](#resumethread)|Snižuje a vlákna pozastavit count.|  
|[CWinThread::Run](#run)|Řídící funkce pro vlákna s zprávy odeslané. Přepsání nastavení za účelem přizpůsobení smyčky výchozí zpráva.|  
|[CWinThread::SetThreadPriority](#setthreadpriority)|Nastaví prioritu aktuální vlákno.|  
|[CWinThread::SuspendThread](#suspendthread)|Zvýší a vlákna pozastavit count.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinThread::operator POPISOVAČ](#operator_handle)|Načte popisovač `CWinThread` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Určuje, jestli chcete odstranit objekt v ukončení vlákna.|  
|[CWinThread::m_hThread](#m_hthread)|Zpracování pro aktuální vlákno.|  
|[CWinThread::m_nThreadID](#m_nthreadid)|ID aktuálního vlákna.|  
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Ukazatel na hlavní okno aplikace kontejneru, pokud je na místě aktivní server služby OLE.|  
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Obsahuje ukazatele na hlavní okno aplikace.|  
  
## <a name="remarks"></a>Poznámky  
 Hlavní vlákno spuštění je obvykle poskytují objektem odvozené z `CWinApp`; `CWinApp` je odvozený od `CWinThread`. Další `CWinThread` objekty povolit více vláken v dané aplikaci.  
  
 Existují dvě obecné typy vláken, `CWinThread` podporuje: vláken uživatelského rozhraní a pracovních vláken. Pracovní vlákna mít žádná zpráva čerpadlo: například vlákno, které provede výpočty pozadí v aplikaci tabulky. Vlákna uživatelského rozhraní mají zprávy odeslané a zpracování zprávy přijaté ze systému. [CWinApp](../../mfc/reference/cwinapp-class.md) a třídy odvozené z něj jsou příklady vlákna uživatelského rozhraní. Jiná vlákna uživatelského rozhraní lze také odvodit přímo z `CWinThread`.  
  
 Objekty třídy `CWinThread` obvykle existovat po dobu trvání vlákno. Pokud chcete-li toto chování změnit, nastavte [m_bAutoDelete](#m_bautodelete) k **FALSE**.  
  
 `CWinThread` Třída je potřeba provést kód a MFC plně bezpečné pro přístup z více vláken. Místní data používá k udržení informace specifické pro vlákno rámcem spravuje `CWinThread` objekty. Z důvodu tuto závislost na `CWinThread` zpracování dat místní, musí být všechny vlákno, které používá MFC vytvořeného rozhraním MFC. Například vlákno vytvořené funkce běhové [_beginthread _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) nelze použít žádné knihovny MFC rozhraní API.  
  
 Chcete-li vytvořit vlákno, volejte [AfxBeginThread](application-information-and-management.md#afxbeginthread). Existují dvě formy, v závislosti na tom, zda chcete vlákno pracovníka nebo uživatelského rozhraní. Pokud chcete vlákna uživatelského rozhraní, předat `AfxBeginThread` ukazatel `CRuntimeClass` z vaší `CWinThread`-odvozené třídy. Pokud chcete vytvořit pracovní vlákno, předat `AfxBeginThread` ukazatel na funkci řízení a parametr řídící funkce. Pracovní vlákna a vlákna uživatelského rozhraní můžete zadat volitelné parametry, které změnit prioritu, velikost zásobníku, vytvoření příznaky a atributů zabezpečení. `AfxBeginThread` vrátí ukazatel na nové `CWinThread` objektu.  
  
 Místo volání `AfxBeginThread`, můžete vytvořit `CWinThread`-odvozené objekt a potom volání `CreateThread`. Tato metoda dvoufázová konstrukce je užitečné, pokud chcete znovu použít `CWinThread` objektu mezi následných vytvoření a ukončení spuštěních přístup z více vláken.  
  
 Další informace o `CWinThread`, najdete v článcích [Multithreading s C++ a MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading: vytváření vláken uživatelského rozhraní](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading: vytváření pracovního procesu Vlákna](../../parallel/multithreading-creating-worker-threads.md), a [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWinThread`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="createthread"></a>  CWinThread::CreateThread  
 Vytvoří vlákno k provedení v adresním prostoru procesu volání.  
  
```  
BOOL CreateThread(
    DWORD dwCreateFlags = 0,  
    UINT nStackSize = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCreateFlags`  
 Určuje další příznak, který řídí vytváření vlákno. Tento příznak může obsahovat jednu ze dvou hodnot:  
  
- **CREATE_SUSPENDED** vlákno začínat pozastavit započítává jako jeden. Použití **CREATE_SUSPENDED** Pokud chcete k inicializaci dat člena z `CWinThread` objektů, jako například [m_bAutoDelete](#m_bautodelete) nebo žádné členy vaší odvozené třídy, než je vlákno spuštění. Po dokončení vaší inicializace použít [CWinThread::ResumeThread](#resumethread) spustit vlákno spuštěna. Dokud nebude spustit vlákno `CWinThread::ResumeThread` je volána.  
  
- **0** spustit vlákno ihned po vytvoření.  
  
 `nStackSize`  
 Určuje velikost v bajtech zásobníku pro nové vlákno. Pokud **0**, aby byla stejná jako u primární vlákna procesu výchozí nastavení velikosti zásobníku.  
  
 `lpSecurityAttrs`  
 Odkazuje na [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, která určuje atributy zabezpečení pro vlákno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové vlákno vytvořeném úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `AfxBeginThread` vytvořit objekt přístup z více vláken a spustit v jednom kroku. Použití `CreateThread` Pokud chcete znovu použít objekt vlákna mezi následných vytváření a ukončení spuštěních přístup z více vláken.  
  
##  <a name="cwinthread"></a>  CWinThread::CWinThread  
 Vytvoří `CWinThread` objektu.  
  
```  
CWinThread();
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zahájit provádění vlákna, zavolejte [CreateThread](#createthread) – členská funkce. Obvykle vytvoříte vláken voláním [AfxBeginThread](application-information-and-management.md#afxbeginthread), který zavolá tento konstruktor a `CreateThread`.  
  
##  <a name="exitinstance"></a>  CWinThread::ExitInstance  
 Voláno rámcem z v rámci zřídka přepsaného [spustit](#run) – členská funkce ukončíte tuto instanci vlákno, nebo pokud volání [InitInstance](#initinstance) selže.  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukončovací kód vlákna; 0 znamená žádné chyby a hodnoty, které jsou větší než 0 indikují chybu. Tato hodnota může být načten voláním [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190).  
  
### <a name="remarks"></a>Poznámky  
 Nevolejte tuto funkci člena z libovolného místa ale uvnitř **spustit** – členská funkce. Tato funkce člen se používá pouze v vlákna uživatelského rozhraní.  
  
 Odstraní výchozí implementace této funkce `CWinThread` objektu Pokud [m_bAutoDelete](#m_bautodelete) je **TRUE**. Tato funkce přepsání, pokud chcete provést další čištění po ukončení vaše vlákna. Vaši implementaci `ExitInstance` by měly volat základní třídy verzi, po provedení kódu.  
  
##  <a name="getmainwnd"></a>  CWinThread::GetMainWnd  
 Pokud je aplikace serveru OLE, volejte tuto funkci k získání ukazatele na aktivní hlavní okno aplikace místo přímo odkazující na `m_pMainWnd` členem objektu application.  
  
```  
virtual CWnd* GetMainWnd();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato funkce vrací ukazatel na jeden ze dvou typů systému windows. Pokud váš přístup z více vláken je součástí OLE server a má objekt, který je na místě aktivní uvnitř aktivní kontejneru, vrátí tato funkce [CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) data členem `CWinThread` objektu.  
  
 Pokud se žádný objekt, který je na místě aktivní do kontejneru, nebo aplikaci není OLE server, vrátí tato funkce [m_pMainWnd](#m_pmainwnd) – datový člen objektu přístup z více vláken.  
  
### <a name="remarks"></a>Poznámky  
 Pro vlákna uživatelského rozhraní, jde o ekvivalent přímo odkazující na `m_pActiveWnd` členem aplikační objekt.  
  
 Pokud vaše aplikace není OLE server, pak volání této funkce je ekvivalentní přímo odkazující na `m_pMainWnd` členem aplikační objekt.  
  
 Přepsání této funkci můžete upravovat výchozí chování.  
  
##  <a name="getthreadpriority"></a>  CWinThread::GetThreadPriority  
 Získá aktuální úroveň priority vlákno podprocesu.  
  
```  
int GetThreadPriority();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální úroveň priority přístup z více vláken v rámci své třídy s prioritou. Hodnota vrácená jednu z těchto, budou seřazeny od nejvyšší prioritou nejnižší:  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **THREAD_PRIORITY_LOWEST**  
  
- **THREAD_PRIORITY_IDLE**  
  
 Další informace o těchto priorit, najdete v části [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) ve Windows SDK.  
  
##  <a name="initinstance"></a>  CWinThread::InitInstance  
 `InitInstance` musí být potlačena za účelem inicializace každou novou instanci třídy vlákna uživatelského rozhraní.  
  
```  
virtual BOOL InitInstance();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěšného; inicializace jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle je přepsat `InitInstance` k provádění úloh, které je třeba provést při prvním vytvoření vlákna.  
  
 Tato funkce člen se používá pouze v vlákna uživatelského rozhraní. Provést inicializaci z pracovních vláken ve funkci řízení předaný [AfxBeginThread](application-information-and-management.md#afxbeginthread).  
  
##  <a name="isidlemessage"></a>  CWinThread::IsIdleMessage  
 Přepsání této funkce můžete zachovat **OnIdle** z volána po vygenerování konkrétní zprávy.  
  
```  
virtual BOOL IsIdleMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `pMsg`  
 Odkazuje na aktuální zprávu zpracovává.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `OnIdle` by měla být volána po zpracování zprávy; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace nevyvolá **OnIdle** po redundantní myši zprávy a zprávy generované blikat carets.  
  
 Pokud byla aplikace vytvořena krátké časovač **OnIdle** bude volána často, způsobuje problémy s výkonem. Chcete-li zvýšit výkon takové aplikace, přepište `IsIdleMessage` do aplikace `CWinApp`-odvozené třídy zkontrolujte `WM_TIMER` zprávy následujícím způsobem:  
  
 [!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]  
  
 Zpracování `WM_TIMER` tímto způsobem bude zlepšit výkon aplikací, které používají krátké časovače.  
  
##  <a name="m_bautodelete"></a>  CWinThread::m_bAutoDelete  
 Určuje, zda `CWinThread` objektu, měla by být automaticky odstraněna při ukončení vlákna.  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_bAutoDelete` – Datový člen je veřejné proměnné typu **BOOL**.  
  
 Hodnota `m_bAutoDelete` nemá vliv na tom, jak je základní popisovač podprocesu uzavřený. Popisovač podprocesu je uzavřen, vždy když `CWinThread` objekt zničena.  
  
##  <a name="m_hthread"></a>  CWinThread::m_hThread  
 Zpracování vlákno připojených k tomuto `CWinThread`.  
  
```  
HANDLE m_hThread;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_hThread` – Datový člen je veřejné proměnné typu `HANDLE`. Ho je platná pouze v případě základní vlákno aktuálně existuje.  
  
##  <a name="m_nthreadid"></a>  CWinThread::m_nThreadID  
 ID podprocesu přiřazené k tomuto `CWinThread`.  
  
```  
DWORD m_nThreadID;  
```  
  
### <a name="remarks"></a>Poznámky  
 **M_nThreadID** – datový člen je veřejné proměnné typu `DWORD`. Ho je platná pouze v případě základní vlákno aktuálně existuje.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [afxgetthread –](application-information-and-management.md#afxgetthread).  
  
##  <a name="m_pactivewnd"></a>  CWinThread::m_pActiveWnd  
 Tento člen data použijte k ukládání ukazatele na objekt aktivní okno na vlákno.  
  
```  
CWnd* m_pActiveWnd;  
```  
  
### <a name="remarks"></a>Poznámky  
 Knihovny Microsoft Foundation Class automaticky přeruší váš přístup z více vláken, když okno odkazuje `m_pActiveWnd` je uzavřený. Pokud tento přístup z více vláken je primární vlákno pro aplikaci, bude aplikace ukončena. Pokud je tento člen dat **NULL**, aktivní okno pro danou aplikaci `CWinApp` zdědí objektu. `m_pActiveWnd` je veřejné proměnné typu **CWnd\***.  
  
 Obvykle tuto proměnnou člen nastavit při přepsání `InitInstance`. V pracovní vlákno je hodnota této – datový člen zděděno od její nadřazené přístup z více vláken.  
  
##  <a name="m_pmainwnd"></a>  CWinThread::m_pMainWnd  
 Tento člen data použijte k ukládání ukazatele na objekt hlavní okno vašeho vlákna.  
  
```  
CWnd* m_pMainWnd;  
```  
  
### <a name="remarks"></a>Poznámky  
 Knihovny Microsoft Foundation Class automaticky přeruší váš přístup z více vláken, když okno odkazuje `m_pMainWnd` je uzavřený. Pokud tento přístup z více vláken je primární vlákno pro aplikaci, bude aplikace ukončena. Pokud je tento člen dat **NULL**, hlavní okno pro danou aplikaci `CWinApp` objektu se použije k určení, kdy ukončit vlákno. `m_pMainWnd` je veřejné proměnné typu **CWnd\***.  
  
 Obvykle tuto proměnnou člen nastavit při přepsání `InitInstance`. V pracovní vlákno je hodnota této – datový člen zděděno od její nadřazené přístup z více vláken.  
  
##  <a name="onidle"></a>  CWinThread::OnIdle  
 Člen funkci k provedení zpracování doby nečinnosti přepište.  
  
```  
virtual BOOL OnIdle(LONG lCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lCount`  
 Čítač zvýší pokaždé, když `OnIdle` je volána, když se fronta zpráv vlákna je prázdný. Toto je čítač nastaven na 0 pokaždé, když je novou zprávu zpracovat. Můžete použít `lCount` parametr k určení relativních dobu, po vlákno bylo nečinné bez zpracování zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty pro příjem více zpracování doby nečinnosti; 0, pokud je potřeba žádné další zpracování nečinnosti.  
  
### <a name="remarks"></a>Poznámky  
 `OnIdle` ve smyčce zpráv výchozí je volána, když fronta zpráv vlákna je prázdný. Pomocí přepsání volání vlastní pozadí úlohy nečinnosti obslužné rutiny.  
  
 `OnIdle` by měl vrátit 0 k označení, že není vyžadováno žádné další zpracování nečinnosti. `lCount` Parametr se zvýší pokaždé, když `OnIdle` je volána, když je prázdný fronty zpráv a nastaven na hodnotu 0 pokaždé, když je novou zprávu zpracovat. Vaše různých nečinnosti rutiny založené na tento počet můžete volat.  
  
 Výchozí implementace této funkce člen uvolní dočasné objekty a nepoužívané knihovny z paměti.  
  
 Tato funkce člen se používá pouze v vlákna uživatelského rozhraní.  
  
 Vzhledem k tomu, že aplikace nemůže zpracovat zprávy, dokud `OnIdle` vrátí, neprovádějte zdlouhavé úlohy v této funkci.  
  
##  <a name="operator_handle"></a>  CWinThread::operator POPISOVAČ  
 Načte popisovač `CWinThread` objektu.  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu popisovač objektu vlákno; v opačném **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Použijte popisovač přímo volat rozhraní API systému Windows.  
  
##  <a name="postthreadmessage"></a>  CWinThread::PostThreadMessage  
 Volané vlastní zprávu do jiného `CWinThread` objektu.  
  
```  
BOOL PostThreadMessage(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `message`  
 ID zprávy definovaný uživatelem.  
  
 `wParam`  
 První parametr zprávy.  
  
 `lParam`  
 Druhý parametr zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Odeslané zprávy mapovaný na obslužnou rutinu správné zpráva makra map zpráv `ON_THREAD_MESSAGE`.  
  
> [!NOTE]
>  Při volání metody Windows [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946) funkce v rámci aplikace MFC zpráv MFC nejsou volány obslužné rutiny. Další informace najdete v článku znalostní báze Knowledge Base, "PRB: MFC zpráva obslužná rutina nebyla volána s PostThreadMessage()" (Q142415).  
  
##  <a name="pretranslatemessage"></a>  CWinThread::PreTranslateMessage  
 Přepsání této funkci můžete filtrovat okno zprávy předtím, než jsou odeslány do funkce Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `pMsg`  
 Odkazuje na [MSG – struktura](../../mfc/reference/msg-structure1.md) obsahující zprávu zpracovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zpráva byla plně zpracovány v `PreTranslateMessage` a nesmí být další zpracování. Nula, pokud by měl být zpráva zpracována běžným způsobem.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen se používá pouze v vlákna uživatelského rozhraní.  
  
##  <a name="processmessagefilter"></a>  CWinThread::ProcessMessageFilter  
 Funkce háku rozhraní framework volá tuto funkci člen filtrovat a reagovat na určité zpráv systému Windows.  
  
```  
virtual BOOL ProcessMessageFilter(
    int code,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `code`  
 Určuje kód háku. Tato funkce člen kód používá určit, jak zpracovat `lpMsg.`  
  
 `lpMsg`  
 Ukazatel na Windows [MSG – struktura](../../mfc/reference/msg-structure1.md).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je zpráva zpracována; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Funkce háku zpracovává události před jejich odesláním do aplikace normální zpráva zpracování.  
  
 Pokud přepíšete tato pokročilé funkce, je nutné volat základní třídy verze Udržovat rozhraní framework napojit zpracování.  
  
##  <a name="processwndprocexception"></a>  CWinThread::ProcessWndProcException  
 Tento člen funkce volá framework vždy, když obslužná rutina nezachytí výjimka vyvolána v jednom z vašeho vlákna zpráva nebo obslužné rutiny příkazů.  
  
```  
virtual LRESULT ProcessWndProcException(
    CException* e,  
    const MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 *e*  
 Body k neošetřené výjimce.  
  
 `pMsg`  
 Odkazuje na [MSG – struktura](../../mfc/reference/msg-structure1.md) obsahující informace o zprávě systému windows, která způsobila, že rozhraní framework má být vyvolána výjimka.  
  
### <a name="return-value"></a>Návratová hodnota  
 -v případě 1 `WM_CREATE` se vygeneruje výjimka; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Nevolejte tuto funkci člen přímo.  
  
 Výchozí implementace této funkce člen zpracovává pouze výjimky generované z následujících zpráv:  
  
|Příkaz|Akce|  
|-------------|------------|  
|`WM_CREATE`|Selhání.|  
|`WM_PAINT`|Ověření ovlivněných okno, takže si jiné `WM_PAINT` zprávu od generován.|  
  
 Člen funkci zajistit globální zpracování vaše výjimek přepište. Základní funkce volejte jenom v případě, že si přejete zobrazit výchozí chování.  
  
 Tato funkce člen se používá pouze v vláken, které mají zprávy odeslané.  
  
##  <a name="pumpmessage"></a>  CWinThread::PumpMessage  
 Obsahuje vlákna zpráva smyčky.  
  
```  
virtual BOOL PumpMessage();
```  
  
### <a name="remarks"></a>Poznámky  
 `PumpMessage` Obsahuje vlákna zpráva smyčky. **PumpMessage** volá `CWinThread` k čerpadla vlákna zprávy. Můžete volat `PumpMessage` přímo k vynucení zpráv, které mají být zpracovány, nebo můžete přepsat `PumpMessage` změnit jeho výchozí chování.  
  
 Volání metody `PumpMessage` přímo a pouze pro pokročilé uživatele se nedoporučuje potlačovat jeho výchozí chování.  
  
##  <a name="resumethread"></a>  CWinThread::ResumeThread  
 Voláno k pokračovat v provádění vlákno, které bylo pozastaveno [SuspendThread](#suspendthread) – členská funkce nebo vlákno vytvořené pomocí **CREATE_SUSPENDED** příznak.  
  
```  
DWORD ResumeThread();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vlákno je předchozí pozastavit počet v případě úspěšného; `0xFFFFFFFF` jinak. Pokud návratovou hodnotu nula, aktuální vlákno není pozastaveno. Pokud návratovou hodnotu, vlákno byla pozastavena, ale teď restartování. Všechny návratovou hodnotu větší než jedna znamená vlákno zůstává přerušena.  
  
### <a name="remarks"></a>Poznámky  
 Pozastavit počet aktuální vlákno se sníží o jedna. Pokud je snížen počet pozastavit na nulu, vlákno obnoví spuštění; v opačném případě vlákno zůstává přerušena.  
  
##  <a name="run"></a>  CWinThread::Run  
 Poskytuje smyčku výchozí zprávu pro vlákna uživatelského rozhraní.  
  
```  
virtual int Run();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `int` Hodnotu, která vrátí vlákno. Tato hodnota může být načten voláním [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190).  
  
### <a name="remarks"></a>Poznámky  
 **Spustit** odeslání zpráv systému Windows, dokud neobdrží aplikace a operace čtení [WM_QUIT](http://msdn.microsoft.com/library/windows/desktop/ms632641) zprávy. Pokud fronta zpráv vlákna aktuálně obsahuje žádné zprávy **spustit** volání `OnIdle` k provedení zpracování doby nečinnosti. Příchozí zprávy přejít na [PreTranslateMessage –](#pretranslatemessage) – členská funkce pro zvláštní zpracování a pak na funkce systému Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) pro překlad standardní klávesnice. Nakonec [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) je volána funkce systému Windows.  
  
 **Spustit** zřídka přepsána, ale můžete ho implementovat zvláštní chování přepsat.  
  
 Tato funkce člen se používá pouze v vlákna uživatelského rozhraní.  
  
##  <a name="setthreadpriority"></a>  CWinThread::SetThreadPriority  
 Tato funkce se nastaví úroveň priority aktuálního vlákna v rámci své třídy s prioritou.  
  
```  
BOOL SetThreadPriority(int nPriority);
```  
  
### <a name="parameters"></a>Parametry  
 `nPriority`  
 Určuje novou úroveň priority přístup z více vláken v rámci své třídy s prioritou. Tento parametr musí mít jednu z následujících hodnot, seřazeny od nejvyšší prioritou nejnižší:  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **THREAD_PRIORITY_LOWEST**  
  
- **THREAD_PRIORITY_IDLE**  
  
 Další informace o těchto priorit, najdete v části [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkce byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Lze volat jen po [CreateThread](#createthread) úspěšně vrátí.  
  
##  <a name="suspendthread"></a>  CWinThread::SuspendThread  
 Zvýší aktuální počet pozastavit vlákna.  
  
```  
DWORD SuspendThread();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vlákno je předchozí pozastavit počet v případě úspěšného; `0xFFFFFFFF` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Pokud žádné vlákno pozastavit počet vyšší než nula, že vlákno není provedena. Vlákno lze obnovit pomocí volání [ResumeThread](#resumethread) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CWinApp – třída](../../mfc/reference/cwinapp-class.md)   
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
