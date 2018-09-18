---
title: Agent – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 33afc48ab06bc12937b36c4ee5ccb4ee0f170216
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047197"
---
# <a name="agent-class"></a>agent – třída
Třída určena pro použití jako základní třída pro všechny agenty nezávislé. Používá se k skrýt stav z další agenty a komunikovat pomocí předávání zpráv.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class agent;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Agent](#ctor)|Přetíženo. Sestaví agenta.|  
|[~ agent – destruktor](#dtor)|Zničí agenta.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Zrušit](#cancel)|Přesune agenta buď z `agent_created` nebo `agent_runnable` stavy `agent_canceled` stavu.|  
|[Spuštění](#start)|Přesune z agenta `agent_created` do stavu `agent_runnable` stavu a plány pro spuštění.|  
|[Stav](#status)|Synchronní zdroj informací o stavu z agenta.|  
|[status_port](#status_port)|Asynchronní zdroj informací o stavu z agenta.|  
|[Počkej](#wait)|Čeká se na agenta a dokončení úkolu.|  
|[wait_for_all](#wait_for_all)|Čeká na všechny zadané agentů k dokončení jejich úloh.|  
|[wait_for_one](#wait_for_one)|Počká, pro každý zadaný agentů a dokončení úkolu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Hotovo](#done)|Přesune do agenta `agent_done` Stav označující, že agent byla dokončena.|  
|[Spuštění](#run)|Představuje hlavního úkolu agenta. `run` by měla být potlačena v odvozené třídě a určuje, jak agenta postupovat po jeho spuštění.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronních agentů](../../../parallel/concrt/asynchronous-agents.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `agent`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> Agent 

 Sestaví agenta.  
  
```
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```  
  
### <a name="parameters"></a>Parametry  
*_PScheduler*<br/>
`Scheduler` Objekt v rámci úkolu spuštění agenta je naplánováno.  
  
*_PGroup*<br/>
`ScheduleGroup` Objekt v rámci úkolu spuštění agenta je naplánováno. `Scheduler` Skupina plánování předpokládá používaný objekt.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PGroup` parametry.  
  
##  <a name="dtor"></a> ~ agent 

 Zničí agenta.  
  
```
virtual ~agent();
```  
  
### <a name="remarks"></a>Poznámky  
 Jedná se o chybu ke zničení agenta, který není ve stavu terminálu (buď `agent_done` nebo `agent_canceled`). To se můžete vyhnout tím, že má agent dosáhne konečného stavu v destruktor třídy, která dědí z `agent` třídy.  
  
##  <a name="cancel"></a> Zrušit 

 Přesune agenta buď z `agent_created` nebo `agent_runnable` stavy `agent_canceled` stavu.  
  
```
bool cancel();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud agenta byla zrušena, `false` jinak. Agenta nelze zrušit, pokud byl již spuštěn nebo již byla dokončena.  
  
##  <a name="done"></a> Hotovo 

 Přesune do agenta `agent_done` Stav označující, že agent byla dokončena.  
  
```
bool done();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud se přesune do agenta `agent_done` stavu, `false` jinak. Agent, který byl zrušen nelze přesunout do `agent_done` stavu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda by měla být volána na konci `run` metodu, když víte, provádění vašeho agenta byla dokončena.  
  
##  <a name="run"></a> Spuštění 

 Představuje hlavního úkolu agenta. `run` by měla být potlačena v odvozené třídě a určuje, jak agenta postupovat po jeho spuštění.  
  
```
virtual void run() = 0;
```  
  
### <a name="remarks"></a>Poznámky  
 Stav agenta se změní na `agent_started` klikněte pravým tlačítkem myši před vyvoláním této metody. Metoda by měla vyvolat `done` pomocí příslušný stav před vrácením a nemusí generovat žádné výjimky.  
  
##  <a name="start"></a> Spuštění 

 Přesune z agenta `agent_created` do stavu `agent_runnable` stavu a plány pro spuštění.  
  
```
bool start();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud agent spuštěn správně, `false` jinak. Nelze spustit agenta, který byl zrušen.  
  
##  <a name="status"></a> Stav 

 Synchronní zdroj informací o stavu z agenta.  
  
```
agent_status status();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktuální stav agenta. Všimněte si, že tento stav vrácený změnit ihned po se vrací.  
  
##  <a name="status_port"></a> status_port – 

 Asynchronní zdroj informací o stavu z agenta.  
  
```
ISource<agent_status>* status_port();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí zprávu zdroj, který může odesílat zprávy o aktuálním stavu agenta.  
  
##  <a name="wait"></a> Počkej 

 Čeká se na agenta a dokončení úkolu.  
  
```
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
*_PAgent*<br/>
Ukazatel na agenta čekání.  
  
*_Vypršení časového limitu*<br/>
Maximální doba, která čekání v milisekundách.  
  
### <a name="return-value"></a>Návratová hodnota  
 `agent_status` Agenta po čekání dokončení. Může to být buď `agent_canceled` nebo `agent_done`.  
  
### <a name="remarks"></a>Poznámky  
 Úlohu agenta je dokončeno, když přejde do agenta `agent_canceled` nebo `agent_done` stavy.  
  
 Pokud parametr `_Timeout` má jinou hodnotu než konstanta `COOPERATIVE_TIMEOUT_INFINITE`, výjimka [operation_timed_out –](operation-timed-out-class.md) je vyvolána, pokud zadaného časového intervalu vyprší agenta dokončí úlohu.  
  
##  <a name="wait_for_all"></a> wait_for_all – 

 Čeká na všechny zadané agentů k dokončení jejich úloh.  
  
```
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
*Počet*<br/>
Počet ukazatelů agenta v poli `_PAgents`.  
  
*_PAgents*<br/>
Pole ukazatelů do agentů čekání.  
  
*_PStatus*<br/>
Ukazatel na pole stavů agenta. Každá hodnota stavu bude reprezentovat stav odpovídajícího agenta po návratu metody.  
  
*_Vypršení časového limitu*<br/>
Maximální doba, která čekání v milisekundách.  
  
### <a name="remarks"></a>Poznámky  
 Úlohu agenta je dokončeno, když přejde do agenta `agent_canceled` nebo `agent_done` stavy.  
  
 Pokud parametr `_Timeout` má jinou hodnotu než konstanta `COOPERATIVE_TIMEOUT_INFINITE`, výjimka [operation_timed_out –](operation-timed-out-class.md) je vyvolána, pokud zadaného časového intervalu vyprší agenta dokončí úlohu.  
  
##  <a name="wait_for_one"></a> wait_for_one – 

 Počká, pro každý zadaný agentů a dokončení úkolu.  
  
```
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
*Počet*<br/>
Počet ukazatelů agenta v poli `_PAgents`.  
  
*_PAgents*<br/>
Pole ukazatelů do agentů čekání.  
  
*_Status*<br/>
Odkaz na proměnnou, kde budou umístěné stav agenta.  
  
*_Index*<br/>
Odkaz na proměnnou umístění indexu agenta.  
  
*_Vypršení časového limitu*<br/>
Maximální doba, která čekání v milisekundách.  
  
### <a name="remarks"></a>Poznámky  
 Úlohu agenta je dokončeno, když přejde do agenta `agent_canceled` nebo `agent_done` stavy.  
  
 Pokud parametr `_Timeout` má jinou hodnotu než konstanta `COOPERATIVE_TIMEOUT_INFINITE`, výjimka [operation_timed_out –](operation-timed-out-class.md) je vyvolána, pokud zadaného časového intervalu vyprší agenta dokončí úlohu.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
