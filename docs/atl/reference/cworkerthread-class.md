---
title: CWorkerThread – třída
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
ms.openlocfilehash: f1aa76514b98bbf12f8e516d3d54f68e8ef4dd7d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496104"
---
# <a name="cworkerthread-class"></a>CWorkerThread – třída

Tato třída vytvoří pracovní vlákno nebo použije existující, počká na jeden nebo více popisovačů objektů jádra a spustí zadanou klientskou funkci, pokud je jeden z popisovačů signalizována.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>Parametry

*ThreadTraits*<br/>
Třída, která poskytuje funkci vytváření vlákna, jako je například [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) nebo [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).

## <a name="members"></a>Členové

### <a name="protected-structures"></a>Chráněné struktury

|Name|Popis|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|Konstruktor pro pracovní vlákno.|
|[CWorkerThread:: ~ CWorkerThread](#dtor)|Destruktor pro pracovní vlákno.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|Voláním této metody přidáte popisovač čekajícího objektu do seznamu spravovaného pracovním vláknem.|
|[CWorkerThread::AddTimer](#addtimer)|Voláním této metody přidáte pravidelný čekací časovač do seznamu spravovaného pracovním vláknem.|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Voláním této metody získáte popisovač vlákna pracovního vlákna.|
|[CWorkerThread::GetThreadId](#getthreadid)|Voláním této metody získáte ID vlákna pracovního vlákna.|
|[CWorkerThread:: Initialize](#initialize)|Voláním této metody inicializujete pracovní vlákno.|
|[CWorkerThread::RemoveHandle](#removehandle)|Voláním této metody odeberete popisovač ze seznamu čekajících objektů.|
|[CWorkerThread:: Shutdown](#shutdown)|Voláním této metody vypnete pracovní vlákno.|

## <a name="remarks"></a>Poznámky

### <a name="to-use-cworkerthread"></a>Použití CWorkerThread

1. Vytvořte instanci této třídy.

1. Zavolejte [CWorkerThread:: Initialize](#initialize).

1. Zavolejte [CWorkerThread:: AddHandle](#addhandle) s popisovačem objektu jádra a ukazatelem na implementaci [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

   \- nebo –

   Zavolejte [CWorkerThread:: addtimer](#addtimer) s ukazatelem na implementaci [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

1. Implementujte [IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) pro provedení určité akce při signalizaci popisovač nebo časovače.

1. Chcete-li odebrat objekt ze seznamu čekajících objektů, zavolejte [CWorkerThread:: RemoveHandle](#removehandle).

1. Chcete-li ukončit vlákno, zavolejte [CWorkerThread:: Shutdown](#shutdown).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil. h

##  <a name="addhandle"></a>CWorkerThread::AddHandle

Voláním této metody přidáte popisovač čekajícího objektu do seznamu spravovaného pracovním vláknem.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Popisovač pro čekací objekt.

*pClient*<br/>
Ukazatel na rozhraní [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) objektu, který má být volán při signalizaci popisovače.

*dwParam*<br/>
Parametr, který má být předán do [IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) při signalizaci popisovače.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

[IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) se bude volat prostřednictvím *pClient* při signalizaci popisovače *hObject*.

##  <a name="addtimer"></a>CWorkerThread::AddTimer

Voláním této metody přidáte pravidelný čekací časovač do seznamu spravovaného pracovním vláknem.

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>Parametry

*dwInterval*<br/>
Určuje periodu časovače v milisekundách.

*pClient*<br/>
Ukazatel na rozhraní [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) objektu, který má být volán při signalizaci popisovače.

*dwParam*<br/>
Parametr, který má být předán do [IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) při signalizaci popisovače.

*phTimer*<br/>
mimo Adresa proměnné popisovače, která při úspěchu obdrží popisovač nově vytvořenému časovači.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

[IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) se bude volat prostřednictvím *pClient* při signalizaci časovače.

Před ukončením časovače předejte popisovač časovače z *phTimer* do [CWorkerThread:: RemoveHandle](#removehandle) .

##  <a name="cworkerthread"></a>CWorkerThread::CWorkerThread

Konstruktor

```
CWorkerThread() throw();
```

##  <a name="dtor"></a>CWorkerThread:: ~ CWorkerThread

Destruktor.

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>Poznámky

Volá [CWorkerThread:: Shutdown](#shutdown).

##  <a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle

Voláním této metody získáte popisovač vlákna pracovního vlákna.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač vlákna nebo hodnotu NULL, pokud pracovní vlákno nebylo inicializováno.

##  <a name="getthreadid"></a>CWorkerThread::GetThreadId

Voláním této metody získáte ID vlákna pracovního vlákna.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ID vlákna nebo hodnotu NULL, pokud pracovní vlákno nebylo inicializováno.

##  <a name="initialize"></a>CWorkerThread:: Initialize

Voláním této metody inicializujete pracovní vlákno.

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>Parametry

*pThread*<br/>
Existující pracovní vlákno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda by měla být volána pro inicializaci objektu po vytvoření nebo po volání metody [CWorkerThread:: Shutdown](#shutdown).

Aby dva nebo více `CWorkerThread` objektů používalo stejné pracovní vlákno, inicializujte jeden z nich bez předání jakýchkoli argumentů a pak předejte ukazatel na tento objekt `Initialize` metodám ostatních. Objekty inicializované pomocí ukazatele by měly být ukončeny před tím, než je objekt použit k jeho inicializaci.

Informace o tom, jak se chování této metody mění při inicializaci pomocí ukazatele na existující objekt, naleznete v tématu [CWorkerThread:: Shutdown](#shutdown) .

##  <a name="removehandle"></a>CWorkerThread::RemoveHandle

Voláním této metody odeberete popisovač ze seznamu čekajících objektů.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Popisovač, který chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Po odebrání popisovače [IWorkerThreadClient:: CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) bude volána u přidruženého objektu, který byl předán do [AddHandle](#addhandle). Pokud se toto volání nezdaří `CWorkerThread` , zavolá funkci Windows [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) na popisovači.

##  <a name="shutdown"></a>CWorkerThread:: Shutdown

Voláním této metody vypnete pracovní vlákno.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>Parametry

*dwWait*<br/>
Čas v milisekundách, po který se má čekat na vypnutí pracovního vlákna ATL_WORKER_THREAD_WAIT je standardně 10 sekund. V případě potřeby můžete pro tento symbol definovat vlastní hodnotu před zahrnutím atlutil. h.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání, například pokud je překročena hodnota časového limitu *dwWait*.

### <a name="remarks"></a>Poznámky

Chcete-li znovu použít objekt, zavolejte [CWorkerThread:: Initialize](#initialize) po volání této metody.

Všimněte si, `Shutdown` že volání na objekt inicializovaný s ukazatelem na `CWorkerThread` jiný objekt nemá žádný účinek a vždy vrátí hodnotu S_OK.

## <a name="see-also"></a>Viz také:

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Třídy](../../atl/reference/atl-classes.md)<br/>
[Multithreading: Vytváření pracovních vláken](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient – rozhraní](../../atl/reference/iworkerthreadclient-interface.md)
