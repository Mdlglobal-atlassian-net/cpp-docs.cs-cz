---
title: 'Postupy: Implementace různých vzorů producent – příjemce'
ms.date: 11/04/2016
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
ms.openlocfilehash: 113518e97b6715384b5e7b84b0d0eab63dfcfcc7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411354"
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>Postupy: Implementace různých vzorů producent – příjemce

Toto téma popisuje způsob implementace vzoru producent – příjemce ve vaší aplikaci. V tomto modelu *producent* posílání zpráv do bloku zprávy a *příjemce* čte zprávy z tohoto bloku.

Téma ukazuje dva scénáře. V prvním případě spotřebitel musí mít každá zpráva, která odesílá výrobce. V druhém scénáři příjemce pravidelně se dotazuje na data a proto není nutné každá zpráva.

Oba příklady v tomto tématu použijte agenty, blokům zpráv a funkce předávání zpráv k přenosu zpráv od výrobce příjemci. Výrobce agent používá [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce pro zapisování zpráv do [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) objektu. Používá agent příjemce [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkce umožní číst zprávy z [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) objektu. Oba agenti obsahovat hodnotu sentinel ke koordinaci konec zpracování.

Další informace o asynchronních agentů najdete v tématu [asynchronních agentů](../../parallel/concrt/asynchronous-agents.md). Další informace o blokům zpráv a funkce předávání zpráv, najdete v části [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md) a [funkce předávání zpráv](../../parallel/concrt/message-passing-functions.md).

## <a name="example"></a>Příklad

V tomto příkladu producent agent odešle posloupnost číslic agent příjemce. Příjemce dostane každá z těchto čísel a vypočítá jejich průměr. Aplikace zapíše průměr do konzoly.

Tento příklad používá [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objekt umožňující producenta zpráv do fronty. `unbounded_buffer` Implementuje třída `ITarget` a `ISource` tak, aby výrobce a příjemce může odesílat a přijímat zprávy do a ze sdílené vyrovnávací paměti. `send` a `receive` funkce koordinovat úlohy šíření data od výrobce příjemci.

[!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
The average is 50.
```

## <a name="example"></a>Příklad

V tomto příkladu producent agent odešle řadu akcií agent příjemce. Agent příjemce pravidelně čte aktuálního uvozovkách a tiskne na konzolu.

Tento příklad se podobá předchozímu, s tím rozdílem, že používá [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) objektu umožňuje odesílateli sdílet jednu zprávu s příjemce. Stejně jako v předchozím příkladu `overwrite_buffer` implementuje třída `ITarget` a `ISource` tak, aby výrobce a příjemce může fungovat pro vyrovnávací paměť sdílené zprávy.

[!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]

Tento příklad vytvoří následující ukázkový výstup.

```Output
Current quote is 24.44.
Current quote is 24.44.
Current quote is 24.65.
Current quote is 24.99.
Current quote is 23.76.
Current quote is 22.30.
Current quote is 25.89.
```

Na rozdíl od s `unbounded_buffer` objektu, `receive` funkce neodebere zprávu `overwrite_buffer` objektu. Pokud příjemce čte z vyrovnávací paměti zpráv předtím, než producent přepis této zprávy více než jednou, příjemce získá pokaždé, když se stejnou zprávu.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `producer-consumer.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /EHsc producer-consumer.cpp**

## <a name="see-also"></a>Viz také:

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)
