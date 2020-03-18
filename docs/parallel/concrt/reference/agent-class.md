---
title: agent – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
ms.openlocfilehash: f0092f5f90bbdf253c09dbdc80849c3db472212f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422260"
---
# <a name="agent-class"></a>agent – třída

Třída určená pro použití jako základní třída pro všechny nezávislé agenty. Slouží ke skrytí stavu od jiných agentů a k interakci s použitím předávání zpráv.

## <a name="syntax"></a>Syntaxe

```cpp
class agent;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[agenta](#ctor)|Přetíženo. Sestaví agenta.|
|[~ Destruktor agenta](#dtor)|Zničí agenta.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[operaci](#cancel)|Přesune agenta z `agent_created` nebo `agent_runnable` stavy do `agent_canceled` stavu.|
|[start](#start)|Přesune agenta ze stavu `agent_created` do stavu `agent_runnable` a naplánuje jeho spuštění.|
|[stav](#status)|Synchronní zdroj informací o stavu od agenta.|
|[status_port](#status_port)|Asynchronní zdroj informací o stavu od agenta.|
|[Počkej](#wait)|Čeká, až agent dokončí úlohu.|
|[wait_for_all](#wait_for_all)|Počká, až všichni určení agenti dokončí své úkoly.|
|[wait_for_one](#wait_for_one)|Počká, až jeden ze zadaných agentů dokončí jeho úlohu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[Hotovo](#done)|Přesune agenta do stavu `agent_done`, což znamená, že byl agent dokončen.|
|[spouštěl](#run)|Představuje hlavní úlohu agenta. `run` by měla být přepsána v odvozené třídě a určuje, co má agent provést po jeho spuštění.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [Asynchronní agenti](../../../parallel/concrt/asynchronous-agents.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`agent`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>agenta

Sestaví agenta.

```cpp
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Objekt `Scheduler`, ve kterém je naplánována úloha spuštění agenta.

*_PGroup*<br/>
Objekt `ScheduleGroup`, ve kterém je naplánována úloha spuštění agenta. Použitý objekt `Scheduler` je odvozen skupinou plánu.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí Plánovač, pokud nezadáte parametry `_PScheduler` nebo `_PGroup`.

## <a name="dtor"></a>~ Agent

Zničí agenta.

```cpp
virtual ~agent();
```

### <a name="remarks"></a>Poznámky

Zničení agenta, který není ve stavu terminálu (`agent_done` nebo `agent_canceled`), je chybou. K tomu je možné se vyhnout čekáním, až agent dorazí na stav terminálu v destruktoru třídy, která dědí z třídy `agent`.

## <a name="cancel"></a>operaci

Přesune agenta z `agent_created` nebo `agent_runnable` stavy do `agent_canceled` stavu.

```cpp
bool cancel();
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byl agent zrušen, jinak **false** . Agenta nelze zrušit, pokud již bylo spuštěno nebo již bylo dokončeno.

## <a name="done"></a>Hotovo

Přesune agenta do stavu `agent_done`, což znamená, že byl agent dokončen.

```cpp
bool done();
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se agent přesune do stavu `agent_done`, jinak **false** . Agenta, který byl zrušen, nelze přesunout do stavu `agent_done`.

### <a name="remarks"></a>Poznámky

Tato metoda by měla být volána na konci `run` metody, pokud víte, že bylo dokončeno spuštění agenta.

## <a name="run"></a>spouštěl

Představuje hlavní úlohu agenta. `run` by měla být přepsána v odvozené třídě a určuje, co má agent provést po jeho spuštění.

```cpp
virtual void run() = 0;
```

### <a name="remarks"></a>Poznámky

Stav agenta se změní na `agent_started` hned před vyvoláním této metody. Metoda by měla vyvolat `done` v agentovi s odpovídajícím stavem před vrácením a nemusí vyvolávat žádné výjimky.

## <a name="start"></a>Čína

Přesune agenta ze stavu `agent_created` do stavu `agent_runnable` a naplánuje jeho spuštění.

```cpp
bool start();
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se agent správně spustil, jinak **false** . Agenta, který byl zrušen, nelze spustit.

## <a name="status"></a>stav

Synchronní zdroj informací o stavu od agenta.

```cpp
agent_status status();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální stav agenta. Všimněte si, že tento vrácený stav může být po vrácení okamžitě změněn.

## <a name="status_port"></a>status_port

Asynchronní zdroj informací o stavu od agenta.

```cpp
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí zdroj zprávy, který může odesílat zprávy o aktuálním stavu agenta.

## <a name="wait"></a>Počkej

Čeká, až agent dokončí úlohu.

```cpp
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*_PAgent*<br/>
Ukazatel na agenta, na který se má čekat.

*_Timeout*<br/>
Maximální doba, po kterou se má čekat (v milisekundách)

### <a name="return-value"></a>Návratová hodnota

`agent_status` agenta po dokončení čekání. Může to být buď `agent_canceled`, nebo `agent_done`.

### <a name="remarks"></a>Poznámky

Úloha agenta je dokončena, když agent vstoupí do `agent_canceled` nebo `agent_done` stavy.

Pokud má parametr `_Timeout` jinou hodnotu než konstanta `COOPERATIVE_TIMEOUT_INFINITE`, je vyvolána výjimka [operation_timed_out](operation-timed-out-class.md) , pokud časový limit vyprší před dokončením úkolu agentem.

## <a name="wait_for_all"></a>wait_for_all

Počká, až všichni určení agenti dokončí své úkoly.

```cpp
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*count*<br/>
Počet ukazatelů agentů přítomných v poli `_PAgents`.

*_PAgents*<br/>
Pole ukazatelů na agenty, na které se má čekat.

*_PStatus*<br/>
Ukazatel na pole stavů agenta. Každá hodnota stavu bude představovat stav odpovídajícího agenta, když se metoda vrátí.

*_Timeout*<br/>
Maximální doba, po kterou se má čekat (v milisekundách)

### <a name="remarks"></a>Poznámky

Úloha agenta je dokončena, když agent vstoupí do `agent_canceled` nebo `agent_done` stavy.

Pokud má parametr `_Timeout` jinou hodnotu než konstanta `COOPERATIVE_TIMEOUT_INFINITE`, je vyvolána výjimka [operation_timed_out](operation-timed-out-class.md) , pokud časový limit vyprší před dokončením úkolu agentem.

## <a name="wait_for_one"></a>wait_for_one

Počká, až jeden ze zadaných agentů dokončí jeho úlohu.

```cpp
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*count*<br/>
Počet ukazatelů agentů přítomných v poli `_PAgents`.

*_PAgents*<br/>
Pole ukazatelů na agenty, na které se má čekat.

*_Status*<br/>
Odkaz na proměnnou, do které bude umístěn stav agenta.

*_Index*<br/>
Odkaz na proměnnou, do které bude umístěn index agenta.

*_Timeout*<br/>
Maximální doba, po kterou se má čekat (v milisekundách)

### <a name="remarks"></a>Poznámky

Úloha agenta je dokončena, když agent vstoupí do `agent_canceled` nebo `agent_done` stavy.

Pokud má parametr `_Timeout` jinou hodnotu než konstanta `COOPERATIVE_TIMEOUT_INFINITE`, je vyvolána výjimka [operation_timed_out](operation-timed-out-class.md) , pokud časový limit vyprší před dokončením úkolu agentem.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
