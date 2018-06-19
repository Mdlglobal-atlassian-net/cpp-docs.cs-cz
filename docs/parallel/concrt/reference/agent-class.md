---
title: Agent – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- agent
- AGENTS/concurrency::agent
- AGENTS/concurrency::agent::agent
- AGENTS/concurrency::agent::cancel
- AGENTS/concurrency::agent::start
- AGENTS/concurrency::agent::status
- AGENTS/concurrency::agent::status_port
- AGENTS/concurrency::agent::wait
- AGENTS/concurrency::agent::wait_for_all
- AGENTS/concurrency::agent::wait_for_one
- AGENTS/concurrency::agent::done
- AGENTS/concurrency::agent::run
dev_langs:
- C++
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fbc8542af8073b2cb95517ea39d89258afac633c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694154"
---
# <a name="agent-class"></a>agent – třída
Třída určena pro použití jako základní třída pro všechny agenty nezávislé. Umožňuje skrýt stavu z jiné agenty a komunikovat pomocí přenosu zpráv.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class agent;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Agent](#ctor)|Přetíženo. Vytvoří agenta.|  
|[~ agent – destruktor](#dtor)|Zničí agenta.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Zrušit](#cancel)|Přesune agenta z buď `agent_created` nebo `agent_runnable` stavy do `agent_canceled` stavu.|  
|[Spuštění](#start)|Přesune agenta z `agent_created` stavu na `agent_runnable` stavu a plány pro spuštění.|  
|[Stav](#status)|Synchronní zdroj informace o stavu z agenta.|  
|[status_port](#status_port)|Asynchronní zdroj informací o stavu z agenta.|  
|[Počkej](#wait)|Čeká na agenta a dokončení úkolu.|  
|[wait_for_all](#wait_for_all)|Čeká na všechny zadané agentů k dokončení úkolů.|  
|[wait_for_one](#wait_for_one)|Čeká se pro každý zadaný agentů a dokončení úkolu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Provést](#done)|Přesune do agenta `agent_done` stavu, která určuje, zda agent byla dokončena.|  
|[Spustit](#run)|Představuje hlavní úlohy agenta. `run` by měla být potlačena v odvozené třídě a určuje, co má provést agenta po jeho spuštění.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronních agentů](../../../parallel/concrt/asynchronous-agents.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `agent`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> Agent 

 Vytvoří agenta.  
  
```
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `_PScheduler`  
 `Scheduler` Objektů v rámci kterého je naplánováno spuštění úlohy agenta.  
  
 `_PGroup`  
 `ScheduleGroup` Objektů v rámci kterého je naplánováno spuštění úlohy agenta. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PGroup` parametry.  
  
##  <a name="dtor"></a> ~ agenta 

 Zničí agenta.  
  
```
virtual ~agent();
```  
  
### <a name="remarks"></a>Poznámky  
 Jedná se o chybu při zavírání agenta, který není ve stavu terminálu (buď `agent_done` nebo `agent_canceled`). Tím se vyhnout tím, že pro agenta dosáhne stavu terminálu v destruktoru třídy, která dědí z `agent` třídy.  
  
##  <a name="cancel"></a> Zrušit 

 Přesune agenta z buď `agent_created` nebo `agent_runnable` stavy do `agent_canceled` stavu.  
  
```
bool cancel();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud agenta byla zrušena, `false` jinak. Agenta nelze zrušit, pokud byl již spuštěn nebo je již dokončena.  
  
##  <a name="done"></a> Provést 

 Přesune do agenta `agent_done` stavu, která určuje, zda agent byla dokončena.  
  
```
bool done();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud se přesune do agenta `agent_done` stavu, `false` jinak. Agenta, který byl zrušen nelze přesunout do `agent_done` stavu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda by měla být volána na konci `run` metodu, když víte, provádění agenta byla dokončena.  
  
##  <a name="run"></a> Spustit 

 Představuje hlavní úlohy agenta. `run` by měla být potlačena v odvozené třídě a určuje, co má provést agenta po jeho spuštění.  
  
```
virtual void run() = 0;
```  
  
### <a name="remarks"></a>Poznámky  
 Stav agenta se změní na `agent_started` před tato metoda je volána. Metoda by měla vyvolat `done` v agentovi odpovídající stavem před vrácením a nemusí výjimku jakékoli výjimky.  
  
##  <a name="start"></a> Spuštění 

 Přesune agenta z `agent_created` stavu na `agent_runnable` stavu a plány pro spuštění.  
  
```
bool start();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud agent spuštěn správně, `false` jinak. Nelze spustit, agenta, který byl zrušen.  
  
##  <a name="status"></a> Stav 

 Synchronní zdroj informace o stavu z agenta.  
  
```
agent_status status();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktuální stav agenta. Všimněte si, že tento stav vrácený změnit ihned po nebyl vrácen.  
  
##  <a name="status_port"></a> status_port – 

 Asynchronní zdroj informací o stavu z agenta.  
  
```
ISource<agent_status>* status_port();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí zdroj zprávy, který může odesílat zprávy o aktuální stav agenta.  
  
##  <a name="wait"></a> Počkej 

 Čeká na agenta a dokončení úkolu.  
  
```
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 `_PAgent`  
 Ukazatel na agenta pro čekání.  
  
 `_Timeout`  
 Maximální doba, pro které chcete počkat, v milisekundách.  
  
### <a name="return-value"></a>Návratová hodnota  
 `agent_status` Agenta při čekání dokončení. To může být buď `agent_canceled` nebo `agent_done`.  
  
### <a name="remarks"></a>Poznámky  
 Když agent zadá dokončení rámci úlohy agenta `agent_canceled` nebo `agent_done` stavy.  
  
 Pokud parametr `_Timeout` má jinou hodnotu než konstanta `COOPERATIVE_TIMEOUT_INFINITE`, výjimka [operation_timed_out](operation-timed-out-class.md) je vyvolána výjimka, jestliže zadaného časového intervalu vyprší agenta dokončí úlohu.  
  
##  <a name="wait_for_all"></a> wait_for_all – 

 Čeká na všechny zadané agentů k dokončení úkolů.  
  
```
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Počet agenta ukazatele v poli `_PAgents`.  
  
 `_PAgents`  
 Pole ukazatele agentů pro čekání.  
  
 `_PStatus`  
 Ukazatel na pole stavy agenta. Každá hodnota stavu bude reprezentovat stav odpovídající agenta, když metoda vrátí.  
  
 `_Timeout`  
 Maximální doba, pro které chcete počkat, v milisekundách.  
  
### <a name="remarks"></a>Poznámky  
 Když agent zadá dokončení rámci úlohy agenta `agent_canceled` nebo `agent_done` stavy.  
  
 Pokud parametr `_Timeout` má jinou hodnotu než konstanta `COOPERATIVE_TIMEOUT_INFINITE`, výjimka [operation_timed_out](operation-timed-out-class.md) je vyvolána výjimka, jestliže zadaného časového intervalu vyprší agenta dokončí úlohu.  
  
##  <a name="wait_for_one"></a> wait_for_one – 

 Čeká se pro každý zadaný agentů a dokončení úkolu.  
  
```
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Počet agenta ukazatele v poli `_PAgents`.  
  
 `_PAgents`  
 Pole ukazatele agentů pro čekání.  
  
 `_Status`  
 Odkaz na proměnnou, kde budou umístěné stav agenta.  
  
 `_Index`  
 Odkaz na proměnnou, kde budou umístěné index agenta.  
  
 `_Timeout`  
 Maximální doba, pro které chcete počkat, v milisekundách.  
  
### <a name="remarks"></a>Poznámky  
 Když agent zadá dokončení rámci úlohy agenta `agent_canceled` nebo `agent_done` stavy.  
  
 Pokud parametr `_Timeout` má jinou hodnotu než konstanta `COOPERATIVE_TIMEOUT_INFINITE`, výjimka [operation_timed_out](operation-timed-out-class.md) je vyvolána výjimka, jestliže zadaného časového intervalu vyprší agenta dokončí úlohu.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
