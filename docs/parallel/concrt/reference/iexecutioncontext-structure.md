---
title: Iexecutioncontext – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
dev_langs:
- C++
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c194dc7ecd4af0092dd304b17a8230cda6a8598
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext – struktura
Rozhraní na kontext spuštění, který můžete spustit na danou virtuálních procesorů a být spolupráce při přepnout kontext.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IExecutionContext;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Iexecutioncontext::Dispatch –](#dispatch)|Metoda, která je volána, když proxy vlákna spustí provádění kontextu konkrétní spuštění. To by měl být hlavní pracovní rutiny pro vašeho scheduleru.|  
|[IExecutionContext::GetId](#getid)|Vrací jedinečný identifikátor pro kontext spuštění.|  
|[IExecutionContext::GetProxy](#getproxy)|Vrátí rozhraní proxy přístup z více vláken, která provádí tohoto kontextu.|  
|[IExecutionContext::GetScheduler](#getscheduler)|Vrátí rozhraní pro Plánovač patří tento kontext spuštění.|  
|[IExecutionContext::SetProxy](#setproxy)|Přidruží tento kontext spuštění proxy přístup z více vláken. Proxy přidružené vlákno vyvolá tato metoda práva před spuštěním provádění podle kontextu `Dispatch` metoda.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud implementujete vlastní plánovače, který rozhraní s Concurrency Runtime Resource Manager, je nutné implementovat `IExecutionContext` rozhraní. Vlákna vytvořili pomocí Správce prostředků práci jménem vašeho scheduleru spuštěním `IExecutionContext::Dispatch` metoda.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IExecutionContext`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dispatch"></a>  Iexecutioncontext::Dispatch – metoda  
 Metoda, která je volána, když proxy vlákna spustí provádění kontextu konkrétní spuštění. To by měl být hlavní pracovní rutiny pro vašeho scheduleru.  
  
```
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pDispatchState`  
 Ukazatel na stav, pod kterým je odesílán tento kontext spuštění. Další informace o stavu odesílání najdete v tématu [dispatchstate –](dispatchstate-structure.md).  
  
##  <a name="getid"></a>  Iexecutioncontext::getid – metoda  
 Vrací jedinečný identifikátor pro kontext spuštění.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo jedinečný identifikátor.  
  
### <a name="remarks"></a>Poznámky  
 Používáte metodu `GetExecutionContextId` získat jedinečný identifikátor pro objekt, který implementuje `IExecutionContext` rozhraní, před použitím rozhraní jako parametr pro metody zadaný správcem prostředků. Předpokládá se, že se vrátíte stejný identifikátor při `GetId` je volána funkce.  
  
 Identifikátor získat z jiného zdroje může vést k nedefinované chování.  
  
##  <a name="getproxy"></a>  Iexecutioncontext::getproxy – metoda  
 Vrátí rozhraní proxy přístup z více vláken, která provádí tohoto kontextu.  
  
```
virtual IThreadProxy* GetProxy() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `IThreadProxy` Rozhraní. Pokud kontext provádění vlákna proxy nebyla inicializována pomocí volání `SetProxy`, musí vracet funkce `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Správce prostředků bude vyvolán `SetProxy` metoda v kontextu spuštění s `IThreadProxy` rozhraní jako parametr, před zadáním `Dispatch` metodu pro daný kontext. Předpokládá se, že tento argument úložiště a vrátit se na volání `GetProxy()`.  
  
##  <a name="getscheduler"></a>  Iexecutioncontext::getscheduler – metoda  
 Vrátí rozhraní pro Plánovač patří tento kontext spuštění.  
  
```
virtual IScheduler* GetScheduler() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `IScheduler` Rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Je nutné inicializovat kontext provádění platný `IScheduler` rozhraní dříve, než ho použijete jako parametr pro metody zadaný správcem prostředků.  
  
##  <a name="setproxy"></a>  Iexecutioncontext::setproxy – metoda  
 Přidruží tento kontext spuštění proxy přístup z více vláken. Proxy přidružené vlákno vyvolá tato metoda práva před spuštěním provádění podle kontextu `Dispatch` metoda.  
  
```
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pThreadProxy`  
 Rozhraní pro přístup z více vláken proxy serverem, který se chystáte zadat `Dispatch` metoda v tomto kontextu spuštění.  
  
### <a name="remarks"></a>Poznámky  
 Předpokládá se, že uložit parametr `pThreadProxy` a vraťte se na volání `GetProxy` metoda. Správce prostředků zaručuje, že proxy vlákno spojený s kontextem provádění nedojde ke změně při proxy vlákno je prováděna `Dispatch` metoda.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Struktura rozhraní IScheduler](ischeduler-structure.md)   
 [IThreadProxy – struktura](ithreadproxy-structure.md)
