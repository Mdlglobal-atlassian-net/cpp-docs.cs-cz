---
title: "Třída CNonStatelessWorker | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
dev_langs: C++
helpviewer_keywords: CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 08b440a60b23182c3efff1c0236773ad2b98bf97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cnonstatelessworker-class"></a>CNonStatelessWorker – třída
Přijímá požadavky od fondu vláken a předává je na objekt pracovního procesu, který je vytvořen a zničen v každé žádosti.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Worker>  
class CNonStatelessWorker
```  
  
#### <a name="parameters"></a>Parametry  
 *Pracovního procesu*  
 Třídu pracovní vlákno, odpovídají [pracovní archetype](../../atl/reference/worker-archetype.md) vhodný pro zpracování požadavků ve frontě na [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CNonStatelessWorker::RequestType](#requesttype)|Implementace [WorkerArchetype::RequestType](worker-archetype.md#requesttype).|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CNonStatelessWorker::Execute](#execute)|Implementace [WorkerArchetype::Execute](worker-archetype.md#execute).|  
|[CNonStatelessWorker::Initialize](#initialize)|Implementace [WorkerArchetype::Initialize](worker-archetype.md#initialize).|  
|[CNonStatelessWorker::Terminate](#terminate)|Implementace [WorkerArchetype::Terminate](worker-archetype.md#terminate).|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída je jednoduchý pracovní vlákno pro použití s [CThreadPool](../../atl/reference/cthreadpool-class.md). Tato třída neposkytuje žádné možnosti zpracování požadavků své vlastní. Místo toho se vytvoří jedna instance *pracovní* každý požadavek a deleguje implementace její metody do této instance.  
  
 Výhodou Tato třída je, že nabízí pohodlný způsob, jak změnit stav modelu pro existující třídy pracovní vlákno. `CThreadPool`vytvoří jeden pracovní dobu jeho existence vlákno, takže pokud pracovní třída obsahuje stav, se bude obsahovat napříč více žádostí. Pomocí třídy v jednoduše zabalení `CNonStatelessWorker` šablony před jeho s použitím `CThreadPool`, doba platnosti pracovního procesu a stát, že obsahuje, je omezený na jednu žádost.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlutil.h  
  
##  <a name="execute"></a>CNonStatelessWorker::Execute  
 Implementace [WorkerArchetype::Execute](worker-archetype.md#execute).  

  
```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří instanci *pracovní* třídy v zásobníku a volání [inicializovat](worker-archetype.md#initialize) na tento objekt. Pokud se inicializace úspěšné, tato metoda také volá [Execute](worker-archetype.md#execute) a [ukončit](worker-archetype.md#terminate) na stejný objekt.  

  
##  <a name="initialize"></a>CNonStatelessWorker::Initialize  
 Implementace [WorkerArchetype::Initialize](worker-archetype.md#initialize).  
  
```
BOOL Initialize(void* /* pvParam */) throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Tato třída neprovádí žádné inicializace `Initialize`.  
  
##  <a name="requesttype"></a>CNonStatelessWorker::RequestType  
 Implementace [WorkerArchetype::RequestType](worker-archetype.md#requesttype).  
  
```
typedef Worker::RequestType RequestType;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato třída zpracovává jako třída používaná pro stejný typ pracovní položky *pracovní* parametr šablony. V tématu [CNonStatelessWorker přehled](../../atl/reference/cnonstatelessworker-class.md) podrobnosti.  
  
##  <a name="terminate"></a>CNonStatelessWorker::Terminate  
 Implementace [WorkerArchetype::Terminate](worker-archetype.md#terminate).  
  
```
void Terminate(void* /* pvParam */) throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato třída neprovádí žádné čištění `Terminate`.  
  
## <a name="see-also"></a>Viz také  
 [CThreadPool – třída](../../atl/reference/cthreadpool-class.md)   
 [Archetype pracovního procesu](../../atl/reference/worker-archetype.md)   
 [Třídy](../../atl/reference/atl-classes.md)
