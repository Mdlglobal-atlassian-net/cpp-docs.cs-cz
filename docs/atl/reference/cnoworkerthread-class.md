---
title: Třída CNoWorkerThread | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85e1962d10f274f4f8c35ba27cb05c41e8bf19cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cnoworkerthread-class"></a>CNoWorkerThread – třída
Tato třída slouží jako argument pro `MonitorClass` parametr šablony do mezipaměti tříd, pokud chcete zakázat dynamické mezipaměti údržby.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CNoWorkerThread
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CNoWorkerThread::AddHandle](#addhandle)|Non-ekvivalentní [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|  
|[CNoWorkerThread::AddTimer](#addtimer)|Non-ekvivalentní [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|  
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Non-ekvivalentní [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|  
|[CNoWorkerThread::GetThreadId](#getthreadid)|Non-ekvivalentní [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|  
|[CNoWorkerThread::Initialize](#initialize)|Non-ekvivalentní [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|  
|[CNoWorkerThread::RemoveHandle](#removehandle)|Non-ekvivalentní [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|  
|[CNoWorkerThread::Shutdown](#shutdown)|Non-ekvivalentní [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje stejné veřejné rozhraní jako [CWorkerThread](../../atl/reference/cworkerthread-class.md). Toto rozhraní se očekává poskytovaný `MonitorClass` parametr šablony do mezipaměti tříd.  
  
 Metody v této třídě jsou implementované se nic nestane. Metody, které vracejí HRESULT vždy vrátí S_OK a metody, které vrátí POPISOVAČ nebo vlákno ID vždy vrátí 0.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlutil.h  
  
##  <a name="addhandle"></a>  CNoWorkerThread::AddHandle  
 Non-ekvivalentní [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
```
HRESULT AddHandle(HANDLE /* hObject
 */,
    IWorkerThreadClient* /* pClient
 */,
    DWORD_PTR /* dwParam
 */) throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Implementace poskytuje tuto třídu neprovede žádnou akci.  
  
##  <a name="addtimer"></a>  CNoWorkerThread::AddTimer  
 Non-ekvivalentní [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).  
  
```
HRESULT AddTimer(DWORD /* dwInterval
 */,
    IWorkerThreadClient* /* pClient
 */,
    DWORD_PTR /* dwParam
 */,
    HANDLE* /* phTimer
 */) throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Implementace poskytuje tuto třídu neprovede žádnou akci.  
  
##  <a name="getthreadhandle"></a>  CNoWorkerThread::GetThreadHandle  
 Non-ekvivalentní [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu NULL.  
  
### <a name="remarks"></a>Poznámky  
 Implementace poskytuje tuto třídu neprovede žádnou akci.  
  
##  <a name="getthreadid"></a>  CNoWorkerThread::GetThreadId  
 Non-ekvivalentní [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Implementace poskytuje tuto třídu neprovede žádnou akci.  
  
##  <a name="initialize"></a>  CNoWorkerThread::Initialize  
 Non-ekvivalentní [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).  
  
```
HRESULT Initialize() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Implementace poskytuje tuto třídu neprovede žádnou akci.  
  
##  <a name="removehandle"></a>  CNoWorkerThread::RemoveHandle  
 Non-ekvivalentní [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).  
  
```
HRESULT RemoveHandle(HANDLE /* hObject
 */) throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Implementace poskytuje tuto třídu neprovede žádnou akci.  
  
##  <a name="shutdown"></a>  CNoWorkerThread::Shutdown  
 Non-ekvivalentní [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Implementace poskytuje tuto třídu neprovede žádnou akci.
