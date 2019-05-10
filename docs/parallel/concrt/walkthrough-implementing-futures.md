---
title: 'Návod: Implementace tříd Future'
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 00ad8bbe6f950ad531bad751686393dce66643bb
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857068"
---
# <a name="walkthrough-implementing-futures"></a>Návod: Implementace tříd Future

Toto téma popisuje způsob implementace tříd Future ve vaší aplikaci. Téma ukazuje, jak sloučit existující funkce v modulu Runtime souběžnosti do něco jiného s více.

> [!IMPORTANT]
>  Toto téma ukazuje koncept termínu pro demonstrační účely. Doporučujeme, abyste použili [std::future](../../standard-library/future-class.md) nebo [concurrency::task](../../parallel/concrt/reference/task-class.md) když, aby asynchronní úloha, která vypočítá hodnoty pro pozdější použití.

A *úloh* je výpočet, který lze rozložit na další detailnější výpočty. A *budoucí* je asynchronní úloha, která vypočítá hodnoty pro pozdější použití.

Implementace tříd Future, určuje toto téma `async_future` třídy. `async_future` Třída používá tyto součásti modulu Runtime souběžnosti: [concurrency::task_group](reference/task-group-class.md) třídy a [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) třídy. `async_future` Třídy používá `task_group` třídy k výpočtu hodnoty asynchronně a `single_assignment` třídu pro ukládání výsledek výpočtu. Konstruktor třídy `async_future` třída má pracovní funkce, která vypočítá výsledek, a `get` metoda načítá výsledek.

### <a name="to-implement-the-asyncfuture-class"></a>Implementace třídy async_future

1. Deklarace šablony třídy s názvem `async_future` , který je s parametry typu výsledný výpočtu. Přidat `public` a `private` části do této třídy.

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. V `private` část `async_future` třídy, deklarujte `task_group` a `single_assignment` datový člen.

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. V `public` část `async_future` třídy, implementaci konstruktoru. Konstruktor je šablonu, která je v pracovní funkce, která vypočítá výsledek s parametry. Konstruktor provádí asynchronně pracovní funkce v `task_group` datový člen a používá [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce pro zápis výsledek, který má `single_assignment` datový člen.

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. V `public` část `async_future` třídy, implementujte destruktor. Destruktor čeká na dokončení úlohy.

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. V `public` část `async_future` třídy, implementujte `get` metody. Tato metoda používá [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkce načíst výsledky pracovní funkce.

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje kompletní `async_future` třídy a tu je ukázka jeho využití. `wmain` Funkce vytvoří std::[vektoru](../../standard-library/vector-class.md) objekt, který obsahuje hodnoty 10 000 náhodné celé číslo. Poté použije `async_future` objekty nejnižší a nejvyšší hodnoty, které jsou součástí `vector` objektu.

### <a name="code"></a>Kód

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>Komentáře

Tento příklad vytvoří následující výstup:

```Output
smallest: 0
largest:  9999
average:  4981
```

V příkladu se používá `async_future::get` metody k načtení výsledků výpočtu. `async_future::get` Metoda čeká na výpočet Pokud výpočtu je pořád aktivní.

## <a name="robust-programming"></a>Robustní programování

K rozšíření `async_future` třídy pro zpracování výjimek, které jsou vyvolány pracovní funkce, upravte `async_future::get` metodu chce volat [Concurrency::task_group:: wait](reference/task-group-class.md#wait) metoda. `task_group::wait` Všechny výjimky, které byly vytvořeny podle pracovní funkce vyvolá metoda výjimku.

Následující příklad ukazuje upravenou verzi `async_future` třídy. `wmain` Funkce používá `try` - `catch` bloku k vytištění výsledku `async_future` objektu nebo vytisknout hodnotu výjimky, který je generován pracovní funkce.

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

Tento příklad vytvoří následující výstup:

```Output
caught exception: error
```

Další informace o tomto modelu zpracování výjimek v Concurrency Runtime naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `futures.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc futures.cpp**

## <a name="see-also"></a>Viz také:

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[task_group – třída](reference/task-group-class.md)<br/>
[single_assignment – třída](../../parallel/concrt/reference/single-assignment-class.md)
