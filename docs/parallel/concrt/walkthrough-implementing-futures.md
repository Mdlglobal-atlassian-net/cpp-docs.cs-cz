---
title: 'Návod: Implementace tříd future'
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 2b9d889dac195bb60651cbb76110d54b6231a5fd
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141982"
---
# <a name="walkthrough-implementing-futures"></a>Návod: Implementace tříd future

Toto téma ukazuje, jak implementovat futures ve vaší aplikaci. Téma ukazuje, jak kombinovat stávající funkce v Concurrency Runtime do něčeho, co více dělá.

> [!IMPORTANT]
> Toto téma ukazuje koncepci futures pro demonstrační účely. Doporučujeme použít [std:: Future](../../standard-library/future-class.md) nebo [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) , pokud požadujete asynchronní úlohu, která vypočítá hodnotu pro pozdější použití.

*Úkol* je výpočet, který je možné rozložit do dalších, jemně odstupňovaných výpočtů. *Budoucí* je asynchronní úloha, která vypočítá hodnotu pro pozdější použití.

Pro implementaci futures toto téma definuje třídu `async_future`. Třída `async_future` používá tyto komponenty Concurrency Runtime: třídu [Concurrency:: task_group](reference/task-group-class.md) a třídu [concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) . Třída `async_future` používá třídu `task_group` k výpočtu hodnoty asynchronně a třídy `single_assignment` k uložení výsledku výpočtu. Konstruktor třídy `async_future` přebírá pracovní funkci, která vypočítá výsledek a metoda `get` načte výsledek.

### <a name="to-implement-the-async_future-class"></a>Implementace třídy async_future

1. Deklarujte třídu šablony s názvem `async_future`, která je parametrizovaná na typ výsledného výpočtu. Přidejte do této třídy oddíly `public` a `private`.

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. V sekci `private` třídy `async_future` deklarujte `task_group` a datový člen `single_assignment`.

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. V sekci `public` třídy `async_future` implementujte konstruktor. Konstruktor je šablona, která je parametrizovaná na pracovní funkci, která vypočítá výsledek. Konstruktor asynchronně spustí pracovní funkci v datovém členu `task_group` a pomocí funkce [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) zapíše výsledek do datového členu `single_assignment`.

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. V sekci `public` třídy `async_future` implementujte destruktor. Destruktor čeká na dokončení úlohy.

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. V sekci `public` třídy `async_future` Implementujte metodu `get`. Tato metoda používá funkci [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) k načtení výsledku pracovní funkce.

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje kompletní třídu `async_future` a příklad jejího použití. Funkce `wmain` vytvoří objekt std::[Vector](../../standard-library/vector-class.md) , který obsahuje 10 000 náhodných celočíselných hodnot. Potom používá `async_future` objektů k nalezení nejmenší a nejvyšší hodnoty, které jsou obsaženy v objektu `vector`.

### <a name="code"></a>Kód

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>Komentáře

Tento příklad vytvoří následující výstup:

```Output
smallest: 0
largest:  9999
average:  4981
```

V příkladu se používá metoda `async_future::get` k načtení výsledků výpočtu. Metoda `async_future::get` čeká na dokončení výpočtu, pokud je výpočet stále aktivní.

## <a name="robust-programming"></a>Robustní programování

Chcete-li zvětšit třídu `async_future`, aby zpracovávala výjimky, které jsou vyvolány pracovní funkcí, upravte metodu `async_future::get` pro volání metody [Concurrency:: task_group:: wait](reference/task-group-class.md#wait) . Metoda `task_group::wait` vyvolá všechny výjimky, které byly vygenerovány pracovní funkcí.

Následující příklad ukazuje upravenou verzi třídy `async_future`. Funkce `wmain` používá blok `try`-`catch` k vytištění výsledku objektu `async_future` nebo k vytištění hodnoty výjimky, která je generována pracovní funkcí.

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

Tento příklad vytvoří následující výstup:

```Output
caught exception: error
```

Další informace o modelu zpracování výjimek v Concurrency Runtime naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `futures.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

**CL. exe/EHsc futures. cpp**

## <a name="see-also"></a>Viz také

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[task_group – třída](reference/task-group-class.md)<br/>
[single_assignment – třída](../../parallel/concrt/reference/single-assignment-class.md)
