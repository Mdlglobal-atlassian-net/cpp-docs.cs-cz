---
title: "Návod: Vytvoření agenta toku dat | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- creating dataflow agents [Concurrency Runtime]
- dataflow agents, creating [Concurrency Runtime]
ms.assetid: 9db5ce3f-c51b-4de1-b79b-9ac2a0cbd130
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b94fb68ad28e45141551b238acf99baedf78ef6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-creating-a-dataflow-agent"></a>Postupy: Vytvoření agenta toku dat
Tento dokument ukazuje, jak vytvářet na základě agenta aplikace, které jsou založené na toku dat, místo tok řízení.  
  
 *Řízení toku* odkazuje pořadí provádění operací v programu. Tok řízení se řídí pomocí řídicí struktury například podmíněné příkazy, smyčky a tak dále. Alternativně *toku dat* odkazuje na programovací model, ve kterém jsou vytvářeny výpočty pouze v případě, všechna požadovaná data je k dispozici. Programovací model toku dat se týká konceptu usnadnění, ve kterém nezávislé komponenty programu vzájemnou komunikaci odesláním zprávy.  
  
 Asynchronní agenti podporovat tok řízení i toku dat programovací modely. I když modelu tok řízení je vhodné v mnoha případech, model toku dat je vhodné v jiné, například když agenta přijímá data a provede akci, která je založena na datovou část data.  
  
## <a name="prerequisites"></a>Požadavky  
 Přečtěte si následující dokumenty, než začnete Tento názorný postup:  
  
- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)  
  
- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [Postupy: použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
##  <a name="top"></a>Oddíly  
 Tento názorný postup obsahuje následující části:  
  
- [Vytvoření agenta základní tok řízení](#control-flow)  
  
- [Vytvoření základní agenta toku dat](#dataflow)  
  
- [Vytvoření agenta protokolování zpráv](#logging)  
  
##  <a name="control-flow"></a>Vytvoření agenta základní tok řízení  
 Podívejte se na následující příklad, který definuje `control_flow_agent` třídy. `control_flow_agent` Třída slouží na tři vyrovnávacích pamětí zpráv: jeden vstupní vyrovnávací paměti a dva výstupní vyrovnávací paměti. `run` Metoda čte z zdrojová vyrovnávací paměť zprávy ve smyčce a používá podmíněného příkaz k přímé toku spuštění programu. Agent zvýší jeden čítač nulová, záporné hodnoty a zvýší jiný čítač nenulové, kladné hodnoty. Po agenta obdrží sentinel hodnota nula, odešle hodnoty čítačů výstupní vyrovnávací paměti zpráv. `negatives` a `positives` metody povolit aplikaci číst počty kladné i záporné hodnoty od agenta.  
  
 [!code-cpp[concrt-dataflow-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_1.cpp)]  
  
 I když tento příklad vytvoří základní použití tok řízení v agenta, ukazuje sériové povaha programování na základě řízení toku. Každá zpráva musí být zpracovány postupně, i když může být k dispozici ve vyrovnávací paměti vstupní zpráva více zpráv. Model toku dat umožňuje obě větve podmíněného příkaz vyhodnotit současně. Model toku dat můžete také vytvořit složitější zasílání zpráv sítě, které fungují na data, jakmile je k dispozici.  
  
 [[Horní](#top)]  
  
##  <a name="dataflow"></a>Vytvoření základní agenta toku dat  
 V této části ukazuje, jak převést `control_flow_agent` třídy pomocí modelu toku dat si provést stejný úkol.  
  
 Agenta toku dat funguje tak, že vytvoření sítě vyrovnávacích pamětí zpráv, z nichž každá má konkrétní účel. Určité bloky zpráv pomocí funkce filtru k přijetí nebo odmítnutí zprávu na základě jeho datové části. Funkce filtru zajistí, že blok zpráv přijímá jenom určité hodnoty.  
  
#### <a name="to-convert-the-control-flow-agent-to-a-dataflow-agent"></a>Převedení agenta toku řízení na agenta toku dat  
  
1.  Zkopírujte text `control_flow_agent` třída k jiné třídě, například `dataflow_agent`. Alternativně můžete přejmenovat `control_flow_agent` třídy.  
  
2.  Odebrat do těla smyčky, která volá `receive` z `run` metoda.  
  
 [!code-cpp[concrt-dataflow-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_2.cpp)]  
  
3.  V `run` metoda po inicializaci proměnné `negative_count` a `positive_count`, přidejte `countdown_event` objekt, který sleduje počet aktivní operace.  
  
 [!code-cpp[concrt-dataflow-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_3.cpp)]  
  
     `countdown_event` Třídy se zobrazí později v tomto tématu.  
  
4.  Vytvořte objekty vyrovnávací paměti, které se budou podílet zprávy v síti toku dat.  
  
 [!code-cpp[concrt-dataflow-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_4.cpp)]  
  
5.  Připojte vyrovnávacích pamětí zpráv k síti.  
  
 [!code-cpp[concrt-dataflow-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_5.cpp)]  
  
6.  Počkejte `event` a `countdown event` objekty, které chcete nastavit. Tyto události signalizují, že agenta přijal sentinel hodnota a že nebudou dokončeny všechny operace.  
  
 [!code-cpp[concrt-dataflow-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_6.cpp)]  
  
 Následující diagram znázorňuje sítě dokončení toku dat pro `dataflow_agent` třídy:  
  
 ![Síť toku dat](../../parallel/concrt/media/concrt_dataflow.png "concrt_dataflow")  
  
 Následující tabulka popisuje členy sítě.  
  
|Člen|Popis|  
|------------|-----------------|  
|`increment_active`|A [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) objekt, který zvýší čítač aktivní událostí a předá vstupní hodnoty do zbytku sítě.|  
|`negatives`, `positives`|[Concurrency::Call](../../parallel/concrt/reference/call-class.md) objekty, které zvýší počet číslic a snižuje čítač aktivní událostí. Objekty každý pomocí filtru tak, aby přijímal záporná čísla nebo kladná čísla.|  
|`sentinel`|A [concurrency::call](../../parallel/concrt/reference/call-class.md) objekt, který přijímá pouze sentinel hodnotu nula a snižuje čítač aktivní událostí.|  
|`connector`|A [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objekt, který se připojuje zdrojová vyrovnávací paměť zprávy k interní síti.|  
  
 Protože `run` metoda je volána v odděleném podprocesu, jiná vlákna mohou zasílat zprávy do sítě, než je plně připojená síť. `_source` – Datový člen je `unbounded_buffer` objekt, který ukládá do vyrovnávací paměti veškerý vstup, který se odesílá z aplikace pro agenta. Abyste měli jistotu sítě zpracuje všechny vstupní zprávy, agenta nejprve propojuje uzlu interní sítě a potom propojuje začátek síti, `connector`do `_source` – datový člen. To zaručuje, že zprávy není zpracovat jako síť je právě vytvořen.  
  
 Vzhledem k síti v tomto příkladu je založená na toku dat, místo na tok řízení sítě musí komunikovat s agenta, je dokončené zpracování jednotlivých vstupní hodnoty, a že uzlu sentinel přijal jeho hodnotu. Tento příklad používá `countdown_event` objekt signál, že všechny vstupní hodnoty byly zpracovány a [concurrency::event](../../parallel/concrt/reference/event-class.md) objektu k označení, že uzel sentinel přijal jeho hodnotu. `countdown_event` Třídy používá `event` objekt, který má být signalizován hodnota čítače hodnota nula. Head sítě toku dat zvýší čítače pokaždé, když to obdrží hodnotu. Každý terminálu uzel sítě snižuje čítač po zpracovává vstupní hodnoty. Po agenta forms toku dat sítě, čeká uzlu sentinel nastavit `event` objekt a `countdown_event` objekt signál, že jeho čítač dosáhl nula.  
  
 Následující příklad ukazuje `control_flow_agent`, `dataflow_agent`, a `countdown_event` třídy. `wmain` Funkce vytvoří `control_flow_agent` a `dataflow_agent` objekt a používá `send_values` odesílat řadu náhodných hodnot do agentů.  
  
 [!code-cpp[concrt-dataflow-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_7.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
Control-flow agent:  
There are 500523 negative numbers.  
There are 499477 positive numbers.  
Dataflow agent:  
There are 500523 negative numbers.  
There are 499477 positive numbers.  
```  
  
### <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `dataflow-agent.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc toku dat – agent.cpp**  
  
 [[Horní](#top)]  
  
##  <a name="logging"></a>Vytvoření agenta protokolování zpráv  
 Následující příklad ukazuje `log_agent` třídy, která vypadá přibližně takto: `dataflow_agent` třídy. `log_agent` Třída implementuje asynchronní protokolování agenta, zápisy do souboru a ke konzole protokolu zpráv. `log_agent` Třída umožňuje aplikaci zařadit do kategorií jako informační zprávy, varování nebo chyba. Umožňuje také aplikace k určení, zda je každá kategorie protokolu zapisovány do souboru, konzole nebo obojí. Tento příklad zapíše všechny zprávy protokolu do souboru a pouze chybové zprávy do konzoly.  
  
 [!code-cpp[concrt-log-filter#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_8.cpp)]  
  
 Tento příklad zapíše následující výstup do konzoly.  
  
```Output  
error: This is a sample error message.  
```  
  
 Tento příklad vytvoří také log.txt soubor, který obsahuje následující text.  
  
```Output  
info: ===Logging started.=== 
warning: This is a sample warning message.  
error: This is a sample error message.  
info: ===Logging finished.=== 
```  
  
### <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `log-filter.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc protokolu filter.cpp**  
  
 [[Horní](#top)]  
  
## <a name="see-also"></a>Viz také  
 [Návody k Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

