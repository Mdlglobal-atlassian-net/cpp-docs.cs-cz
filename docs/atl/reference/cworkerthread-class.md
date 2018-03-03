---
title: "Třída CWorkerThread | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be7a000e48cb044a67f7eee120206f46ecaef2ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cworkerthread-class"></a>CWorkerThread – třída
Tato třída vytvoří pracovní vlákno nebo používá existující, čeká na jeden nebo více objektů obslužných rutin jádra a provede funkci zadaného klienta, když se jeden z obslužné rutiny pro zpracování signalizace.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class ThreadTraits = DefaultThreadTraits>  
class CWorkerThread
```  
  
#### <a name="parameters"></a>Parametry  
 `ThreadTraits`  
 Třída poskytuje funkce vytváření vláken, například [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) nebo [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).  
  
## <a name="members"></a>Členové  
  
### <a name="protected-structures"></a>Chráněné struktury  
  
|Název|Popis|  
|----------|-----------------|  
|`WorkerClientEntry`||  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CWorkerThread::CWorkerThread](#cworkerthread)|V konstruktoru pro pracovní vlákno.|  
|[CWorkerThread:: ~ CWorkerThread](#dtor)|Destruktor pro pracovní vlákno.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWorkerThread::AddHandle](#addhandle)|Voláním této metody lze přidat do seznamu udržované pracovní vlákno waitable objekt popisovače.|  
|[CWorkerThread::AddTimer](#addtimer)|Voláním této metody lze přidat do seznamu udržované pracovní vlákno pravidelné waitable časovač.|  
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Voláním této metody lze získat přístup z více vláken popisovač pracovní vlákno.|  
|[CWorkerThread::GetThreadId](#getthreadid)|Voláním této metody lze získat přístup z více vláken ID pracovní vlákno.|  
|[CWorkerThread::Initialize](#initialize)|Volejte tuto metodu za účelem inicializace pracovního vlákna.|  
|[CWorkerThread::RemoveHandle](#removehandle)|Volejte tuto metodu za účelem odebrání popisovač seznamu waitable objektů.|  
|[CWorkerThread::Shutdown](#shutdown)|Voláním této metody lze vypnout pracovní vlákno.|  
  
## <a name="remarks"></a>Poznámky  
  
### <a name="to-use-cworkerthread"></a>Chcete-li použít CWorkerThread  
  
1.  Vytvoření instance této třídy.  
  
2.  Volání [CWorkerThread::Initialize](#initialize).  
  
3.  Volání [CWorkerThread::AddHandle](#addhandle) s popisovačem objekt jádra a ukazatel na implementaci pro [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
     - nebo –  
  
     Volání [CWorkerThread::AddTimer](#addtimer) s ukazatel na implementaci pro [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
4.  Implementace [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) určitou akci při signalizace popisovač nebo časovače.  
  
5.  Chcete-li odebrat objekt ze seznamu waitable objektů, volejte [CWorkerThread::RemoveHandle](#removehandle).  
  
6.  Chcete-li ukončit vlákno, volejte [CWorkerThread::Shutdown](#shutdown).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlutil.h  
  
##  <a name="addhandle"></a>CWorkerThread::AddHandle  
 Voláním této metody lze přidat do seznamu udržované pracovní vlákno waitable objekt popisovače.  
  
```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Popisovač waitable objektu.  
  
 `pClient`  
 Ukazatele myši [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) rozhraní na objekt, který má být volána, když signalizace popisovač.  
  
 `dwParam`  
 Parametr mají být předány [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) při signalizace popisovač.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) bude volána prostřednictvím `pClient` při popisovač, `hObject`, signalizace.  
  
##  <a name="addtimer"></a>CWorkerThread::AddTimer  
 Voláním této metody lze přidat do seznamu udržované pracovní vlákno pravidelné waitable časovač.  
  
```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dwInterval*  
 Určuje dobu časovač v milisekundách.  
  
 `pClient`  
 Ukazatele myši [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) rozhraní na objekt, který má být volána, když signalizace popisovač.  
  
 `dwParam`  
 Parametr mají být předány [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) při signalizace popisovač.  
  
 `phTimer`  
 [out] Adresa proměnné obslužná RUTINA, která v případě úspěchu obdrží popisovač pro nově vytvořený časovač.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) bude volána prostřednictvím `pClient` při signalizace časovač.  
  
 Předat časovače popisovač z `phTimer` k [CWorkerThread::RemoveHandle](#removehandle) zavřete časovač.  
  
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
 Volání [CWorkerThread::Shutdown](#shutdown).  
  
##  <a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle  
 Voláním této metody lze získat přístup z více vláken popisovač pracovní vlákno.  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač podprocesu nebo hodnota NULL, pokud pracovní vlákno nebyla inicializována.  
  
##  <a name="getthreadid"></a>CWorkerThread::GetThreadId  
 Voláním této metody lze získat přístup z více vláken ID pracovní vlákno.  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ID vlákna nebo hodnota NULL, pokud pracovní vlákno nebyla inicializována.  
  
##  <a name="initialize"></a>CWorkerThread::Initialize  
 Volejte tuto metodu za účelem inicializace pracovního vlákna.  
  
```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pThread`  
 Existující pracovní vlákno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda by měla být volána k inicializaci objektu po vytvoření nebo po volání [CWorkerThread::Shutdown](#shutdown).  
  
 Dva nebo více `CWorkerThread` objekty použít stejný pracovní vlákno, jeden z nich bez předávání všechny argumenty pak předejte ukazatel na tento objekt k inicializaci `Initialize` jiné metody. Objekty inicializována pomocí ukazatele by měl být vypnutý předtím, než objekt použitý k inicializaci je.  
  
 V tématu [CWorkerThread::Shutdown](#shutdown) informace o jak dané metody chování změní, když inicializována pomocí ukazatele na existující objekt.  
  
##  <a name="removehandle"></a>CWorkerThread::RemoveHandle  
 Volejte tuto metodu za účelem odebrání popisovač seznamu waitable objektů.  
  
```
HRESULT RemoveHandle(HANDLE hObject) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Popisovač odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Po odebrání popisovač [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) bude volána při přidruženého objektu, který byl předán [AddHandle](#addhandle). Pokud toto volání selže, `CWorkerThread` bude volat Windows [funkce CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211) funkce na popisovač.  
  
##  <a name="shutdown"></a>CWorkerThread::Shutdown  
 Voláním této metody lze vypnout pracovní vlákno.  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwWait`  
 Doba v milisekundách pro čekání pracovního vlákna vypnout. Výchozí hodnota ATL_WORKER_THREAD_WAIT je 10 sekund. V případě potřeby můžete definovat vlastní hodnotu pro tento symbol před zahrnutím atlutil.h. 
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK na úspěch nebo Chyba HRESULT při selhání, jako třeba když hodnota časového limitu `dwWait`, byl překročen.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li znovu použít objekt, volejte [CWorkerThread::Initialize](#initialize) po voláním této metody.  
  
 Všimněte si, že volání **vypnutí** objektu inicializovat pomocí ukazatele na jiný `CWorkerThread` objekt nemá žádný vliv a vždy vrátí hodnotu S_OK.  
  
## <a name="see-also"></a>Viz také  
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [Třídy](../../atl/reference/atl-classes.md)   
 [Multithreading: Vytváření pracovních vláken](../../parallel/multithreading-creating-worker-threads.md)   
 [IWorkerThreadClient – rozhraní](../../atl/reference/iworkerthreadclient-interface.md)
