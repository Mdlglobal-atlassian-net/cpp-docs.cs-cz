---
title: Třída CWorkerThread
ms.date: 11/04/2016
f1_keywords:
- CWorkerThread
- ATLUTIL/ATL::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::AddHandle
- ATLUTIL/ATL::CWorkerThread::AddTimer
- ATLUTIL/ATL::CWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CWorkerThread::GetThreadId
- ATLUTIL/ATL::CWorkerThread::Initialize
- ATLUTIL/ATL::CWorkerThread::RemoveHandle
- ATLUTIL/ATL::CWorkerThread::Shutdown
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
ms.openlocfilehash: 05e6b432d44927fa7e276792643e29c80c42d822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330213"
---
# <a name="cworkerthread-class"></a>Třída CWorkerThread

Tato třída vytvoří pracovní vlákno nebo použije existující, čeká na jeden nebo více popisovačů objektu jádra a spustí zadanou klientskou funkci, když je signalizován jeden z popisovačů.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>Parametry

*ThreadTraits*<br/>
Třída poskytující funkci vytváření vláken, například [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) nebo [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).

## <a name="members"></a>Členové

### <a name="protected-structures"></a>Chráněné struktury

|Name (Název)|Popis|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|Konstruktor pro pracovní vlákno.|
|[CWorkerThread::~CWorkerThread](#dtor)|Destruktor pracovního vlákna.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|Volání této metody přidat popisovač čekatelný objekt do seznamu spravované pracovní ho vlákna.|
|[CWorkerThread::AddTimer](#addtimer)|Volání této metody přidat periodické čekací časovač do seznamu udržuje pracovní ho vlákna.|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Volání této metody získat popisovač podprocesu pracovního vlákna.|
|[CWorkerThread::GetThreadId](#getthreadid)|Volání této metody získat ID vlákna pracovního vlákna.|
|[CWorkerThread::Inicializovat](#initialize)|Volání této metody k inicializaci pracovního vlákna.|
|[CWorkerThread::RemoveHandle](#removehandle)|Volání této metody odebrat popisovač ze seznamu počkejtých objektů.|
|[CWorkerThread::Vypnutí](#shutdown)|Volání této metody vypnout pracovní vlákno.|

## <a name="remarks"></a>Poznámky

### <a name="to-use-cworkerthread"></a>Použití cworkerthread

1. Vytvořte instanci této třídy.

1. Volání [CWorkerThread::Inicializovat](#initialize).

1. Volání [CWorkerThread::AddHandle](#addhandle) s popisovačem objektu jádra a ukazatelem na implementaci [iWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

   \-nebo -

   Volání [CWorkerThread::AddTimer](#addtimer) s ukazatelem na implementaci [iWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

1. Implementujte [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) provést nějakou akci, když je signalizován popisovač nebo časovač.

1. Chcete-li odebrat objekt ze seznamu čekatelných objektů, zavolejte [CWorkerThread::RemoveHandle](#removehandle).

1. Chcete-li ukončit vlákno, zavolejte [CWorkerThread::Shutdown](#shutdown).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="cworkerthreadaddhandle"></a><a name="addhandle"></a>CWorkerThread::AddHandle

Volání této metody přidat popisovač čekatelný objekt do seznamu spravované pracovní ho vlákna.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>Parametry

*hObjekt*<br/>
Popisovač na čekatelný objekt.

*pKlient*<br/>
Ukazatel na rozhraní [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) na objekt, který má být volán při signalizaci popisovače.

*dwParam*<br/>
Parametr, který má být předán [iWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) při signalizaci popisovače.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) bude volána prostřednictvím *pClient,* když je signalizován popisovač *hObject*.

## <a name="cworkerthreadaddtimer"></a><a name="addtimer"></a>CWorkerThread::AddTimer

Volání této metody přidat periodické čekací časovač do seznamu udržuje pracovní ho vlákna.

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>Parametry

*dwInterval*<br/>
Určuje dobu časovače v milisekundách.

*pKlient*<br/>
Ukazatel na rozhraní [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) na objekt, který má být volán při signalizaci popisovače.

*dwParam*<br/>
Parametr, který má být předán [iWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) při signalizaci popisovače.

*phTimer řekl:*<br/>
[out] Adresa handle proměnné, která na úspěch obdrží popisovač nově vytvořený časovač.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) bude volána prostřednictvím *pClient,* když je signalizován časovač.

Předejte popisovač časovače z *phTimer* na [CWorkerThread::RemoveHandle](#removehandle) pro zavření časovače.

## <a name="cworkerthreadcworkerthread"></a><a name="cworkerthread"></a>CWorkerThread::CWorkerThread

Konstruktor

```
CWorkerThread() throw();
```

## <a name="cworkerthreadcworkerthread"></a><a name="dtor"></a>CWorkerThread::~CWorkerThread

Destruktor.

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>Poznámky

Volání [CWorkerThread::Shutdown](#shutdown).

## <a name="cworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle

Volání této metody získat popisovač podprocesu pracovního vlákna.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač vlákna nebo hodnotu NULL, pokud pracovní podproces nebyl inicializován.

## <a name="cworkerthreadgetthreadid"></a><a name="getthreadid"></a>CWorkerThread::GetThreadId

Volání této metody získat ID vlákna pracovního vlákna.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ID vlákna nebo hodnotu NULL, pokud pracovní podproces nebyl inicializován.

## <a name="cworkerthreadinitialize"></a><a name="initialize"></a>CWorkerThread::Inicializovat

Volání této metody k inicializaci pracovního vlákna.

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>Parametry

*pVlákno*<br/>
Existující pracovní podproces.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda by měla být volána k inicializaci objektu po vytvoření nebo po volání [CWorkerThread::Shutdown](#shutdown).

Chcete-li mít `CWorkerThread` dva nebo více objektů používat stejné pracovní vlákno, inicializovat jeden z `Initialize` nich bez předání jakékoli argumenty pak předat ukazatel na tento objekt metody ostatních. Objekty inicializované pomocí ukazatele by měly být ukončeny dříve, než je objekt použitý k jejich inicializaci.

Viz [CWorkerThread::Shutdown](#shutdown) pro informace o tom, jak se chování této metody změní při inicializování pomocí ukazatele na existující objekt.

## <a name="cworkerthreadremovehandle"></a><a name="removehandle"></a>CWorkerThread::RemoveHandle

Volání této metody odebrat popisovač ze seznamu počkejtých objektů.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>Parametry

*hObjekt*<br/>
Popisovač odstranit.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Při odebrání popisovače [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) bude volána na přidružený objekt, který byl předán [AddHandle](#addhandle). Pokud se toto volání nezdaří, `CWorkerThread` bude volat windows [closehandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) funkce na popisovač.

## <a name="cworkerthreadshutdown"></a><a name="shutdown"></a>CWorkerThread::Vypnutí

Volání této metody vypnout pracovní vlákno.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>Parametry

*dwWait*<br/>
Čas v milisekundách čekání na vypnutí pracovního vlákna. ATL_WORKER_THREAD_WAIT výchozí hodnoty na 10 sekund. V případě potřeby můžete definovat vlastní hodnotu pro tento symbol před zahrnutím atlutil.h.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chyba HRESULT při selhání, například pokud je překročena hodnota časového limitu *dwWait*.

### <a name="remarks"></a>Poznámky

Chcete-li objekt znovu použít, zavolejte [CWorkerThread::Initialize](#initialize) po volání této metody.

Všimněte `Shutdown` si, že volání objektu `CWorkerThread` inicializovaného ukazatelem na jiný objekt nemá žádný vliv a vždy vrátí S_OK.

## <a name="see-also"></a>Viz také

[Výchozí threadtraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Třídy](../../atl/reference/atl-classes.md)<br/>
[Multithreading: Vytváření pracovních vláken](../../parallel/multithreading-creating-worker-threads.md)<br/>
[Rozhraní IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)
