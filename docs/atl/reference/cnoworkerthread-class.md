---
title: Cnoworkerthread – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 16eafd8c33bf1c9a42b95c31a333ff1df55b3495
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962501"
---
# <a name="cnoworkerthread-class"></a>Cnoworkerthread – třída
Použijte tuto třídu jako argument pro `MonitorClass` parametr šablony třídy mezipaměti, pokud chcete zakázat dynamické mezipaměti údržby.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CNoWorkerThread
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CNoWorkerThread::AddHandle](#addhandle)|Nefunkční ekvivalent [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|  
|[CNoWorkerThread::AddTimer](#addtimer)|Nefunkční ekvivalent [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|  
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Nefunkční ekvivalent [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|  
|[CNoWorkerThread::GetThreadId](#getthreadid)|Nefunkční ekvivalent [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|  
|[CNoWorkerThread::Initialize](#initialize)|Nefunkční ekvivalent [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|  
|[CNoWorkerThread::RemoveHandle](#removehandle)|Nefunkční ekvivalent [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|  
|[CNoWorkerThread::Shutdown](#shutdown)|Nefunkční ekvivalent [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje stejné veřejné rozhraní jako [cworkerthread –](../../atl/reference/cworkerthread-class.md). Očekává se toto rozhraní je poskytovat `MonitorClass` parametr šablony tříd mezipaměti.  
  
 Metody této třídy jsou implementovány neprovede žádnou akci. Metody, které vracejí HRESULT vždy vrátí hodnotu S_OK a metody, které vrátí ID POPISOVAČ nebo vlákno vždy vrátí 0.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlutil.h  
  
##  <a name="addhandle"></a>  CNoWorkerThread::AddHandle  
 Nefunkční ekvivalent [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
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
 Provádění, poskytuje tato třída nemá žádný účinek.  
  
##  <a name="addtimer"></a>  CNoWorkerThread::AddTimer  
 Nefunkční ekvivalent [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).  
  
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
 Provádění, poskytuje tato třída nemá žádný účinek.  
  
##  <a name="getthreadhandle"></a>  CNoWorkerThread::GetThreadHandle  
 Nefunkční ekvivalent [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu NULL.  
  
### <a name="remarks"></a>Poznámky  
 Provádění, poskytuje tato třída nemá žádný účinek.  
  
##  <a name="getthreadid"></a>  CNoWorkerThread::GetThreadId  
 Nefunkční ekvivalent [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Provádění, poskytuje tato třída nemá žádný účinek.  
  
##  <a name="initialize"></a>  CNoWorkerThread::Initialize  
 Nefunkční ekvivalent [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).  
  
```
HRESULT Initialize() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Provádění, poskytuje tato třída nemá žádný účinek.  
  
##  <a name="removehandle"></a>  CNoWorkerThread::RemoveHandle  
 Nefunkční ekvivalent [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).  
  
```
HRESULT RemoveHandle(HANDLE /* hObject
 */) throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Provádění, poskytuje tato třída nemá žádný účinek.  
  
##  <a name="shutdown"></a>  CNoWorkerThread::Shutdown  
 Nefunkční ekvivalent [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Provádění, poskytuje tato třída nemá žádný účinek.
