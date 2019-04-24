---
title: Funkce usnadnění
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 1a1790a08403bcc1d016a39e27c7a121c288af4d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62185994"
---
# <a name="message-passing-functions"></a>Funkce usnadnění

Asynchronní knihovnou agentů poskytuje několik funkcí, které umožňují předávání zpráv mezi součástmi.

Tyto funkce předávání zpráv se používají s různými typy bloku zpráv. Další informace o typech bloku zpráv, které jsou definovány pomocí modulu Runtime souběžnosti, naleznete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

##  <a name="top"></a> Oddíly

Toto téma popisuje následující funkce předávání zpráv:

- [odesílání a asend –](#send)

- [přijímat a try_receive –](#receive)

- [Příklady](#examples)

##  <a name="send"></a> odesílání a asend –

[Concurrency::send](reference/concurrency-namespace-functions.md#send) funkce odešle zprávu do zadané cílové synchronně a [concurrency::asend](reference/concurrency-namespace-functions.md#asend) funkce odešle zprávu do zadané cílové asynchronně. Jak `send` a `asend` funkce Počkejte, až cílový označuje, že bude nakonec přijmout nebo odmítnout zprávu.

`send` Funkce počká, až cílový přijme nebo odmítne zprávy ještě před jeho vrácením. `send` Vrací funkce **true** Pokud byla zpráva doručena a **false** jinak. Vzhledem k tomu, `send` funkce pracuje synchronně, `send` funkce čeká na cíl, který chcete zobrazit zpráva, před jeho vrácením.

Naopak `asend` funkce nečeká cíl, který chcete přijmout nebo odmítnout zprávu, před jeho vrácením. Místo toho `asend` vrací funkce **true** Pokud cíl přijme zprávu a bude nakonec trvat. V opačném případě `asend` vrátí **false** k označení, že cíl odmítl zprávu, nebo odloženo rozhodnutí o tom, jestli se zpráva.

[[Horní](#top)]

##  <a name="receive"></a> přijímat a try_receive –

[Concurrency::receive](reference/concurrency-namespace-functions.md#receive) a [concurrency::try_receive](reference/concurrency-namespace-functions.md#try_receive) funkce čtou data z daného zdroje. `receive` Funkce čeká data k dispozici, že `try_receive` funkce vrátí hodnotu okamžitě.

Použití `receive` fungovat v případě, že musíte mít data, abyste mohli pokračovat. Použití `try_receive` fungovat, pokud nesmí blokovat aktuální kontext nebo nemusíte mít data, abyste mohli pokračovat.

[[Horní](#top)]

##  <a name="examples"></a> Příklady

Příklady, které používají `send` a `asend`, a `receive` funkce, najdete v následujících tématech:

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Postupy: Implementace různých vzorů producent–příjemce](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [Postupy: Poskytování pracovních funkcí třídám call a transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [Postupy: Použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [Postupy: Výběr z dokončených úloh](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [Postupy: Odesílání zpráv v pravidelných intervalech](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [Postupy: Použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[Horní](#top)]

## <a name="see-also"></a>Viz také:

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Send – funkce](reference/concurrency-namespace-functions.md#send)<br/>
[asend – funkce](reference/concurrency-namespace-functions.md#asend)<br/>
[Receive – funkce](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive – funkce](reference/concurrency-namespace-functions.md#try_receive)
