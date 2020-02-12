---
title: 'Postupy: Použití filtru bloku zpráv'
ms.date: 11/04/2016
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
ms.openlocfilehash: 074d3989ce48b0b6d69206e3f83c374a2ec65c93
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142807"
---
# <a name="how-to-use-a-message-block-filter"></a>Postupy: Použití filtru bloku zpráv

Tento dokument ukazuje, jak použít funkci filtru k povolení bloku asynchronní zprávy přijmout nebo odmítnout zprávu na základě datové části této zprávy.

Při vytváření objektu bloku zprávy, například [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), [Concurrency:: Call](../../parallel/concrt/reference/call-class.md)nebo [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md), můžete zadat *funkci filtru* , která určuje, zda blok zpráv přijímá nebo odmítá zprávu. Funkce filtru je užitečný způsob, jak zaručit, že blok zpráv přijímá pouze určité hodnoty.

Funkce filtru jsou důležité, protože umožňují připojit bloky zpráv pro vytvoření *sítí toku*dat. V síti toku dat ovládací prvky pro řízení toku dat zpracovávají pouze zprávy, které splňují určitá kritéria. Porovnejte je s modelem toku řízení, kde je tok dat regulován pomocí řídicích struktur, jako jsou podmíněné příkazy, smyčky a tak dále.

Tento dokument poskytuje základní příklad použití filtru zpráv. Další příklady, které používají filtry zpráv a model toku dat pro připojení bloků zpráv, najdete v tématu [Návod: Vytvoření agenta toku](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) dat a [Návod: vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

## <a name="example"></a>Příklad

Vezměte v úvahu následující funkci `count_primes`, která znázorňuje základní použití bloku zprávy, který nefiltruje příchozí zprávy. Blok zpráv připojí prvočísla k objektu [std:: Vector](../../standard-library/vector-class.md) . Funkce `count_primes` odesílá do bloku zpráv několik čísel, přijímá výstupní hodnoty z bloku zpráv a tiskne tato čísla do konzoly.

[!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]

Objekt `transformer` zpracovává všechny vstupní hodnoty; Nicméně vyžaduje pouze ty, které jsou primární. I když může být aplikace napsaná tak, aby odesílatel zprávy odesílal pouze prvočísla, požadavky na přijímače zpráv nemohou být vždy známy.

## <a name="example"></a>Příklad

Následující funkce `count_primes_filter`provede stejnou úlohu jako funkce `count_primes`. Objekt `transformer` v této verzi však používá funkci filtru k přijetí pouze těch hodnot, které jsou hlavní. Funkce, která provádí akci, přijímá pouze hlavní čísla. proto nemusí volat funkci `is_prime`.

Vzhledem k tomu, že objekt `transformer` přijímá pouze čísla primárních objektů, může pole `transformer` sám obsahovat hlavní čísla. Jinými slovy, objekt `transformer` v tomto příkladu není vyžadován pro přidání apostrofů do objektu `vector`.

[!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]

Objekt `transformer` nyní zpracovává pouze ty hodnoty, které jsou hlavní. V předchozím příkladu `transformer` objekt zpracovává všechny zprávy. Proto předchozí příklad musí přijmout stejný počet zpráv, které odesílá. Tento příklad používá výsledek funkce [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) k určení počtu zpráv, které mají být přijímány z objektu `transformer`. Funkce `send` vrátí **hodnotu true** , pokud vyrovnávací paměť zprávy akceptuje zprávu a **hodnotu false** , pokud se zpráva odmítne do vyrovnávací paměti. Proto počet pokusů, kolikrát vyrovnávací paměť zpráv akceptuje zprávu, odpovídá počtu primárních čísel.

## <a name="example"></a>Příklad

Následující kód ukazuje kompletní příklad. V příkladu je volána funkce `count_primes` a funkce `count_primes_filter`.

[!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `primes-filter.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc PRIMES-Filter. cpp**

## <a name="robust-programming"></a>Robustní programování

Funkce Filter může být funkce lambda, ukazatel na funkci nebo objekt funkce. Každá funkce filtru má jednu z následujících forem:

```Output
bool (T)
bool (T const &)
```

Chcete-li eliminovat zbytečné kopírování dat, použijte druhý formulář, pokud máte agregovaný typ, který je přenášen hodnotou.

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Postupy: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[transformer – třída](../../parallel/concrt/reference/transformer-class.md)
