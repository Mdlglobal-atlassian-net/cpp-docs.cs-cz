---
title: 'Návod: Předcházení zablokování pomocí spojení'
ms.date: 11/19/2018
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
ms.openlocfilehash: 2f9e0f50866ed0635fbaa4b700dbf522f09458d9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303050"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>Návod: Předcházení zablokování pomocí spojení

Toto téma používá problém obědvajících filozofů si ukážeme, jak používat [concurrency::join](../../parallel/concrt/reference/join-class.md) třídy, aby se zabránilo zablokování v aplikaci. V případě aplikace softwaru *zablokování* nastane, pokud dva nebo více procesů jednotlivých uložení prostředku a vzájemně počkat na jiný proces uvolnit jiný prostředek.

Problém obědvajících filozofů je konkrétní příklad sady obecných problémů, které mohou nastat při sadu prostředků je sdílen mezi více souběžných procesů.

## <a name="prerequisites"></a>Požadavky

Před zahájením tohoto návodu, přečtěte si následující témata:

- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

- [Návod: Vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)

- [Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)

##  <a name="top"></a> Oddíly

Tento návod obsahuje následující části:

- [Problém obědvajících Filozofů](#problem)

- [Naivní implementace](#deadlock)

- [Použití metody join k zabránění vzájemnému zablokování](#solution)

##  <a name="problem"></a> Problém obědvajících Filozofů

Problém obědvajících filozofů ukazuje, jak v aplikaci dojde k zablokování. V tomto problému pět filozofů sedí u kulatého stolu. Každý filosofovi střídá uvažujete a využít. Každý filosofovi musí nasdílet chopstick sousední vlevo a jinou chopstick s sousední vpravo. Následující obrázek znázorňuje toto rozložení.

![Problém obědvajících Filozofů](../../parallel/concrt/media/dining_philosophersproblem.png "problém obědvajících Filozofů")

K jíst filosofovi musí mít dva chopsticks. Pokud každý filosofovi obsahuje pouze jednu chopstick a čeká na jiný, poté můžete bez filosofovi jíst a všechny nezablokuje.

[[Horní](#top)]

##  <a name="deadlock"></a> Naivní implementace

Následující příklad ukazuje na naivní implementace problém obědvajících filozofů. `philosopher` Třída, která je odvozena z [concurrency::agent](../../parallel/concrt/reference/agent-class.md), umožňuje každý filosofovi jednali nezávisle. V příkladu se používá sdílené pole [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) objekty dát `philosopher` exkluzivní přístup k pár chopsticks objektu.

K implementaci na obrázku `philosopher` třída představuje jeden filosofovi. `int` Proměnná představuje každý chopstick. `critical_section` Objekty slouží jako zástupné znaky, na kterých chopsticks rest. `run` Metoda simuluje životnosti filosofovi. `think` Metoda simuluje act přemýšlení a `eat` metoda simuluje v rámci využít.

A `philosopher` objekt uzamkne obě `critical_section` objekty pro simulaci odebrání chopsticks z zástupné znaky dříve, než se zavolá `eat` metoda. Po volání `eat`, `philosopher` objekt vrátí chopsticks držitelům tak, že nastavíte `critical_section` objektů zpět do stavu odemknout.

`pickup_chopsticks` Metoda ukazuje, kde může dojít k zablokování. Pokud každý `philosopher` objektu získá přístup k jeden zámků a ne `philosopher` objekt může pokračovat, protože na uzamčení se řídí jiné `philosopher` objektu.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

### <a name="code"></a>Kód

[!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `philosophers-deadlock.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc filozofů deadlock.cpp**

[[Horní](#top)]

##  <a name="solution"></a> Použití metody join k zabránění vzájemnému zablokování

Tato část ukazuje, jak můžete eliminovat riziko zablokování vyrovnávací paměti zpráv a funkce předávání zpráv.

K propojení tohoto příkladu a dřívějších verzí `philosopher` třídy nahradí každou `critical_section` s použitím [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objektu a `join` objektu. `join` Objekt slouží jako arbiter, která poskytuje chopsticks filosofovi.

V tomto příkladu `unbounded_buffer` třídy, protože když cíl obdrží zprávu od `unbounded_buffer` objektu, zpráva se odebere z fronty zpráv. To umožňuje `unbounded_buffer` objekt, který obsahuje zprávu, která označuje, že chopstick je k dispozici. `unbounded_buffer` Objekt, který obsahuje žádná zpráva označuje, že chopstick používá.

Tento příklad používá bez metody greedy `join` objektu, protože spojení typu non-greedy poskytuje každý `philosopher` objekt přístup k oběma chopsticks pouze tehdy, když oba `unbounded_buffer` objekty obsahují zprávu. Greedy spojení by zabránit zablokování, protože greedy spojení přijímá zprávy, jakmile budou k dispozici. Zablokování může dojít, pokud všechny greedy `join` objekty zobrazit jedna z zprávy, ale stále čekat pro jiné než bude k dispozici.

Další informace o spojení s metodou greedy a bez metody greedy a rozdíly mezi různými typy vyrovnávací paměti zpráv najdete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

#### <a name="to-prevent-deadlock-in-this-example"></a>Jak v tomto příkladu zabránit zablokování

1. Odeberte z příkladu následující kód.

[!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]

1. Změna typu `_left` a `_right` datové členy `philosopher` třídu `unbounded_buffer`.

[!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]

1. Upravit `philosopher` konstruktoru se `unbounded_buffer` objekty jako svoje parametry.

[!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]

1. Upravit `pickup_chopsticks` metodu použít bez metody greedy `join` objektu pro příjem zpráv z vyrovnávací paměti zpráv pro obě chopsticks.

[!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]

1. Upravit `putdown_chopsticks` metodu pro uvolnění přístup k chopsticks odesláním zprávy do vyrovnávací paměti zpráv pro obě chopsticks.

[!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]

1. Upravit `run` metodu pro ukládání výsledků `pickup_chopsticks` – metoda a předávat tyto výsledky `putdown_chopsticks` metody.

[!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]

1. Upravte deklaraci `chopsticks` proměnné v `wmain` funkci pole `unbounded_buffer` objekty, že každý obsahovat jednu zprávu.

[!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následuje ukázka dokončené příklad, který používá bez metody greedy `join` objekty riziko zablokování.

### <a name="code"></a>Kód

[!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_9.cpp)]

### <a name="comments"></a>Komentáře

Tento příklad vytvoří následující výstup.

```Output
aristotle ate 50 times.
descartes ate 50 times.
hobbes ate 50 times.
socrates ate 50 times.
plato ate 50 times.
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `philosophers-join.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /EHsc philosophers-join.cpp**

[[Horní](#top)]

## <a name="see-also"></a>Viz také:

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br/>
[Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)
