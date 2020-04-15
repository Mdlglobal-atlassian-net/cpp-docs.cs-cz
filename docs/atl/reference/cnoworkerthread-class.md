---
title: Třída CNoWorkerThread
ms.date: 11/04/2016
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
ms.openlocfilehash: 90056e648a53218ac06083d43ca34870e1ca72fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326710"
---
# <a name="cnoworkerthread-class"></a>Třída CNoWorkerThread

Tuto třídu použijte jako `MonitorClass` argument pro parametr šablony pro ukládání tříd do mezipaměti, pokud chcete zakázat údržbu dynamické mezipaměti.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CNoWorkerThread
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CNoWorkerThread::Přidejte handle](#addhandle)|Nefunkční ekvivalent [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|
|[CNoWorkerThread::Addtimer](#addtimer)|Nefunkční ekvivalent [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Nefunkční ekvivalent [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|
|[CNoWorkerThread::GetThreadId](#getthreadid)|Nefunkční ekvivalent [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|
|[CNoWorkerThread::Inicializovat](#initialize)|Nefunkční ekvivalent [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|
|[CNoWorkerThread::RemoveHandle](#removehandle)|Nefunkční ekvivalent [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|
|[CNoWorkerThread::Vypnutí](#shutdown)|Nefunkční ekvivalent [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje stejné veřejné rozhraní jako [CWorkerThread](../../atl/reference/cworkerthread-class.md). Očekává se, že toto `MonitorClass` rozhraní bude poskytnuto parametrem šablony pro třídy mezipaměti.

Metody v této třídě jsou implementovány neprovádět žádné. Metody, které vracejí HRESULT vždy vrátit S_OK a metody, které vracejí POPISOVAČ nebo ID vlákna vždy vrátí 0.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="cnoworkerthreadaddhandle"></a><a name="addhandle"></a>CNoWorkerThread::Přidejte handle

Nefunkční ekvivalent [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy se vrací S_OK.

### <a name="remarks"></a>Poznámky

Implementace poskytované této třídy neprovede žádné provádění.

## <a name="cnoworkerthreadaddtimer"></a><a name="addtimer"></a>CNoWorkerThread::Addtimer

Nefunkční ekvivalent [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy se vrací S_OK.

### <a name="remarks"></a>Poznámky

Implementace poskytované této třídy neprovede žádné provádění.

## <a name="cnoworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CNoWorkerThread::GetThreadHandle

Nefunkční ekvivalent [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Implementace poskytované této třídy neprovede žádné provádění.

## <a name="cnoworkerthreadgetthreadid"></a><a name="getthreadid"></a>CNoWorkerThread::GetThreadId

Nefunkční ekvivalent [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

Implementace poskytované této třídy neprovede žádné provádění.

## <a name="cnoworkerthreadinitialize"></a><a name="initialize"></a>CNoWorkerThread::Inicializovat

Nefunkční ekvivalent [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy se vrací S_OK.

### <a name="remarks"></a>Poznámky

Implementace poskytované této třídy neprovede žádné provádění.

## <a name="cnoworkerthreadremovehandle"></a><a name="removehandle"></a>CNoWorkerThread::RemoveHandle

Nefunkční ekvivalent [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy se vrací S_OK.

### <a name="remarks"></a>Poznámky

Implementace poskytované této třídy neprovede žádné provádění.

## <a name="cnoworkerthreadshutdown"></a><a name="shutdown"></a>CNoWorkerThread::Vypnutí

Nefunkční ekvivalent [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>Návratová hodnota

Vždy se vrací S_OK.

### <a name="remarks"></a>Poznámky

Implementace poskytované této třídy neprovede žádné provádění.
