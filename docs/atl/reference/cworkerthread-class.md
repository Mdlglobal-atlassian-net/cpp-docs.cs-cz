---
title: Cworkerthread – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e2c3e0eb625c492cb9f0e9a1234d33149ac201a1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040229"
---
# <a name="cworkerthread-class"></a>Cworkerthread – třída

Tato třída vytvoří pracovní vlákno nebo použije existující předplatné, čeká na jeden nebo více jádra manipulačních bodů objektu a provede funkci zadaného klienta v případě jednoho z úchytů signalizován.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

#### <a name="parameters"></a>Parametry

*ThreadTraits*<br/>
Třída poskytující funkce vytvoření vláken, jako například [crtthreadtraits –](../../atl/reference/crtthreadtraits-class.md) nebo [win32threadtraits –](../../atl/reference/win32threadtraits-class.md).

## <a name="members"></a>Členové

### <a name="protected-structures"></a>Chráněné struktury

|Název|Popis|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|Konstruktor pro pracovní vlákno.|
|[Cworkerthread –:: ~ cworkerthread –](#dtor)|Destruktor pro pracovní vlákno.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|Voláním této metody lze přidat popisovač generický objekt do seznamu spravuje pomocí pracovní vlákno.|
|[CWorkerThread::AddTimer](#addtimer)|Voláním této metody lze přidat do seznamu spravuje pomocí pracovní podproces pravidelné generický časovače.|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Volejte tuto metodu za účelem získání popisovač vlákna pracovního podprocesu.|
|[CWorkerThread::GetThreadId](#getthreadid)|Voláním této metody k získání ID vlákna pracovního podprocesu.|
|[CWorkerThread::Initialize](#initialize)|Volejte tuto metodu za účelem inicializace pracovního vlákna.|
|[CWorkerThread::RemoveHandle](#removehandle)|Volejte tuto metodu za účelem odebrání popisovač seznamu generický objektů.|
|[CWorkerThread::Shutdown](#shutdown)|Volejte tuto metodu pro ukončení pracovního vlákna.|

## <a name="remarks"></a>Poznámky

### <a name="to-use-cworkerthread"></a>Cworkerthread – použití

1. Vytvoření instance této třídy.

2. Volání [CWorkerThread::Initialize](#initialize).

3. Volání [CWorkerThread::AddHandle](#addhandle) s popisovačem objekt jádra a ukazatel na implementaci [iworkerthreadclient –](../../atl/reference/iworkerthreadclient-interface.md).

     - nebo –

     Volání [CWorkerThread::AddTimer](#addtimer) s ukazatelem na implementaci [iworkerthreadclient –](../../atl/reference/iworkerthreadclient-interface.md).

4. Implementace [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) k provedlo určitou akci, když je signál, popisovač nebo časovače.

5. Chcete-li odebrat objekt ze seznamu generický objektů, zavolejte [CWorkerThread::RemoveHandle](#removehandle).

6. Chcete-li ukončit vlákno, volejte [CWorkerThread::Shutdown](#shutdown).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

##  <a name="addhandle"></a>  CWorkerThread::AddHandle

Voláním této metody lze přidat popisovač generický objekt do seznamu spravuje pomocí pracovní vlákno.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Popisovač na generický objekt.

*pClient*<br/>
Ukazatel [iworkerthreadclient –](../../atl/reference/iworkerthreadclient-interface.md) rozhraní na objekt, který má volat, pokud je signalizována popisovač.

*dwParam*<br/>
Parametr má být předán [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) při signalizován popisovač.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) zavolá prostřednictvím *pClient* při zpracování, *hObject*, signalizován.

##  <a name="addtimer"></a>  CWorkerThread::AddTimer

Voláním této metody lze přidat do seznamu spravuje pomocí pracovní podproces pravidelné generický časovače.

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>Parametry

*dwInterval*<br/>
Určuje dobu, po časovače v milisekundách.

*pClient*<br/>
Ukazatel [iworkerthreadclient –](../../atl/reference/iworkerthreadclient-interface.md) rozhraní na objekt, který má volat, pokud je signalizována popisovač.

*dwParam*<br/>
Parametr má být předán [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) při signalizován popisovač.

*phTimer*<br/>
[out] Adresa proměnné POPISOVAČ, který v případě úspěchu, obdrží popisovač do nově vytvořeného časovače.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) zavolá prostřednictvím *pClient* při signalizován časovač.

Předejte časovače popisovač z *phTimer* k [CWorkerThread::RemoveHandle](#removehandle) zavřete časovač.

##  <a name="cworkerthread"></a>  CWorkerThread::CWorkerThread

Konstruktor

```
CWorkerThread() throw();
```

##  <a name="dtor"></a>  Cworkerthread –:: ~ cworkerthread –

Destruktor.

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>Poznámky

Volání [CWorkerThread::Shutdown](#shutdown).

##  <a name="getthreadhandle"></a>  CWorkerThread::GetThreadHandle

Volejte tuto metodu za účelem získání popisovač vlákna pracovního podprocesu.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač vlákna nebo hodnota NULL, pokud pracovní podproces nebyla inicializována.

##  <a name="getthreadid"></a>  CWorkerThread::GetThreadId

Voláním této metody k získání ID vlákna pracovního podprocesu.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ID vlákna nebo hodnota NULL, pokud pracovní podproces nebyla inicializována.

##  <a name="initialize"></a>  CWorkerThread::Initialize

Volejte tuto metodu za účelem inicializace pracovního vlákna.

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

Tato metoda by měla být volána k inicializaci objektu po vytvoření nebo po volání [CWorkerThread::Shutdown](#shutdown).

Má dvě nebo více `CWorkerThread` objekty použít stejný pracovní vlákno, jeden z nich bez předávání argumentů poté předat ukazatel na tento objekt k inicializaci `Initialize` ostatních metod. Objekty inicializován pomocí ukazatele byste před objekt použitý k jejich inicializaci vypněte.

Zobrazit [CWorkerThread::Shutdown](#shutdown) informace o tom, jak mění chování této metody při inicializaci pomocí ukazatele na existující objekt.

##  <a name="removehandle"></a>  CWorkerThread::RemoveHandle

Volejte tuto metodu za účelem odebrání popisovač seznamu generický objektů.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Obslužná rutina pro odebrání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Když se odebere popisovač [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) bude volána při přidruženého objektu, který byl předán [AddHandle](#addhandle). Pokud se toto volání se nezdaří, `CWorkerThread` zavolá Windows [CloseHandle](https://msdn.microsoft.com/library/windows/desktop/ms724211) funkce na popisovač.

##  <a name="shutdown"></a>  CWorkerThread::Shutdown

Volejte tuto metodu pro ukončení pracovního vlákna.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>Parametry

*dwWait*<br/>
Čas v milisekundách pro čekání pracovního vlákna, vypnout. ATL_WORKER_THREAD_WAIT výchozí hodnota je 10 sekund. V případě potřeby můžete definovat vlastní hodnotu pro tento symbol před zahrnutím atlutil.h.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK na úspěch nebo chybu HRESULT při selhání, třeba když hodnota časového limitu *dwWait*, dojde k překročení.

### <a name="remarks"></a>Poznámky

Chcete-li znovu použít objekt, zavolejte [CWorkerThread::Initialize](#initialize) po volání této metody.

Všimněte si, že volání `Shutdown` na objekt inicializován pomocí ukazatele na jiný `CWorkerThread` objekt nemá žádný vliv a vždy vrátí hodnotu S_OK.

## <a name="see-also"></a>Viz také

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Třídy](../../atl/reference/atl-classes.md)<br/>
[Multithreading: Vytváření pracovních vláken](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient – rozhraní](../../atl/reference/iworkerthreadclient-interface.md)
