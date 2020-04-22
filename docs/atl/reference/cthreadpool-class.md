---
title: Třída CThreadPool
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
ms.openlocfilehash: 5e52868f23883836919b96be9aec1815bc1c17b3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747447"
---
# <a name="cthreadpool-class"></a>Třída CThreadPool

Tato třída poskytuje fond pracovních podprocesů, které zpracovávají fronty pracovních položek.

## <a name="syntax"></a>Syntaxe

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Parametry

*Pracovník*<br/>
Třída, která odpovídá [archetypu pracovního procesu,](../../atl/reference/worker-archetype.md) který poskytuje kód používaný ke zpracování pracovních položek zařazených do fronty ve fondu vláken.

*ThreadTraits*<br/>
Třída poskytující funkci použitou k vytvoření podprocesů ve fondu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|Konstruktor pro fond vláken.|
|[CThreadPool::~CThreadPool](#dtor)|Destruktor pro fond vláken.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CThreadPool::Přidat odkaz](#addref)|Provádění `IUnknown::AddRef`.|
|[CThreadPool::GetNumThreads](#getnumthreads)|Volání této metody získat počet podprocesů ve fondu.|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Volání této metody získat popisovač portu dokončení vi slouží k fronty pracovních položek.|
|[CThreadPool::GetSize](#getsize)|Volání této metody získat počet podprocesů ve fondu.|
|[CThreadPool::GetTimeout](#gettimeout)|Volání této metody získat maximální čas v milisekundách, že fond vláken bude čekat na vypnutí podprocesu.|
|[CThreadPool::Inicializovat](#initialize)|Volání této metody k inicializaci fondu vláken.|
|[CThreadPool::QueryInterface](#queryinterface)|Provádění `IUnknown::QueryInterface`.|
|[CThreadPool::QueueRequest](#queuerequest)|Volání této metody do fronty pracovní položky, které mají být zpracovány podprocesem ve fondu.|
|[CThreadPool::Vydání](#release)|Provádění `IUnknown::Release`.|
|[CThreadPool::SetSize](#setsize)|Volání této metody nastavit počet podprocesů ve fondu.|
|[CThreadPool::SetTimeout](#settimeout)|Volání této metody nastavit maximální dobu v milisekundách, že fond vláken bude čekat na vypnutí podprocesu.|
|[CThreadPool::Vypnutí](#shutdown)|Volání této metody vypnout fondu vláken.|

## <a name="remarks"></a>Poznámky

Vlákna ve fondu jsou vytvořeny a zničeny při inicializování, velikosti nebo vypnutí fondu. Instance třídy *Worker* bude vytvořena v zásobníku každého pracovního vlákna ve fondu. Každá instance bude žít po dobu životnosti vlákna.

Ihned po vytvoření *Worker*vlákna`Initialize` bude worker :: volán na objekt přidružený k tomuto vláknu. Bezprostředně před zničením *Worker*vlákna`Terminate` bude volána worker :: . Obě metody musí přijmout **neplatný** <strong>\*</strong> argument. Hodnota tohoto argumentu je předána do fondu vláken prostřednictvím parametru *pvWorkerParam* [cthreadpool::Initialize](#initialize).

Pokud jsou pracovní položky ve frontě a pracovní podprocesy k dispozici pro práci, pracovní podproces vytáhne položku z fronty a volání `Execute` metody *Worker* objektu pro toto vlákno. Metodě jsou pak předány tři položky: položka `pvWorkerParam` z fronty, `Initialize` stejná předána *pracovníkovi*:: a *Pracovník*:: `Terminate`a ukazatel na [překrývající se](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) strukturu použitou pro frontu portů dokončení vi.

Worker *Třída* deklaruje typ položek, které budou zařazeny do fronty ve `RequestType`fondu vláken poskytnutím typedef, *Worker*:: . Tento typ musí být možné převrhnout do ULONG_PTR a z ULONG_PTR.

Příkladem třídy *Worker* je [třída CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="cthreadpooladdref"></a><a name="addref"></a>CThreadPool::Přidat odkaz

Provádění `IUnknown::AddRef`.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí 1.

### <a name="remarks"></a>Poznámky

Tato třída neimplementuje řízení životnosti pomocí počítání odkazů.

## <a name="cthreadpoolcthreadpool"></a><a name="cthreadpool"></a>CThreadPool::CThreadPool

Konstruktor pro fond vláken.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje hodnotu časového času, která má ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Výchozí čas je 36 sekund. V případě potřeby můžete definovat vlastní kladnou hodnotu celéčíslo pro tento symbol před zahrnutím atlutil.h.

## <a name="cthreadpoolcthreadpool"></a><a name="dtor"></a>CThreadPool::~CThreadPool

Destruktor pro fond vláken.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Poznámky

Volání [CThreadPool::Shutdown](#shutdown).

## <a name="cthreadpoolgetnumthreads"></a><a name="getnumthreads"></a>CThreadPool::GetNumThreads

Volání této metody získat počet podprocesů ve fondu.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet podprocesů ve fondu.

## <a name="cthreadpoolgetqueuehandle"></a><a name="getqueuehandle"></a>CThreadPool::GetQueueHandle

Volání této metody získat popisovač portu dokončení vi slouží k fronty pracovních položek.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač fronty nebo hodnotu NULL, pokud nebyl inicializován fond vláken.

## <a name="cthreadpoolgetsize"></a><a name="getsize"></a>CThreadPool::GetSize

Volání této metody získat počet podprocesů ve fondu.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Parametry

*pnNumThreads*<br/>
[out] Adresa proměnné, která při úspěchu obdrží počet podprocesů ve fondu.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cthreadpoolgettimeout"></a><a name="gettimeout"></a>CThreadPool::GetTimeout

Volání této metody získat maximální čas v milisekundách, že fond vláken bude čekat na vypnutí podprocesu.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Parametry

*pdwMaxWait*<br/>
[out] Adresa proměnné, která při úspěchu obdrží maximální dobu v milisekundách, po kterou bude fond vláken čekat na vypnutí vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato hodnota časového opovce je [použitc CThreadPool::Shutdown,](#shutdown) pokud žádná jiná hodnota je zadán a tato metoda.

## <a name="cthreadpoolinitialize"></a><a name="initialize"></a>CThreadPool::Inicializovat

Volání této metody k inicializaci fondu vláken.

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>Parametry

*pvWorkerParam*<br/>
Pracovní parametr, který má být předán `Initialize`objektu pracovního vlákna , `Execute`a `Terminate` metody.

*nNumThreads*<br/>
Požadovaný počet podprocesů ve fondu.

Pokud *nNumThreads* je záporná, jeho absolutní hodnota se vynásobí počtem procesorů v počítači získat celkový počet podprocesů.

Pokud *nNumThreads* je nula, ATLS_DEFAULT_THREADSPERPROC se vynásobí počtem procesorů v počítači získat celkový počet podprocesů.  Výchozí hodnota je 2 vlákna na procesor. V případě potřeby můžete definovat vlastní kladnou hodnotu celéčíslo pro tento symbol před zahrnutím atlutil.h.

*dwStackVelikost*<br/>
Velikost zásobníku pro každé vlákno ve fondu.

*hDokončení*<br/>
Popisovač objektu přidružit k portu dokončení.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="cthreadpoolqueryinterface"></a><a name="queryinterface"></a>CThreadPool::QueryInterface

Provádění `IUnknown::QueryInterface`.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Poznámky

Objekty této třídy lze úspěšně `IUnknown` dotazován pro rozhraní a [iThreadPoolConfig.](../../atl/reference/ithreadpoolconfig-interface.md)

## <a name="cthreadpoolqueuerequest"></a><a name="queuerequest"></a>CThreadPool::QueueRequest

Volání této metody do fronty pracovní položky, které mají být zpracovány podprocesem ve fondu.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Parametry

*Požadavek*<br/>
Požadavek, který má být zařazen do fronty.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Tato metoda přidá pracovní položku do fronty. Podprocesy ve fondu vyskladnit položky z fronty v pořadí, ve kterém jsou přijaty.

## <a name="cthreadpoolrelease"></a><a name="release"></a>CThreadPool::Vydání

Provádění `IUnknown::Release`.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí 1.

### <a name="remarks"></a>Poznámky

Tato třída neimplementuje řízení životnosti pomocí počítání odkazů.

## <a name="cthreadpoolsetsize"></a><a name="setsize"></a>CThreadPool::SetSize

Volání této metody nastavit počet podprocesů ve fondu.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Parametry

*nNumThreads*<br/>
Požadovaný počet podprocesů ve fondu.

Pokud *nNumThreads* je záporná, jeho absolutní hodnota se vynásobí počtem procesorů v počítači získat celkový počet podprocesů.

Pokud *nNumThreads* je nula, ATLS_DEFAULT_THREADSPERPROC se vynásobí počtem procesorů v počítači získat celkový počet podprocesů. Výchozí hodnota je 2 vlákna na procesor. V případě potřeby můžete definovat vlastní kladnou hodnotu celéčíslo pro tento symbol před zahrnutím atlutil.h.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pokud je zadaný počet podprocesů menší než počet vláken, které jsou aktuálně ve fondu, umístí objekt zprávu o vypnutí do fronty, která má být vyzvednuta čekajícím vláknem. Když čekající vlákno vytáhne zprávu z fronty, upozorní fondu vláken a ukončí postup podprocesu. Tento proces se opakuje, dokud počet podprocesů ve fondu nedosáhne zadaného čísla nebo dokud žádné vlákno nebylo ukončeno v období určeném [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). V takovém případě metoda vrátí HRESULT odpovídající WAIT_TIMEOUT a čekající zpráva o vypnutí je zrušena.

## <a name="cthreadpoolsettimeout"></a><a name="settimeout"></a>CThreadPool::SetTimeout

Volání této metody nastavit maximální dobu v milisekundách, že fond vláken bude čekat na vypnutí podprocesu.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Požadovaná maximální doba v milisekundách, po kterou bude fond vláken čekat na vypnutí vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Časový čas je inicializován, aby ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Výchozí čas je 36 sekund. V případě potřeby můžete definovat vlastní kladnou hodnotu celéčíslo pro tento symbol před zahrnutím atlutil.h.

Všimněte si, že *dwMaxWait* je čas, který fond bude čekat na vypnutí jednoho vlákna. Maximální doba, která by mohla být přijata k odebrání více vláken z fondu může být o něco menší než *dwMaxWait* vynásobené počet podprocesů.

## <a name="cthreadpoolshutdown"></a><a name="shutdown"></a>CThreadPool::Vypnutí

Volání této metody vypnout fondu vláken.

```cpp
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Požadovaná maximální doba v milisekundách, po kterou bude fond vláken čekat na vypnutí vlákna. Pokud je zadána hodnota 0 nebo žádná, bude tato metoda používat časový čas nastavený [CThreadPool::SetTimeout](#settimeout).

### <a name="remarks"></a>Poznámky

Tato metoda zaúčtuje požadavek na vypnutí do všech vláken ve fondu. Pokud vyprší časový limit, tato metoda bude volat [TerminateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-terminatethread) na libovolné vlákno, které nebylo ukončeno. Tato metoda je volána automaticky z destruktoru třídy.

## <a name="see-also"></a>Viz také

[Rozhraní IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[Výchozí threadtraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Třídy](../../atl/reference/atl-classes.md)
