---
title: 'Postupy: použití filtru bloku zpráv | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b16dee4d0a3c5a6d09c1fd19006c832be400d5a4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411068"
---
# <a name="how-to-use-a-message-block-filter"></a>Postupy: Použití filtru bloku zpráv

Tento dokument ukazuje, jak používat funkce filtru pro povolení blok asynchronních zpráv přijmout nebo odmítnout zprávu na základě datovou část zprávy.

Při vytváření objektu blok zpráv, jako [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency::call](../../parallel/concrt/reference/call-class.md), nebo [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md), můžete zadat *funkce filtrování* , který určuje, zda blok zpráv přijme nebo odmítne zprávy. Funkce filtru je užitečný způsob, jak zajistit, že blok zpráv přijme jenom konkrétní hodnoty.

Funkce filtru jsou důležité, protože umožňují připojit blokům zpráv do formuláře *toku dat sítě*. Bloky zpráv v síti toku dat, řízení toku dat zpracováním pouze zprávy, které splňují určitá kritéria. Porovnejte to s modelem tok řízení, kde je řídit tok dat pomocí ovládacího prvku struktury, jako jsou podmíněné příkazy a smyčky a tak dále.

Tento dokument poskytuje základní příklad použití filtru zpráv. Další příklady, které používají filtry zpráv a model toku dat pro připojení blokům zpráv, najdete v článku [návod: vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) a [návod: vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md) .

## <a name="example"></a>Příklad

Vezměte v úvahu následující funkci `count_primes`, který ukazuje základní použití blok zpráv, který není filtrovat příchozí zprávy. Připojí prvočísel do bloku zpráv [std::vector](../../standard-library/vector-class.md) objektu. `count_primes` Funkce odešle několik čísel do bloku zpráv, přijímá výstupní hodnoty z bloku zpráv a vytiskne těchto čísel, které jsou prime do konzoly.

[!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]

`transformer` Objekt zpracovává všechny vstupní hodnoty, ale vyžaduje jenom hodnoty, které jsou primární. I když se aplikace může být napsaná tak, aby odesílatel odešle jenom prvočísel, nemůže být vždy známé požadavky příjemce zprávy.

## <a name="example"></a>Příklad

Následující funkce `count_primes_filter`, provádí stejnou úlohu, jako `count_primes` funkce. Ale `transformer` objekt v této verzi používá funkci filtru tak, aby přijímal pouze hodnoty, které jsou primární. Funkce, která provede akci přijímá pouze prvočísel; Proto se nemá volat `is_prime` funkce.

Protože `transformer` objektu přijímá pouze prvočísel, `transformer` samotného objektu může obsahovat prvočísel. Jinými slovy `transformer` objekt v tomto příkladu není povinné pro přidání prvočísel k `vector` objektu.

[!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]

`transformer` Objekt nyní zpracovává jenom hodnoty, které jsou primární. V předchozím příkladu `transformer` objekt zpracovávat všechny zprávy. V předchozím příkladu proto musí být stejný počet zpráv, které se odešle. Tento příklad používá výsledek [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce k určení, kolik zpráv pro příjem z `transformer` objektu. `send` Vrací funkce `true` když vyrovnávací paměti zpráv přijme zprávu a `false` při vyrovnávací paměti zpráv odmítne zprávy. Počet pokusů, vyrovnávací paměti zpráv přijímá zprávy proto odpovídá počtu prvočísel.

## <a name="example"></a>Příklad

Následující kód ukazuje kompletní příklad. Příklad volá i `count_primes` funkce a `count_primes_filter` funkce.

[!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `primes-filter.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc základen filter.cpp**

## <a name="robust-programming"></a>Robustní programování

Funkce filtru může být funkce lambda, ukazatele na funkci nebo objektu funkce. Každá funkce filtru má jednu z následujících forem:

```Output
bool (T)
bool (T const &)
```

Chcete-li odstranit zbytečnému kopírování dat, používejte druhý formulář, pokud máte požadovaný typ agregace, která se přenášejí podle hodnoty.

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Postupy: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[transformer – třída](../../parallel/concrt/reference/transformer-class.md)
