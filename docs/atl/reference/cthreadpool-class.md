---
title: "Třída CThreadPool | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6739e179843864c952a5e864de1389b466d7ca7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cthreadpool-class"></a>CThreadPool – třída
Tato třída poskytuje fond pracovních vláken, které zpracovávají fronty pracovních položek.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Worker, class ThreadTraits = DefaultThreadTraits>  
class CThreadPool : public IThreadPoolConfig
```  
  
#### <a name="parameters"></a>Parametry  
 *Pracovního procesu*  
 Třídy, který odpovídá [archetype pracovní](../../atl/reference/worker-archetype.md) poskytuje kód používá ke zpracování pracovní položky ve frontě na fond vláken.  
  
 `ThreadTraits`  
 Třída poskytuje funkce použitá k vytvoření vláken ve fondu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CThreadPool::CThreadPool](#cthreadpool)|V konstruktoru pro fond vláken.|  
|[CThreadPool:: ~ CThreadPool](#dtor)|Destruktor pro fond vláken.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CThreadPool::AddRef](#addref)|Implementace `IUnknown::AddRef`.|  
|[CThreadPool::GetNumThreads](#getnumthreads)|Volejte tuto metodu za účelem získání počet vláken ve fondu.|  
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Voláním této metody lze získat popisovač port dokončení vstupně-výstupní operace používaný do fronty pracovní položky.|  
|[CThreadPool::GetSize](#getsize)|Volejte tuto metodu za účelem získání počet vláken ve fondu.|  
|[CThreadPool::GetTimeout](#gettimeout)|Volejte tuto metodu za účelem získání maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se.|  
|[CThreadPool::Initialize](#initialize)|Volejte tuto metodu za účelem inicializace fondu vláken.|  
|[CThreadPool::QueryInterface](#queryinterface)|Implementace **IUnknown::QueryInterface**.|  
|[CThreadPool::QueueRequest](#queuerequest)|Volejte tuto metodu do fronty pracovní položku zpracovávat vláken ve fondu.|  
|[CThreadPool::Release](#release)|Implementace `IUnknown::Release`.|  
|[CThreadPool::SetSize](#setsize)|Volejte tuto metodu a nastavit počet vláken ve fondu.|  
|[CThreadPool::SetTimeout](#settimeout)|Volejte tuto metodu a nastavit maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se.|  
|[CThreadPool::Shutdown](#shutdown)|Voláním této metody lze vypnout fondu vláken.|  
  
## <a name="remarks"></a>Poznámky  
 Vláken ve fondu jsou vytvořen a zničen při fondu je inicializován, po změně velikosti nebo vypnutí. Instance třídy *pracovní* se vytvoří v zásobníku každý pracovní vlákno ve fondu. Každá instance bude za provozu, po dobu jeho existence vlákno.  
  
 Okamžitě po vytvoření vlákna *pracovní*:: `Initialize` bude volána při objekt přidružený k této přístup z více vláken. Bezprostředně před odstraňování vlákno *pracovní*:: `Terminate` bude volána. Obě metody musí přijmout **void\***  argument. Hodnota argumentu je předaná do fondu vláken prostřednictvím `pvWorkerParam` parametr [CThreadPool::Initialize](#initialize).  
  
 Kdy pracovních položek ve frontě a pracovní vlákna k dispozici pro práci, pracovní vlákno načte položku vypnout fronty a volání **Execute** metodu *pracovní* objekt pro tento přístup z více vláken. Tři položky jsou potom předána metodě: položky z fronty stejné `pvWorkerParam` předaný *pracovní*:: `Initialize` a *pracovní*:: `Terminate`a odkazy [OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) struktura používaná pro frontu port dokončení vstupně-výstupní operace.  
  
 *Pracovní* třída deklaruje typ položky, které se zařadí do fronty ve fondu vláken tím, že poskytuje typedef, *pracovní*:: `RequestType`. Tento typ musí být schopný se přetypovat do a z **ULONG_PTR**.  
  
 Příklad *pracovní* třída je [CNonStatelessWorker třída](../../atl/reference/cnonstatelessworker-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IUnknown`  
  
 [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)  
  
 `CThreadPool`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlutil.h  
  
##  <a name="addref"></a>CThreadPool::AddRef  
 Implementace `IUnknown::AddRef`.  
  
```
ULONG STDMETHODCALLTYPE AddRef() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 1.  
  
### <a name="remarks"></a>Poznámky  
 Tato třída neimplementuje životnost ovládacího prvku s použitím počítání odkazů.  
  
##  <a name="cthreadpool"></a>CThreadPool::CThreadPool  
 V konstruktoru pro fond vláken.  
  
```
CThreadPool() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje hodnota časového limitu pro `ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT`. Výchozí doba je 36 sekund. V případě potřeby můžete definovat vlastní kladnou celočíselnou hodnotu pro tento symbol před zahrnutím atlutil.h.  
  
##  <a name="dtor"></a>CThreadPool:: ~ CThreadPool  
 Destruktor pro fond vláken.  
  
```
~CThreadPool() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání [CThreadPool::Shutdown](#shutdown).  
  
##  <a name="getnumthreads"></a>CThreadPool::GetNumThreads  
 Volejte tuto metodu za účelem získání počet vláken ve fondu.  
  
```
int GetNumThreads() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet vláken ve fondu.  
  
##  <a name="getqueuehandle"></a>CThreadPool::GetQueueHandle  
 Voláním této metody lze získat popisovač port dokončení vstupně-výstupní operace používaný do fronty pracovní položky.  
  
```
HANDLE GetQueueHandle() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač fronty nebo hodnota NULL, pokud fond vláken nebyla inicializována.  
  
##  <a name="getsize"></a>CThreadPool::GetSize  
 Volejte tuto metodu za účelem získání počet vláken ve fondu.  
  
```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pnNumThreads`  
 [out] Adresa proměnné, která v případě úspěchu obdrží počet vláken ve fondu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="gettimeout"></a>CThreadPool::GetTimeout  
 Volejte tuto metodu za účelem získání maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se.  
  
```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pdwMaxWait`  
 [out] Adresa proměnné, která v případě úspěchu obdrží maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota časového limitu je používán [CThreadPool::Shutdown](#shutdown) Pokud jiná hodnota zadaný do této metody.  
  
##  <a name="initialize"></a>CThreadPool::Initialize  
 Volejte tuto metodu za účelem inicializace fondu vláken.  
  
```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pvWorkerParam`  
 Parametr pracovního procesu mají být předány objekt pracovní vlákno `Initialize`, **Execute**, a `Terminate` metody.  
  
 `nNumThreads`  
 Požadovaný počet vláken ve fondu.  
  
 Pokud `nNumThreads` je záporná, jeho absolutní hodnota vynásobeny počet procesorů v počítači získat celkový počet vláken.  
  
 Pokud `nNumThreads` rovná nule, `ATLS_DEFAULT_THREADSPERPROC` vynásobeny počet procesorů v počítači získat celkový počet vláken.  Výchozí hodnota je 2 vláken na procesor. V případě potřeby můžete definovat vlastní kladnou celočíselnou hodnotu pro tento symbol před zahrnutím atlutil.h.
  
 `dwStackSize`  
 Velikost zásobníku pro každé vlákno ve fondu.  
  
 *hCompletion*  
 Popisovač objektu přidružit portu dokončení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="queryinterface"></a>CThreadPool::QueryInterface  
 Implementace **IUnknown::QueryInterface**.  
  
```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Objekty této třídy může úspěšně dotázána ohledně **IUnknown** a [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) rozhraní.  
  
##  <a name="queuerequest"></a>CThreadPool::QueueRequest  
 Volejte tuto metodu do fronty pracovní položku zpracovávat vláken ve fondu.  
  
```
BOOL QueueRequest(Worker::RequestType request) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `request`  
 Požadavek ve frontě.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidá do fronty pracovní položku. Vláken ve fondu vyberte položky vypnout fronty v pořadí, ve kterém jsou přijaty.  
  
##  <a name="release"></a>CThreadPool::Release  
 Implementace `IUnknown::Release`.  
  
```
ULONG STDMETHODCALLTYPE Release() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 1.  
  
### <a name="remarks"></a>Poznámky  
 Tato třída neimplementuje životnost ovládacího prvku s použitím počítání odkazů.  
  
##  <a name="setsize"></a>CThreadPool::SetSize  
 Volejte tuto metodu a nastavit počet vláken ve fondu.  
  
```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nNumThreads`  
 Požadovaný počet vláken ve fondu.  
  
 Pokud `nNumThreads` je záporná, jeho absolutní hodnota vynásobeny počet procesorů v počítači získat celkový počet vláken.  
  
 Pokud `nNumThreads` rovná nule, `ATLS_DEFAULT_THREADSPERPROC` vynásobeny počet procesorů v počítači získat celkový počet vláken. Výchozí hodnota je 2 vláken na procesor. V případě potřeby můžete definovat vlastní kladnou celočíselnou hodnotu pro tento symbol před zahrnutím atlutil.h.
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud počet vláken, zadaný je menší než počet vláken aktuálně ve fondu, objekt zprávu vypnutí zařadí do fronty, být zachyceny čekání na vlákno. Při čekání na vlákno přebírá zprávu vypnout fronty, upozorní fondu vláken a ukončí proceduru přístup z více vláken. Tento postup se opakuje, dokud nedosáhne zadané číslo počet vláken ve fondu, nebo dokud žádný přístup z více vláken byl ukončen během období zadaného pomocí [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). V této situaci metoda vrátí HRESULT odpovídající **WAIT_TIMEOUT** a zrušení zpráva čeká na vypnutí.  
  
##  <a name="settimeout"></a>CThreadPool::SetTimeout  
 Volejte tuto metodu a nastavit maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se.  
  
```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwMaxWait`  
 Požadovaný maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Časový limit je inicializováno `ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT`. Výchozí doba je 36 sekund. V případě potřeby můžete definovat vlastní kladnou celočíselnou hodnotu pro tento symbol před zahrnutím atlutil.h. 
  
 Všimněte si, že `dwMaxWait` je čas, který fondu budou čekat na jedno vlákno k vypnutí. Maximální dobu, po který může být provedena, aby více vláken odebrat z fondu může být mírně nižší než `dwMaxWait` násobí hodnotou počet vláken.  
  
##  <a name="shutdown"></a>CThreadPool::Shutdown  
 Voláním této metody lze vypnout fondu vláken.  
  
```
void Shutdown(DWORD dwMaxWait = 0) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwMaxWait`  
 Požadovaný maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se. Pokud je zadaný 0 nebo žádnou hodnotu, tato metoda použije vypršení časového limitu, která nastavuje [CThreadPool::SetTimeout](#settimeout).  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odešle žádost o vypnutí pro všechna vlákna ve fondu. Pokud vyprší časový limit, bude volat tuto metodu [TerminateThread](http://msdn.microsoft.com/library/windows/desktop/ms686717) na jakékoli vlákno, které se neukončil. Tato metoda je volána automaticky z destruktor třídy.  
  
## <a name="see-also"></a>Viz také  
 [IThreadPoolConfig rozhraní](../../atl/reference/ithreadpoolconfig-interface.md)   
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [Třídy](../../atl/reference/atl-classes.md)
