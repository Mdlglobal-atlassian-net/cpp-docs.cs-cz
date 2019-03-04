---
title: Cthreadpool – třída
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
ms.openlocfilehash: 7d363de0d787ecc5015093005b39a379acd82e71
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262698"
---
# <a name="cthreadpool-class"></a>Cthreadpool – třída

Tato třída poskytuje fondu pracovních vláken, které zpracovávají fronty pracovních položek.

## <a name="syntax"></a>Syntaxe

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Parametry

*Pracovního procesu*<br/>
Třída odpovídají [archetyp pracovního procesu](../../atl/reference/worker-archetype.md) poskytuje kód používá ke zpracování pracovní položky ve frontě fondu vláken.

*ThreadTraits*<br/>
Třída poskytující funkce použitá k vytvoření vláken ve fondu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|Konstruktor pro fond vláken.|
|[CThreadPool::~CThreadPool](#dtor)|Destruktor pro fond vláken.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|Provádění `IUnknown::AddRef`.|
|[CThreadPool::GetNumThreads](#getnumthreads)|Volejte tuto metodu za účelem získání počet vláken ve fondu.|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Voláním této metody lze získat popisovač sloužící k vytvoření fronty pracovních položek port dokončení vstupně-výstupních operací.|
|[CThreadPool::GetSize](#getsize)|Volejte tuto metodu za účelem získání počet vláken ve fondu.|
|[CThreadPool::GetTimeout](#gettimeout)|Volejte tuto metodu za účelem získání maximální dobu v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.|
|[CThreadPool::Initialize](#initialize)|Volejte tuto metodu za účelem inicializace fondu vláken.|
|[CThreadPool::QueryInterface](#queryinterface)|Provádění `IUnknown::QueryInterface`.|
|[CThreadPool::QueueRequest](#queuerequest)|Volání této metody do fronty pracovní položku zpracovávat vláken ve fondu.|
|[CThreadPool::Release](#release)|Provádění `IUnknown::Release`.|
|[CThreadPool::SetSize](#setsize)|Voláním této metody nastavte počet vláken ve fondu.|
|[CThreadPool::SetTimeout](#settimeout)|Volejte tuto metodu za účelem nastavení maximální doby v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.|
|[CThreadPool::Shutdown](#shutdown)|Volejte tuto metodu k vypnutí fondu vláken.|

## <a name="remarks"></a>Poznámky

Vláken ve fondu se vytvoří a zničeno při inicializován, změně velikosti nebo vypnutí fondu. Instance třídy *pracovního procesu* se vytvoří v zásobníku každého pracovního vlákna ve fondu. Každá instance bude live pro životnost vlákna.

Ihned po vytvoření vlákna *pracovního procesu*::`Initialize` bude volána na objektu souvisejícího s tímto vláknem. Bezprostředně před ničení vlákna *pracovního procesu*::`Terminate` , zavolá se. Obě metody musíte souhlasit **void** <strong>\*</strong> argument. Byla předána hodnota tohoto argumentu do fondu vláken prostřednictvím *pvWorkerParam* parametr [CThreadPool::Initialize](#initialize).

Pokud nejsou pracovní položky ve vláknech frontu a pracovní proces k dispozici pro práci, pracovní vlákno přetáhne položky fronty a volání `Execute` metodu *pracovního procesu* objektu pro toto vlákno. Tři položky jsou potom předány metodě: položky z fronty, stejné `pvWorkerParam` předán *pracovního procesu*:: `Initialize` a *pracovního procesu*:: `Terminate`a ukazatel [OVERLAPPED](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) struktura používaná pro frontu port dokončení vstupně-výstupních operací.

*Pracovního procesu* třída deklaruje typ položky, které bude zařazená do fronty ve fondu vláken poskytuje definice typu, *pracovního procesu*:: `RequestType`. Tento typ musí být schopné přetypování do a z ULONG_PTR.

Příklad *pracovního procesu* třída je [cnonstatelessworker – třída](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

##  <a name="addref"></a>  CThreadPool::AddRef

Provádění `IUnknown::AddRef`.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 1.

### <a name="remarks"></a>Poznámky

Tato třída neimplementuje životnost ovládací prvek s použitím počítání odkazů.

##  <a name="cthreadpool"></a>  CThreadPool::CThreadPool

Konstruktor pro fond vláken.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Poznámky

Hodnota časového limitu pro ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT inicializuje. Výchozí doba je 36 sekund. V případě potřeby můžete definovat vlastní kladnou celočíselnou hodnotu pro tento symbol před zahrnutím atlutil.h.

##  <a name="dtor"></a>  CThreadPool::~CThreadPool

Destruktor pro fond vláken.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Poznámky

Volání [CThreadPool::Shutdown](#shutdown).

##  <a name="getnumthreads"></a>  CThreadPool::GetNumThreads

Volejte tuto metodu za účelem získání počet vláken ve fondu.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet vláken ve fondu.

##  <a name="getqueuehandle"></a>  CThreadPool::GetQueueHandle

Voláním této metody lze získat popisovač sloužící k vytvoření fronty pracovních položek port dokončení vstupně-výstupních operací.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač fronty nebo hodnota NULL, pokud nebyla inicializována fondu vláken.

##  <a name="getsize"></a>  CThreadPool::GetSize

Volejte tuto metodu za účelem získání počet vláken ve fondu.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Parametry

*pnNumThreads*<br/>
[out] Adresa proměnné, která v případě úspěchu, obdrží počet vláken ve fondu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="gettimeout"></a>  CThreadPool::GetTimeout

Volejte tuto metodu za účelem získání maximální dobu v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Parametry

*pdwMaxWait*<br/>
[out] Adresa proměnné, která v případě úspěchu, obdrží maximální dobu v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato hodnota časového limitu je používán [CThreadPool::Shutdown](#shutdown) Pokud k této metodě není zadána žádná hodnota.

##  <a name="initialize"></a>  CThreadPool::Initialize

Volejte tuto metodu za účelem inicializace fondu vláken.

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>Parametry

*pvWorkerParam*<br/>
Parametr pracovního procesu se mají předat objekt vlákna pracovního procesu `Initialize`, `Execute`, a `Terminate` metody.

*nNumThreads*<br/>
Požadovaný počet vláken ve fondu.

Pokud *nNumThreads* je záporný, jeho absolutní hodnota se vynásobí číslo odpovídající počtu procesorů v počítači, chcete-li získat celkový počet vláken.

Pokud *nNumThreads* je nula, ATLS_DEFAULT_THREADSPERPROC bude vynásobené celkovým počtem procesorů v počítači, chcete-li získat celkový počet vláken.  Výchozí hodnota je 2 vláken na procesor. V případě potřeby můžete definovat vlastní kladnou celočíselnou hodnotu pro tento symbol před zahrnutím atlutil.h.

*dwStackSize*<br/>
Velikost zásobníku pro každé vlákno ve fondu.

*hCompletion*<br/>
Popisovač objektu pro přidružení k port dokončení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="queryinterface"></a>  CThreadPool::QueryInterface

Provádění `IUnknown::QueryInterface`.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Poznámky

Objekty této třídy může být dotázán úspěšně pro `IUnknown` a [ithreadpoolconfig –](../../atl/reference/ithreadpoolconfig-interface.md) rozhraní.

##  <a name="queuerequest"></a>  CThreadPool::QueueRequest

Volání této metody do fronty pracovní položku zpracovávat vláken ve fondu.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Parametry

*Požadavek*<br/>
Požadavek na zařadí do fronty.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda přidá do fronty pracovní položku. Vláken ve fondu v pořadí, ve kterém jsou přijímány vybrat položky z fronty.

##  <a name="release"></a>  CThreadPool::Release

Provádění `IUnknown::Release`.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 1.

### <a name="remarks"></a>Poznámky

Tato třída neimplementuje životnost ovládací prvek s použitím počítání odkazů.

##  <a name="setsize"></a>  CThreadPool::SetSize

Voláním této metody nastavte počet vláken ve fondu.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Parametry

*nNumThreads*<br/>
Požadovaný počet vláken ve fondu.

Pokud *nNumThreads* je záporný, jeho absolutní hodnota se vynásobí číslo odpovídající počtu procesorů v počítači, chcete-li získat celkový počet vláken.

Pokud *nNumThreads* je nula, ATLS_DEFAULT_THREADSPERPROC bude vynásobené celkovým počtem procesorů v počítači, chcete-li získat celkový počet vláken. Výchozí hodnota je 2 vláken na procesor. V případě potřeby můžete definovat vlastní kladnou celočíselnou hodnotu pro tento symbol před zahrnutím atlutil.h.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pokud zadaný počet podprocesů je menší než počet vláken aktuálně ve fondu, převede objekt vypnutí zprávu ve frontě na vyzvednutí vláknem čekání. Při čekání vlákno přebírá zprávu z fronty, upozorní fondu vláken a ukončí proceduru vlákna. Tento postup se opakuje, dokud nedosáhne zadané číslo počet vláken ve fondu, nebo dokud žádné vlákno neskončí v rámci zadané období [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). V této situaci metoda vrátí odpovídající WAIT_TIMEOUT HRESULT a zprávu čeká na vypnutí se zruší.

##  <a name="settimeout"></a>  CThreadPool::SetTimeout

Volejte tuto metodu za účelem nastavení maximální doby v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Maximální požadovaný čas v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Časový limit je inicializován na ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Výchozí doba je 36 sekund. V případě potřeby můžete definovat vlastní kladnou celočíselnou hodnotu pro tento symbol před zahrnutím atlutil.h.

Všimněte si, že *dwMaxWait* je doba, kterou fond počká na jedno vlákno pro vypnutí. Maximální doba, kterou lze provést z fondu odebrat více vláken může být o něco menší než *dwMaxWait* počtem vláken.

##  <a name="shutdown"></a>  CThreadPool::Shutdown

Volejte tuto metodu k vypnutí fondu vláken.

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Maximální požadovaný čas v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí. Pokud je zadána žádná hodnota nebo 0, tato metoda použije časový limit nastavený [CThreadPool::SetTimeout](#settimeout).

### <a name="remarks"></a>Poznámky

Tato metoda odešle žádost o vypnutí na všechna vlákna ve fondu. Pokud vyprší časový limit bude volat tuto metodu [TerminateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-terminatethread) v libovolném vlákně, které se neukončil. Tato metoda je volána automaticky z destruktoru třídy.

## <a name="see-also"></a>Viz také:

[IThreadPoolConfig – rozhraní](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Třídy](../../atl/reference/atl-classes.md)
