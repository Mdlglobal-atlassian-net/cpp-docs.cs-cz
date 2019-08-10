---
title: CThreadPool – třída
ms.date: 11/04/2016
f1_keywords:
- CThreadPool
- ATLUTIL/ATL::CThreadPool
- ATLUTIL/ATL::CThreadPool::CThreadPool
- ATLUTIL/ATL::CThreadPool::AddRef
- ATLUTIL/ATL::CThreadPool::GetNumThreads
- ATLUTIL/ATL::CThreadPool::GetQueueHandle
- ATLUTIL/ATL::CThreadPool::GetSize
- ATLUTIL/ATL::CThreadPool::GetTimeout
- ATLUTIL/ATL::CThreadPool::Initialize
- ATLUTIL/ATL::CThreadPool::QueryInterface
- ATLUTIL/ATL::CThreadPool::QueueRequest
- ATLUTIL/ATL::CThreadPool::Release
- ATLUTIL/ATL::CThreadPool::SetSize
- ATLUTIL/ATL::CThreadPool::SetTimeout
- ATLUTIL/ATL::CThreadPool::Shutdown
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
ms.openlocfilehash: 07fd470a6aeab0575f2733d72650bd695b8e2752
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915691"
---
# <a name="cthreadpool-class"></a>CThreadPool – třída

Tato třída poskytuje fond pracovních vláken, která zpracovávají frontu pracovních položek.

## <a name="syntax"></a>Syntaxe

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Parametry

*Zaměstnanec*<br/>
Třída, která odpovídá [Archetype pracovního procesu](../../atl/reference/worker-archetype.md) , poskytuje kód používaný ke zpracování pracovních položek ve frontě ve fondu vláken.

*ThreadTraits*<br/>
Třída, která poskytuje funkci použitou k vytvoření vláken ve fondu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|Konstruktor pro fond vláken.|
|[CThreadPool::~CThreadPool](#dtor)|Destruktor pro fond vláken.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CThreadPool:: AddRef](#addref)|`IUnknown::AddRef`Implementace.|
|[CThreadPool::GetNumThreads](#getnumthreads)|Voláním této metody získáte počet vláken ve fondu.|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Voláním této metody získáte popisovač portu pro vstupně-výstupní operace, který se používá k zařazení pracovních položek do fronty.|
|[CThreadPool:: GetSize](#getsize)|Voláním této metody získáte počet vláken ve fondu.|
|[CThreadPool::GetTimeout](#gettimeout)|Voláním této metody získáte maximální dobu v milisekundách, po kterou bude fond vláken čekat na vypnutí vlákna.|
|[CThreadPool:: Initialize](#initialize)|Voláním této metody inicializujete fond vláken.|
|[CThreadPool::QueryInterface](#queryinterface)|`IUnknown::QueryInterface`Implementace.|
|[CThreadPool::QueueRequest](#queuerequest)|Voláním této metody zařadíte do fronty pracovní položku, která má být zpracována vláknem ve fondu.|
|[CThreadPool:: Release](#release)|`IUnknown::Release`Implementace.|
|[CThreadPool:: SetSize](#setsize)|Voláním této metody nastavíte počet vláken ve fondu.|
|[CThreadPool:: SetTimeout](#settimeout)|Voláním této metody nastavíte maximální dobu v milisekundách, po kterou bude fond vláken čekat na vypnutí vlákna.|
|[CThreadPool::Shutdown](#shutdown)|Voláním této metody vypnete fond vláken.|

## <a name="remarks"></a>Poznámky

Vlákna ve fondu jsou vytvořena a zničena při inicializaci fondu, změně velikosti nebo vypnutí. Instance *pracovního procesu* třídy se vytvoří v zásobníku všech pracovních vláken ve fondu. Každá instance bude po celou dobu životnosti vlákna živá.

Ihned po vytvoření vlákna *pracovní*proces::`Initialize` bude volána u objektu přidruženého k danému vláknu. Bezprostředně před zničením vlákna, *Worker*::`Terminate` bude volána. Obě metody musí přijmout argument **void** <strong>\*</strong> . Hodnota tohoto argumentu je předána fondu vláken prostřednictvím parametru *PvWorkerParam* [CThreadPool:: Initialize](#initialize).

Pokud jsou ve frontě dostupné pracovní položky a pracovní vlákna jsou k dispozici pro práci, pracovní podproces vyžádá položku mimo frontu a zavolá `Execute` metodu objektu *Worker* daného vlákna. Tři položky `pvWorkerParam` jsou následně předány do metody: položka z fronty, která byla předána `Initialize` pracovnímu procesu:: a *Worker*: `Terminate`:, a ukazatel na překrývající se strukturu použitou pro frontu portů při dokončování v/v. [](/windows/desktop/api/minwinbase/ns-minwinbase-overlapped) .

Třída *Worker* deklaruje typ položek, které budou zařazeny do fronty ve fondu vláken poskytnutím typedef, Worker:: `RequestType`. Tento typ musí být schopný přetypování do a z ULONG_PTR.

Příkladem třídy *pracovního procesu* je [Třída CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil. h

##  <a name="addref"></a>CThreadPool:: AddRef

`IUnknown::AddRef`Implementace.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždycky vrátí hodnotu 1.

### <a name="remarks"></a>Poznámky

Tato třída neimplementuje řízení životnosti pomocí počítání odkazů.

##  <a name="cthreadpool"></a>CThreadPool::CThreadPool

Konstruktor pro fond vláken.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje hodnotu timeout na ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Výchozí čas je 36 sekund. V případě potřeby můžete pro tento symbol definovat vlastní kladnou celočíselnou hodnotu před zahrnutím atlutil. h.

##  <a name="dtor"></a>CThreadPool:: ~ CThreadPool

Destruktor pro fond vláken.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Poznámky

Volá [CThreadPool:: Shutdown](#shutdown).

##  <a name="getnumthreads"></a>CThreadPool::GetNumThreads

Voláním této metody získáte počet vláken ve fondu.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet vláken ve fondu.

##  <a name="getqueuehandle"></a>CThreadPool::GetQueueHandle

Voláním této metody získáte popisovač portu pro vstupně-výstupní operace, který se používá k zařazení pracovních položek do fronty.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač fronty nebo hodnotu NULL, pokud fond vláken nebyl inicializován.

##  <a name="getsize"></a>CThreadPool:: GetSize

Voláním této metody získáte počet vláken ve fondu.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Parametry

*pnNumThreads*<br/>
mimo Adresa proměnné, která po úspěchu obdrží počet vláken ve fondu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="gettimeout"></a>CThreadPool:: GetTime

Voláním této metody získáte maximální dobu v milisekundách, po kterou bude fond vláken čekat na vypnutí vlákna.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Parametry

*pdwMaxWait*<br/>
mimo Adresa proměnné, která po úspěchu získá maximální dobu v milisekundách, po kterou bude fond vláken čekat na vypnutí vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tuto hodnotu časového limitu používá [CThreadPool:: Shutdown](#shutdown) , pokud k této metodě není dodána žádná jiná hodnota.

##  <a name="initialize"></a>CThreadPool:: Initialize

Voláním této metody inicializujete fond vláken.

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>Parametry

*pvWorkerParam*<br/>
Parametr pracovního procesu, který se má předat metodám objektu `Initialize`pracovního vlákna, `Execute`a. `Terminate`

*nNumThreads*<br/>
Požadovaný počet vláken ve fondu.

Pokud je *nNumThreads* záporné, jeho absolutní hodnota se vynásobí počtem procesorů v počítači, aby se získal celkový počet vláken.

Pokud má *nNumThreads* hodnotu nula, ATLS_DEFAULT_THREADSPERPROC se vynásobí počtem procesorů v počítači, aby se získal celkový počet vláken.  Výchozí hodnota je 2 vlákna na procesor. V případě potřeby můžete pro tento symbol definovat vlastní kladnou celočíselnou hodnotu před zahrnutím atlutil. h.

*dwStackSize*<br/>
Velikost zásobníku pro každé vlákno ve fondu.

*hCompletion*<br/>
Popisovač objektu, který má být přidružen k portu pro dokončení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="queryinterface"></a>  CThreadPool::QueryInterface

`IUnknown::QueryInterface`Implementace.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Poznámky

K `IUnknown` objektům této třídy se můžete úspěšně dotázat na rozhraní a [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) .

##  <a name="queuerequest"></a>CThreadPool::QueueRequest

Voláním této metody zařadíte do fronty pracovní položku, která má být zpracována vláknem ve fondu.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Parametry

*Request*<br/>
Požadavek, který se má zařadit do fronty

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda přidá do fronty pracovní položku. Vlákna ve fondu umožňují vybrat položky mimo frontu v pořadí, ve kterém byly přijaty.

##  <a name="release"></a>CThreadPool:: Release

`IUnknown::Release`Implementace.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždycky vrátí hodnotu 1.

### <a name="remarks"></a>Poznámky

Tato třída neimplementuje řízení životnosti pomocí počítání odkazů.

##  <a name="setsize"></a>CThreadPool:: SetSize

Voláním této metody nastavíte počet vláken ve fondu.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Parametry

*nNumThreads*<br/>
Požadovaný počet vláken ve fondu.

Pokud je *nNumThreads* záporné, jeho absolutní hodnota se vynásobí počtem procesorů v počítači, aby se získal celkový počet vláken.

Pokud má *nNumThreads* hodnotu nula, ATLS_DEFAULT_THREADSPERPROC se vynásobí počtem procesorů v počítači, aby se získal celkový počet vláken. Výchozí hodnota je 2 vlákna na procesor. V případě potřeby můžete pro tento symbol definovat vlastní kladnou celočíselnou hodnotu před zahrnutím atlutil. h.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pokud je zadaný počet podprocesů menší než počet vláken, která jsou aktuálně ve fondu, objekt umístí do fronty zprávu o vypnutí, která má být vyzvednuta čekajícím vláknem. Když čekající vlákno odešle zprávu z fronty, upozorní fond vláken a ukončí proceduru vlákna. Tento proces se opakuje, dokud počet vláken ve fondu nedosáhne zadaného počtu nebo dokud se žádné vlákno neukončilo během období určeného parametrem [GetTime](#gettimeout)/ -[setTimeout](#settimeout). V této situaci metoda vrátí hodnotu HRESULT odpovídající WAIT_TIMEOUT a zpráva čeká na vypnutí se zruší.

##  <a name="settimeout"></a>CThreadPool:: SetTimeout

Voláním této metody nastavíte maximální dobu v milisekundách, po kterou bude fond vláken čekat na vypnutí vlákna.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Požadovaný maximální čas v milisekundách, po který bude fond vláken čekat na vypnutí vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Časový limit se inicializuje do ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Výchozí čas je 36 sekund. V případě potřeby můžete pro tento symbol definovat vlastní kladnou celočíselnou hodnotu před zahrnutím atlutil. h.

Všimněte si, že *dwMaxWait* je čas, po který bude fond čekat na vypnutí jednoho vlákna. Maximální doba, kterou by bylo možné učinit pro odebrání více vláken z fondu, může být trochu menší než *dwMaxWait* vynásobená počtem vláken.

##  <a name="shutdown"></a>CThreadPool:: Shutdown

Voláním této metody vypnete fond vláken.

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Požadovaný maximální čas v milisekundách, po který bude fond vláken čekat na vypnutí vlákna. Pokud není zadána hodnota 0 nebo žádná hodnota, tato metoda použije časový limit nastavený hodnotou [CThreadPool:: setTimeout](#settimeout).

### <a name="remarks"></a>Poznámky

Tato metoda účtuje požadavek na vypnutí do všech vláken ve fondu. Pokud časový limit vyprší, tato metoda bude volat [TerminateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-terminatethread) na jakémkoli vlákně, které nebylo ukončeno. Tato metoda je volána automaticky z destruktoru třídy.

## <a name="see-also"></a>Viz také:

[IThreadPoolConfig – rozhraní](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Třídy](../../atl/reference/atl-classes.md)
