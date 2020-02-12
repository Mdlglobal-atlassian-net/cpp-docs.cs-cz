---
title: 'Postupy: Vytvoření agenta toku dat'
ms.date: 04/25/2019
helpviewer_keywords:
- creating dataflow agents [Concurrency Runtime]
- dataflow agents, creating [Concurrency Runtime]
ms.assetid: 9db5ce3f-c51b-4de1-b79b-9ac2a0cbd130
ms.openlocfilehash: fa19d965a35909dfefc5f586c772bc9b4565e814
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142975"
---
# <a name="walkthrough-creating-a-dataflow-agent"></a>Postupy: Vytvoření agenta toku dat

Tento dokument ukazuje, jak vytvořit aplikace založené na agentech, které jsou založené na toku dat, místo řízení toku.

*Tok řízení* odkazuje na pořadí provádění operací v programu. Tok řízení je regulován pomocí řídicích struktur, jako jsou podmíněné příkazy, smyčky a tak dále. Navíc *datový tok* odkazuje na programovací model, ve kterém jsou výpočty provedeny pouze v případě, že jsou k dispozici všechna požadovaná data. Programovací model Dataflow se vztahuje na pojem předávání zpráv, ve kterém vzájemně komunikují zprávy nezávislými komponentami programu.

Asynchronní agenti podporují programovací modely toku řízení a toku. I když model toku řízení je vhodný v mnoha případech, model toku dat je vhodný pro jiné, například když agent obdrží data a provede akci, která je založena na datové části těchto dat.

## <a name="prerequisites"></a>Požadavky

Než začnete tento návod, přečtěte si následující dokumenty:

- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Postupy: Použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)

## <a name="top"></a>Řezů

Tento návod obsahuje následující oddíly:

- [Vytváření základního agenta toku řízení](#control-flow)

- [Vytváření základního agenta toku dat](#dataflow)

- [Vytvoření agenta protokolování zpráv](#logging)

## <a name="control-flow"></a>Vytváření základního agenta toku řízení

Vezměte v úvahu následující příklad, který definuje třídu `control_flow_agent`. Třída `control_flow_agent` pracuje se třemi vyrovnávacími pamětmi zpráv: jednu vstupní vyrovnávací paměť a dvě výstupní vyrovnávací paměti. Metoda `run` čte ze zdrojové vyrovnávací paměti zpráv ve smyčce a používá podmíněný příkaz k nasměrování toku provádění programu. Agent zvýší jeden čítač na nenulové, záporné hodnoty a zvýší jiný čítač na nenulové kladné hodnoty. Jakmile agent obdrží hodnotu Sentinel nula, pošle hodnoty čítačů do výstupní vyrovnávací paměti zpráv. Metody `negatives` a `positives` umožňují aplikaci číst počty záporných a kladných hodnot od agenta.

[!code-cpp[concrt-dataflow-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_1.cpp)]

I když tento příklad používá základní použití toku řízení v agentovi, ukazuje sériovou povahu programování založeného na řízení toku. Každá zpráva musí být zpracována sekvenčně, i když ve vyrovnávací paměti vstupní zprávy může být k dispozici více zpráv. Model toku dat umožňuje souběžné vyhodnocení obou větví podmíněného příkazu. Model toku dat také umožňuje vytvářet složitější sítě pro zasílání zpráv, které fungují s daty, jakmile budou k dispozici.

[[Nahoře](#top)]

## <a name="dataflow"></a>Vytváření základního agenta toku dat

V této části se dozvíte, jak převést třídu `control_flow_agent`, aby používala model toku dat k provedení stejné úlohy.

Agent toku dat funguje tak, že vytvoří síť vyrovnávací paměti zpráv, z nichž každá zajišťuje konkrétní účel. Některé bloky zpráv používají funkci filtru k přijetí nebo odmítnutí zprávy na základě její datové části. Funkce Filter zajišťuje, že blok zpráv obdrží pouze určité hodnoty.

#### <a name="to-convert-the-control-flow-agent-to-a-dataflow-agent"></a>Převedení agenta toku řízení na agenta toku dat

1. Zkopírujte tělo třídy `control_flow_agent` do jiné třídy, například `dataflow_agent`. Alternativně můžete přejmenovat třídu `control_flow_agent`.

1. Odstraňte tělo smyčky, která volá `receive` z metody `run`.

[!code-cpp[concrt-dataflow-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_2.cpp)]

1. V metodě `run` po inicializaci proměnných `negative_count` a `positive_count`přidejte objekt `countdown_event`, který sleduje počet aktivních operací.

[!code-cpp[concrt-dataflow-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_3.cpp)]

   Třída `countdown_event` je uvedena dále v tomto tématu.

1. Vytvořte objekty vyrovnávací paměti zprávy, které se budou podílet na síti toku dat.

[!code-cpp[concrt-dataflow-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_4.cpp)]

1. Připojte vyrovnávací paměti zpráv pro vytvoření sítě.

[!code-cpp[concrt-dataflow-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_5.cpp)]

1. Počkejte, než se nastaví `event` a objekty `countdown event`. Tyto události signalizují, že agent přijal hodnotu Sentinel a že všechny operace byly dokončeny.

[!code-cpp[concrt-dataflow-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_6.cpp)]

Následující diagram znázorňuje kompletní síť toku dat pro třídu `dataflow_agent`:

![Síť toku dat](../../parallel/concrt/media/concrt_dataflow.png "Síť toku dat")

V následující tabulce jsou popsány členové sítě.

|Člen|Popis|
|------------|-----------------|
|`increment_active`|Objekt [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) , který zvyšuje aktivní čítač událostí a předá vstupní hodnotu zbytku sítě.|
|`negatives`, `positives`|[Concurrency:: Call](../../parallel/concrt/reference/call-class.md) Objects zvyšuje počet čísel a snižuje aktivní čítač událostí. Jednotlivé objekty používají filtr pro příjem buď záporných čísel, nebo kladných čísel.|
|`sentinel`|Objekt [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) , který přijímá pouze hodnotu Sentinel 0 a snižuje aktivní čítač událostí.|
|`connector`|Objekt [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) , který připojuje vyrovnávací paměť zdrojové zprávy k interní síti.|

Vzhledem k tomu, že je metoda `run` volána v samostatném vlákně, další vlákna mohou odesílat zprávy do sítě před tím, než je síť plně připojená. Datový člen `_source` je objekt `unbounded_buffer`, který ukládá do vyrovnávací paměti veškerý vstup, který je odeslán z aplikace do agenta. Aby bylo zajištěno, že síť zpracovává všechny vstupní zprávy, agent nejprve propojí interní uzly sítě a poté propojí začátek této sítě, `connector`k datovému členu `_source`. To zaručuje, že se zprávy nezpracovávají při seformátování sítě.

Vzhledem k tomu, že síť v tomto příkladu je založená na toku dat, nikoli v řízení toku, musí síť komunikovat s agentem, že dokončila zpracování každé vstupní hodnoty a že uzel Sentinel přijal svou hodnotu. Tento příklad používá objekt `countdown_event` k signalizaci, že byly zpracovány všechny vstupní hodnoty a objekt [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) , který označuje, že uzel Sentinel přijal svou hodnotu. Třída `countdown_event` používá objekt `event` k signalizaci, když hodnota čítače dosáhne nuly. Vedoucí sítě toku dat zvýší čítač pokaždé, když obdrží hodnotu. Každý uzel terminálu sítě snižuje čítače po zpracování vstupní hodnoty. Poté, co agent vytvoří síť toku dat, počká, až uzel Sentinel nastaví objekt `event` a objekt `countdown_event` k signalizaci, že jeho čítač dosáhl nuly.

Následující příklad ukazuje třídy `control_flow_agent`, `dataflow_agent`a `countdown_event`. Funkce `wmain` vytvoří `control_flow_agent` a objekt `dataflow_agent` a pomocí funkce `send_values` odešle do agentů řadu náhodných hodnot.

[!code-cpp[concrt-dataflow-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_7.cpp)]

Tento příklad vytvoří následující vzorový výstup:

```Output
Control-flow agent:
There are 500523 negative numbers.
There are 499477 positive numbers.
Dataflow agent:
There are 500523 negative numbers.
There are 499477 positive numbers.
```

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `dataflow-agent.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

**CL. exe/EHsc Dataflow-agent. cpp**

[[Nahoře](#top)]

## <a name="logging"></a>Vytvoření agenta protokolování zpráv

Následující příklad ukazuje třídu `log_agent`, která se podobá `dataflow_agent` třídy. Třída `log_agent` implementuje asynchronního agenta protokolování, který zapisuje zprávy protokolu do souboru a do konzoly nástroje. Třída `log_agent` umožňuje aplikaci kategorizovat zprávy jako informativní, varovné nebo chybové. Aplikace taky umožňuje určit, jestli se mají jednotlivé kategorie protokolů zapisovat do souboru, konzoly nebo obou. Tento příklad zapisuje všechny zprávy protokolu do souboru a pouze chybové zprávy do konzoly.

[!code-cpp[concrt-log-filter#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_8.cpp)]

Tento příklad zapíše následující výstup do konzoly.

```Output
error: This is a sample error message.
```

Tento příklad také vytvoří soubor log. txt, který obsahuje následující text.

```Output
info: ===Logging started.===
warning: This is a sample warning message.
error: This is a sample error message.
info: ===Logging finished.===
```

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `log-filter.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

**CL. exe/EHsc log-Filter. cpp**

[[Nahoře](#top)]

## <a name="see-also"></a>Viz také

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
