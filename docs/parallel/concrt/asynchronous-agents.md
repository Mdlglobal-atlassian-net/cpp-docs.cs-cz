---
title: "Asynchronní agenti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- asynchronous agents
- agents [Concurrency Runtime]
ms.assetid: 6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c4ce3240041987a79657c7e8bf296f9e89acb7a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="asynchronous-agents"></a>Asynchronní agenti
*Asynchronní agenta* (nebo jenom *agenta*) je aplikace, kterou asynchronně funguje s jinými prostředky k řešení větší výpočetní úlohy. Agent si můžete představit jako úlohu, která má nastavené životní cyklus. Například jeden agent může číst data ze zařízení s vstupu a výstupu (například klávesnici, soubor na disku nebo připojení k síti) a jiné agent může provádět akce na data, jakmile je k dispozici. První agent používá předávání zpráv k informování druhý agenta další data nejsou k dispozici. Plánovač úloh Concurrency Runtime poskytuje efektivní mechanismus, aby agenty blokovat a yield spolupráce při bez nutnosti méně efektivní přerušení.  
  

 Knihovna agentů definuje [concurrency::agent](../../parallel/concrt/reference/agent-class.md) třída představující asynchronní agenta. `agent`je abstraktní třída, který deklaruje virtuální metody [concurrency::agent::run](reference/agent-class.md#run). `run` Metoda spustí úlohy, které se provádí pomocí agenta. Protože `run` je abstraktní, musíte implementací této metody v každé třídy, které pocházejí z `agent`.  
  
## <a name="agent-life-cycle"></a>Životní cyklus agenta  
 Agenti mají nastavte životní cyklus. [Concurrency::agent_status](reference/concurrency-namespace-enums.md#agent_status) výčet definuje různé stavy agenta. Na následujícím obrázku je diagram stavu, který ukazuje, jak agenty průběhu z jednoho stavu do jiného. V tomto obrázku plné čáry představují metody, které volají z vaší aplikace; Tečkovaná řádky představují metody, které se nazývají z modulu runtime.  
  
 ![Diagram stavu agenta](../../parallel/concrt/media/agentstate.png "agentstate")  
  
 Následující tabulka popisuje všechny stavy v `agent_status` výčtu.  
  
|Stav agenta|Popis|  
|-----------------|-----------------|  
|`agent_created`|Agent nebyl bylo naplánováno spuštění.|  
|`agent_runnable`|Modul runtime je plánování agenta pro spuštění.|  
|`agent_started`|Agent bylo zahájeno a běží.|  
|`agent_done`|Agent byl dokončen.|  
|`agent_canceled`|Agenta byla zrušena dříve, než ho zadat `started` stavu.|  
  
 `agent_created`Počáteční stav agenta, `agent_runnable` a `agent_started` jsou aktivní stavy a `agent_done` a `agent_canceled` jsou terminálu stavy.  
  
 Použití [concurrency::agent::status](reference/agent-class.md#status) metoda pro načtení aktuálního stavu `agent` objektu. I když `status` metoda bezpečných souběžnosti, stav agenta můžete změnit čas `status` metoda vrátí. V může být například agenta `agent_started` stavu při volání `status` metoda, ale přesunout do `agent_done` právě po stavu `status` metoda vrátí.  

  
## <a name="methods-and-features"></a>Metody a funkce  
 V následující tabulce jsou uvedeny některé důležité metody, které patří do `agent` třídy. Další informace o všech `agent` metody třídy najdete v tématu [agent – třída](../../parallel/concrt/reference/agent-class.md).  
  
|Metoda|Popis|  
|------------|-----------------|  
|[spuštění](reference/agent-class.md#start)|Plány `agent` objekt pro provedení a nastaví na `agent_runnable` stavu.|  
|[Spustit](reference/agent-class.md#run)|Spustí úlohu, která je provést `agent` objektu.|  
|[provést](reference/agent-class.md#done)|Přesune agenta `agent_done` stavu.|  
|[Zrušit](../../parallel/concrt/cancellation-in-the-ppl.md#cancel)|Pokud agenta nebyla spuštěna, tato metoda zruší spuštění agenta a nastaví na `agent_canceled` stavu.|  
|[Stav](reference/agent-class.md#status)|Načte aktuální stav `agent` objektu.|  
|[Počkej](reference/agent-class.md#wait)|Čeká `agent` objekt, který chcete zadat `agent_done` nebo `agent_canceled` stavu.|  
|[wait_for_all –](reference/agent-class.md#wait_for_all)|Čeká na všechny zadané `agent` objekty, které chcete zadat `agent_done` nebo `agent_canceled` stavu.|  
|[wait_for_one –](reference/agent-class.md#wait_for_one)|Čeká na alespoň jeden ze zadaných `agent` objekty, které chcete zadat `agent_done` nebo `agent_canceled` stavu.|  
  
 Po vytvoření objektu agenta, volání [concurrency::agent::start](reference/agent-class.md#start) metodu ji naplánovat na spuštění. Volání modulu runtime `run` metoda po plánuje agenta a nastaví na `agent_runnable` stavu.  
  
 Modul runtime nespravuje výjimky, které jsou vyvolány asynchronních agentů. Další informace o zpracování výjimek a agentů najdete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
## <a name="example"></a>Příklad  
 Příklad, který ukazuje, jak vytvořit základní aplikaci založené na agentovi, naleznete v části [návod: vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md).  
  
## <a name="see-also"></a>Viz také  
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)

