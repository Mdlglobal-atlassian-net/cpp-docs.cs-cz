---
title: 'Postupy: Vytvoření agenta toku dat'
ms.date: 11/19/2018
helpviewer_keywords:
- creating dataflow agents [Concurrency Runtime]
- dataflow agents, creating [Concurrency Runtime]
ms.assetid: 9db5ce3f-c51b-4de1-b79b-9ac2a0cbd130
ms.openlocfilehash: 26ea7d520c3dbc4935699e5d52871d21739a3d88
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176078"
---
# <a name="walkthrough-creating-a-dataflow-agent"></a>Postupy: Vytvoření agenta toku dat

Tento dokument ukazuje, jak vytvářet aplikace pro systém agenta, které jsou založeny na toku dat, namísto tok řízení.

*Řízení toku* odkazuje na pořadí provádění operací v programu. Tok řízení je upravena pomocí ovládacího prvku struktury, jako jsou podmíněné příkazy, smyčky a tak dále. Alternativně *toku dat* odkazuje na programovací model, ve kterém výpočty jsou provedeny pouze v případě, všechna požadovaná data je k dispozici. Programovací model toku dat se týká koncept předávání, zpráv, ve kterém nezávislé komponenty aplikace komunikovat mezi sebou odesíláním zpráv.

Asynchronní agenti podporu tok řízení a toku dat programovacích modelů. I když je vhodné v mnoha případech model tok řízení, model toku dat je vhodné pro ostatní, například, pokud agent přijímá data a provádějí akci, která je založena na datovou část data.

## <a name="prerequisites"></a>Požadavky

Před zahájením tohoto návodu, přečtěte si následující dokumenty:

- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Postupy: Použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)

##  <a name="top"></a> Oddíly

Tento návod obsahuje následující části:

- [Vytvoření agenta toku řízení základní](#control-flow)

- [Vytvoření základního agenta toku dat](#dataflow)

- [Vytvoření agenta protokolování zpráv](#logging)

##  <a name="control-flow"></a> Vytvoření agenta toku řízení základní

Podívejte se na následující příklad, který definuje `control_flow_agent` třídy. `control_flow_agent` Třídy funguje na tři vyrovnávací paměti zpráv: jeden vstupní vyrovnávací paměti a dvě výstupní vyrovnávací paměti. `run` Metoda načte ze zdrojové vyrovnávací paměti zpráv ve smyčce a podmíněný příkaz používá k řízení toku programu. Agent zvýší jeden čítač pro nenulové, záporné hodnoty a zvýší jiný čítač pro nenulové, kladné hodnoty. Po agent obdrží sentinel hodnota nula, odešle do výstupní vyrovnávací paměti zpráv hodnoty čítače. `negatives` a `positives` metody umožňují aplikaci číst počty kladné i záporné hodnoty od agenta.

[!code-cpp[concrt-dataflow-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_1.cpp)]

Přestože tento příklad využívá základní tok řízení v agentovi, ukazuje sériového portu povaze programování na základě řízení toku. Každá zpráva musí být zpracovány postupně, i když může být k dispozici ve vyrovnávací paměti vstupní zprávy více zpráv. Model toku dat umožňuje obou větvích podmíněný příkaz pro vyhodnocení současně. Model toku dat také umožňuje vytvářet složitější sítě zasílání zpráv, které působí na data, jakmile je k dispozici.

[[Horní](#top)]

##  <a name="dataflow"></a> Vytvoření základního agenta toku dat

Tato část ukazuje, jak převést `control_flow_agent` třídy k použití modelu datového toku k provedení stejné úlohy.

Agenta toku dat funguje tak, že vytvoříte síť vyrovnávacích pamětí zpráv, z nichž každý slouží pro konkrétní účel. Některé blokům zpráv pomocí funkce filtru přijmout nebo odmítnout zprávu na základě její datové části. Funkce filtru se zajistí, že blok zpráv přijme jenom konkrétní hodnoty.

#### <a name="to-convert-the-control-flow-agent-to-a-dataflow-agent"></a>Převedení agenta toku řízení na agenta toku dat

1. Zkopírujte text `control_flow_agent` třídu pro jiné třídy, například `dataflow_agent`. Alternativně můžete přejmenovat `control_flow_agent` třídy.

1. Odeberte tělo smyčky, která volá `receive` z `run` metody.

[!code-cpp[concrt-dataflow-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_2.cpp)]

1. V `run` metoda po inicializaci proměnné `negative_count` a `positive_count`, přidejte `countdown_event` objekt, který sleduje počet aktivními operacemi.

[!code-cpp[concrt-dataflow-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_3.cpp)]

   `countdown_event` Třídy je uveden dále v tomto tématu.

1. Vytvořte zprávu vyrovnávací paměti objektů, které se budou podílet v síti datového toku.

[!code-cpp[concrt-dataflow-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_4.cpp)]

1. Připojte vyrovnávací paměti zpráv a vytvoří síť.

[!code-cpp[concrt-dataflow-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_5.cpp)]

1. Počkejte `event` a `countdown event` objektů, která se má nastavit. Tyto události signalizují, že agent přijal hodnotu sentinel a že nebudou dokončeny všechny operace.

[!code-cpp[concrt-dataflow-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_6.cpp)]

Následující diagram znázorňuje sítě dokončení toku dat pro `dataflow_agent` třídy:

![Tok dat sítě](../../parallel/concrt/media/concrt_dataflow.png "sítě toku dat")

Následující tabulka popisuje členy v síti.

|Člen|Popis|
|------------|-----------------|
|`increment_active`|A [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) objekt, který zvýší Čítač Aktivní události a předává vstupní hodnoty do zbytku sítě.|
|`negatives`, `positives`|[Concurrency::Call](../../parallel/concrt/reference/call-class.md) objekty, které zvětšit jejich celkový počet čísel a dekrementuje čítače aktivní události. Všechny objekty pomocí filtru tak, aby přijímal záporná čísla nebo kladná čísla.|
|`sentinel`|A [concurrency::call](../../parallel/concrt/reference/call-class.md) objekt, který přijímá pouze hodnotu sentinel nula a sníží Čítač Aktivní události.|
|`connector`|A [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objekt, který zdrojová vyrovnávací paměť zpráv se připojí k interní síti.|

Vzhledem k tomu, `run` metoda je volána v samostatném vlákně, ostatní vlákna mohou odesílat zprávy k síti předtím, než je plně připojená síť. `_source` Datový člen je `unbounded_buffer` objekt, který ukládá do vyrovnávací paměti veškerý vstup, který se odesílá z aplikace do agenta. Abyste měli jistotu, že síť zpracovává všechny vstupní zprávy, agenta nejprve propojuje uzly interní sítě a pak propojí začátku této síti `connector`, možnosti `_source` datový člen. Zaručí se tak, že zprávy nezpracovávají jako síti je právě vytvořen.

Protože sítě v tomto příkladu je založená na toku dat, spíše než v toku řízení sítě musí komunikovat agentům, že bylo dokončeno zpracování každé vstupní hodnota a že ověřovací uzel byl přijat jeho hodnotu. Tento příklad používá `countdown_event` objekt, který signalizuje, že byly zpracovány všechny vstupní hodnoty a [concurrency::event](../../parallel/concrt/reference/event-class.md) objektu k označení, že ověřovací uzel byl přijat jeho hodnotu. `countdown_event` Třídy používá `event` objekt, který signalizuje, že když hodnota čítače dosáhne nuly. Vedoucí toku dat sítě zvýší čítač pokaždé, když se obdrží hodnotu. Každý terminálu uzel sítě dekrementuje čítače po zpracovává vstupní hodnota. Po forms agenta toku dat sítě, čeká ověřovací uzel pro nastavení `event` objekt a pro `countdown_event` objektu na signál, že jeho čítač bylo dosaženo nula.

Následující příklad ukazuje `control_flow_agent`, `dataflow_agent`, a `countdown_event` třídy. `wmain` Vytvoří funkci `control_flow_agent` a `dataflow_agent` a použije `send_values` funkce Odeslat posloupnost náhodných hodnot do agentů.

[!code-cpp[concrt-dataflow-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_7.cpp)]

Tento příklad vytvoří následující ukázkový výstup:

```Output
Control-flow agent:
There are 500523 negative numbers.
There are 499477 positive numbers.
Dataflow agent:
There are 500523 negative numbers.
There are 499477 positive numbers.
```

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `dataflow-agent.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc toku dat agent.cpp**

[[Horní](#top)]

##  <a name="logging"></a> Vytvoření agenta protokolování zpráv

Následující příklad ukazuje `log_agent` třídu, která vypadá podobně jako `dataflow_agent` třídy. `log_agent` Třída implementuje asynchronního protokolování agenta, zápisy do souboru a ke konzole protokolování zpráv. `log_agent` Třída umožňuje aplikaci ke kategorizaci jako informační zprávy, upozornění nebo chyby. Umožňuje také aplikace k určení, jestli je každé kategorie protokolu zapisovat do souboru nebo konzoly. Tento příklad zapíše všechny zprávy protokolu do souboru a pouze chybové zprávy do konzoly.

[!code-cpp[concrt-log-filter#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_8.cpp)]

Tento příklad zapíše následující výstup do konzoly.

```Output
error: This is a sample error message.
```

Tento příklad také vytvoří soubor log.txt, který obsahuje následující text.

```Output
info: ===Logging started.===
warning: This is a sample warning message.
error: This is a sample error message.
info: ===Logging finished.===
```

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `log-filter.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc log-filter.cpp**

[[Horní](#top)]

## <a name="see-also"></a>Viz také

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

