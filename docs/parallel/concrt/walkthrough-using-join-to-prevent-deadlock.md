---
title: 'Návod: Použití metody join k zabránění vzájemnému zablokování'
ms.date: 04/25/2019
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
ms.openlocfilehash: 4df83e944552fd6c0d2482efa72883d87cd45f8c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140659"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>Návod: Použití metody join k zabránění vzájemnému zablokování

V tomto tématu se používá obědvajících problém stravování, který ilustruje použití třídy [Concurrency:: JOIN](../../parallel/concrt/reference/join-class.md) k zabránění zablokování v aplikaci. V softwarové aplikaci dochází k *vzájemnému zablokování* , když dva nebo více procesů každý z nich podrží určitý prostředek a zároveň čekají na další proces pro uvolnění nějakého jiného prostředku.

Problém stravování obědvajících je specifickým příkladem obecné sady problémů, ke kterým může dojít, když se sada prostředků sdílí mezi několika souběžnými procesy.

## <a name="prerequisites"></a>Požadavky

Než začnete tento návod, přečtěte si následující témata:

- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

- [Návod: Vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)

- [Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)

## <a name="top"></a>Řezů

Tento návod obsahuje následující oddíly:

- [Problém stravování obědvajících](#problem)

- [Implementace Naive](#deadlock)

- [Zabránění zablokování pomocí spojení](#solution)

## <a name="problem"></a>Problém stravování obědvajících

Problém stravování obědvajících ukazuje, jak probíhá zablokování v aplikaci. V tomto problému se pět obědvajících nachází v kulaté tabulce. Každé Philosopher alternativy mezi přemýšlejemi a jídlo. Každý Philosopher musí sdílet chopstick se sousedním směrovačem vlevo a druhým chopstick se sousedem vpravo. Toto rozložení je znázorněno na následujícím obrázku.

![Problém stravování obědvajících](../../parallel/concrt/media/dining_philosophersproblem.png "Problém obědvajících filozofů")

Pro jíst musí Philosopher obsahovat dvě Chopsticks. Pokud každý Philosopher obsahuje pouze jeden chopstick a čeká na jiný, pak žádné Philosopher nemůže jíst a všechny omezují.

[[Nahoře](#top)]

## <a name="deadlock"></a>Implementace Naive

Následující příklad ukazuje Naive implementaci obědvajících problému stravování. Třída `philosopher`, která je odvozena z [Concurrency:: Agent](../../parallel/concrt/reference/agent-class.md), umožňuje každému Philosopher jednat nezávisle. V příkladu se používá sdílené pole objektů [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) , které každému objektu `philosopher` udělí výhradní přístup k páru Chopsticks.

Chcete-li spojit implementaci s ilustrací, třída `philosopher` představuje jeden Philosopher. `int` proměnná reprezentuje jednotlivé chopstick. Objekty `critical_section` slouží jako držitelé, na kterých Chopsticks REST. Metoda `run` simuluje životnost Philosopher. Metoda `think` simuluje Act a metoda `eat` simuluje Act jídlo.

Objekt `philosopher` zamkne `critical_section` objekty pro simulaci odebrání Chopsticks od držitelů před voláním metody `eat`. Po volání `eat`vrátí objekt `philosopher` Chopsticks na držitele nastavením objektů `critical_section` zpět do stavu odemčeno.

`pickup_chopsticks` metoda znázorňuje, kde může dojít k zablokování. Pokud každý objekt `philosopher` získá přístup k jednomu z zámků, nesmí žádný objekt `philosopher` pokračovat, protože druhý zámek je ovládán jiným objektem `philosopher`.

### <a name="example"></a>Příklad

[!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `philosophers-deadlock.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Philosophers-deadlock. cpp**

[[Nahoře](#top)]

## <a name="solution"></a>Zabránění zablokování pomocí spojení

V této části se dozvíte, jak používat vyrovnávací paměti zpráv a funkce předávání zpráv, aby se vyloučila možnost zablokování.

Chcete-li tento příklad spojit se starším, třída `philosopher` nahradí každý objekt `critical_section` pomocí objektu [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) a objektu `join`. Objekt `join` slouží jako arbiter, který poskytuje Chopsticks pro Philosopher.

V tomto příkladu se používá třída `unbounded_buffer`, protože když cíl obdrží zprávu z objektu `unbounded_buffer`, zpráva se odebere z fronty zpráv. To umožňuje objektu `unbounded_buffer`, který obsahuje zprávu, aby označoval, že je chopstick k dispozici. Objekt `unbounded_buffer`, který neobsahuje žádnou zprávu, indikuje, že se používá chopstick.

V tomto příkladu se používá nehladec `join` objekt, protože spojení typu non-hlad poskytne každému objektu `philosopher` přístup k oběma chopsticksům pouze v případě, že oba objekty `unbounded_buffer` obsahují zprávu. Připojení hladce nebrání zablokování, protože připojení hladce přijímá zprávy, jakmile budou k dispozici. K zablokování může docházet, pokud všechny hlad `join` objekty dostanou jednu ze zpráv, ale počká, až se druhá stane k dispozici.

Další informace o hladovém a nehladém spojení a rozdílech mezi různými typy vyrovnávací paměti zpráv naleznete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="to-prevent-deadlock-in-this-example"></a>Jak v tomto příkladu zabránit zablokování

1. Z příkladu odeberte následující kód.

[!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]

1. Změňte typ `_left` a `_right` datových členů třídy `philosopher` na `unbounded_buffer`.

[!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]

1. Upravte konstruktor `philosopher` tak, aby jako parametry převzal objekty `unbounded_buffer`.

[!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]

1. Upravte metodu `pickup_chopsticks` pro použití nehladového `join` objektu pro příjem zpráv z vyrovnávací paměti zpráv pro obě Chopsticks.

[!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]

1. Upravte metodu `putdown_chopsticks` pro uvolnění přístupu k Chopsticks odesláním zprávy do vyrovnávací paměti zpráv pro obě Chopsticks.

[!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]

1. Upravte metodu `run` pro uložení výsledků `pickup_chopsticks` metody a předání těchto výsledků do metody `putdown_chopsticks`.

[!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]

1. Upravte deklaraci proměnné `chopsticks` ve funkci `wmain` tak, aby byla polem `unbounded_buffer` objektů, ve kterých každá z nich drží jednu zprávu.

[!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]

### <a name="description"></a>Popis

Následující příklad ukazuje dokončený příklad, který používá nehladec `join` objektů k odstranění rizika zablokování.

### <a name="example"></a>Příklad

[!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_9.cpp)]

Tento příklad vytvoří následující výstup.

```Output
aristotle ate 50 times.
descartes ate 50 times.
hobbes ate 50 times.
socrates ate 50 times.
plato ate 50 times.
```

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `philosophers-join.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Philosophers-JOIN. cpp**

[[Nahoře](#top)]

## <a name="see-also"></a>Viz také

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br/>
[Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)
