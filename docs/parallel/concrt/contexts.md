---
title: Kontexty
ms.date: 11/04/2016
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
ms.openlocfilehash: d511f8fa751d61c3c490a184dae660096dd9f76f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148338"
---
# <a name="contexts"></a>Kontexty

Tento dokument popisuje roli kontextech v modulu Runtime souběžnosti. Podproces, který je připojen k plánovače se označuje jako *kontextu spuštění*, nebo jen *kontextu*. [Concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkce a souběžnost::[třídy kontextu](../../parallel/concrt/reference/context-class.md) vám umožňují řídit chování kontexty. Použití `wait` funkce pozastavení aktuální kontext pro určitou dobu. Použití `Context` třídy, když potřebujete větší kontrolu nad při kontexty blokovat, odblokovat a pozastavit nebo pokud chcete přidělit nadměrnému počtu procesů aktuálního kontextu.

> [!TIP]
>  Poskytuje výchozí plánovač Concurrency Runtime, a proto není nutné vytvořit ve vaší aplikaci. Vzhledem k tomu, že Plánovač úloh umožňuje optimalizovat výkon vašich aplikací, doporučujeme začít s [knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) máte nového modulu runtime souběžnosti.

## <a name="the-wait-function"></a>Wait – funkce

[Concurrency::wait](reference/concurrency-namespace-functions.md#wait) kooperativně předá vykonávání aktuální kontext pro zadaný počet milisekund, funkce. Modul runtime používá k provádění další úloh čas yield. Po uplynutí zadané doby, modul runtime přeplánuje kontext spuštění. Proto `wait` funkce může pozastavit delší než hodnota zadaná pro aktuální kontext `milliseconds` parametr.

Předejte 0 (nula) `milliseconds` parametr způsobí, že modul runtime pro dočasné pozastavení aktuálního kontextu, dokud všech ostatních kontextech aktivní jsou příležitost k provedení práce. To umožňuje pozastavit úlohu pro všechny ostatní aktivní úlohy.

### <a name="example"></a>Příklad

Příklad, který se používá `wait` funkce výnosu z aktuálního kontextu a tím umožní jiných kontextů provést, najdete v článku [jak: Použití skupin plánů k ovlivnění pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="the-context-class"></a>Třídy kontextu

Souběžnost::[třídy kontextu](../../parallel/concrt/reference/context-class.md) poskytuje programovací abstrakce pro kontext spuštění a nabízí dvě důležité funkce: možnost spolupráce při blokovat, odblokovat a výnosu z aktuálního kontextu a možnost přidělit nadměrnému počtu procesů aktuálního kontextu.

### <a name="cooperative-blocking"></a>Spolupráce blokování

`Context` Třída umožňuje blokovat nebo pozastavit aktuální kontext spuštění. Blokování nebo získávání je užitečné při aktuálním kontextu nemůže pokračovat, protože prostředek není k dispozici.

[Concurrency::Context::Block](reference/context-class.md#block) metoda blokuje aktuální kontext. Kontext, který je blokovaný provede jeho zpracování prostředků tak, aby modul runtime můžete provádět další úlohy. [Concurrency::Context::Unblock](reference/context-class.md#unblock) metoda odblokuje kontext blokované. `Context::Unblock` Metoda musí být volána v jiném kontextu než ten, který volá `Context::Block`. Modul runtime vyvolá [concurrency::context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) Pokud pokusí odblokovat samotný kontext.

Spolupráce při blokovat a odblokovat kontextu, obvykle zavoláte [concurrency::Context::CurrentContext](reference/context-class.md#currentcontext) níž načítají ukazatel na `Context` objekt, který je spojen s aktuálním vláknem a uložit výsledek. Poté je zapotřebí zavolat `Context::Block` metoda blokování aktuálního kontextu. Později, volání `Context::Unblock` ze samostatné kontextu odblokujete kontextu blokované.

Každý pár volání musí odpovídat `Context::Block` a `Context::Unblock`. Modul runtime vyvolá [concurrency::context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) při `Context::Block` nebo `Context::Unblock` metoda je volána po sobě jdoucích bez odpovídajícího volání jiné metody. Ale není potřeba volat `Context::Block` před voláním `Context::Unblock`. Například, pokud jeden kontext volání `Context::Unblock` před další volání kontextu `Context::Block` stejného kontextu, zůstane tento kontext odblokované.

[Concurrency::Context::Yield](reference/context-class.md#yield) metoda předá vykonávání, tak, aby modul runtime můžete provádět další úlohy a následně přeplánovat kontext spuštění. Při volání `Context::Block` metody, modul runtime není přeplánovat kontextu.

#### <a name="example"></a>Příklad

Příklad, který se používá `Context::Block`, `Context::Unblock`, a `Context::Yield` metody k implementaci třídy semaforu pro spolupráci, viz [jak: Použití třídy kontextu pro implementaci semaforu pro spolupráci](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

##### <a name="oversubscription"></a>Překryvný odběr

Výchozí plánovač vytváří stejný počet vláken, jsou k dispozici hardwarových vláken. Můžete použít *překryvného odběru* vytvořit další vlákna pro daný hardware vlákno.

Pro výpočetně náročných operací překryvného odběru obvykle nejsou adekvátní protože zavádí další režie. Ale pro úlohy, které mají vysoké množství latence, například čtení dat z disku nebo ze síťového připojení, překryvného odběru může zlepšit celkové efektivity některé aplikace.

> [!NOTE]
>  Povolte překročení stanovených pouze z vlákna, které bylo vytvořeno pomocí modulu Runtime souběžnosti. Kompenzujte nemá žádný vliv, pokud se volá z vlákna, která nebyla vytvořena modulu runtime (včetně hlavní vlákno).

Chcete-li povolit překročení stanovených v aktuálním kontextu, zavolejte [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) metodu `_BeginOversubscription` parametr nastaven na **true**. Když povolíte překročení stanovených ve vlákně, které bylo vytvořeno pomocí modulu Runtime souběžnosti, způsobí, že modul runtime vytvořte jedno další vlákno. Za všechny úkoly, které vyžadují překryvného odběru dokončit, volání `Context::Oversubscribe` s `_BeginOversubscription` parametr nastaven na **false**.

Můžete povolit překročení stanovených více než jednou z aktuálního kontextu, ale je nutné jej vypnout stejný počet případů, kdy ji povolit. Překryvný odběr také může být vnořena; To znamená úkol, který je vytvořen jinou úlohou, která používá překryvného odběru můžete také přidělit nadměrnému počtu procesů jeho kontextu. Nicméně pokud vnořená úloha a její nadřazené patří do stejného kontextu, pouze nejkrajnější volání `Context::Oversubscribe` způsobí vytvoření další vlákno.

> [!NOTE]
>  Modul runtime vyvolá [concurrency::invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) Pokud více úloh než je zakázaná, předtím, než je povolené.

###### <a name="example"></a>Příklad

Příklad použití překryvného odběru latence, jež je způsobena čtení dat z připojení k síti, najdete v části [jak: Latence vytvořením nadbytečného](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

## <a name="see-also"></a>Viz také:

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Postupy: Použití skupin plánů k ovlivnění pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[Postupy: Použití třídy kontextu pro implementaci semaforu pro spolupráci](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Postupy: Kompenzace latence vytvořením nadbytečného počtu vláken](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)
