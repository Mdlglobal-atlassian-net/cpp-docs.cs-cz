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
ms.openlocfilehash: 43154e1ec4c6b856ad203a4b9ac49e4f4bcf9576
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421413"
---
# <a name="cwinthread-class"></a>CWinThread – třída

Představuje vlákno provádění v rámci aplikace.

## <a name="syntax"></a>Syntaxe

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CWinThread:: CWinThread](#cwinthread)|Vytvoří objekt `CWinThread`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWinThread:: CreateThread](#createthread)|Spustí spuštění objektu `CWinThread`.|
|[CWinThread:: ExitInstance](#exitinstance)|Přepsat pro vyčištění po ukončení vlákna.|
|[CWinThread:: GetMainWnd](#getmainwnd)|Načte ukazatel na hlavní okno vlákna.|
|[CWinThread:: GetThreadPriority](#getthreadpriority)|Získá prioritu aktuálního vlákna.|
|[CWinThread:: InitInstance](#initinstance)|Přepište pro provedení inicializace instance vlákna.|
|[CWinThread:: IsIdleMessage](#isidlemessage)|Kontroluje speciální zprávy.|
|[CWinThread:: OnIdle](#onidle)|Přepište pro provádění zpracování nečinnosti specifické pro vlákno.|
|[CWinThread::P ostThreadMessage](#postthreadmessage)|Odešle zprávu na jiný objekt `CWinThread`.|
|[CWinThread::P reTranslateMessage](#pretranslatemessage)|Filtruje zprávy předtím, než jsou odesílány do funkcí Windows Functions [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).|
|[CWinThread::P rocessMessageFilter](#processmessagefilter)|Zachycuje určité zprávy dřív, než dosáhnou aplikace.|
|[CWinThread::P rocessWndProcException](#processwndprocexception)|Zachycuje všechny neošetřené výjimky vyvolané obslužnými rutinami zpráv a příkazů vlákna.|
|[CWinThread::P umpMessage](#pumpmessage)|Obsahuje smyčku zpráv vlákna.|
|[CWinThread:: ResumeThread](#resumethread)|Sníží počet pozastavení vlákna.|
|[CWinThread:: Run](#run)|Řízení funkce pro vlákna s čerpadlem zpráv. Přepsáním přizpůsobíte výchozí smyčku zpráv.|
|[CWinThread:: SetThreadPriority](#setthreadpriority)|Nastaví prioritu aktuálního vlákna.|
|[CWinThread:: SuspendThread](#suspendthread)|Zvýší počet pozastavení vlákna.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CWinThread:: operator – popisovač](#operator_handle)|Načte popisovač objektu `CWinThread`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CWinThread:: m_bAutoDelete](#m_bautodelete)|Určuje, zda zničit objekt při ukončení vlákna.|
|[CWinThread:: m_hThread](#m_hthread)|Popisovač k aktuálnímu vláknu.|
|[CWinThread:: m_nThreadID](#m_nthreadid)|ID aktuálního vlákna|
|[CWinThread:: m_pActiveWnd](#m_pactivewnd)|Ukazatel na hlavní okno aplikace typu kontejner, pokud je server OLE aktivní na místě.|
|[CWinThread:: m_pMainWnd](#m_pmainwnd)|Obsahuje ukazatel na hlavní okno aplikace.|

## <a name="remarks"></a>Poznámky

Hlavní vlákno provádění je obvykle poskytováno objektem odvozeným od `CWinApp`; `CWinApp` je odvozen z `CWinThread`. Další objekty `CWinThread` v rámci dané aplikace umožňují více vláken.

Existují dva obecné typy vláken, které `CWinThread` podporovány: pracovní vlákna a vlákna uživatelského rozhraní. Pracovní vlákna neobsahují žádné čerpadlo zpráv: například vlákno, které provádí výpočty na pozadí v aplikaci v tabulce. V vláknech uživatelského rozhraní se nachází čerpadlo zpráv a zpracování zpráv ze systému. [CWinApp](../../mfc/reference/cwinapp-class.md) a třídy, které jsou z něj odvozeny, jsou příklady vláken uživatelského rozhraní. Další vlákna uživatelského rozhraní lze také odvodit přímo z `CWinThread`.

Objekty třídy `CWinThread` obvykle existují po dobu trvání vlákna. Pokud chcete toto chování změnit, nastavte [m_bAutoDelete](#m_bautodelete) na false.

Třída `CWinThread` je nezbytná, aby váš kód a knihovna MFC byly plně bezpečné pro přístup z více vláken. Místní data vlákna používaná rozhraním pro uchovávání informací specifických pro vlákno jsou spravována objekty `CWinThread`. Z důvodu této závislosti na `CWinThread` pro zpracování místních dat vlákna musí být jakékoli vlákno, které používá knihovnu MFC, vytvořeno knihovnou MFC. Například vlákno vytvořené funkcí run-time [_beginthread _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) nemůže používat žádná rozhraní API knihovny MFC.

Chcete-li vytvořit vlákno, zavolejte metodu [AfxBeginThread](application-information-and-management.md#afxbeginthread). Existují dvě formy v závislosti na tom, zda chcete pracovní podproces nebo uživatelské rozhraní. Pokud chcete vlákno uživatelského rozhraní, předejte `AfxBeginThread` ukazatel na `CRuntimeClass` třídy odvozené od `CWinThread`. Chcete-li vytvořit pracovní vlákno, předejte `AfxBeginThread` ukazatel na řídicí funkci a parametr do řídicí funkce. Pro pracovní vlákna i pro vlákna uživatelského rozhraní můžete zadat volitelné parametry, které mění prioritu, velikost zásobníku, příznaky vytváření a atributy zabezpečení. `AfxBeginThread` vrátí ukazatel na nový objekt `CWinThread`.

Namísto volání `AfxBeginThread`lze vytvořit objekt odvozený `CWinThread`a pak volat `CreateThread`. Tato dvoufázové metoda konstrukce je užitečná, pokud chcete znovu použít objekt `CWinThread` mezi následným vytvořením a ukončením provádění vlákna.

Další informace o `CWinThread`naleznete v článcích [ C++ MULTITHREADING s a MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading: vytváření vláken uživatelského rozhraní](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading: vytváření pracovních vláken](../../parallel/multithreading-creating-worker-threads.md)a [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="createthread"></a>CWinThread:: CreateThread

Vytvoří vlákno, které se provede v adresním prostoru volajícího procesu.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parametry

*dwCreateFlags*<br/>
Určuje další příznak, který řídí vytvoření vlákna. Tento příznak může obsahovat jednu ze dvou hodnot:

- CREATE_SUSPENDED spustit vlákno s počtem pozastavení jednoho. Použijte CREATE_SUSPENDED, pokud chcete inicializovat jakákoli Členská data objektu `CWinThread`, jako je [m_bAutoDelete](#m_bautodelete) nebo jakékoli členy odvozené třídy, před spuštěním vlákna. Po dokončení inicializace je nutné použít příkaz [CWinThread:: ResumeThread](#resumethread) ke spuštění vlákna spuštěného. Vlákno nebude spuštěno, dokud není voláno `CWinThread::ResumeThread`.

- **0** spustit vlákno ihned po vytvoření.

*nStackSize*<br/>
Určuje velikost zásobníku v bajtech pro nové vlákno. Pokud je hodnota **0**, výchozí velikost zásobníku je stejná jako velikost primárního vlákna procesu.

*lpSecurityAttrs*<br/>
Odkazuje na strukturu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , která určuje atributy zabezpečení pro vlákno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je vlákno vytvořeno úspěšně; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pomocí `AfxBeginThread` vytvořit objekt vlákna a spustit ho v jednom kroku. Použijte `CreateThread`, pokud chcete znovu použít objekt vlákna mezi následným vytvořením a ukončením provádění vlákna.

##  <a name="cwinthread"></a>CWinThread:: CWinThread

Vytvoří objekt `CWinThread`.

```
CWinThread();
```

### <a name="remarks"></a>Poznámky

Chcete-li zahájit provádění vlákna, zavolejte členskou funkci [CreateThread](#createthread) . Vlákna obvykle vytvoříte voláním [AfxBeginThread](application-information-and-management.md#afxbeginthread), která bude volat tento konstruktor a `CreateThread`.

##  <a name="exitinstance"></a>CWinThread:: ExitInstance

Volá se rozhraním v rámci zřídka přepsané členské funkce [Run](#run) , aby se ukončila tato instance vlákna, nebo pokud volání [InitInstance](#initinstance) neproběhne úspěšně.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Návratová hodnota

Ukončovací kód vlákna; 0 značí žádné chyby a hodnoty větší než 0 označují chybu. Tuto hodnotu lze načíst voláním [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Poznámky

Nevolejte tuto členskou funkci odkudkoli, ale v rámci `Run` členské funkce. Tato členská funkce se používá pouze v vláknech uživatelského rozhraní.

Výchozí implementace této funkce odstraní objekt `CWinThread`, pokud má [m_bAutoDelete](#m_bautodelete) hodnotu true. Tuto funkci přepište, pokud chcete provést další vyčištění při ukončení vlákna. Vaše implementace `ExitInstance` by měla po provedení kódu volat verzi základní třídy.

##  <a name="getmainwnd"></a>CWinThread:: GetMainWnd

Pokud je vaše aplikace serverem OLE, zavolejte tuto funkci, aby načetla ukazatel na aktivní hlavní okno aplikace namísto přímo odkazující na `m_pMainWnd` člen objektu aplikace.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>Návratová hodnota

Tato funkce vrací ukazatel na jeden ze dvou typů Windows. Pokud je vlákno součástí serveru OLE a má objekt, který je místně aktivní uvnitř aktivního kontejneru, vrátí tato funkce datový člen [CWinApp:: m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) objektu `CWinThread`.

Pokud není k dispozici žádný objekt, který je místně aktivní v rámci kontejneru nebo aplikace není serverem OLE, vrátí tato funkce datový člen [m_pMainWnd](#m_pmainwnd) objektu vlákna.

### <a name="remarks"></a>Poznámky

Pro vlákna uživatelského rozhraní se jedná o ekvivalent přímo odkazující na `m_pActiveWnd` člena objektu aplikace.

Pokud vaše aplikace není serverem OLE, pak volání této funkce je ekvivalentní přímo odkazující na `m_pMainWnd` člena objektu aplikace.

Přepsáním této funkce upravíte výchozí chování.

##  <a name="getthreadpriority"></a>CWinThread:: GetThreadPriority

Získá aktuální úroveň priority vlákna tohoto vlákna.

```
int GetThreadPriority();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální úroveň priority vlákna v rámci své třídy priorit. Vrácená hodnota bude jedna z následujících hodnot uvedená od nejvyšší priority k nejnižší:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Další informace o těchto prioritách najdete v tématu [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v Windows SDK.

##  <a name="initinstance"></a>CWinThread:: InitInstance

`InitInstance` musí být přepsány k inicializaci každé nové instance vlákna uživatelského rozhraní.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je inicializace úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Obvykle přepíšete `InitInstance` k provádění úloh, které musí být dokončeny při prvním vytvoření vlákna.

Tato členská funkce se používá pouze v vláknech uživatelského rozhraní. Proveďte inicializaci pracovních vláken v řídící funkci předanou do [AfxBeginThread](application-information-and-management.md#afxbeginthread).

##  <a name="isidlemessage"></a>CWinThread:: IsIdleMessage

Potlačením této funkce zachováte `OnIdle` volání po vygenerování určitých zpráv.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Odkazuje na aktuálně zpracovávanou zprávu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud by mělo být po zpracování zprávy voláno `OnIdle`; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace nevolá `OnIdle` po redundantních zprávách myši a zprávách vygenerovaných blikajícími blikajícími kurzory.

Pokud aplikace vytvořila krátký časovač, `OnIdle` bude často volána, což způsobí problémy s výkonem. Chcete-li zlepšit výkon takové aplikace, přepište `IsIdleMessage` v odvozené třídě `CWinApp`aplikace, aby kontrolovala WM_TIMER zprávy následujícím způsobem:

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

Manipulace WM_TIMER tímto způsobem zvýší výkon aplikací, které používají krátké časovače.

##  <a name="m_bautodelete"></a>CWinThread:: m_bAutoDelete

Určuje, zda má být objekt `CWinThread` automaticky odstraněn při ukončení vlákna.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Poznámky

Datový člen `m_bAutoDelete` je veřejná proměnná typu BOOL.

Hodnota `m_bAutoDelete` neovlivňuje způsob, jakým je uzavřený popisovač podprocesu, ale má vliv na načasování tohoto popisovače. Popisovač vlákna je vždy uzavřen při zničení objektu `CWinThread`.

##  <a name="m_hthread"></a>CWinThread:: m_hThread

Popisovač k vláknu připojenému k tomuto `CWinThread`.

```
HANDLE m_hThread;
```

### <a name="remarks"></a>Poznámky

Datový člen `m_hThread` je veřejná proměnná typu HANDLE. Je platný jenom v případě, že objekt podkladového vlákna jádra momentálně existuje a popisovač ještě není uzavřený.

Destruktor CWinThread volá CloseHandle na `m_hThread`. Pokud [m_bAutoDelete](#m_bautodelete) má hodnotu true při ukončení vlákna, je objekt CWinThread zničen, což zruší platnost všech ukazatelů na objekt CWinThread a jeho členské proměnné. Je možné, že budete potřebovat člena `m_hThread` pro kontrolu hodnoty ukončení vlákna nebo pro čekání na signál. Chcete-li zachovat objekt CWinThread a jeho `m_hThread` člena během provádění vlákna a po jeho ukončení, nastavte `m_bAutoDelete` na hodnotu FALSE, aby bylo možné pokračovat ve zpracování vlákna. Jinak vlákno může skončit, zničit objekt CWinThread a před tím, než se pokusíte ho použít, zavřít popisovač. Pokud použijete tento postup, zodpovídáte za odstranění objektu CWinThread.

##  <a name="m_nthreadid"></a>CWinThread:: m_nThreadID

ID vlákna připojené k tomuto `CWinThread`.

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>Poznámky

Datový člen `m_nThreadID` je veřejná proměnná typu DWORD. Je platný jenom v případě, že objekt podkladového vlákna jádra aktuálně existuje.
Viz také poznámky týkající se [m_hThread](#m_hthread) doby života.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [AfxGetThread](application-information-and-management.md#afxgetthread).

##  <a name="m_pactivewnd"></a>CWinThread:: m_pActiveWnd

Tento datový člen slouží k uložení ukazatele na objekt aktivního okna vašeho vlákna.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>Poznámky

Knihovna Microsoft Foundation Class automaticky ukončí vlákno, pokud je zavřeno okno, na které odkazuje `m_pActiveWnd`. Pokud je toto vlákno primárním vláknem aplikace, aplikace bude také ukončena. Pokud je tento datový člen NULL, dojde k dědění aktivního okna pro objekt `CWinApp` aplikace. `m_pActiveWnd` je veřejná proměnná typu `CWnd*`.

Obvykle nastavujete tuto členskou proměnnou při přepisování `InitInstance`. V pracovním vlákně je hodnota tohoto datového členu zděděna z nadřazeného vlákna.

##  <a name="m_pmainwnd"></a>CWinThread:: m_pMainWnd

Tento datový člen slouží k uložení ukazatele do objektu hlavního okna vlákna.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>Poznámky

Knihovna Microsoft Foundation Class automaticky ukončí vlákno, pokud je zavřeno okno, na které odkazuje `m_pMainWnd`. Pokud je toto vlákno primárním vláknem aplikace, aplikace bude také ukončena. Pokud je tento datový člen NULL, použije se hlavní okno pro objekt `CWinApp` aplikace k určení, kdy se má vlákno ukončit. `m_pMainWnd` je veřejná proměnná typu `CWnd*`.

Obvykle nastavujete tuto členskou proměnnou při přepisování `InitInstance`. V pracovním vlákně je hodnota tohoto datového členu zděděna z nadřazeného vlákna.

##  <a name="onidle"></a>CWinThread:: OnIdle

Přepište tuto členskou funkci, aby prováděla zpracování nečinných časů.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parametry

*lCount*<br/>
Čítač se zvýší pokaždé, když se `OnIdle` zavolá, když je fronta zpráv vlákna prázdná. Tento počet se resetuje na 0 pokaždé, když se zpracuje nová zpráva. Pomocí parametru *lCount* můžete určit relativní dobu nečinnosti vlákna bez zpracování zprávy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud chcete získat větší dobu nečinnosti při zpracování; 0, pokud není potřeba žádná další doba zpracování nečinnosti.

### <a name="remarks"></a>Poznámky

`OnIdle` se volá ve výchozí smyčce zpráv, když je fronta zpráv vlákna prázdná. Použijte své přepsání pro volání vlastních úloh obslužných rutin nečinných na pozadí.

`OnIdle` by měl vrátit 0, aby označovala, že se nevyžaduje žádná další doba nečinnosti při zpracování. Parametr *lCount* se zvýší pokaždé, když se `OnIdle` volá, když je fronta zpráv prázdná a při každém zpracování nové zprávy se resetuje na 0. Na základě tohoto počtu můžete volat různé nečinné rutiny.

Výchozí implementace této členské funkce uvolní dočasné objekty a nepoužívané knihovny DLL z paměti.

Tato členská funkce se používá pouze v vláknech uživatelského rozhraní.

Vzhledem k tomu, že aplikace nemůže zpracovat zprávy, dokud `OnIdle` nevrátí, neprovádějte v této funkci zdlouhavé úlohy.

##  <a name="operator_handle"></a>CWinThread:: operator – popisovač

Načte popisovač objektu `CWinThread`.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu, popisovač objektu vlákna; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Použijte popisovač k přímému volání rozhraní API systému Windows.

##  <a name="postthreadmessage"></a>CWinThread::P ostThreadMessage

Volá se, aby se mohl odeslat zpráva definovaná uživatelem do jiného objektu `CWinThread`.

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*message*<br/>
ID uživatelsky definované zprávy

*wParam*<br/>
První parametr zprávy

*lParam*<br/>
Druhý parametr zprávy

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Odeslaná zpráva je namapována na správnou obslužnou rutinu zprávy pomocí ON_THREAD_MESSAGE makro mapa zprávy.

> [!NOTE]
> Při volání [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)se zpráva umístí do fronty zpráv vlákna. Protože však zprávy vystavené tímto způsobem nejsou přidruženy k oknu, knihovna MFC je neodešle do obslužných rutin zpráv nebo příkazů. Aby bylo možné tyto zprávy zpracovat, přepište funkci `PreTranslateMessage()` vaší odvozené třídy (CWinApp) a zpracujte zprávy ručně.

##  <a name="pretranslatemessage"></a>CWinThread::P reTranslateMessage

Přepište tuto funkci pro filtrování zpráv oken před odesláním do funkcí Windows Functions [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Odkazuje na [strukturu MSG](/windows/win32/api/winuser/ns-winuser-msg) obsahující zprávu ke zpracování.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla zpráva plně zpracována v `PreTranslateMessage` a neměla by být zpracována dále. Nula, pokud má být zpráva zpracována normálním způsobem.

### <a name="remarks"></a>Poznámky

Tato členská funkce se používá pouze v vláknech uživatelského rozhraní.

##  <a name="processmessagefilter"></a>CWinThread::P rocessMessageFilter

Funkce Hooku rozhraní volá tuto členskou funkci k filtrování a reakci na určité zprávy systému Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*znakovou*<br/>
Určuje kód vidlice. Tato členská funkce používá kód k určení způsobu zpracování *lpMsg.*

*lpMsg*<br/>
Ukazatel na [strukturu zprávy](/windows/win32/api/winuser/ns-winuser-msg)systému Windows.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je zpráva zpracována; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Funkce zavěšení zpracovává události před odesláním do normálního zpracování zprávy aplikace.

Pokud přepíšete tuto rozšířenou funkci, ujistěte se, že jste volali verzi základní třídy, aby se zachovalo zpracování zavěšení rozhraní.

##  <a name="processwndprocexception"></a>CWinThread::P rocessWndProcException

Rozhraní volá tuto členskou funkci pokaždé, když obslužná rutina nezachytává výjimku vyvolanou v jedné z obslužných rutin zprávy nebo příkazu vlákna.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*cerebrální*<br/>
Odkazuje na neošetřenou výjimku.

*pMsg*<br/>
Odkazuje na [strukturu MSG](/windows/win32/api/winuser/ns-winuser-msg) obsahující informace o zprávě systému Windows, která způsobila, že rozhraní vyvolalo výjimku.

### <a name="return-value"></a>Návratová hodnota

-1, pokud je vygenerována výjimka WM_CREATE; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Nevolejte tuto členskou funkci přímo.

Výchozí implementace této členské funkce zpracovává pouze výjimky vygenerované z následujících zpráv:

|Příkaz|Akce|
|-------------|------------|
|WM_CREATE|Proběhne.|
|WM_PAINT|Ověří ovlivněné okno, čímž zabrání v generování jiné WM_PAINTové zprávy.|

Přepište tuto členskou funkci tak, aby poskytovala globální zpracování vašich výjimek. Základní funkce volejte pouze v případě, že chcete zobrazit výchozí chování.

Tato členská funkce se používá jenom v vláknech, které mají pumpu zpráv.

##  <a name="pumpmessage"></a>CWinThread::P umpMessage

Obsahuje smyčku zpráv vlákna.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>Poznámky

`PumpMessage` obsahuje smyčku zpráv vlákna. `PumpMessage` je volána `CWinThread` k vytvoření pumpy zpráv vlákna. Můžete volat `PumpMessage` přímo k vynucení zpracování zpráv nebo můžete přepsat `PumpMessage` a změnit výchozí chování.

Pro pokročilé uživatele se doporučuje volat `PumpMessage` přímo a přepsat jeho výchozí chování.

##  <a name="resumethread"></a>CWinThread:: ResumeThread

Volá se, aby se obnovilo provádění vlákna, které bylo pozastavené členskou funkcí [SuspendThread](#suspendthread) , nebo vlákno vytvořeného pomocí příznaku CREATE_SUSPENDED.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>Návratová hodnota

Počet pozastavených vláken v případě úspěchu `0xFFFFFFFF` jinak. Pokud je vrácená hodnota nula, aktuální vlákno nebylo pozastaveno. Pokud je vrácená hodnota jedna, vlákno bylo pozastaveno, ale nyní je restartováno. Libovolná vrácená hodnota větší než jedna znamená, že vlákno zůstane pozastaveno.

### <a name="remarks"></a>Poznámky

Počet pozastavení aktuálního vlákna je zmenšen o jednu. Pokud je počet pozastavení snížen na hodnotu nula, vlákno pokračuje v provádění. jinak vlákno zůstane pozastaveno.

##  <a name="run"></a>CWinThread:: Run

Poskytuje výchozí smyčku zpráv pro vlákna uživatelského rozhraní.

```
virtual int Run();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota typu **int** , která je vrácena vláknem. Tuto hodnotu lze načíst voláním [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Poznámky

`Run` získá a odešle zprávy systému Windows, dokud aplikace neobdrží zprávu [WM_QUIT](/windows/win32/winmsg/wm-quit) . Pokud fronta zpráv vlákna aktuálně neobsahuje žádné zprávy, `Run` volání `OnIdle` provést zpracování nečinného času. Příchozí zprávy přecházejí do členské funkce [PreTranslateMessage](#pretranslatemessage) pro zvláštní zpracování a následně do funkce Windows Function [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) pro překlad standardních klávesnic. Nakonec se zavolá funkce [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systému Windows.

`Run` je zřídka přepsáno, ale můžete ho přepsat pro implementaci speciálního chování.

Tato členská funkce se používá pouze v vláknech uživatelského rozhraní.

##  <a name="setthreadpriority"></a>CWinThread:: SetThreadPriority

Tato funkce nastaví úroveň priority aktuálního vlákna v rámci své třídy priorit.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>Parametry

*nPriority*<br/>
Určuje novou úroveň priority vlákna v rámci své třídy priorit. Tento parametr musí být jedna z následujících hodnot, která je uvedená od nejvyšší priority k nejnižší:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Další informace o těchto prioritách najdete v tématu [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Dá se volat jenom po úspěšném vrácení [CreateThread](#createthread) .

##  <a name="suspendthread"></a>CWinThread:: SuspendThread

Zvýší počet pozastavení aktuálního vlákna.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>Návratová hodnota

Počet pozastavených vláken v případě úspěchu `0xFFFFFFFF` jinak.

### <a name="remarks"></a>Poznámky

Pokud je v jakémkoli vlákně počet pozastavení, toto vlákno se nespustí. Vlákno lze obnovit voláním členské funkce [ResumeThread](#resumethread) .

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWinApp – třída](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
