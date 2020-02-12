---
title: Funkce usnadnění
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 4e1052a59f355c4ad5a7c6b57724268c24a209b4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143288"
---
# <a name="message-passing-functions"></a>Funkce usnadnění

Knihovna asynchronních agentů poskytuje několik funkcí, které umožňují předávat zprávy mezi komponentami.

Tyto funkce předávání zpráv se používají s různými typy bloku zpráv. Další informace o typech bloků zpráv, které jsou definovány Concurrency Runtime, naleznete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="top"></a>Řezů

V tomto tématu jsou popsány následující funkce pro předávání zpráv:

- [Odeslat a asend](#send)

- [přijmout a try_receive](#receive)

- [Příklady](#examples)

## <a name="send"></a>Odeslat a asend

Funkce [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) odesílá zprávu do zadaného cíle synchronně a funkce [Concurrency:: asend](reference/concurrency-namespace-functions.md#asend) posílá zprávu do zadaného cíle asynchronně. Funkce `send` i `asend` čekají na to, dokud cíl neindikuje, že bude zprávu nakonec akceptovat nebo odmítnout.

Funkce `send` počká, dokud cíl nepřijme nebo odmítne zprávu před tím, než se vrátí. Funkce `send` vrátí **hodnotu true** , pokud byla zpráva doručena a jinak **false** . Vzhledem k tomu, že funkce `send` funguje synchronně, funkce `send` počká, než cíl obdrží zprávu, než se vrátí.

Naopak funkce `asend` nečeká na cíl přijmout nebo odmítnout zprávu předtím, než se vrátí. Místo toho funkce `asend` vrátí **hodnotu true** , pokud cíl přijme zprávu a nakonec ji převezme. Jinak `asend` vrátí **hodnotu false** , aby označovala, že cíl odmítl zprávu, nebo odložil rozhodnutí o tom, jestli se má zpráva provést.

[[Nahoře](#top)]

## <a name="receive"></a>přijmout a try_receive

Funkce [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) a [concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive) čtou data z daného zdroje. Funkce `receive` čeká na zpřístupnění dat, zatímco funkce `try_receive` vrátí hodnotu okamžitě.

Použijte funkci `receive`, pokud je nutné mít data, aby bylo možné pokračovat. Použijte funkci `try_receive`, pokud nesmíte blokovat aktuální kontext nebo nemusíte mít data, aby bylo možné pokračovat.

[[Nahoře](#top)]

## <a name="examples"></a>4.6

Příklady použití funkcí `send` a `asend`a `receive` funkce naleznete v následujících tématech:

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Postupy: Implementace různých vzorů producent–příjemce](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [Postupy: Poskytování pracovních funkcí třídám call a transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [Postupy: Použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [Postupy: Výběr z dokončených úloh](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [Postupy: Odesílání zpráv v pravidelných intervalech](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [Postupy: Použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[Nahoře](#top)]

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send – funkce](reference/concurrency-namespace-functions.md#send)<br/>
[asend – funkce](reference/concurrency-namespace-functions.md#asend)<br/>
[Receive – funkce](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive funkce](reference/concurrency-namespace-functions.md#try_receive)
